D3 Node Editor [![Build Status](https://travis-ci.org/Ni55aN/D3-Node-editor.svg?branch=master)](https://travis-ci.org/Ni55aN/D3-Node-editor)
====
#### JavaScript library 
![node editor](https://codepen.io/Ni55aN/pen/jBEKBQ/image/large.png)

### Dependencies
  - [D3.js](https://github.com/d3/d3)
  - [d3-extended](https://github.com/wbkd/d3-extended)

### Usage
Download the library and styles. Include it in your html.
```html
<script src="js/node-editor.min.js"></script>
<link  href="css/node-editor.css" rel="stylesheet" type="text/css"></link>
```
Create needed sockets
```js
var numSocket = new D3NE.Socket('number', 'Number value', 'hint');
var imageSocket = new D3NE.Socket('image', 'Image', 'hint');
```
Define them styles
```css
.socket.number{
    fill: #96b38a
}
.socket.image{
    fill: #cc2a6a
}
```
Create some NodeBuilder's
```js
var texturebuilder = new D3NE.NodeBuilder("Texture",function(){
            var out = new D3NE.Output("Texture",imageSocket);
            return new D3NE.Node("Texture")
                        .addOutput(out);
         });
         
var shapebuilder = new D3NE.NodeBuilder("Shape",function(){
            var input = new D3NE.Input("Texture",imageSocket);
            var out = new D3NE.Output("Value",numSocket);
            return new D3NE.Node("Shape")
            	    	.addInput(input)
                        .addOutput(out);			
            });
```
And create NodeEditor
```js
 var nodeEditor = new D3NE.NodeEditor('nodeEditor', 
                        [shapebuilder,texturebuilder],
                        new D3NE.Events());
```
For detail see [demo](https://codepen.io/Ni55aN/pen/jBEKBQ)


License
----
MIT