---
title: "gedit doesn't save ä,ö properly"
date: 2006-04-06
forum: General Help
---

### Post by Ragazzo on 2006-04-06
When I write a html file with gedit and then view this page with Firefox, all ä's and ö's have changed into Ã¤ Ã¶. How can I fix this?

---

### Post by Sajjen on 2006-04-06
HTML is not supposed to contain non-standard characters such as å, ä and ö. You should write them as &aring; &auml; and &ouml;
You could probably get it to display correctly by setting the charset of the HTML document, but it's not the correct way to do it. A tip is to check out W3C's validation service at [http://validator.w3.org/](http://validator.w3.org/).

---

### Post by engla on 2006-04-06
No forget entities like &auml;, html entities should be a thing of the past.

Gedit saves your document by default as utf-8. Declare that in your [X]HTML:

in the <head> tag:

```
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
```

---

### Post by Ragazzo on 2006-04-06
Thanks. The meta-tag works.

---

### Post by TheApe on 2006-05-09
Is there a way to replace html special entities?
I know bluefish does it, but you have to select the text you want it to be done.
Dreamweaver is able to find and replace it in a lot of files.
Is there a tool for it in linux?

---

