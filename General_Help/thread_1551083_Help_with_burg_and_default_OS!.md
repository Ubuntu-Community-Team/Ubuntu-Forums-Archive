---
title: "Help with burg and default OS!"
date: 2010-08-11
forum: General Help
---

### Post by SonOfWolf on 2010-08-11
I have installed burg and its working fine apart from it always loads Ubuntu by default.

When burg is displayed I need to select the 3rd icond across on the bar to load into my windows boot loader.

How to I go about changing burg to make windows default?

I have tried chaging the default os with burg manager.

Thankss

---

### Post by JedMeister on 2010-12-29
I know this forum is a little old but it hasn't been answered. I came across it from Google when trying to solve this exact same problem so I thought I'd post the answer that I found elsewhere to assist others who may come across it.

There are a number of possible solutions (have a look [here]("http://ubuntuforums.org/showthread.php?t=1308701") for more ideas and links) but here is the one I found the easiest:

```
sudo mv /etc/burg.d/30_os-prober /etc/burg.d/09_os-prober
sudo update-burg
```
This changes the name of the os_prober (the bit that checks for other OS installations). As these scripts are executed in order (by update-burg) changing the first part of the name to 09 will run before the other scripts (eg the one that adds the linux kernel).

This also applies to Grub2 as well, you just need to change it a little:
```
sudo mv /etc/grub.d/30_os-prober /etc/grub.d/09_os-prober
sudo update-grub
```

---

### Post by dcstar on 2010-12-30
> **JedMeister said:**
> I know this forum is a little old but it hasn't been answered. I came across it from Google when trying to solve this exact same problem so I thought I'd post the answer that I found elsewhere to assist others who may come across it.
.........

There is no need whatsoever to stuff around with the correct setup to change the default booting selection, simply change the /etc/default/burg file with the following:

```
# If you change this file, run 'update-burg' afterwards to update
# /boot/burg/burg.cfg.

**GRUB_DEFAULT=saved**
GRUB_TIMEOUT=3
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# If you want to enable the save default function, uncomment the following
# line, and set GRUB_DEFAULT to saved.
**GRUB_SAVEDEFAULT=true**
.......
```

---

### Post by JedMeister on 2010-12-30
That's a nice option that I wasn't aware of, thanks. That fix would be a great one in some usage scenarios.

My only concern with doing it that way is that I suspect it probably saves the default as the boot entry number rather than the entry itself. Perhaps I'm wrong (I haven't checked) and if so its probably a neater solution. But if that is how it does it, then this leaves Windows last on the list. When the kernel is next updated the default will now point to an old Linux kernel. I know that the next time you boot into Win it would be fixed but some of the tech newbs whose PCs I help with need stuff to be almost foolproof!

In a dual boot scenario, my method will always make Windows the first entry and the default. But thats the beauty of Linux, there is always multiple ways to do things and if they are clearly documented then end user can choose the one that works best for them in their scenario :)

---

### Post by dcstar on 2010-12-31
> **JedMeister said:**
> 
........
In a dual boot scenario, **my method will always make Windows the first entry and the default**. But thats the beauty of Linux, there is always multiple ways to do things and if they are clearly documented then end user can choose the one that works best for them in their scenario :)

Until the Burg/Grub package is updated and all the non-standard system configuration files are then overwritten with the proper ones from the package.

Then all of these users who made this change - perhaps months ago - will be wondering what happened and have to waste more time trying to remember what they did to "fix" it in the first place.

That is the price to pay for mucking around with things that shouldn't be touched.

---

### Post by sangeethar44 on 2012-09-06
I understand that this is an old topic now. I had the same problem, the  default OS wouldnt change to Win 7 at all even after updating the  /etc/default/burg file. Here is what i did. It surely works and its just  one of the possible ones:

Code:  	sudo mv /etc/burg.d/30_os-prober /etc/burg.d/09_os-prober sudo update-burg 
 and then install Superboot manager.  Start Super-boot-manager and in the  parameters tab, change the default OS to which ever you want. Tats it!

---

### Post by lisati on 2012-09-07
I think we'll leave resurrection from the dead in other places.

Old thread closed.

---

