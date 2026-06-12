---
title: "Maverick: Can't share folder"
date: 2011-08-23
forum: General Help
---

### Post by jfed on 2011-08-23
Hello. I have a bit of, shall we say unconventional software on my Wii. And I would like to mark a folder as shared so I can access it over my network and play back media files. I have done this before, and the process on Ubuntu is fairly simple. All I have to do is right click the folder in Ubuntu, go to properties, and go to the Share tab, check the box "Share this folder" then click the Create Share button. Great, easy. Only issue is, for some reason when I do that, I get this error.

[IMG]http://img820.imageshack.us/img820/3580/thingol.png[/IMG]

I have no idea how to proceed. How do I fix this?

Any input is appreciated, thanks in advance.

---

### Post by Morbius1 on 2011-08-23
Add the following package:
```
sudo apt-get install samba-common-bin
```Restart samba:
```
sudo service smbd restart
```OR
```
sudo service smbd start
```Then see if the error message goes away.

---

### Post by jfed on 2011-08-23
Thanks! I'll try that and report my findings back here.

---

### Post by jfed on 2011-08-23
Wow, haha it turns out that all I needed to do was run
```
sudo apt-get update && sudo apt-get upgrade
```

Guess I should have googled this before posting..:oops:

Thanks for your help anyway!

---

