---
title: "Can't find Windows Partition after switching from Ubuntu to Xubuntu"
date: 2011-02-13
forum: General Help
---

### Post by haunty on 2011-02-13
Hello!

I've switched from Ubuntu Hardy to Xubuntu using the terminal. The only problem is I can't find my WinXP partition any more. In Ubuntu I used to mount it by going to 'Places' menu and clicking the folder icon. It's now gone. I can't see the icon in Xubuntu.

Been reading other threads trying to find out what to do, but I'm relatively new to Linux. I can't find the folder under /media either. Also, I don't know what types my partitions are. Is this important? I figured I could access my Win folder in Xubuntu the way I would in Ubuntu. Was I wrong?

---

### Post by Hippytaff on 2011-02-13
I'm not up to speed with xfce but I think you have to edit the fstab file so that the windows partition mounts and is visable from xubuntu - however messing with fstab is dodgy if you don't know what your doing so read the man page and see [this thread]("http://ubuntuforums.org/showthread.php?t=920358")

And welcome to the forums :-)

---

### Post by aeiah on 2011-02-13
the difference is that thunar (xfce's file manager) doesnt populate the places bar on the side with partitions.

i think the way nautilus does it is it'll mount it for you the first time you click on it (within a session) so that's why it isnt in /media

best route would be to mount it permanently in fstab, then you can bookmark it or whatever you like. you'll need to identify which partition is your windows partition. there are several ways to do this and there should be tutorials aplenty scattered around the interwebs.

---

### Post by haunty on 2011-02-13
Thanks for the quick replies and the welcome. I've solved the problem. In case someone needs to know this in future, here's what I did:

Note, the partition is fat32, not ntfs.

To identify your win drive type in terminal: sudo fdisk-l.
In my case it is: /dev/sda1

Then type:

sudo /bin/bash
mkdir /media/disk
mount -t vfat -o umask=000 /dev/sda1 /media/disk

Close terminal.

The outcome is that I have the partition mounted under /media/disk.
It worked for me, but pls note that I'm a complete noob, so you'll do this at your own risk.

---

### Post by Hippytaff on 2011-02-13
Glad you sorted it - I'll make a note of your fix for future reference :-)

---

