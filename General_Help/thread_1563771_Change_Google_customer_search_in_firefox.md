---
title: "Change Google customer search in firefox"
date: 2010-08-29
forum: General Help
---

### Post by slooksterpsv on 2010-08-29
Ok so I have Mint on my computer as a separate partition and that and Firefox uses a custom search layout for google searches. I've tried searching on how to remove this or change it to default google and that, but I'm unable to find it. I think my keywords are off.

So does anyone know how to change it?

---

### Post by slooksterpsv on 2010-08-29
Found it after searching my computer, here's how to do it (to get the regular search back):
Open Terminal via Applications -> Accessories -> Terminal
Type in the following:
```

gksudo gedit /usr/lib/firefox-addons/searchplugins/en-US/google.xml

```

And remove the line, not typing in the value as it's way long and may differ:
[php]
 <Param name="cx" value="..."/>
[/php]
And change the line:
[php]
<Url type="text/html" method="GET" template="http://www.google.com/cse">
[/php]
to
[php]
<Url type="text/html" method="GET" template="http://www.google.com/search">
[/php]

Next restart firefox and you're done.

---

