---
title: "Help with unraring files"
date: 2009-07-27
forum: General Help
---

### Post by ztmike on 2009-07-27
I have a movie that I want to unrar, so I downloaded 7zip and I right-click 1 of the rar files and click on "extract here" and I get this error

[IMG]http://img339.imageshack.us/img339/407/21031232.png[/IMG]

Any ideas on what I need to do?

---

### Post by credobyte on 2009-07-27
Install unrar:
```
sudo apt-get install unrar

```

Open archive with Archive Manager ( or Extract Here ) & you'll be fine :)

---

### Post by ztmike on 2009-07-27
So I don't need 7zip?

---

### Post by credobyte on 2009-07-27
> **ztmike said:**
> So I don't need 7zip?

7zip is a command line utility and you can't use it by pressing Extract Here ( as it's a command from Archive Manager, which is another tool, independent from 7zip ).
I haven't found a single file I wouldn't be able to extract with unrar, so .. no, you don't need it :)

---

### Post by ztmike on 2009-07-27
Thanks it worked..kinda scared me though for a second..when it was done installing via terminal my screen blinked and I lost all my desktop effects ..a reboot got them back though.

---

