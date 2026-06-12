---
title: "Newbie:Installed Ubuntu on Virtualbox how to access files?"
date: 2010-07-27
forum: General Help
---

### Post by steve1040 on 2010-07-27
Hi all,
I installed Ubuntu on my Win7 machine into a Virtuebox environment.
 
So now I want to place a script that I have within the Ubuntu world. How do I make a folder within my Window 7 world read/writable to my Ubuntu install?
 
Thanks

---

### Post by CharlesA on 2010-07-27
I think you can use the "shared folder" feature on virtualbox.

EDIT: I got it working, for linux, you basically have to mount the share from a terminal like so:

```
sudo mount -t vboxsf [-o OPTIONS] sharename mountpoint
```

replace sharename with the name of the share
replace mountpoint with the path to where you want it mounted

---

