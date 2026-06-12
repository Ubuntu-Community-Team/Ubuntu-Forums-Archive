---
title: "gnome virtual filesystem issues"
date: 2006-05-19
forum: General Help
---

### Post by manannan on 2006-05-19
To cut a long story short,

```
mihai@noun:/tmp$ gnomevfs-info Lecture04.pdf | head -n4
Name              : Lecture04.pdf
Type              : Regular
MIME type         : application/x-extension-pdf
Default app       : gpdf-usercustom.desktop
mihai@noun:/tmp$ gnomevfs-info -s Lecture04.pdf | head -n4
Name              : Lecture04.pdf
Type              : Regular
MIME type         : application/pdf
Default app       : evince.desktop
mihai@noun:/tmp$ grep "pdf" /usr/share/mime/globs
application/pdf:*.pdf
mihai@noun:/tmp$
```
It looks like fast MIME type detection is ignoring the setting in /usr/share/mime/globs -- and this is causing me a lot of grief. How do I fix this? Is there any place I can learn about gnome's handling of MIME types?

---

