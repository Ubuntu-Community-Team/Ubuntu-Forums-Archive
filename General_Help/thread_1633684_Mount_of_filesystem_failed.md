---
title: "Mount of filesystem failed?"
date: 2010-11-29
forum: General Help
---

### Post by Freddyg1912345 on 2010-11-29
I know there are probably thousands of threads on this but here goes...

I'm running Ubuntu 9.10 on a dell desktop from idk when, its fairly old but regardless it was all running fine until about a week ago I got the infamous:

Mount of filesystem failed.
A maintenance shell will now be started.
Control-D will terminate this shell and start a new one.
admin@ or whatever it is you get the point.

I've been trying all the possible solutions I could find and nothing seems to work. I just want to be able to use this computer. I don't care if I lose files, or have to re-install Ubuntu or any of that, if I can just get the thing running again. I've tried re-installing, and booting from the disc etc. none of which have worked. Basically, I just want to erase Ubuntu and re-install it. Any help on how to do this would be great. 

Thanks,
Fred.

---

### Post by thisjew on 2010-11-29
are u sure the drive has not failed? had that happen on an old system awhile back?
try fdisk or  cfdisk /dev/sda or what ever your disk is to see if cfdisk can see it....:o

you stated you don't care if data is lot  maybe easier to reinstall.

---

### Post by Freddyg1912345 on 2010-11-29
> **thisjew said:**
> are u sure the drive has not failed? had that happen on an old system awhile back?
try fdisk or  cfdisk /dev/sda or what ever your disk is to see if cfdisk can see it....:o

you stated you don't care if data is lot  maybe easier to reinstall.

yeah, I can't even get it reinstall, I'll give what you said a try and see what happens.

---

### Post by wojox on 2010-11-29
You should be in Root.
Just execute this command
```
fsck
```
Yes that's all. After this command it will ask you to auto-fix file-system problems. Give "yes or y" . And then it will say "I finished my job, restart computer"
type
```
sudo shutdown -r now
```
And it is finished.
I hope it solves your problem too.

---

