---
title: "GRUB Ubuntu 9.10 &amp; Windows 7"
date: 2009-11-20
forum: General Help
---

### Post by rDwyP44y on 2009-11-20
How do I edit my GRUB in ubuntu?

I recently installed Windows 7 and ubuntu 9.10 on a new Desktop.

But for some reason I cant seem to get my GRUB "time out" (time it allows me before it makes a OS selectiong to run) to be changed!


I basically want it to wait 1 minute (60 seconds) for me to select an OS to boot from!

The default is 5 or 10 seconds (i think)... which never leaves me enough time when I restart the computer( i restart unatanded to get something to eat)!

Please help me I seem to have some Issue with it as i previously asked people in the IRC chat #ubuntu room and they them selbves cant seem to figure it out!

Thanks in advance!

---

### Post by Locutus_of_Borg on 2009-11-20
sudo gedit /boot/grub/menu.lst


change number after word "timeout" to 60


save file


ta-da

---

### Post by QLee on 2009-11-20
[QUOTE=rDwyP44y]How do I edit my GRUB in ubuntu?

I recently installed Windows 7 and ubuntu 9.10 on a new Desktop.

But for some reason I cant seem to get my GRUB "time out" (time it allows me before it makes a OS selectiong to run) to be changed!
[/QUOTE]

Since it is a new install of 9.10 you will have GRUB2, rather than the legacy GRUB with which you might be familiar.

Have a look at this link, down the page where it tells how to properly edit the new GRUB.
[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

---

### Post by P4man on 2009-11-20
the above link will explain all you need to know, but grub2 is cumbersome to configure. If you just want to change the timeout, I would suggest installing startup-manager from the the repository. Nice simple gui to configure basic things in grub and grub2.

---

### Post by ajgreeny on 2009-11-20
> **P4man said:**
> the above link will explain all you need to know, but grub2 is cumbersome to configure. If you just want to change the timeout, I would suggest installing startup-manager from the the repository. Nice simple gui to configure basic things in grub and grub2.
This may be partly true, but SM is not fully compliant with grub2 yet, and it makes some sense to get to know the grub2 system files and how to edit them.

You need to edit /etc/default/grub to change the timeout.  Look for
> # If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
[COLOR=Red]GRUB_TIMEOUT="5"[/COLOR]
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entrys
#GRUB_DISABLE_LINUX_RECOVERY="true"
As you can see I have changed my timeout to 5 secs in the red line, as I do not need more, but just change the default 10 to 60 in your file and you will get the minute you want.

Also worth looking at the grub2 wiki, and another very useful thread in this forum.
[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

