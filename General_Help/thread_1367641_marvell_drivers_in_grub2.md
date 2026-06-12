---
title: "marvell drivers in grub2"
date: 2009-12-29
forum: General Help
---

### Post by tinmice on 2009-12-29
I have an ASUS M2V motherboard, and to use the third SATA port I had to follow these instructions before to edit menu.lst in grub,
[http://www.deuxpi.ca/2009/01/enabling-the-marvell-sata-cont.html](http://www.deuxpi.ca/2009/01/enabling-the-marvell-sata-cont.html)
Since grub has been changed though for 9.10 I can't figure out what to change or where to add the line mentioned on the above link. I've read the grub2 page and googled, but had no luck so far.

Thanks for your help

---

### Post by synapsys on 2009-12-29
That site links to this page...

[http://wiki.debian.org/pata_marvell](http://wiki.debian.org/pata_marvell)

---

### Post by crazy_bob_uk on 2010-01-14
tinmice,
I created a custom boot option in /etc/grub.d/40_custom that included the ahci.marvell_enable=1  option, and then set that as the default boot option in /etc/default/grub

have a read here [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275) 

I've only been using linux a few months so dont know if this was the best way of doing it but it seamed to work though i'm still having problems using mdadm on the marvell chipset.

---

### Post by Vale- on 2010-01-21
I am interested in doing this also.

I have no idea how to create a custom boot entry to add the "ahci marvell_enable = 1" boot parameter. Is it possible to add it to a current boot option like I could when editing the menu.lst file.

I need to get this working so ubuntu server can detect my raid connected to my marvell sata card. At the moment I am only detecting my primary harddrive which is connected via my VIA sata controller onboard.

Anyone have any hints or tips to help me get this working?

EDIT: I have found a explanation on how to do this from the site linked in this thread. It is mentioned in the comments. Teach me not to read comments eh?

I will post it here anyway just incase someone misses it like me.

> The special boot options are specified in the file "/etc/default/grub". To edit this file you can run the command in the Terminal:
      sudo gedit /etc/default/grub
  and enter your password if requested.
  Find the line
      GRUB_CMDLINE_LINUX=""
  and change it to
 
    GRUB_CMDLINE_LINUX="ahci.marvell_enable=1"
  then save the file. Close the text editor, then run the command:
      sudo update-grub
  to apply the configuration changes. When you reboot, Ubuntu should be able to detect the SATA drives on the Marvell controller.

---

### Post by Leppie on 2010-01-21
to set kernel options, you need to edit your grub defaults file:
```
gksudo gedit /etc/default/grub
```
you can set the options using the following lines:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
```
you could make it something like this:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="ahci.marvell_enable=1"
```
then save and exit and regenerate your grub.cfg:
```
sudo grub-mkconfig
```
this will show you the grub.cfg while it's being generated. check that your kernel option appears. if it's going to fast, you can check it afterwards like this:
```
cat /boot/grub/grub.cfg | grep marvell
```
if the last command produces output, modifications have been applied.

---

