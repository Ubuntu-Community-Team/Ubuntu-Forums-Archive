---
title: "Terminal nested quotes"
date: 2009-10-30
forum: General Help
---

### Post by temp4746 on 2009-10-30
How do I do nested quotes in a Linux Terminal for example in the case of:
gksu "mount ..." 
If I need to use some argument that requires quotes.
(gksu doesnt work well without quotes on commands with arguments)

---

### Post by Lekensteyn on 2009-10-30
Not sure, but I think it's adding escape quotes like:
```
command "after this a nested quote\" just quoted"
```

---

### Post by sisco311 on 2009-10-30
use single quotes:
```
gksu  "mount /dev/sdXY '/media/Program Files'"
```

or if you are using karmic, use pkexec instead of gksu:
```
pkexec mount /dev/sdXY "/media/My Files"
```

---

### Post by temp4746 on 2009-10-30
> **Lekensteyn said:**
> Not sure, but I think it's adding escape quotes like:
```
command "after this a nested quote\" just quoted"
```
This will make it print " as a character without any special meaning which i need to preserve for using it for command arguments.
 
> **sisco311 said:**
> use single quotes:
```
gksu  "mount /dev/sdXY '/media/Program Files'"
```
 
or if you are using karmic, use pkexec instead of gksu:
```
pkexec mount /dev/sdXY "/media/My Files"
```
Thanks this works. :)

---

