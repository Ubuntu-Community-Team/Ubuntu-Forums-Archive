---
title: "Upgrading XP Pro to Windows 7 - need to repair GRUB"
date: 2009-07-22
forum: General Help
---

### Post by PsychedelicWonders on 2009-07-22
Hey guys, I am going to be upgrading to XP Pro to Windows 7 64.
 
Now both Ubuntu & windows are on the same HDD, but 2 different partitions.
 
Now I believe the entire HDD is NTFS.
 
I was told by the windows guys that by me doing the upgrade, it will over-write the Grub menu.
 
So how will I get my Grub menu back after the upgrade?
 
They also suggested using the Live Cd, which I have - but dont know how to do it.
 
I have a 20g partition for Ubuntu... this should be more than enough shouldnt it?

---

### Post by rbc on 2009-07-22
[http://www.supergrubdisk.org/w/index.php5?title=Boot_Problems](http://www.supergrubdisk.org/w/index.php5?title=Boot_Problems)

---

### Post by PsychedelicWonders on 2009-07-22
Man thats kind of an information overload.  I'm not that advanced yet...
 
Do I want to re-install Grub via bios, Live Cd, running it in the terminal... what is the easiest way?

---

### Post by PsychedelicWonders on 2009-07-22
I'm hoping to upgrade to Win 7 tonight even if I can have the Grub thing figured out.

---

### Post by merlinus on 2009-07-22
You can do it via a terminal from ubuntu or the live cd.

```
sudo grub
find /boot/grub/stage1 #you will get a response such as root (hd0,2)
root (hd0,2) #use the numbers from the previous command
setup (hd0)
quit 
```

---

### Post by PsychedelicWonders on 2009-07-22
> **merlinus said:**
> You can do it via a terminal from ubuntu or the live cd.
 
```
sudo grub
find /boot/grub/stage1 #you will get a response such as root (hd0,2)
root (hd0,2) #use the numbers from the previous command
setup (hd0)
quit 
```
 
Ok I will try everything tonight...
 
Once I get Win 7 installed, if there is no Grub, how do I get into Ubuntu to run the terminal?
 
I guess I have to use the Live CD?

---

### Post by darco on 2009-07-22
I installed Win7 not long ago and couldnt boot back into Linux...
this helped me (twice)
See "restore grub"

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

good luck
darco

---

### Post by PsychedelicWonders on 2009-07-22
> **darco said:**
> I installed Win7 not long ago and couldnt boot back into Linux...
this helped me (twice)
See "restore grub"
 
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
 
good luck
darco
 
Did you get everything working properly?
 
Or is it not going to work with win 7?

---

### Post by darco on 2009-07-22
works perfect.....

darco

---

