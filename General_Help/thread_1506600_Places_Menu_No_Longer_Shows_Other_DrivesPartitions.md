---
title: "Places Menu No Longer Shows Other Drives/Partitions"
date: 2010-06-10
forum: General Help
---

### Post by wkulecz on 2010-06-10
The Gnome "Places" menu used to show my other drives/partitions, now they are gone.  Is this a side effect of the recent updates?

How do I get the old behavior back?

If I open "Computer" I see them listed in the icons and double clicking the icon mounts the drive/partition

Just noticed, its even worse :(

CDs don't automount anymore.  Have to open Computer and double click the CD Icon.  This is not progress, in fact its a regression to the behavior in 6.06 :(

---

### Post by wkulecz on 2010-06-11
Bump, no help?

I've figured out a repeatable situation where the drives will appear in Gnome Places menu or not, depending on how the system is configured when I boot.


Its a multi-boot system -- 10.04, 8.04, 6.06, Windows 2000.

Windows 2000 is on IDE primary master, DVD burner on primary slave.

Secondary master has a removable drive carrier, used for system cloning, beta tests etc. Secondary slave is never used.

SATA 1 is the Ubuntu disk, four primary partitions, for the three OS versions and swap.

SATA 2 is a duplicate disk partitioned the same and used as a target to back up the Ubuntu systems nightly via rsync.  This drive I *do not* want visible in the Places Gnome menu.


Back in the days of 6.06 I learned if you don't want a drive/partition showing in Places, make an /etc/fstab entry for it, but set noauto after the defaults for the mount options.  This still works (either if the drives show in places or not, as they don't show up in Computer either case) and I mount the backup partitions as needed from the cron script that does the rsync backup and has worked well for years (and still does).


Basically if the removable carrier is empty when the system boots (the "normal" situation) then none of the other three partitions (6.06, 8.04, W2K) are in the places menu, although they can be mounted by opening up "Computer" and clicking their icon.

If the removable carrier has a drive (doesn't seem to matter as long as its got a mountable filesystem) in it, then I get the entries for the drives/partitions I want, along with what is on the dirve in the carrier, in the Places menu.

Anyone know what the heck is going on here?


I've not enjoyed fighting with grub2 and the new dynamic drive mapping scheme.  UUID mounts appears to be the final solution, but this is a major PITA since the UUID are nearly impossible to type in and impossible to know before putting the drive in a working system -- those ~$30 USB drive adaptor dongles have been a life saver here.
all the partitions are labeled to avoid having gibberish like /media/35786097-c6fc-449d-a244-a7283b01fcdc in rsync commands :(

---

### Post by X-Windows on 2010-06-11
Perhaps slightly off topic, but how exactly did you remove them from the places menu? I would prefer to be able to set my bookmarks instead of having Gnome tell me what goes in the places menu.

---

### Post by wkulecz on 2010-06-11
As I said you just add an entry to the /etc/fstab file of the partition you don't want displayed in Places or Computer.

You'll have something like this in your fstab from the install:

UUID=65bb1818-046d-4ca4-baee-86fd3406d915 /  ext4    errors=remount-ro 0   1

For the partition you don't want to be visible add:
/dev/sdd1 /media/foobar  ext4    defaults, noauto 0   1

And the sdd1 partition will not appear.  Although with 10.04 you have to use UUID instead of /dev entries if you expect it to survive trivial system mods.

Get the UUID with sudo blkid when the drive is mounted.

you can then mount the partition with:
mount /media/foobar

HTH,

I have no idea how to add a "bookmark" to the places menu except for network shares where it offers you the option when you connect.

--wally.

---

### Post by nerdzero on 2010-06-11
Check the value of /apps/nautilus/preferences/media_automount in gconf-editor.  Maybe it got unchecked somehow.

---

### Post by radddi on 2010-06-12
I have the same problem. However, upon checking gconf-editor it turns out that the setting /apps/nautilus/preferences/media_automount is set to TRUE! The drive (a nokia mobile phone in my case) used to automount just fine. Can this be some sort of nautilus bug?

---

### Post by kesten on 2011-10-10
I just had the same thing happen to me.

I was trying to change the permissions on ./opt/py32 so i could download to it.
Using Home Folder I went to File->Permissions.  Options for sharing were greyed out so I tried sharing it.  Download and update status bars ran for a while.  Then i was prompted to restart the computer for the changes to take effect.

And voila, no more OS or DATA drives, only my ubuntu partition "File System" and home directory are in Places now.  Definitely seems like a bug to me.

kesten

running ubuntu 11.04, switched from windows7 to a dual boot 3 days ago.

---

### Post by kesten on 2011-10-10
"If I open computer and click on them..."

How do you do this?  My OS and DATA seem to have been dis-mounted.  Sim links pointing to files contained therein say target doesn't exist.

kesten

Ok, found it.  With Home Folder active go to the menu Go -> Computer.  Double click and they reappear.  Sim links to targets now work.  Lifesaver workaround for now.  thanks.

---

