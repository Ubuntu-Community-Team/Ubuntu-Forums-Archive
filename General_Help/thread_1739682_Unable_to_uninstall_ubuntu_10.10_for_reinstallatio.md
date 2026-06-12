---
title: "Unable to uninstall ubuntu 10.10 for reinstallation on new partition"
date: 2011-04-26
forum: General Help
---

### Post by infinitifizz on 2011-04-26
Hi,

I am a complete ubuntu noob so bear with me, but I recently installed Ubuntu 10.10 (to make me do more work by taking away the distractions of Windows games etc) but for some reason it decided to install on a really small partition even though I left everything as default and so after about 1 day of using it and installing some programs it keeps warning me "There is only 11mb free space!" etc. and everything runs really slow because of this.

So I am wanting to uninstall ubuntu and grub so I can reinstall them but I don't know how to uninstall. In win7 if I go into Computer>Manage>Storage>Disk Management, there is no Ubuntu partition, just the 1TB partition that win7 is on, so I can't go about the "deleting the partition" method that people have given as a solution on this and other forums.

A screenshot of what my DiskManagement looks like is attached.

Has anyone got any idea where ubuntu is hiding? And how I could go about uninstalling, properly setting up a partition and reinstalling?

Thanks for your time,

Infinitifizz

---

### Post by Ronalddig on 2011-04-26
how did u install, wubi or using seperate partitions

---

### Post by Mark Phelps on 2011-04-26
You didn't install it in a really small partition; you used Wubi and installed it inside your NTFS partition in a file that it created.  It's small because that is the default file size for Wubi installs.

To remove it, you simply use Programs and Features in Win7 and remove it -- like any other program.

To properly reinstall it, I would suggest the following:
1) Make a Win7 Repair CD: Go into Backup feature in Win7 and use the option to create and burn a Win7 Repair CD.  You might need this later to repair the boot loader.
2) Go into Disk Management and use that to shrink the Win7 OS partition to make some room for Ubuntu.  Do NOT format the new unallocated space.
3) Insert the Ubuntu CD and install it to the unallocated space -- but be VERY CAREFUL.  If you end up accidentally formatting the wrong space, you will erase your Win7 install.

---

### Post by infinitifizz on 2011-04-26
Ahhh I did this a few months back and so completely forgot I did a wubi install, I'll do it the partition way this time.

Thanks so much for the help and I'll report back how it went.

---

