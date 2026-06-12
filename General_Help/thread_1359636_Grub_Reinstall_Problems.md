---
title: "Grub Reinstall Problems"
date: 2009-12-19
forum: General Help
---

### Post by alancop on 2009-12-19
[FONT="Arial"]
Ubuntu 9.10 desktop 32 bit.  I manually checked to see if /boot/grub/stage1 even exists, and it does not.  I am so confused by this problem.  This is some code I thought may be useful.
```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x48000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9327    74919096   83  Linux
/dev/sda4            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris

ubuntu@ubuntu:~$ sudo grub


grub> find /boot/grub/stage1

Error 15: File not found

grub> root (hd0,0)

grub> setup (hd0,0)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... no

Error 15: File not found

grub> 

```
Anyone have any advice?
 [/FONT]

---

### Post by garyed on 2009-12-19
You probably have the new grub2 installed so there is no stage1 ..or 2 menu.lst...etc..
```
sudo grub-install -v 
```
will give you the grub version 1.xx will be Grub2 or 0.xx is old Grub legacy.

---

### Post by alancop on 2009-12-19
```
ubuntu@ubuntu:~$ sudo grub-install -v
grub-install (GNU GRUB 0.97)
ubuntu@ubuntu:~$
```

---

### Post by garyed on 2009-12-19
how are you getting to the grub prompt?

---

### Post by alancop on 2009-12-19
First I would like to say that I am using a 9.10 live cd, so in order to get to it:

```
Sudo grub
```

That gives you a prompt that looks like this.

```
grub> 
```

---

### Post by alancop on 2009-12-19
I am going to try re-flagging the partition as bootable and see if it doesnt work. will report back soon.

---

### Post by garyed on 2009-12-19
I'm assuming you're not getting a grub menu any more but if I'm wrong then these steps are not needed:
Anyways:
Boot from the 9.10 live CD, open a terminal & do:

```
sudo mount /dev/sda1 /mnt
```
```
sudo grub-install --root-directory=/mnt/ /dev/sda
```
then reboot, take out the CD & hopefully you'll get a grub menu to get you back into Ubuntu. Once there get to a terminal & do:
[CODE]sudo update-grub[CODE]

If that doesn't work you could try to substitute hda.. for sda..

---

### Post by alancop on 2009-12-20
That worked like a charm! Thank you very much Gary, sometimes google just doesn't cut it. If i were to make a Tutorial about this would you like to be mentioned?

---

### Post by garyed on 2009-12-20
> **alancop said:**
> That worked like a charm! Thank you very much Gary, sometimes google just doesn't cut it. If i were to make a Tutorial about this would you like to be mentioned?

Glad things worked out. I spent a few days recently working on a similar Grub2 problem on a new installation so it was fresh in my mind. I can't take credit for something someone else figured out before me but I appreciate the thought.

---

### Post by Physicist on 2010-03-04
This works!

> **garyed said:**
> I'm assuming you're not getting a grub menu any more but if I'm wrong then these steps are not needed:
Anyways:
Boot from the 9.10 live CD, open a terminal & do:

```
sudo mount /dev/sda1 /mnt
```
```
sudo grub-install --root-directory=/mnt/ /dev/sda
```
then reboot, take out the CD & hopefully you'll get a grub menu to get you back into Ubuntu. Once there get to a terminal & do:
[CODE]sudo update-grub[CODE]

If that doesn't work you could try to substitute hda.. for sda..

---

