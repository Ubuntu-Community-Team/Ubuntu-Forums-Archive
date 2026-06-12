---
title: "Booting later distros with GRUB Legacy"
date: 2011-05-17
forum: General Help
---

### Post by IntentAnalysis on 2011-05-17
It's a little silly to ask this, as I am about to try it anyway, but is it theoretically possible to use a GRUB Legacy USB boot cd to boot a distro beyond 9.04?  Or do I need to get to reading about GRUB 2?

EDIT:  As the USB Boot CD needs to be created from the GRUB files existing inside the Distro that it is intended to boot, this is impossible.  Question answered.  My apologies.

EDIT EDIT:  Unless I revert to GRUB legacy inside the Distro itself.  Ok.  Neat.  I guess I just needed a place to write it down to figure it out.  Again, my apologies.

---

### Post by IntentAnalysis on 2011-05-17
EDIT EDIT EDIT: WUBI Install the distro I'm looking for, then utilize Pendrive Linux's instructions for copying a WUBI install to a USB drive [here]("http://www.pendrivelinux.com/move-wubi-to-a-usb-flash-drive/").

Then boot the USB installation using my com that is *able* to  boot USB, then follow the instructions on uninstalling Grub2 and reverting to Grub Legacy [here]("https://help.ubuntu.com/community/Grub2#Uninstalling%20GRUB%202").

Then follow the instructions for writing a USB Boot CD [here]("https://help.ubuntu.com/community/BootFromUSB#Booting the kernel from a bootable CD").

Kalm :)

---

### Post by garvinrick4 on 2011-05-17
**EDIT: EDIT: EDIT:  This is for partition install not a WUBI install. WUBI attaches itself to Windows boot manager. Messing with WUBI boot 
             well beyond my pay grade.** 
* I do prefer grub2 over grub-legacy myself by far and would not recommend not going backwards to grub-legacy.* Here is code below though.

grub = grub-legacy
grub-pc = grub2

I would imagine if you went to a live Cd and and Chroot into install and purge grub-common
and grub-pc and install grub and then install grub into the mbr of your drive would be Ok.
Make sure your internet is working in Live Cd. 
```

Using sda1 use what yours is.      [CODE]sudo mount /dev/sda1 /mnt
``` ```
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt$i; done  
``` ```
sudo cp /etc/resolv.conf  /mnt/etc/resolv.conf
``` ```
sudo chroot /mnt
``` ```
apt-get update
``````
apt-get purge grub grub-common grub-pc
``````
apt-get install grub
``` select sda for grub install not sda1. Or which drive using sda, sdb, sdc, ect. ect. ect. Use tab to toggle.```
update-grub
``````
exit
```                                ```
for i in /dev/pts /dev /proc /sys; do sudo umount /mnt$i ; done
``` ```
sudo umount /mnt
``` ```
sudo reboot
```[/CODE]# you have mounted partition
#You have mounted and bind /dev /dev/pts /proc /sys
#Copied internet connection
#update to make sure internet working if will not update stop and use last 3 lines and start over with internet working in Live Cd
#You have purged grub (grub-legacy) and grub2 (grub-pc)
#you installed grub (grub-legacy)
#updated grub
#exit and 
#unmount and reboot.

Here is link below for any further explanation:
[HOWTO: Purge and Reinstall Grub 2 from the Live CD - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1581099")

---

### Post by IntentAnalysis on 2011-05-17
NOTE:  The computer I'm working with doesn't have an accessible MBR (doesn't have an internal hard drive)

Doesn't the newly copied WUBI install, once moved over to the USB, function as a partition install, lacking only a bootloader?  And couldn't the created USB boot CD function as that bootloader?

Read: Install the original WUBI on my USB (as per provided instruction), boot into it, update-grub, restart com, boot into it, convert from Grub2 to Grub Legacy (regenerating the Grub menu as specified), and then using the LiveCD of the matching install to write a USB Boot CD so that I can boot into it on my Non-BIOS PC? 

I only ask because this is the route in which I am currently embroiled, making a USB drive, with a pendrive install of Ubuntu, into the main hard drive of a computer which lacks both an internal hard drive, and a BIOS which can be edited at startup.

Edit:  Of course, I -could- just learn how to use Grub2 lol

---

