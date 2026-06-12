---
title: "manual css override, when external css exists"
date: 2010-01-15
forum: General Help
---

### Post by readycarpenter on 2010-01-15
I have an external css file
with...
```
#bg {
	margin:0 auto;
	padding:0;
	background:transparent ;
	background-image: url( bg.jpg ) ;
 	background-repeat:no-repeat;	
	background-position: center top ;
}

```
in my html i use
```
<div id="bg">
```

it works fine, but I want to manually override the background image without changing the external css

---

### Post by aklo on 2010-01-15
<html>
<head>
<link rel="stylesheet" type="text/css" href="default.css">
<style type="text/css">
#bg {
	margin:0 auto;
	padding:0;
	background:transparent ;
	background-image: url( bg.jpg ) ;
 	background-repeat:no-repeat;	
	background-position: center top ;
}

</style>
</head>

Place it IN your html file.

This is called internal css.

There is another method called inline css.

<div style="background-image:url(bg.jpg);">


External 
Internal (This overrides external)
Inline (This overrides the above 2)





</html>

---

### Post by readycarpenter on 2010-01-15
thank you, inline is what i was looking for. this worked for only overriding the background-image

```
        <div id="bg" style="background-image:url(bg.jpg);">
```

---

