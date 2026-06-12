---
title: "Urgent and serious data loss problem"
date: 2009-08-23
forum: General Help
---

### Post by MartinEve on 2009-08-23
Hi all,

I am having a seriously bad day as, when I started my PC today, all my work from yesterday afternoon was gone - about 7 hours worth.

After a bit of digging around, I can prove that I am *not* going mad and am working on the correct PC. My auth.log contains the following line:

```

2009-08-22 18:21:04	theoria	sudo	  martin : TTY=pts/4 ; PWD=/home/martin/Projects/DataExecutor ; USER=root ; COMMAND=/usr/bin/gacutil -i mysql.data.dll

```

But today, /home/martin/Projects/DataExecutor does *not* exist.

My .bash_history contains none of my console commands from yesterday.

My downloads from yesterday are gone.

In short *no* file inside my home directory seems to have been modified yesterday.

The sequence of events:

1.) Boot PC.
2.) Sign-in (KDE 4.3)
3.) My wife starts her own session (Switch user)
4.) I resume my session (leaving hers running)
5.) *snip* (lots of work)
6.) I shutdown (terminating her session)
7.) I boot today (fsck runs) - all data in /home/martin since yesterday gone

/etc/fstab
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0

# ROOT /
# /dev/sda6
UUID=5a780978-59b1-44f0-960d-ee330a46eb30 /               ext3    relatime,errors=remount-ro 0       1

# SWAP /swap
# /dev/sda5
UUID=3e8b300d-ce0a-4742-93f6-53a78251f417 none            swap    sw              0       0

# CDROM drive
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

# REDUNDANT entry for RAID on ntfs
#/dev/mapper/nvidia_babcffib1 /media/RAID ntfs-3g defaults,nls=utf8,umask=022,uid=1000,gid=1000 0 1

# HOMEDIR mounted on FAKE-RAID /home
/dev/mapper/nvidia_babcffib1 /home ext3 relatime,errors=remount-ro 0 1

# mdadm SOFT-RAID
/dev/md/d0      /home/martin/Music2     ext3    defaults,noauto,user    1 0

```

Please someone tell me what has happened :(

If someone reported this to me, I know I would be completely incredulous and claim it can't have happened, or that I was "on the wrong PC"; the auth.log confirms that this is not the case. This monitor and mouse are connected to *one* pc that has not changed since yesterday.

Please help.

Martin

---

### Post by bchurchill on 2009-08-23
Sounds like a bad day.  :/

Have you checked with your wife on if she's missing files?  That seems like the obvious thing to do. You may also want to check /var/log/syslog and /var/log/messages for what was going on during those seven hours or so, if anything.  I'd be very surprised if all those logs were blank.  You may also want to try running

```

find -atime +0 -atime -2

```in a folder that seems to have missing files.  That will list all the files accessed between 1 and 2 days ago.  Hopefully you may be able to find something that will give you a clue... check with the man if you need to adjust the time on that.

EDIT: another possibility: are the files that are missing on a separate partition?  like maybe a home partition not mounted?  seems unlikely...

Good luck!

---

### Post by MartinEve on 2009-08-23
Hi,

Many thanks for your reply - greatly appreciated.

I've been running find commands on the whole system this morning to no avail.

The only action my wife took was to read some Wikipedia articles in Firefox.

Her Firefox history no longer holds this activity.

Indeed, were it not for the presence of the auth.log entry, this would lead me to believe that yesterday did not occur!

It seems that nothing inside the /home directory (a dmraid mounted array) was written to any time after 10.31.27 yesterday:

find ~/ -type f -daystart -mtime 1 -printf '%p %a\n'
```

/home/martin/.thumbnails/large/6207aeba5a460b712b33872c2136785f.png Sun Aug 23 09:31:40.0000000000 2009
/home/martin/.beagle/Log/2009-08-22-08-24-58-BeagleExceptions Sat Aug 22 08:25:06.0000000000 2009
/home/martin/.beagle/Log/2009-08-22-08-35-05-IndexHelper Sat Aug 22 08:35:05.0000000000 2009
/home/martin/.beagle/Log/2009-08-22-08-24-58-Beagle Sat Aug 22 08:24:58.0000000000 2009
/home/martin/.kde/share/config/nepomukserverrc Sat Aug 22 10:31:27.0000000000 2009
/home/martin/.kde/share/config/gwenviewrc Sat Aug 22 10:30:43.0000000000 2009
/home/martin/.kde/share/config/nepomukserverrc~ Sat Aug 22 08:35:12.0000000000 2009
/home/martin/.kde/share/apps/gwenview/recentfolders/P10271rc Sat Aug 22 10:30:44.0000000000 2009
/home/martin/.kde/share/apps/kabc/std.vcf_6 Sat Aug 22 10:31:27.0000000000 2009

```

Around this time I was trying to fix a problem with gwenview crashing and had just reinstalled the soprano-sesame backend for nepomuk. I can't really imagine how this could cause the problem.

In order to ascertain the sequence of events, I then ran:

sudo find / -type f -daystart -mtime 1 -printf '%p %a\n' > find3.txt

This yielded some interest.

The next file write was:
```

/var/log/dmesg.2.gz Sat Aug 22 10:34:48.0000000000 2009

```

Inspection of dmesg.2.gz revealed the following, suspect, entries:
```

[  145.224176] kjournald starting.  Commit interval 5 seconds
[  145.224184] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[  145.224353] sd 2:0:0:0: [sdc] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  145.224357] end_request: I/O error, dev sdc, sector 2048
[  145.224506] EXT3 FS on dm-1, internal journal
[  145.224511] EXT3-fs: mounted filesystem with ordered data mode.

```

*SNIP*

```

[  143.852069] sd 2:0:0:0: [sdc] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  143.852073] end_request: I/O error, dev sdc, sector 18706576
[  143.852078] device-mapper: raid1: Mirror read failed from 8:32. Trying alternative device.
[  143.852102] sd 2:0:0:0: [sdc] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  143.852105] end_request: I/O error, dev sdc, sector 390338576
[  145.224176] kjournald starting.  Commit interval 5 seconds
[  145.224184] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[  145.224353] sd 2:0:0:0: [sdc] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  145.224357] end_request: I/O error, dev sdc, sector 2048

```

I am assuming that:

1.) The write failed to one of the disks
2.) It was written only to the other disk
3.) The hardware (on reboot) spots the desync between the mirrors and decides to resync them, only it fails and...
4.) Copies the unwritten to disk onto the written-to disk

Does this sound plausible?

Martin

---

### Post by tredegar on 2009-08-23
It's a long-shot, but maybe try this:

```

sudo -i                             #Become root
cd /root                            #if you are not already in /root
umount /dev/mapper/nvidia_babcffib1 #Unmount your /home
ls /home/martin                     #Were your files "hidden" by the mount?
                                    #if so, copy them to /root/Martin (for example) then
mount /dev/mapper/nvidia_babcffib1  #and copy then back where they belong
```

Also, note that you have warnings about it being time for you to run **fsck**

---

### Post by MartinEve on 2009-08-23
Tredegar - thanks for the suggestion. Unfortunately, I had already tried this by booting into a recovery console and umounting my home dir. Sadly, nothing hidden.

I think this is the softraid gone severely awry. I will, therefore, backup all my data onto another PC and, in future, work with Unison to sync 2 HDDs across my network :(

---

