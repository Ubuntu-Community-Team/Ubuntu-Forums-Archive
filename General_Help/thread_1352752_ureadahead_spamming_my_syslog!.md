---
title: "ureadahead spamming my syslog!"
date: 2009-12-12
forum: General Help
---

### Post by Kensey on 2009-12-12
While tuning up my system last night, I noticed that something was slamming the HD pretty hard.  iotop showed rsyslogd topping the I/O pretty frequently.  Looking at the syslog, I was seeing messages like this 4 times a second:

Dec 11 01:49:35 localhost init: ureadahead-other main process (7570) terminated with status 4

There's a [bug open about it]("https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/484677") in Ubuntu's Bugzilla.  The maintainer seems to think the real bug is the output of the messages -- but I'm more interested in fixing whatever is causing this process to flap in the first place.  For the moment I have the exec lines in both ureadahead.conf and ureadahead-other.conf commented out, which has at least given my syslog a break.

Of note is that after finding and working around this issue, I found that mountall was hammering my HD (continuously trying to mount my hibernated Windows partition).  Maybe with that problem fixed, this problem will go away on its own?

---

### Post by lamego on 2009-12-12
The bug that you have linked does is about a few messages during startup, not as spamming. 
I am experiencing endless logging of the message, reported it now on [bug 495917]("https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/495917")

---

### Post by Zularan on 2009-12-15
Had this problem too after moving hard drives around.
Was spamming rsyslog -c4 like mad and it was corrected when I fixed my 'fstab' to match the new hdd layout.

Guess it was trying to mount a drive that was /dev/sda3 instead of my new /dev/sda5 and I'd changed the drive format.  Once I made sure my fstab matched my hard drive/partition setup the problem went away.

But yeah,

```
Dec 15 14:42:12 david-xps init: ureadahead-other main process (29105) terminated with status 4
Dec 15 14:42:12 david-xps init: ureadahead-other main process (29112) terminated with status 4
Dec 15 14:42:12 david-xps init: ureadahead-other main process (29119) terminated with status 4
Dec 15 14:42:12 david-xps init: ureadahead-other main process (29126) terminated with status 4
Dec 15 14:42:12 david-xps init: ureadahead-other main process (29133) terminated with status 4
Dec 15 14:42:12 david-xps init: ureadahead-other main process (29140) terminated with status 4
Dec 15 14:42:12 david-xps init: ureadahead-other main process (29147) terminated with status 4
Dec 15 14:42:12 david-xps init: ureadahead-other main process (29154) terminated with status 4
Dec 15 14:42:12 david-xps init: ureadahead-other main process (29161) terminated with status 4
Dec 15 14:42:12 david-xps init: ureadahead-other main process (29168) terminated with status 4
Dec 15 14:42:12 david-xps init: ureadahead-other main process (29175) terminated with status 4
Dec 15 14:42:12 david-xps init: ureadahead-other main process (29182) terminated with status 4
Dec 15 14:42:12 david-xps init: ureadahead-other main process (29189) terminated with status 4
Dec 15 14:42:12 david-xps init: ureadahead-other main process (29196) terminated with status 4
Dec 15 14:42:12 david-xps init: ureadahead-other main process (29203) terminated with status 4
Dec 15 14:42:12 david-xps init: ureadahead-other main process (29210) terminated with status 4
Dec 15 14:42:12 david-xps init: ureadahead-other main process (29217) terminated with status 4
Dec 15 14:42:12 david-xps init: ureadahead-other main process (29228) terminated with status 4
Dec 15 14:42:12 david-xps init: ureadahead-other main process (29247) terminated with status 4
Dec 15 14:42:12 david-xps init: ureadahead-other main process (29254) terminated with status 4
Dec 15 14:42:12 david-xps init: ureadahead-other main process (29261) terminated with status 4
Dec 15 14:42:12 david-xps init: ureadahead-other main process (29268) terminated with status 4
Dec 15 14:42:12 david-xps init: ureadahead-other main process (29275) terminated with status 4
Dec 15 14:42:12 david-xps init: ureadahead-other main process (29282) terminated with status 4
Dec 15 14:42:12 david-xps init: ureadahead-other main process (29289) terminated with status 4
Dec 15 14:42:12 david-xps init: ureadahead-other main process (29296) terminated with status 4
Dec 15 14:42:12 david-xps init: ureadahead-other main process (29303) terminated with status 4
Dec 15 14:42:12 david-xps init: ureadahead-other main process (29310) terminated with status 4
Dec 15 14:42:13 david-xps init: ureadahead-other main process (29317) terminated with status 4
```


every second was slowing things down and had the drive / syslog going crazy.

Hope this helps.

---

### Post by Cimmo on 2010-01-02
Edit /etc/fstab and comment any Windows partitions mounted.

---

### Post by Maxei on 2010-01-16
Hi cimmo, thanks for the post. I checked my fstab and what a nasty surprise ! it looks as though my /etc/fstab has been totally re-invented. How come??? Please take a look at it and please advice:
--------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=bf675647-c966-47c6-af5a-b77cf8afce4c /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda5 during installation
UUID=7d774552-43d2-4fb6-bb26-2d2d98ff620f /boot           ext4    defaults        0       2
# /home was on /dev/sda6 during installation
UUID=534e92dc-53c3-4211-b48e-b02e860e5077 /home           ext4    defaults        0       2
# /tmp was on /dev/sda8 during installation
UUID=9787faa7-39d9-416f-8f42-c632be1dc9a2 /tmp            ext4    defaults        0       2
# /usr was on /dev/sda7 during installation
UUID=f57be107-3cba-4c99-a6ad-b92cb3da4c31 /usr            ext4    defaults        0       2
# /var was on /dev/sda4 during installation
UUID=cdaac3ae-0a32-4365-88f9-90ee8f42b903 /var            ext4    defaults        0       2
# swap was on /dev/sda3 during installation
UUID=8c07a20a-1be1-463b-993b-bcecb607c4df none            swap    sw              0       0
/dev/sdb1	/media/disk1	ext3	user,noauto,exec,rw	0	2
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
------------------

So, what on earth these UUID=crazylong numbers mean? My fstab file was not like this before. THis is Karmic clean install and now I have ureadahead errors all the time at boot. I believe this happened after some fukcing update. For sure the system modified fstab, puting all those long garbage numbers. Please advice. Thanks

---

### Post by Kensey on 2010-01-27
> **Maxei said:**
> So, what on earth these UUID=crazylong numbers mean? My fstab file was not like this before. THis is Karmic clean install and now I have ureadahead errors all the time at boot. I believe this happened after some fukcing update. For sure the system modified fstab, puting all those long garbage numbers. Please advice. Thanks

The UUID is a unique way of identifying a filesystem.  It's mostly useful for situations where a device's name may change (e.g. a USB disk volume may be /dev/sdb1 if it's plugged in at boot, but /dev/sdc1 if it's plugged in later after another external disk is plugged in).  The UUID identifies the same filesystem no matter what its device name is, so you can mount reliably using the UUID.

You can see the mapping between UUIDs and device names by doing:

```
ls -l /dev/disk/by-uuid
```

---

### Post by bl8n8r on 2010-03-26
> init: ureadahead-other main process (7570) terminated with status 4

# aptitude purge sreadahead ureadahead 
works for me ;)

---

