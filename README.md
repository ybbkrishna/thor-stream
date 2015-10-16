# thor-stream

# ![thor-strem](img/thor-stream.gif)
---

Unended Stream, useful for piping streams one after another


## doc

<a name="thorStream"></a>
## thorStream(on, setting) ⇒ <code>stream</code>
Creates a writable and readable stream

**Kind**: global function  
**Returns**: <code>stream</code> - a simplified stream  
**Write**: <code>function</code> on write function  

| Param | Type | Description |
| --- | --- | --- |
| on | <code>end</code> | end function |
| setting | <code>options</code> | autoDestroy will destory stream once stream ended defaults to true,                     setting thorMode will keep the stream stay long [:iywim:] |



## usage

```
var urls = ['http://x', 'http://y'];

function requestUrl(scrollId, stream) {
    var url = 'http:// sss' + scrollId;
    return request(url)
        .pipe(JSONStream.parse('hits.hits.*'))
        .pipe(stream);
}

var stream = thorStream(function write(data) {
        count++;
        this.emit('data', data);
    },
    function end () {
        //ending the stream if no data received for this
        if(count === 0) {
            this.endThor();
            this.emit('end');
            return;
        }
        count = 0;
        requestUrl(scrollId, stream);
    });

```