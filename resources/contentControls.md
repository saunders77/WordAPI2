# ContentControls 
 Represents a a collection of ContentControl objects, on the specified scope.  

## Properties

None

## Relationships

None


## Methods


| Method     | Return Type    |Description|Notes  |
|:-----------------|:--------|:----------|:------|
|[`getById(id: string)`](#getbyid)| [ContentControl](contentControl.md) object |Returns the content control with the specified Id, returns null if the content control does not exist|  |
|[`getByName(name: string)`](#getbyname)| [ContentControls](contentControls.md) collection |Returns the collection of the content controls matching the specified name| Since there could be many Content Controls with the same name, this method returns a collection|  
|[`getByTag(tag: string)`](#getbytag)| [ContentControls](contentControls.md) collection |Returns the collection of the content controls matching the specified tag| Since there could be many Content Controls with the same name, this method returns a collection |


### Methods 

#### Examples

### getById

Gets the content control with the specified ID. 

#### Syntax

```js
var myContentContol = ctx.document.getByID(ccid);

```

#### Parameters 

Parameter      | Type   | Description
-------------- | ------ | ------------
`id`          | string | Required. Id of the content control.

#### Returns

[ContentControl](contentContol.md) object.

#### Examples

```js
// this is an example of inserting a content control then getting the content control by ID and changing its title. 
var ctx = new Word.WordClientContext();
var myContentControl = ctx.document.body.paragraphs.getItemAt(1).insertContentControl();
var myContentContolId = myContentControl.id;
ctx.executeAsync().then(
    function() {
    }
);


var myCC = ctx.document.contentControls.getById(myContentContolId);
ctx.load(myCC);
ctx.executeAsync().then(
    function () {
        var results = new Array();
    	 myCC.title = "this is the new title";
},  function (result) {
        console.log("Failed: ErrorCode=" + result.errorCode + ", ErrorMessage=" + result.errorMessage);
        console.log(result.traceMessages);
    }

);
```
[Back](#methods)


### getByName

Gets a collection of content controls with the same name/title.

#### Syntax
```js
var ccs = document.getByName("Customer Address");
```
#### Parameters

Parameter      | Type   | Description
-------------- | ------ | ------------
`name`          | string | Required. Name/title of the content control(s) to retrieve.

#### Returns

[ContentControls](contentControls.md) collection.


#### Examples

```js
var ccs = document.getByName("Address");
```
[Back](#methods)


### getByTag

Gets a collection of content controls with the same tag.

#### Syntax
```js
var ccs = document.getByTag("TagForName");
```
#### Parameters

Parameter      | Type   | Description
-------------- | ------ | ------------
`tag`          | string | Required. Tag of the content control(s) to retrieve.


#### Returns

[ContentControls](contentControls.md) collection.


#### Examples

```js
var ccs = document.getByTag("TagForName");
```
[Back](#methods)