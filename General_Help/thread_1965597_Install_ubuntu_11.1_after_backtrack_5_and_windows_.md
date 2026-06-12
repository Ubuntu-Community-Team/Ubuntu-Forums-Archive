---
title: "Install ubuntu 11.1 after backtrack 5 and windows 7"
date: 2012-04-26
forum: General Help
---

### Post by j1k on 2012-04-26
Hi, I have installed in the same HDD Windows 7 and backtrack 5 R2.
How can i installl ubuntu 11.1 and make the 3 systems appear in the same GRUB?
Thanks!!!
I´m very new to linux so i hope you can bring the right instructions.

---

### Post by ronaldbrijo on 2012-04-26
When u run the installation, you will get to the partitioning options and you will be asked what would you like to do? 

Use entire disc or alongside..

Use the side by side option... That way grub will add the other OS's..

---

### Post by oldfred on 2012-04-26
With multiple installs, it is probably better to partition in advance and use Something Else or manual install to choose the / partition. It should auto reuse the existing swap. You can create a separate /home if you want with manual partitioning.

If shrinking Windows to make space use the Windows tools to shrink Windows, but not to create any partitions. Reboot Windows several times to recognize its new size. It will probably run chkdsk.

Then use gparted from a liveCD and swap-off on swap partition to unmount all partitions so you can edit them.

With manual install you get a choice on where to install the grub2 boot loader. Just install to sda. You should then be booting with Ubuntu's grub in the MBR and its grub.cfg which should have your other menu items. If not run this:

```
sudo update-grub
```

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by j1k on 2012-04-27
So  can´t i just run the ubuntu installer in windows? I was expecting to do that and that the grub automatically recognize all my OS , is a easier way to install it???

---

### Post by j1k on 2012-04-27
> **ronaldbrijo said:**
> When u run the installation, you will get to the partitioning options and you will be asked what would you like to do? 

Use entire disc or alongside..

Use the side by side option... That way grub will add the other OS's..

Have you done that before????? I mean i just need to select the install alongside option and that´s all????!!!!

---

