---
title: "No Graphical Log-In Booting 9.04 After Upgrading VirtualBox"
date: 2009-11-04
forum: General Help
---

### Post by x777 on 2009-11-04
[FONT=Arial][SIZE=2]Hi there,

This is my first time posting ... so I hope that I'm in the right area.  Otherwise, please point me to where I should post this problem.

I've had this posted on LaunchPad since the 29 Oct. and still haven't had a single response ... so I'm re-posting it here, hopefully with a quicker response to solve my 2 issues.

I have been switching between Ubuntu and Windows XP Pro. on and off for little over a year, without any problems.  Until I upgraded VirtualBox to the latest version 3.0.6, (at the time) from the Open Source Edition. That's when my problems began.

I have 2 Issues that Need Resolving:

1. I'm not able to boot into Ubuntu 9.04, after installing VirtualBox v3.0.6.  I received the following errors during the boot process:
    a. udevd[863] specified group 'vboxusers' unknown.  Sometimes, [864] is displayed.
    b. Cannot change owner vboxusers for device /dev/vboxdrv

All examples of these errors that I was able to find, none specifically mention, (that I've read) the problem during boot up, only while using VirtualBox.  After reading, all examples, I removed VirtualBox, and the above errors no longer appear.  However, it still never makes it to the log-in screen.

2. I'm using the Ubuntu 8.04 LiveCD, and "ubuntu - Live session user" has locked, (taken ownership) of both my SD Cards, (File System is FAT16).  One plugs into a Multi-Card Reader, the other using an USB / SD Card Adapter, (if that helps with any ideas). I'm not able to take ownership, in the usual manner, i.e. right-click on SD Card on the desktop. Nor while the SD Card folder is open.  Also, chmod, gives me the following errors:
    &#5121; chmod: changing permissions of '/media/2GB SD/some_file': Read-only file system and
    &#5121; No space left on device -- for the other card.

Of course it won't allow me to copy to or re-name files, either.  There's more than ample free space on both cards.  The problem on one SD card, (read-only file system) only seems to happen when the file name is more than 1 word long ... most times.  But, the last few times it was a 1 word file name.  Also, if I try to change the file name from 1 word to the original, (when it actually allows me to save it on the SD Card) I get a similar error message.

How do I restore permissions, so I'm the owner again?

Is there any way of fixing these problems, without re-installing Ubuntu.  I have files I cannot afford to lose, some are backed up and some are not.

Also, I'm not a power user of Linux / Ubuntu, so please keep that in mind when posting solutions.

I appreciate and thanks in advance for all the help.  Only valid working suggestions please.

PS: Is there a How-To on, I'd like to set up, e.g. 3 workspaces:
    1. For Work / Daily Use,
    2. For Study, and
    3. For Games / Entertainment

With corresponding names, (Not the Default 'Desk 1', 'Desk 2', etc.), software, different wallpaper and themes, mostly used files, etc.  Can it be done?

Thanks once again for all the help.[/SIZE][/FONT]

---

