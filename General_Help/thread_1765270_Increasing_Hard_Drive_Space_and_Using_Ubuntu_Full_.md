---
title: "Increasing Hard Drive Space and Using Ubuntu Full Time"
date: 2011-05-22
forum: General Help
---

### Post by CDelia on 2011-05-22
Hello, my name is Chris. I have just acquired a new Toshiba Satellite laptop today and the first thing I did was install Ubuntu 10.04. This is the first time that I have used the Ubuntu operating system before. I am used to using the Mac OSX operating system and I am still trying to figure out how everything works on Ubuntu. So far from first impressions, I believe that this is the beginning of a beautiful friendship.

In trying to import my files onto my new laptop from my external hard drive, I discovered that I only have 12.5 gigs available when this is has a 250 gb hard drive. My question is actually a two parter, firstly how do I safely access the remaining free space on my hard drive?  

Second, I installed Ubuntu after downloading the .exe file from the Ubuntu.com website and I have to select which operating system to use every time I log in. I would much rather use Ubuntu full time and not have to go through this step every time I turn on my computer. Hell has a better chance of freezing over before I would ever use Windows 7. What do I have to do to accomplish having just Ubuntu as my only operating system and safely eliminate windows 7?
 
Thank you all so much for helping a newbie out. Take care and have a wonderful evening.

---

### Post by linuxinstalledfromhdd on 2011-05-22
I love those laptops..  They work really well with 10.10

[http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/](http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/)

---

### Post by Rubi1200 on 2011-05-23
Hi and welcome to the forums CDelia :-)

If I understand your post correctly, you installed Ubuntu inside Windows using the Wubi installer.

Some comments:

1. there is a way to increase the size of the root.disk
[http://ubuntuforums.org/showthread.php?t=1625371](http://ubuntuforums.org/showthread.php?t=1625371)

2. you can access Windows partitions like this:
Places > Computer > File System > Host

3. you can migrate the Wubi install to a dedicated partition on the drive using this guide:
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

4. don't be so hasty to get rid of Windows. First get comfortable with Ubuntu and dual-booting for a few months before making such a decision. After all, you never know if you might need Windows for work or a program that won't work with emulation in Ubuntu

5. read some useful information:
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

If you have any questions, feel free to ask.

---

### Post by katykat on 2011-05-23
There is alot of information in that link - perhaps overwhelming. 

The OP apparently has a very large Win7  gobbling up most of the hard drive. 

I wont go near 7 so no expert on it, but if it is similar enough to XP I would suggest first going into Win and either deleting or moving to CD or DVD any unnecessary files such as music or videos. 

Get as much off as possible, and go to ADD/REMOVE programs in COntrol Panel and remove any unnecessary programs. 

Google or search the torrents or rapidshare for a copy of HIREN'S BOOTCD - get the latest copy available, download it, burn it to CD and set the BIOS (during bootup) to boot to CD as the first choice. 

Next step, and this is important, is to DEFRAG in Win. May need to google for how to do that in 7. 

Insert the CD and reboot. Search for Partition Magic - it seems alot more user friendlly than GParted, though its important to read the basic docs on it - choices must be finalized - a step which may not be readily apparent. 

Then increase the size of the second partition (presumably the Linux one - after removing any important files on it) - the maximum allowable. 

FInalize the operation and reboot. 

Boot to Win and use FDISK to check partition information.

(At this point I personally would remove 7 and replace it with XP). 

A former Mac user would probably be more at home with Meerkat, and it certainly seems faster than Lucid. I would recommend downloading and burning the install disk, and test driving it. 

If all is well, then simply install the version desired in the enlarged second partition, letting it reformat/overwrite the prior installation. When increasing the disk size, Linux will also want to increase the size of other 'partitions' it uses (actual user space is only around 90% of disk space). So keeping the old installation may not be a good idea. 

During the installation Meerkat SHOULD install Grub2 which should present a boot menu when all is said and done.  If there is any problems update-grub *should* fix it. 

A couple of reboots may be needed for some systems. 

There is also the option of Natty, but I personally wont go near anything that is not native to Gnome.

---

### Post by CDelia on 2011-05-23
Thank you all for your suggestions, I will look into them, and let you all know how it works out. Take care, namaste!!!

---

### Post by coldraven on 2011-05-23
Hi and welcome.
Firstly, all I know of Wubi is that it installs Ubuntu inside of Windows.
Most likely your new laptop has it's drive full of Windows restore partitions etc.
If you PC is new and you do not have any personal data on it I would do this.

First, did it come with a Windows restore disc? If not create one, search the Windows Help for that.

Second, I would erase the entire drive. You would need to download an Ubuntu Desktop "Live CD", boot from it and use the partition manager "Gparted".
I would recommend version 10.10 (Maverick Meerkat) from here: [http://releases.ubuntu.com/](http://releases.ubuntu.com/)

Alternate step two is to do as I have done, just install Ubuntu on the  whole drive, then install VirtualBox and install Windows as a virtual  machine. This would not be too difficult but you would need some advice. Skip step three.

Third, create two equal partitions and re-install Windows on the first one and Ubuntu on the other. 

We will make a computer whizz out of you yet :)

---

