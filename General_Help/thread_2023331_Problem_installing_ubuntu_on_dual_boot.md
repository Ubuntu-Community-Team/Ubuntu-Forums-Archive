---
title: "Problem installing ubuntu on dual boot"
date: 2012-07-12
forum: General Help
---

### Post by desmoguga on 2012-07-12
Hi everyone,
I'm trying to install Ubuntu 12.04 on my pc where is already installed windows 7. I've followed all the guide to do instal ubuntu using an usb device.
I've used unetbootin, linux live usb creator and universal usb installer to make the iso image bootable but the problem is always the same.
When I launch the usb (via bios) i can choose:
1) Install ubuntu
2) Try ubuntu
3) check disc errors
I've tried all these options but after choosing one of them my screen is totally black and nothing happens.
I've tried to do the same with the 11.10 and 10.04 version but the problem is always the same.
I'm thinking that it is a problem of my nvidia gforce gt. it could be?
I would really appreciate everyone who can help me.
Thanks in advance

---

### Post by oldfred on 2012-07-12
Welcome to the forums.

I have nVidia 9600GT and every boot from CD or USB and first boot after installing I have to use nomodeset.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
I had to do this with my Nvidia 9600GT:
To install Ubuntu, boot from the cd press any key at accessibility circle and keyboard, press F6 and then select the nomodeset option.
USB boot - At the menu press tab on the first option to edit the boot options and replaced the 'splash' option with 'nomodeset'. 
then
On first boot after install, press e on getting the GRUB bootloader menu. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode), install nVidia driver suggested my Ubuntu

If booting from USB it just may be easier to edit syslinux with whatever boot parameters you need like this which is for an Intel but same way to edit syslinux.cfg:
Ubuntu 12.04 has been officially released and, with minor adjustments, the intel gma500 video card is working out of the box.
[http://blog.bodhizazen.net/linux/ubuntu-12-04-gma500-poulsbo-boot-options/](http://blog.bodhizazen.net/linux/ubuntu-12-04-gma500-poulsbo-boot-options/)
simply edit &#8220;syslinux.cfg&#8221;

---

