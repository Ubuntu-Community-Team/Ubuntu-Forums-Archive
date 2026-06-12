---
title: "Looks like I accidentaly modified file system type"
date: 2010-01-20
forum: General Help
---

### Post by Lender on 2010-01-20
Hi everybody, sorry for disturbing you, but I need some Help, as I'm quite newbie in Ubuntu/Linux and especially in partition.

I was just disturbed by the fact that i needed to put my password to mount my data partition (the one I use to save data in general), and I went to Disk Utility to change it. I've marked the option bootable and changed it. But it seems that the File System Type was changed, because neither windows, nor ubuntu could recognize this partition.

Now I don't know what to do. I would be very grateful if you guys could help me out. Thanks

EDIT: Just to say. Looks like it wasn't formated, because after the changes and before restarting my PC, I could still use the disk.
And sorry if my english is bad >_>.

---

### Post by majickmann on 2010-01-20
First change your data partition back so it is not bootable.  Never set a data only partition to boot.

Second, is your data partition on NAS or nfs?  When I have an nfs mounted, the password prompt provides three options...  do not save password, save password for this session only, or save forever.  Wording may be slightly different but meanings the same.  Obviously, I select "save forever" so it does not prompt me again.

You have to determine whether this is a good policy or not.

Hope this helps...

:-)
--majickmann

---

### Post by Lender on 2010-01-20
I've already tried it, but it's not working. I think I got confused and really changed the file system to try to recover the partition. Changed it to NTFS and just put not bootable, but still not working.

What should I do, as it was formated originally as NTFS by Windows 7? =/

Is there any way to recover the partition?

---

### Post by jamesisin on 2010-01-20
You say you changed the file system type.  That would be pretty bad and also pretty difficult to accomplish.  It is more likely that you changed the file system type designation (in your fstab file for instance).

What do you get from running this command:

sudo fdisk -l

---

