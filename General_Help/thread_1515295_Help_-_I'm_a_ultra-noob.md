---
title: "Help - I'm a ultra-noob"
date: 2010-06-22
forum: General Help
---

### Post by mandarpowale on 2010-06-22
Hi

I just installed the latest Ubuntu Desktop Edition 10.04. Somehow I managed to get it installed on my 80 GB HDD which has 2 partitions. I formatted them to the linux's file format. 

The installation has been successful according to all the tell-tales. I have even had a session or two in the OS.

First of all, I've been a windows user until now, so i can't get around to understanding how to view drives (For e.g i had f & g drives where i have now installed Ubuntu) I do not yet understand the Linux File System.

Now i can't see the F & G drives. I had intended to use F: for linux (OS) and G: for linux related softwares/data. Can i do that. I am used to viewing drives names at the 'my computer' equivalent.

I also can't seem to access my DVDRW. I tried installing my on-board Lan-Card drivers (drivers being allOS ones) from a CD (written under windows) since my default network is not being detected. 

I am using internet over windows 7 right now which is setup to use a PPPoe type of dialup connection through Lan. I don't know how to set up similar connection under the UBUNTU environment. The ISP tech support has not been much help in this department. Linux is uncharted territory to them.

So to summarize the two main problems I have are: Can't see DVDRW/CDROM & can't connect to net. 

I would also like to know if there is any software included in UNBUNTU to view files on NTFS partitions, or windows files. I have heard of wine, but don't know the specifics. 

Its really irksome to use windows for internet, now that i want to use linux.

Any assistance would be appreciated

My current config is 
Intel P4 2.66 Ghz
1gb DDR 333 Ram
500GB WD Sata2(3 partitions containing XP & Windows 7)
80 GB IDE Seagate (2 partitions, containing linux on first partition, don't know how to view the second one)

Nvidia Geforce 7300GS

REgards,
Mandar Powale

---

### Post by wilee-nilee on 2010-06-22
Can't help you with the Internet connection, but in Ubuntu if you go to home the windows partition should be in the side bar. The best thing to do is have a shared ntfs partition tah MS and Linux can read. With opening the MS partition you have to search for what you want.

---

### Post by 3rdalbum on 2010-06-22
I don't know anything about computer-initiated PPPoE (most places use modem-initiated PPPoE) and I'm also having a problem with DVD and CD media on one of my computers, so I can't help there.

How exactly did you install Ubuntu? Did you use the installer that runs in Windows, or did you boot your computer from the CD? Your description indicates that you booted from the CD and installed Ubuntu that way; clarification would be helpful.

Your Windows partitions should be able to be mounted and accessed from the Places menu. They will then appear on the desktop and in the filesystem under /media.

Linux does not use "drive letters" so get used to not seeing them.

Also, you won't be able to use a seperate partition or hard disk to store Linux programs in. Linux programs install files to lots of places in your filesystem and you cannot choose a different location. You can, however, have your user files (/home) stored on a different partition or hard disk; maybe have a look for a tutorial on this, but for the meanwhile you might not want to fiddle with this because it does involve some editing of configuration files.

---

### Post by mandarpowale on 2010-06-22
> **3rdalbum said:**
> 
How exactly did you install Ubuntu? Did you use the installer that runs in Windows, or did you boot your computer from the CD? Your description indicates that you booted from the CD and installed Ubuntu that way; clarification would be helpful.


Yes

First I ran it off the CD (Demo Mode followed by full install). How-ever when running off the CD (in demo mode), it showed my windows partitions and the data in them. But when I install the OS it does not show them. Has this something to do with file system (ext4/ext3/ext2) which one is best to work in tandem with windows as a primary OS.

I kept the default ext4

> **3rdalbum said:**
> 

Your Windows partitions should be able to be mounted and accessed from the Places menu. They will then appear on the desktop and in the file system under /media.


How to check if windows partitions are mountable, I tried running the System > Administration > Disk 'something' It showed descriptions of drives and partitions once, Just the once.

I've removed Linux for the time being, so I will re-install and check /media option.

> 
About the Internet

The ISP told me he does not have support for Linux in his system.


But why is my Sony DVDRW not being detected or where to find it. It should be detected since I installed the Linux from a CD after all.


My 80GB HDD has bad sectors ,also Linux gives some kind of error message (failed to install from CD) while starting the OS when i try to run it off the CD

Hi

I managed to get internet up and running. I used pppoeconf to setup a conection from the terminal.

Now the question of detecting DVDRW remains. The DVDRW  is accessible in Demo mode, just not in full version up till now. 

Also HDD windows partitions are not visible in full mode, only demo mode works till latest. Should I try installing Linux with 'side-by-side' option ?

Thank you for all the help given till now and in the future.

Regards,
Mandar

---

### Post by mooreted on 2010-06-22
First of all; drives are designated such as:

sda
sdb
sdc

and partitions on those drives would be listed such as:

sda1
sda2
sda3

Your DVD drive is probably cdrom0

When I place a DVD or CD into my drive it automatically shows up in the file manager and on my desktop. It is mounted at /media/cdrom0 and I can open the file manager, click File System/Media/cdrom0 to see it's contents.

Unlike Windows you wont see a cd-rom device in the file manager unless it's mounted. It wont be mounted unless you put media in the drive.

For your hard drives, they may not be mounted automatically at boot time. You can make Ubuntu mount the drives on boot by editing your /etc/fstab configuration file.

You can open a terminal and enter:

sudo fdisk -l

This will show available drives and partitions. Your Windows partition may show up something like:

/dev/sdb1

Now you want to create a directory to mount to:

sudo mkdir /media/Windows

Then edit your fstab file:

sudo gedit /etc/fstab

Then add the line that corresponds to your Windows drive such as:

/dev/sdb1 /media/Windows ntfs defaults 0 0 

Then you can mount the drive without rebooting by entering the command:

sudo mount -a

Also your Windows partition will now be mounted at each boot.

Also at the terminal you can see what devices are detected on your system by entering these commands at the terminal:

lspci

and

lsusb

---

### Post by coldraven on 2010-06-22
The NTFS partitions should be showing up in "Places", I'm hoping that you have not installed on the wrong disk!
What options do you see when you boot up?

I don't know why your CD is not working, try loading an audio CD or a Movie DVD and see if it appears on your desktop.

A handy command in the terminal is ```
sudo lshw
``` which will list your hardware.
To save the output to a text file called "myhardware.txt" type ```
sudo lshw > myhardware.txt
``` and will be saved in your home directory.

---

