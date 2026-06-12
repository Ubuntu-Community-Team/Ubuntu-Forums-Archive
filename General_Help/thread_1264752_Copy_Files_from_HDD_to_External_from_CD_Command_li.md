---
title: "Copy Files from HDD to External from CD Command line"
date: 2009-09-12
forum: General Help
---

### Post by dandrews on 2009-09-12
I have a Hp pavilion dv3500rn with windows installed, windows will not boot into anything other than safe mode. At this point I am going to wipe the hard drive but I need the files off my HDD.

Provided that I am booted into the Ubuntu cd, what are the commands from the terminal that I should use to copy the files from my HDD to my External USB drive?

I am fairly experienced in the terminal, but I am compiling instructions for a friend who is a complete beginner. 

Thanks

---

### Post by PeEllAvaj on 2009-09-12
Perhaps I am misunderstanding the goal, but with an Ubuntu live CD it should be fairly simple to open the windows (ntfs) disk, and copy and paste onto an external drive, all using the nautilus gui (or dolphin with Kubuntu).

Things from the command line are more complicated for beginners, as the drives have to be mounted, you have to know where the drive was mounted, and then use a simple rsync or copy command.

Could you explain more about the goal if I am missing something?

---

### Post by ddrichardson on 2009-09-12
Backing up?

You need to mount the two drives, the external drive should be picked up when inserted if running from a Live CD.

Of course, Nautilus would be easier but if for whatever reason you're using the terminal then you need to mount from the command line.

If you do:```
sudo fdisk -l
```
It should be clear which partition is your Windows one, most likely /dev/sda1.

Then mount them, you might need to create a directory to mount to.
```
mkdir ~/windows
mount /dev/sda1 ~/windows
```

You may need to use the ntfs-3g utilities, not to sure about the Live CD. If you do its the same, only substitute "mount" for "ntfs-3g".

---

