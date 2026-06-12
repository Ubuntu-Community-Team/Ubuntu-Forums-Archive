---
title: "Ubuntu - Error while installing any software/package."
date: 2010-02-01
forum: General Help
---

### Post by johnvit on 2010-02-01
I am newbie in ubuntu. (Version 9.10) I get following error while installing any software from the Ubuntu Software Center.I also get same error while I update ubuntu from Ubuntu Update Center.

Any help??

[IMG]http://img109.imageshack.us/img109/5210/screenshot3yp.png[/IMG]

---

### Post by HiImTye on 2010-02-01
try entering this into the terminal:
```
sudo apt-get update
```

---

### Post by johnvit on 2010-02-01
> **HiImTye said:**
> try entering this into the terminal:
```
sudo apt-get update
```


Thanks for reply.But it didn't help at all.It rapidly displayed some list.But didn't help at all.Any other help?

---

### Post by HiImTye on 2010-02-01
it just re-downloaded your package lists

try this
```
sudo apt-get remove tzdata && sudo apt-get upgrade && sudo apt-get install tzdata
```

edit: backup your files first, who knows how dependant on tzdata ubuntu is (shrug)

---

### Post by johnvit on 2010-02-01
> **HiImTye said:**
> it just re-downloaded your package lists

try this
```
sudo apt-get remove tzdata && sudo apt-get upgrade && sudo apt-get install tzdata
```

edit: backup your files first, who knows how dependant on tzdata ubuntu is (shrug)

Thanks again.But its kinda embarrassing.Its giving the same error again.
```
Reading database ... 25%dpkg: unrecoverable fatal error, aborting:
 files list file for package 'tzdata' is missing final newline
E: Sub-process /usr/bin/dpkg returned an error code (2)
```

---

### Post by jerrrys on 2010-02-01
try a different download site?

---

### Post by johnvit on 2010-02-01
How can I do that?

---

### Post by Swagman on 2010-02-01
Is  "Universe & Multiverse" enabled in software sources ?

Also you can change download location

[img]http://www.upload3r.com/serve/010210/1265038120.jpeg[/img]

---

### Post by johnvit on 2010-02-01
> **Swagman said:**
> Is  "Universe & Multiverse" enabled in software sources ?

Being a newbie, I don't know what u are talking abt.Can u please explain how to check that?
Thanks.

---

### Post by Swagman on 2010-02-01
> **johnvit said:**
> Being a newbie, I don't know what u are talking abt.Can u please explain how to check that?
Thanks.

Click [**THIS LINK** ]( http://www.upload3r.com/serve/010210/1265038427.jpeg)

for a screengrab (It's too big to embed on here)

---

### Post by johnvit on 2010-02-01
> **Swagman said:**
> Click [**THIS LINK** ]( http://www.upload3r.com/serve/010210/1265038427.jpeg)

for a screengrab (It's too big to embed on here)

It is enabled.What next now?

---

### Post by jerrrys on 2010-02-01
if your in the states, change it to this one, its a good one...

[ATTACH]145628[/ATTACH]

---

