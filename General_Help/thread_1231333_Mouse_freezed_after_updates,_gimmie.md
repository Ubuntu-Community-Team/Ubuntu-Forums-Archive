---
title: "Mouse freezed after updates, gimmie"
date: 2009-08-04
forum: General Help
---

### Post by afrodeity on 2009-08-04
My mouse started acting strangely last night. It now freezes. I tried reinstalling the xorg.conf backup, but nothing changed. I also removed gimmie which I installed along with a lot of updates over the weekend. Still nothing changed. Frozen. Did an apt-get remove of gimmie, but probably should have done a purge first. Any help debugging? How to get mouse working again?

---

### Post by afrodeity on 2009-08-04
Well don't all rush. Its not a hardware problem, because I booted with a live disk and mouse fine. I tried the following 
```
 dmesg |tail
psmouse.c: bad data from KBC - timeout
psmouse.c: wheelmouse at ISA0060/Serio1/Input0 lost synchronisation, throwing 1byte away
psmouse.c: resync failed, issuing reconnect request 
```
A few people have reported the KBC mouse spasm and freeze problem. Can't post the links, because I writing this from a console :) Followed two leads. One suggested I reinstall hal, aptitude reinstall hal. Nothing changed. Other suggested it could be kernal problem. In fact there was a major kernal update over weekend, so tried booting with an older kernal. No give. Don't see why I should have to replace the mouse all of a sudden, any help appreciated.

---

### Post by afrodeity on 2009-08-04
Solved. And nobody around to celebrate. 

The dmesg | tail should have alerted me to what I was looking for. Okay, so the data from the mouse was getting corrupted. So what? A lot of people simply went looking for a new mouse. Or trashed Ubuntu. 

When in doubt, lsmod 

Which should confirm the problem.

But what you really want to do is remove the offending module, which is of course *psmouse*, and reload. Easier said than done.

I tried a number of combinations including **rmmod psmouse**, but this worked:

```
modprobe -r psmouse 
```

then

```
modprobe psmouse
```

if the above still not working try to strip the versioning information from the module which might stop it from loading.

```
modprobe -f psmouse
```

I guess the problem in my case was the versioning change with the last round of updates. I did notice some rather strange moves in the versioning of the linux headers, and it has affected the whole system, so even if I tried to load an older kernal, the versioning of the psmouse prevented it from loading properly. Hence the failure to resynch. Somebody should build in a reversioning module into the kernal, so that Ubuntu self-heals!

---

