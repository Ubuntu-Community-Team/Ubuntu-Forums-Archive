---
title: "EXT4 mount options for data safety"
date: 2010-03-26
forum: General Help
---

### Post by cryptotheslow on 2010-03-26
Hi,

I've had a lot of recent problems with frequent lock-ups (complete hardware lock requiring power-cycle) - mostly cured now by adding the *clock=hpet* option to grub.

What I noticed after those lock-ups was that I would lose any recent changes to documents I was working on - i.e. any changes saved within the last 2 minutes or so before the lockup. Very frustrating when you're making lots of small changes to multiple html files whilst re-designing a website, as each time you have to backtrack to see what has or hasn't stuck.

Having read around this seems to be an EXT4 "feature" to improve performance and I've been lucky not to end up with completely empty files.

So need some advice on EXT4 mount options to improve data safety (yes I know this will be at the expense of performance).

As far as I can tell from [http://ubuntuforums.org/showthread.php?t=1096467](http://ubuntuforums.org/showthread.php?t=1096467) these 2 options should do it:
[B]
data=journal[/B] All data are committed into the journal prior to being
written into the main file system.

**commit=nrsec **(*) Ext4 can be told to sync all its data and metadata
every 'nrsec' seconds.

Just need some confirmation from someone who knows more about filesystems than me (which is nothing) that this will indeed help and not break anything.

Current fstab looks like this:
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=2626561b-9f95-4b63-a19c-d64fe74cb134 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=268ce370-49a3-4e70-9a12-40901c9b1f0a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```I presume I can just add the options like this (??):
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=2626561b-9f95-4b63-a19c-d64fe74cb134 /               ext4    errors=remount-ro data=journal commit=5 0       1
# swap was on /dev/sda6 during installation
UUID=268ce370-49a3-4e70-9a12-40901c9b1f0a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```
Apologies for the long post and thanks in advance for any help :)

Ta
Graham

---

### Post by gmargo on 2010-03-26
First of all, _***STOP***_!  Think about it.  Do not do experimental tests on your root filesystem.  Use a throw-away partition or a file mounted in loopback.

Update: (had to get the above out).  Mount options should be separated by a comma, not space.  Assuming your options are correct, that would be: 
errors=remount-ro,data=journal,commit=5

---

### Post by cryptotheslow on 2010-03-26
Thanks gmargo, I'll try it on a new junk partition first - once I have confirmed it ~should~ help as I think it will.

---

