---
title: "Moving /home folder to new install"
date: 2009-10-10
forum: General Help
---

### Post by dyingsun on 2009-10-10
Hi all

I've backed up my /home/user folder on an external HDD, and I'm going to install Jaunty. (Currently using Hardy, time for an update, methinks.)

I assume I can copy my backed up home folder into the new installation with no dramas, from the command line? Can I just use cp -i pr something like that? Just looking for expert opinion before I make the move and stuff everything up :)

Any other tips to make the process smoother?

Thanks in advance!
Damien

---

### Post by t0p on 2009-10-10
I don't think it's as simple as just copying and pasting your existing /home into a new install.  I *think* you need to create a new partition for /home on your current installation (as described [here]("http://www.psychocats.net/ubuntu/separatehome")), then when you do the new installation, make a separate /home partition there (like [this]("http://www.psychocats.net/ubuntu/installseparatehome")).

Alternatively, you can back-up all your files, and the various application config files that exist in your /home directory (they're "hidden" files, whose names begin with a "."), and paste them into your new /home.  Not quite the same as copying and pasting your entire /home directory.

---

### Post by slakkie on 2009-10-10
It is as simple as cp'ing files from A to B. Or from external device to $HOME in this case. I do this regulary, just to have a backup of my homedir on an external disk. When I remove my /home partition for whatever reason I can restore it. My external disk has ext3 filesystem so all permissions are the same:

```

# backup
cp -rp $HOME /path/to/external/disk/
# restore
cp -rp /path/to/external/disk/$USER /home

```

If you have FAT or NTFS you might want to run:

```

# Backup
cp -r cp -rp $HOME /path/to/external/disk/
find $HOME -exec stat -c "chmod %a %n; chown %U:%G %n" {} + > /path/to/external/disk/homedir.permissions
# Restore
cp -rp /path/to/external/disk/$USER /home
bash /path/to/external/disk/homedir.permissions

```

The only thing you need to be aware about it to login/logout once you are done. Because not all settings will work right after the copy action is done.

Creating a seperate slice to mount as /home is a good idea, so you don't need to cp over files after a fresh install because you just will say to the installer use /dev/sda6 (this will be different on your install no doubt) should be mounted as /home.

---

### Post by 3rdalbum on 2009-10-10
Yes, you can copy your files over. Make sure you copy all the hidden files and directories to the backup!

Actually, the recent Ubuntu installers will be able to see that you have an existing home directory on the destination disk and will be able to retain its contents as long as you use the "Manual partitioning" screen and don't click the "format" checkbox for the partition. I still recommend backing up though, you wouldn't want to be hit by an undiscovered bug in Ubiquity!

---

### Post by t0p on 2009-10-11
Ooops! Well, I didn't know that.  But now I do.

Thanks for the education folks.

---

### Post by dyingsun on 2009-10-12
Thanks for your replies everyone, I installed 9.04 Studio 64, copied my home folder across, chowned it and it was all hunky-dory. And I want to go back to Hardy :(   I´m getting freeze after freeze - spent the last 24 hours googling (through the Mint 7 box) and AFAIK there are issues with nVidia. (Im using a Gigabyte mobo with integrated nVidia graphics). Worked beautifully on Hardy, is a disaster on Jaunty. Cant seem to figure out a fix for it :(

Oh well, thanks again all!

---

### Post by dyingsun on 2009-10-13
Just in case anybody is interested...

I wiped the system clean of my 9.04 Studio 64 install, and installed a regular, desktop Jaunty from an image I burned several months ago. So far (touch wood) it hasn't crashed once. My hardware is all working, out of the box, even set my printer up in 30 seconds! No proprietary graphics drivers. 250mb of updates waiting for me, but this time neither Update Manager nor Synaptic are crashing the system. It's all good so far, Im just adding the packages bit by bit. 

Still not sure what was causing the lockups. But happy its not happening anymore! :-D

---

### Post by P4man on 2009-10-13
best guess: a kernel update conflicting with your acpi bios. If you start getting freezing again, boot an older kernel, or try some acpi switches. I read somewhere that they recently turned off some workarounds in the kernel for buggy bioses to put the incentive again to bios developpers to fix their stuff

---

### Post by dyingsun on 2009-10-13
Thanks P4Man, I haven't had a lick of trouble since I wiped 9.04 Studio off and replaced it with the normal desktop version. Is the kernel different between Studio and the normal ver? I've got the most recent one that Update manager has thrown at me, and that's the one I'm booting. its good thus far, still using Open drivers. Hi graphics stuff is still a little choppier than it used to be under Hardy, I might give the NVidias a go.

---

### Post by P4man on 2009-10-14
> **dyingsun said:**
> Thanks P4Man, I haven't had a lick of trouble since I wiped 9.04 Studio off and replaced it with the normal desktop version. Is the kernel different between Studio and the normal ver?

Yes, I think studio uses a realtime kernel.

---

