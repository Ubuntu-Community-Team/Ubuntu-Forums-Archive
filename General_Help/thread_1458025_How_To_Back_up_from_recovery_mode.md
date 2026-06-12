---
title: "How To Back up from recovery mode"
date: 2010-04-19
forum: General Help
---

### Post by tperwez on 2010-04-19
Hi Everyone,

I would appreciate some advice on this probmel.

I have a sytem that keeps crashing after it was upgraded to 9.10 from 9.04 (with ISO image). The X Server just locks up and requires hard boot every time. It happens so often that the system is practically unusable. I think that my only recourse is to do a clean install.

I want to back up my home directory (or perhaps most data) to a USB drive. But since it takes a while to do this backup and the system crashes in the meantime, I think that perhaps I should boot in text mode (Recovery Mose?) to avoid X Server. Then I should mount USB drive and copy home directory to it. My questions are as follows:

1. What is the best way to start the system to boot in the text mode? Is this the way to go?

2. When logged on in this text mode, how do I mount the USB drive? What commands?

3. What command to use to copy the entire home directory to be able to get the dot files etc also copied?

Is this the preferred way to do things.

I need to do cleans install on this system and would appreciate any other advice/suggestions. Best regards,

Tariq

---

### Post by Untitled_No4 on 2010-04-19
You have upgraded from 9.10 to 9.04? Was it the other way around or have you upgraded to 10.04 (Lucid Lynx)?

My first step if you are on either 9.10 or 10.04 would be to log on to recover mode (see step 1 below) and run:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.bak
reboot
```
You might just get lucky.

If I were you I'd start the computer with a live cd and, then mount the home directory (usually finding it in Dolphin/Nautilus and entering it is enough) and then back up the home directory using grsync:
```
sudo aptitude install grsync
```
from terminal, then run it and you will have to choose a source and a destination directories and run it.

If you want to do it from the command line you will have hold shift after your bios has finished loading and select recovery mode in grub. Then when you are faced with the menu select drop to command prompt (or something along those lines). If you have set up a root password you will have to log in. I'll assume you're NOT root in the following commands, but if you are just drop the sudo.

1. Connect your usb drive and run
```
ls /dev
```
For me it will be sdb1 but it depends on how many drives you have so it might be sdc, etc.

2. Mount it (assuming it is sdb1)
```
sudo mount /dev/sdb1 /mnt
```
Now your /mnt folder points to the USB drive.

3. Make a folder your USB drive
```
mkdir /mnt/home_backup
```
this should run without sudo, but if you have a problem with permissions, just add sudo.

4. Copy your files
```
cp /home /mnt/home_backup -R
```
-R = recursively, i.e. go into all subdirectories and copy them and the files in them too

5. If you want to unplug your USB drive before shutting down the system run
```
sudo umount /mnt
```
to safely unmount the drive.

6. Before you wipe out your hard drive, make sure that everything was indeed copied to your usb drive. Better safe then sorry.

---

### Post by mike555 on 2010-04-19
Can't you just use the "live" cd and mount the partition and copy to usb?

---

