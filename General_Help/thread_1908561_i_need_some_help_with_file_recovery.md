---
title: "i need some help with file recovery"
date: 2012-01-13
forum: General Help
---

### Post by juustahiker on 2012-01-13
hi, i am currently running ubuntu 11.10(sort of) but i downloaded the wrong graphics card driver and now the moniter can't display anything.
 
so i threw in the install disc for my origenal installation of ubuntu (11.04) and put it in try me mode the moniter works now but i only have 5 of 32 gigabytes backed up and i want to get the rest off before i reinstall ubuntu. when i access my folders i can see the folder of my 11.10 account but i can't access the folder because i don't have permission, is there any way to get permission? i know all of my passwords and encryptions if that is helpful.
 
open to all suggestions, thanks.

---

### Post by juustahiker on 2012-01-14
update:
 
 i accidentally downloaded a graphics card driver that may or may not have been built for my card (an nVIDIA 7500 GTx) and rebooted. then when it stopped functioning (the monitor shut down during booting) i decided that i would just reinstall ubuntu and destroy all the old data. 
after doing so i incountered the same promblem with this development:
 
it gave me 2 error messages that were different every time and this:
 
the disk drive for /Dev/mapper/cryptswap1 is not ready to use
 
then the monitor shut down.
 
so using the trial mode on the boot disc (which worked perfectly for some reason) i poked around to find a damaged hard drive partition and deleted it(in hindsight this was stupid) and now the monitor shuts down in trial mode to so I'm sorta out of options.

---

### Post by dino99 on 2012-01-14
if your issue is due to a graphic driver, then into a terminal:

sudo rm /etc/X11/xorg.conf
sudo apt-get install synaptic
sudo reboot
sudo synaptic
there, purge every Nvidia package(s) installed, then: reload to check for updates then install nvidia-current & nvidia-settings

close synaptic & reboot, you should be ok then.

---

### Post by varunendra on 2012-01-15
> **juustahiker said:**
> when i access my folders i can see the folder of my 11.10 account but i can't access the folder because i don't have permission, is there any way to get permission? i know all of my passwords and encryptions if that is helpful.For attempting recovery/repairing of the system, try what dino suggested above.

For accessing the directories, you can open nautilus as root: press **Alt+F2** > type **gksu nautilus** > press 'Enter'.

But if the files are encrypted, then I'm not sure how to proceed. Probably you should first try to get into your current installation then, and copy files from there. If it is just a graphics driver problem, then 'failsafeX' option in grub's 'Recovery mode' menu should allow you to login normally in low graphics mode. (you may have to press and hold 'shift' key during system startup to bring up grub menu if it does not show up by default)

> **juustahiker said:**
> and now the monitor shuts down in trial mode.. 
..I don't get this part. How can a change in drivers or partitions on an installed system can affect the behaviour of graphics on a live system which is 'freezed'? Is it a Live USB with persistence that you are referring to as "installation disc"?

As far as I know, the only thing that may interact/interfere with a Live booting is an existing swap partition, but I don't think it can interfere with its graphics. So make sure your hardware and connections are okay.


**_EDIT_:**
By pressing any key while booting from cd/usb we get to the advance boot menu of a live session. There, pressing F6 > then selecting 'nomodeset' option is same as booting with 'failsafeX' graphics mode in an installed system. They both let you boot in safe graphics mode. So try that as well if normal booting is no more possible.
Details and other boot options: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)



**_EDIT2_:**
Just realized you've already marked it [solved] (perhaps while I was posting or editing). Can you please share the experience with us?
Thank You.

---

