---
title: "32 and 64 bit versions on one Live CD"
date: 2012-09-23
forum: General Help
---

### Post by Nikolai D. on 2012-09-23
Hi there,
Some people in the Church are asking me what can they do about their old and sluggish Windows PC's. And since i already installed Dual Boot for someone as i do it on my Mac to. So that u can use Ubuntu as a default OS for basic usage like surf and multimedia. And in case u need some Win specific something u just choose Win while booting. And that works perfect. And i know i never will be coming back to this person because of his new PC just working forever. And not slowing down over time by some adware/spyware/browser tabs. And other nonsense that i dont even know where they are getting it. And this person for whom i have set up the dual boot loves it and loves the Ubuntu and Unity. Im telling new ppl like lol ill just give u a CD which will solve all the problems you ever had with your computer.
So i was thinking like hmm, without me coming to them for installing it myself. Because i just got not all the time in the world to fix everyone's broken Windozez. I wondered, which sort of hardware would they have? And then i tought, oh wait on a Windows install CD i can choose to install 32 or 64 bit version. So i started to google for Linux Live CD which already includes 32 and 64 bit Live CD versions. And to my big surprise i dont see directly something like this on the internet. Come on that cannot be true nobody has yet put this together and uploaded it somewhere so it just can be downloaded already and used. So anyone is aware of any some obscure not so popular Ubuntu tuned version with something like that which i dont know about? Or any other multi linux live cd around there? Something maybe like Super OS. Which is not so popular but i still like to use it. Because its exactly what i want. Pure Ubuntu lightly tweaked. Not like Mint with changed interface with start button like parading which i dont want.
Thanks in advance,
Nikolai

---

### Post by oldfred on 2012-09-23
If computers are not so old as to not boot from USB then it is relatively easy.  I did it manually before several scripts started to become available. Grub can loopmount an ISO file directly, so you copy multiple ISO to one flash drive an boot the ISO.

Mutli-boot ----------------------------------------------------------
These are scripts to install many ISOs. Some that will not loopmount by installing a kernel and boot image.
MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk w/grub2
[https://help.ubuntu.com/community/InstallAndBootMultipleLinuxFromPendriveFlashDriveUSBDisk](https://help.ubuntu.com/community/InstallAndBootMultipleLinuxFromPendriveFlashDriveUSBDisk)
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)
[http://sourceforge.net/projects/multibootusb/files/](http://sourceforge.net/projects/multibootusb/files/)
MultiSystem Another LiveUSB Multiboot French(translate) w/grub2 
[http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)
Another: multiboot055.sh
[http://blog.p-mt.net/blog/2009/12/27/multiboot-usb-stick/](http://blog.p-mt.net/blog/2009/12/27/multiboot-usb-stick/)
See yumi for multi-boot versions
[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864)
Install grub2 to USB -general info
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB]("http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB")

I have not tried these for CD or DVD:
multicd.sh - combine Linux ISOS into one - syslinux boot loader or isolinux.cfg 
[http://ubuntuforums.org/showthread.php?t=1071869](http://ubuntuforums.org/showthread.php?t=1071869)
[http://multicd.tuxfamily.org/](http://multicd.tuxfamily.org/)

How to create an Ubuntu All-in-one Live DVD uses grub4dos
[http://prshah.blogspot.com/2009/10/how-to-create-ubuntu-all-in-one-dvd.html](http://prshah.blogspot.com/2009/10/how-to-create-ubuntu-all-in-one-dvd.html)

---

### Post by Nikolai D. on 2012-09-24
Hi, thanks for the fast reply,
This all is off course cool that i can do all this stuff. And i also have already found like this: [http://askubuntu.com/questions/28299/dvd-with-both-32-bit-and-64-bit-ubuntu](http://askubuntu.com/questions/28299/dvd-with-both-32-bit-and-64-bit-ubuntu)

But what seemed kind of weird to me is that there is no already ready version yet on internet that i just can download. Or at least not one that is easy to find.

And im like not planning like giving usb sticks to all those ppl who ask me about their slow PC.

---

