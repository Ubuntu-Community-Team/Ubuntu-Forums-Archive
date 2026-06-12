---
title: "Help with Ubuntu on Toshiba Satellite C655"
date: 2010-07-26
forum: General Help
---

### Post by chriscorbin on 2010-07-26
My mother recently purchased a Toshiba Satellite C655 to replace her dead iMac, since she has gotten used to using Ubuntu on my netbook i had planned to install it on her new laptop.

I burned the latest LiveCD and installed it on her computer, it was a bit sluggish and the wireless networking didnt work, much like when i boot off a CD to install ubuntu on another computer, but it appears that after installation Ubuntu didnt recognize that this was a laptop and wireless network as well as wired doesnt work at all. It doesnt detect the battery either.

Help would be much appricated, i dont want to have to deal with the insanity of windows again.

---

### Post by itsjoshgrant on 2010-08-08
bump!
also having network issuses

---

### Post by tallinspanish on 2010-09-19
I also just installed 10.04 on a Toshiba satellite C655, and the  wireless started working after I followed some of the directions found  here: [http://ubuntuforums.org/showthread.php?t=1554604](http://ubuntuforums.org/showthread.php?t=1554604) . They are reproduced below for convenience:

--------------

when you reboot at the grub menu press 'e' on the first item of the list this will bring you to a bunch of commands.
Move to the line:
> linux /vmlinuz... ro quiet splash
add options to the end of the line; for example:
> linux /vmlinuz... ro quiet splash apci=off

Type <Ctrl>-x <Enter>                                 
this should get you into ubuntu
after you boot in do this:
 
 open your terminal
and type:  
$ cd /etc/default
$ sudo gedit grub

Change the line:
> GRUB_CMDLINE_LINUX=""
to:
> GRUB_CMDLINE_LINUX="acpi=ht"
quotes required.

save as "/etc/default/grub"

Update the GRUB2 bootloader:
$ sudo update-grub                                 
reboot

------------

I am pretty new to Linux myself, but I did this to fix some problems I  was having with shutting down and restarting, and after doing this, the  wireless started working. Rebooting now works too, although shutting  down is still not working perfectly.

---

