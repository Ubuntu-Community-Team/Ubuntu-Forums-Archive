---
title: "Latest Kernel"
date: 2010-03-16
forum: General Help
---

### Post by MrGreen on 2010-03-16
Hi,

Looking to find a way to get latest kernel too install on Lucid [10.04] currently have 2.6.31-19-generic on my desktop.

How do I update to latest kernel [laptop is running 2.6.32??? 10.04]?

Thanks

MrG

---

### Post by MrGreen on 2010-03-16
I tried running update grub, although it found new kernel it has not added anything to menu.lst

Is there a way I can update too latest kernel from a terminal 

Need to get Virtualbox working again

```
title		Ubuntu 9.10, kernel 2.6.31-19-generic
uuid		866f878c-9c19-4d6c-9008-c6d3a8f032f8
kernel		/vmlinuz-2.6.31-19-generic root=
```

This does not look right at all 

Since I am running 10.04???

MrG

---

### Post by howefield on 2010-03-16
> **MrGreen said:**
> Since I am running 10.04???

What makes you think that ? (Sorry if it sounds a stupid question)

---

### Post by MrGreen on 2010-03-16
The contents of /boot

```
mrgreen@mrgreen-desktop:/boot$ ls
abi-2.6.31-19-generic         memtest86+.bin
abi-2.6.32-16-generic         System.map-2.6.31-19-generic
config-2.6.31-19-generic      System.map-2.6.32-16-generic
config-2.6.32-16-generic      vmcoreinfo-2.6.31-19-generic
grub                          vmcoreinfo-2.6.32-16-generic
initrd.img-2.6.31-19-generic  vmlinuz-2.6.31-19-generic
initrd.img-2.6.32-16-generic  vmlinuz-2.6.32-16-generic

```

MrG

---

### Post by howefield on 2010-03-16
All that means is that you have some kernels that are also found in Lucid, it doesn't mean you are running the development release.

What is the output of the terminal command

```
lsb_release -a
```

---

### Post by MrGreen on 2010-03-17
```
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu lucid (development branch)
Release:	10.04
Codename:	lucid

```

I assume the problems I am having with plymouth may be related to kernel too

Thought about adding an entry in grub but was not sure if that would work

MrG

---

### Post by MrGreen on 2010-03-18
Added too grub menu.lst 2.6.32-16 entry and it worked

Virtualbox is running again and plymouth is starting to show up

Will keep an eye on system and make sure I update 

Thanks for your help

MrG

---

### Post by Oliphant on 2010-03-18
Curious if this could help me too.  I upgraded from Jaunty however maintained the Jaunty menu.lst.  I didnt pay much attention but it turns out I don't have sound.  I've tried everything I could find Google results and still have no luck.  I read something that lead me to the possibility it could be the kernel needs to be updated. 

I don't know if that makes sense but I sure could use a hint.

---

### Post by MrGreen on 2010-03-18
Problem is I do not know the reason why grub was not updated during upgrade

First thing I noticed after a recent update was Virtualbox stopped working and just simply would not load or run

Everything else seems fine

But noticed the 2.6.32 in /boot and wondered what was going on

Plymouth although still buggy does work of sorts now

May look at nvidia drivers next

MrG

---

### Post by Oliphant on 2010-03-18
Ok, I remember when I installed Jaunty I did some messing around in menu.lst.  When I upgraded to Karmic it asked if I wanted to keep the same on or install the new one.  I opted for maintaining the jaunty.  

For the heck of it I just upgraded to Lucid and was asked again if I wanted to maintain the original or upgrade.  This time I upgrades. Sound problem fixed :)!

---

