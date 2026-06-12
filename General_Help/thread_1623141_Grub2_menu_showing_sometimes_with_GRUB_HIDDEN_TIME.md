---
title: "Grub2 menu showing sometimes with GRUB_HIDDEN_TIMEOUT=0"
date: 2010-11-16
forum: General Help
---

### Post by jcf-pt on 2010-11-16
Hi,

I'm experiencing an unusual problem. I have my grub2 configuration set to show no menu. However, sometimes it still shows and waits for input for no apparent reason. On a regular PC this wouldn't be much of a problem but on this particular machine I must make sure grub2 always loads Ubuntu without hanging.

I'm using Ubuntu 10.10 and the Grub2 installed package is 1.98+20100804-5ubuntu3.  

My grub configuration is as follows (and I have ran update-grub after changing it):

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```Any help would be appreciated. Even if no solution seems apparent, a workaround to stop it from waiting for input would still be much appreciated.

Thanks in advance.

---

### Post by Rubi1200 on 2010-11-16
Hi and welcome to the forums :)

Do you have other operating systems on the machine or just Ubuntu?

---

### Post by drs305 on 2010-11-16
In your /etc/default/grub you have the following setting, which should show the menu for 10 seconds:
> GRUB_TIMEOUT=10


**If you mean that it *never* boots until you provide input:**

Grub may fail to boot at the end of the timeout period (even if GRUB_TIMEOUT=0) if the system recognizes a 'recordfail' event.

> 
Even if no solution seems apparent, a workaround to stop it from waiting for input would still be much appreciated.

While bypassing the recordfail option is not normally desired, the next time the system fails to boot automatically, you can see if it's recordfail that is causing the autoboot failure by temporarily modifying grub.cfg. This modification will cause the system to boot even if a recordfail event is registered.

Open the file:
```
gksu gedit /boot/grub/grub.cfg
```
Change:
> if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=2
fi
to (set the timeout to the number of seconds before it boots):
> if [ "${recordfail}" = 1 ]; then
  set timeout=2
else
  set timeout=2
fi
Note this is more a test than anything else. The grub.cfg file will be overwritten the next time update-grub is run by you or automatically following certain system updates.

**If you mean it still shows the display but eventually boots, and you have a dual OS system:**
We can alter the scripts so the menu won't display, although the default is to display the menu on multi-OS systems.

---

### Post by jcf-pt on 2010-11-16
> **Rubi1200 said:**
> Hi and welcome to the forums :smile:

Do you have other operating systems on the machine or just Ubuntu?

I only have Ubuntu installed on this machine.


> **drs305 said:**
> In your /etc/default/grub you have the following setting, which should show the menu for 10 seconds:


**If you mean that it *never* boots until you provide input:**

Grub may fail to boot at the end of the timeout period (even if GRUB_TIMEOUT=0) if the system recognizes a 'recordfail' event.


While bypassing the recordfail option is not normally desired, the next time the system fails to boot automatically, you can see if it's recordfail that is causing the autoboot failure by temporarily modifying grub.cfg. This modification will cause the system to boot even if a recordfail event is registered.

Open the file:
```
gksu gedit /boot/grub/grub.cfg
```Change:

to (set the timeout to the number of seconds before it boots):

Note this is more a test than anything else. The grub.cfg file will be overwritten the next time update-grub is run by you or automatically following certain system updates.

**If you mean it still shows the display but eventually boots, and you have a dual OS system:**
We can alter the scripts so the menu won't display, although the default is to display the menu on multi-OS systems.

Even though GRUB_TIMEOUT is set to 10, it usually doesn't show the menu which is what I intended. Only on very rare occasions it does show the menu and waits for input, which is what ruins my day. I've tried to recreate the conditions where this happened, mostly by removing certain peripherals that are not attached when it's supposed to run on its own, such as mouse, keyboard and screen. But I haven't been able to see it happen again to search for its cause.

What is a recordfail event? What could cause it?

Thank you for your time!

---

### Post by drs305 on 2010-11-16
> Even though GRUB_TIMEOUT is set to 10, it usually doesn't show the menu which is what I intended. 

The default menu behavior for Grub 2 is to not display the menu on single OS machines (which is probably one reason *Rubi1200* asked). To display the menu, if you want to see it on every boot, you place a comment in front of the GRUB_HIDDEN_TIMEOUT line in /etc/default/grub:
> **#**GRUB_HIDDEN_TIMEOUT=0

Even though you don't want to see the menu, since it's inconsistent for you now perhaps you should try commenting the above. Then set the timeout for 1 second to see if it consistently boots without manual intervention.

I don't know all the events that trigger a recordfail event. It can be triggered if a boot is interrupted/aborted. The next time Ubuntu starts it remembers the previous failure and displays the menu so the user can elect a different option if desired.

I believe, though I haven't tested it since Grub 1.96, that the recordfail event is noted in /boot/grub/grubenv. If that is the case, you can try to clear it with "sudo grub-editenv create", although for a one-time interrupted boot it should clear automatically after the next successful boot.

---

