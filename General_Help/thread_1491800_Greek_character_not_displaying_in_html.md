---
title: "Greek character not displaying in html"
date: 2010-05-24
forum: General Help
---

### Post by strider22 on 2010-05-24
I have the greek XI character (the 3 bars) in a title in an html file as;
<h1>&#926;JSF&#926;</h1>
but when saved by gedit and pulled up in firefox it shows;
ÎžJSFÎž

Could you offer suggestions as to how to fix this please.

I think this is a firefox or Ubuntu problem rather than gedit because when I go into vim it shows &#926;JSF&#926;.

It could be the css;
	body {
		font-family:arial,helvetica,sans-serif;
		font-size:12px;
	}
----------------------

Solved;
I put in unicode sequences of &#x039E; and that worked fine without adding any font family to the css. So now the line is;

<h1>&#x039E;JSF&#x039E;</h1>

---

### Post by simosx on 2010-05-25
The proper solution is to configure the webpage (or even the web server) to specify that the default encoding is UTF-8 (Unicode).

In a nutshell, add 
> <meta http-equiv="Content-Type" content="text/html; charset=utf-8">

in the <head></head> section of the HTML file.

See [http://tlt.its.psu.edu/suggestions/international/web/tips/declare.html](http://tlt.its.psu.edu/suggestions/international/web/tips/declare.html)
for more details.

---

