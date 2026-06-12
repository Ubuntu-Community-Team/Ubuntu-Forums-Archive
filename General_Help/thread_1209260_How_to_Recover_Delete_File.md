---
title: "How to Recover Delete File"
date: 2009-07-10
forum: General Help
---

### Post by mthalis on 2009-07-10
I open nautilus browser. while i using that my important data file delete. so how can i restore that file. Normally it goes to trash but i couldn't find any file in trash. please help.

---

### Post by earthpigg on 2009-07-10
if this is a really critical file, it is imperative you stop booting from/using that hard drive/partition immediately. anything saved -- temporary files, a firefox bookmark, anything -- lowers the chances of recovering that file.

restart the computer and boot from a live CD. right now. until you either give up on recovering the file or successfully recover it, the live cd is your new operating environment. if you have a dual boot system set up with windows or another linux distro, that is ok too.

ill edit this post and add more information, but what i mentioned above needs to happen asap.

edit:

i am going to assume you have booted from the live CD at this point.

rather than reinvent the wheel, i am going to point you in the right direction:

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
and
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

i have used this successfully to recover 'deleted' files.

it is included in a number of dedicated data-recovery live CD's, or you can install it and use it from an ubuntu live cd:

```
sudo apt-get install testdisk
```

don't let the name 'photorec' mislead you -- it works on files other than images.

what type of file was it that you deleted? if it is supported by photorec (included when you install testdisk), then photorec may be the best route for you.

---

### Post by Hominym on 2009-07-10
Try looking in ~/.local/share/Trash/files

If it's not there, you can try using [Foremost]("http://foremost.sourceforge.net/").

---

### Post by mthalis on 2009-07-10
Thank Hominym You're method work.

---

### Post by Hominym on 2009-07-10
You're welcome.

---

### Post by earthpigg on 2009-07-10
i suppose i turned an ant-hill into a mountain. :D

---

