## Copy paste filter label (can retain the specified label)
#### HTML code
```html
<div class="con" contenteditable="true"></div>
```
#### JS code
```javascript
$(".con").bind("paste", function(){
			var _this = $(this);
			setTimeout(function(){				
				var con = _this.html();				
				var i, match;
				match = con.match(/<[^>]+>/gi);
	            if (match) {
	                for (i in match) {
	                    if (!match[i].match(/<(input|div|br).*?(?:>|\/>)/gi)) {
	                        con = con.replace(match[i], '');
	                    }
	                }
	            }
	            match = con.match(/{[^}]+}/gi);
	            if (match) {
	                for (i in match) {
	                    if (!match[i].match(/<(input|div|br).*?(?:>|\/>)/gi)) {
	                        con = con.replace(match[i], '');
	                    }
	                }
	            }
				_this.html(con);
			}, 30)
		})
