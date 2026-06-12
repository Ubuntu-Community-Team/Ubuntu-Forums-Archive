---
title: "Just some general help please..."
date: 2011-01-16
forum: General Help
---

### Post by JohnKyo on 2011-01-16
Okay first off...I need to have a straight forward answer.

I have a **** ton of programs I really would like to NOT reinstall and I have tons of files on an external. Can I install Ubuntu without messing with any of that? Or is there a way I can install it so that I can freely switch between windows and ubuntu...or will that just make ubuntu slower?

Also, I am new to using Ubuntu and I would like some basic help if ANY can be provided. Such as where to start. Some basic little tutorials I can go through, etc. Answers to all of this would be appreciated.

---

### Post by amsterdamharu on 2011-01-16
Hi and welcome to Ubuntu.

> Can I install Ubuntu without messing with any of that? NO, there will always be a risk that installing or resizing partitions will mess up your harddisk.
The chance is very small though and gets bigger depending on your hard disk configuration. If you have unpartitioned space it could use that without resizing and you'll have no risk but if you want to resize than there is a risk it'll go wrong.


> Is there a way  I can install it so that I can freely switch between windows and  ubuntu.If you're in Ubuntu you can reboot into Windows and visa versa, they won't be bothered by each other. Windows will normally be booted by GRUB which is a program to tell the computer how and where to start operating systems.

You can download the iso and burn it on a CD/use unetbootin to put it on a usb then start with the CD/usb and choose "try Ubuntu" that will let you run it off the CD but it'll be slower than running it off the harddisk and it runs out of memory so after a reboot all your changes are gone.
When you can boot into the live CD it's best to post your hardware here to see if there is any incompatible hardware. The command to do so is:
```
sudo lspci -k
sudo lsusb
```To execute the commands you can press alt + F2, type gnome-terminal and click run. Then copy one command and paste it in the terminal (black screen that showed up after you clicked run). Use the mouse to paste commands in the terminal.
Then you can select all the text in the terminal, right click and select copy. When pasting it here please wrap it in  &#91;code] &#91;/code] tags. In other words: &#91;code][COLOR=Red]Your pasted stuff[/COLOR]&#91;/code]
I would suggest getting Ubuntu 10.04 called Lucid.

Ubuntu is not Windows and many things are done differently, a simple manual can be found here:
[http://ubuntu-manual.org/](http://ubuntu-manual.org/)

When you decide to install I would recommend manually partition since there was a post somewhere of people having their Windows overwritten.
You need 3 partitions:
1. / (called root) needs to be about 8 to 12Gig depending on how many software you want to install
2. swap needs to be twice the amount of memory you've got
3. /home Here is where you store your personal documents/movies/photos and setting/preference files for your programs. Needs to be whatever you need.

You can access your nt or fat partitions from Ubuntu so there is no need for really big home partition.

---

### Post by Godspell on 2011-01-16
Hi there,

From my perspective, you can install Ubuntu whilst Windows already occupied on your HDD. Upon installation, Ubuntu automatically detects the HDD and shows you how much space Windows has occupied and that how much Ubuntu can get space for itself.
You can then proceed on installing it without having to make technical decisions (although you can if you wish).

Installation is very fast and on next reboot, you should have a GRUB menu which will ask you to choose an OS to boot. This probably is the fastest and safest way to switch between them (alternative is Virtual Machine i.e. Windows installed inside Ubuntu).

I have done this 7 or 8 times and had no problems, data loss whatsoever in the past.
Generally speaking, this procedure shouldn't affect any applications, personalisations or data.

However, like **amsterdamharu** said, it is a big risk especially if you're handling large amount of data.
I personally know a lot of people who have had problems with this process and will disagree with it.

I am ONLY suggesting you this as an option solely from my experience.
So, don't take it seriously like 100% Do wait for other replies if you wish.
If you would like to know more about it, check this out.
> [https://help.ubuntu.com/community/WindowsDualBoot#Install%20Ubuntu%20after%20Windows](https://help.ubuntu.com/community/WindowsDualBoot#Install%20Ubuntu%20after%20Windows)

As far as my knowledge goes, this is all I can tell you :)

Hope its useful. Thank you.

Regards,
GS

---

### Post by mastablasta on 2011-01-16
You will have to defragment the disk a few times first, so that any data stays together and you don't corrupt it. then you resize the disk in windows using disk manager (leaving a partition empty)

but a lot of people done it and made it through succesfully. i suggest you use the 10.04, as 10.10 has some bugs. you can always upgrade later to version 10.10 if you wish. thoguh it's not necessary. besides 10.04 is LTS (Long term support) and is a bit more stable. anyway during install if you install to largest free disk space (unformated partition) Ubuntu will create all partitions it needs automaticly. later you can sitll create more or make for exampel a separate parittion for Home folder (which is like MyDocuments in Windows)

---

### Post by Godspell on 2011-01-18
So, have you installed it yet? Or found an alternative way?

I read couple more online articles on this and it's somewhat confirmed that Ubuntu doesn't give any trouble whatsoever to Windows partition.

Then again, some might still suggest there's a possibility on damaging the format and stuff.

I think it's up to you as a user, really.

Anyway, let us know how you get on :)

Regards,
GS

---

### Post by Mark Phelps on 2011-01-18
> Can I install Ubuntu without messing with any of that?

Yes ... provided that you do NOT use the Ubuntu installer to shrink your MS Windows install to make room for Ubuntu.  Doing that in Win7 or Vista has a history of sometimes corrupting the Windows OS partition.

The safer way is to use the Windows Disk Management utility to shrink the Windows OS partition -- and then boot into it a couple of times afterward to allow it tyo resync its filesystem.

Also, when you later install Ubuntu -- be very careful!  The "new" installer no longer provides the "largest free space" option, and makes it very easy to accidentally wipe out your MS Windows partition during the Ubuntu install.

---

### Post by Godspell on 2011-01-18
> **Mark Phelps said:**
>  -- be very careful!  The "new" installer no longer provides the "largest free space" option, and makes it very easy to accidentally wipe out your MS Windows partition during the Ubuntu install.

I thought "largest free space" option was still in Lucid? No?

I'm surprised you said it's better to use Windows Disk Management Utility to shrink the partition than Ubuntu installer? I thought it's the other way around. Any particular reason for that?

I'm just curious. It's always good to learn something new :)

Thank you.

Regards,
GS

---

