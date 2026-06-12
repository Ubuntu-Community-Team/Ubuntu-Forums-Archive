---
title: "Grub Rescue"
date: 2010-01-10
forum: General Help
---

### Post by galchen on 2010-01-10
i managed to cause some damage by deleting a partition which im not using.
 
i have one hard drive with sda1 for windows and sda2 extended into 4 partitions.
 
i removed one of the extended partitions and now when grub loads on boot i get into grub menu.
i get:
error: unknown filesystem
 
grub rescue> ls
(hd0) (hd0,7) (hd0,6) (hd0,5) (hd0,3) (hd0,1) (fd0) (fd1)
 
the (fd0) and (fd1) are not loaded immidiately, it takes about 1 or 2 seconds after the (hdx,y) are loaded, and when it loads the (fd) it says error: no such disk
 
set:
prefix=(hd0,7)
root=hd0,7
 
any idea?

---

### Post by Brandon Williams on 2010-01-10
[Here](https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode) is a bunch of useful information about how to boot into your installed system from the Grub command prompt. [This post](http://ubuntuforums.org/showthread.php?t=1195275) has a section titled 'Booting from the Rescue Mode' that gives a brief runthrough without as much detail as the first link.

Once you have used the information in those sources to boot into your installed system, run 'sudo grub-install /dev/sda && sudo update-grub' to reinstall grub to the MBR and rebuild your grub.cfg file. Hopefully that will get you back to a bootable if state.

If any of the above doesn't work, let us know and we can offer more help.

---

### Post by blueridgedog on 2010-01-10
What version of grub and Ubuntu are you using?  The solution is very different if you have the version of grub that came with a clean install of 9.10.

---

### Post by Leppie on 2010-01-10
> **galchen said:**
> 
i get:
error: unknown filesystem
 
grub rescue> ls
(hd0) (hd0,7) (hd0,6) (hd0,5) (hd0,3) (hd0,1) (fd0) (fd1)
 
the (fd0) and (fd1) are not loaded immidiately, it takes about 1 or 2 seconds after the (hdx,y) are loaded, and when it loads the (fd) it says error: no such disk
 
set:
prefix=(hd0,7)
root=hd0,7
 
any idea?
try this:
```
set root=hd0,6
```

---

