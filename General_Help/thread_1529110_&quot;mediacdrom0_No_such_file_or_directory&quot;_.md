---
title: "&quot;/media/cdrom0: No such file or directory&quot; After Fresh Lucid Install. How to Fix????"
date: 2010-07-11
forum: General Help
---

### Post by OzzyFrank on 2010-07-11
**[COLOR="DarkRed"]/media/cdrom0: No such file or directory[/COLOR]**

This is what the terminal throws at me, and is something I haven't had to deal with for ages, as any launchers pointing to my disc drive, and any command-line aliases using it, have worked throughout many upgrades.

However, I've just done a fresh install, and copied over a bunch of settings, and going to do a routine disc verification threw that message at me. It seems that now (in this fresh install, not my upgraded 10.04 system) each disc is mounted in a different folder based on the name (eg: **/media/Documents Backup**), meaning each disc will have a totally different mount point (which is useless for launchers and bash aliases!).

How do I make a permanent link or whatever to /media/cdrom0? And anyone know what actually changed to make this happen?

---

### Post by OzzyFrank on 2010-07-11
Also noticed the command **[COLOR="Red"]mount|grep ^’/dev’[/COLOR]** (to list mount points etc) no longer does anything - no output, no error message, just back to the prompt without seemingly doing anything.

---

### Post by cariboo on 2010-07-11
Udev looks after mounting CD/DVD's they should automagically mount the disk:

```
ls -l
total 18
drwxr-xr-x  2 root root 4096 2010-07-10 12:01 documents
drwxr-xr-x  2 root root 4096 2010-07-10 12:01 movies
drwxr-xr-x  2 root root 4096 2010-07-10 12:01 music
drwxr-xr-x  2 root root 4096 2010-07-10 12:01 stuff
dr-xr-xr-x 10 jimk jimk 2048 2010-07-07 00:09 Ubuntu 10.10 amd64
```

As you can see from the output above, the CD is mounted as **Ubuntu 10.10 amd64**.

---

### Post by OzzyFrank on 2010-07-12
**[COLOR="Red"]ls -l[/COLOR]** worked fine (still kinda freaked **[COLOR="Red"]mount|grep ^&#8217;/dev&#8217;[/COLOR]** didn't, since that recently worked in my upgraded system... so not sure why in this fresh install that command gives nothing).

Anyway, I might have to boot up the old upgraded system I'm migrating from, and see what gives. I know old bits and pieces survive throughout upgrades, and you only notice their absence in a fresh install. I always had the feeling **[COLOR="Purple"]/media/cdrom0[/COLOR]** was just a default mount point for optical drives, since I've seen it for so long, but who knows, perhaps I created a symlink or ran some commands to always that path accessible to commands/launchers.

But I think this may be something new (c'mon, I'm sure some of you have been following development and already know all about this), though figure there must be a way to have a permanent mount point for the CD/DVD drive. Maybe I even specified it in **fstab**, which I haven't bothered touching in this new system, so will look into that too.

**EDIT:** Figured out why **[COLOR="RoyalBlue"]mount|grep ^&#8217;/dev&#8217;[/COLOR]** didn't work - I copied it from my WordPress blog, and they do this stupid autoformatting which in fact changes the characters (only just found about about this), rendering commands relying on the correct characters useless. The correct command with quotes retyped is: **[COLOR="RoyalBlue"]mount|grep ^'/dev'[/COLOR]**

---

### Post by OzzyFrank on 2010-07-12
Just so everyone is clear about what I am trying to achieve, and why:

With mount points for discs automagically being created based on the label (which usually I would think is cool), commands like the following are rendered useless:

**[COLOR="DarkGreen"]cd /media/cdrom0 && md5sum -c md5sum.txt[/COLOR]**

I would have to tailor each command individually to show the correct path (which I'd have to go check first), and so much for running that command (or 2 commands together, actually) by typing an easy alias like **[COLOR="DarkGreen"]cd5[/COLOR]** (which is all I ever have to do to verify the data on any disc with an *md5sum.txt* file).

I have a whole bunch of commands ready to be run with easy to remember aliases, even a panel launcher to immediately erase a rewritable without further input, but they all rely on the disc's mount point being **/media/cdrom0**. As you can imagine, auto-changing mount points is totally messing this up, which is why I am trying to figure out how to set it to what I want permanently. Cheers

---

### Post by OzzyFrank on 2010-07-12
PS: Running **wodim --devices** gives me **[COLOR="Red"]/dev/scd0[/COLOR]**, but running **sudo mount -t iso9660 /dev/scd0 /media/cdrom0/** (with no disc in the drive), ends up with **[COLOR="Red"]mount: no medium found on /dev/_sr0_[/COLOR]** (only mentioning that in case the different device name means anything).

Of course, trying to mount it with a disc in the tray (ie: when it is already mounted) throws up an error, which in this case is mount: block device /dev/sr0 is write-protected, mounting read-only. At the moment, it seems I would have to unmount a disc after it is mounted, then mount it again to **/media/cdrom0**, so if there is actually a way to turn of this label-based mounting, I'd appreciate the info!

---

### Post by OzzyFrank on 2010-07-14
OK, I figured it out, and it is indeed an **[COLOR="Red"]fstab[/COLOR]** issue. My **fstab** has pretty much stayed the same throughout upgrades (except for a couple of years back when I had to set mounting of drives based on UUIDs, as drive paths kept changing on me). One thing I am pretty sure I never had to set myself was the mounting of discs, which explains why so many out there share the path of **/media/cdrom0**.

Not sure if this is something in 10.04, or implemented in 9.10 or possibly earlier, but in this fresh install there is no longer a line in **fstab** for the optical disc drive. I would assume this is why discs are mounted in freshly-created folders based on the label of the disc. As I said, this is actually quite cool, yet becomes less than so if you rely on a set path like I do.

Anyway, for those with the same issue, run **[COLOR="Indigo"]wodim --devices[/COLOR]** to make sure of the device block name (eg: **/dev/sr0**), then open **fstab** for editing: [B][COLOR="Indigo"]sudo gedit /etc/fstab
[/COLOR][/B]
Since as yet I couldn't be bothered booting my old system just to have a look at **fstab**, I nutted through the various options, including finding an option to unmount without root privileges (which is omitted from most example CD drive **fstab** entries you see in online guides), so a line like the following should work:

**[COLOR="Red"]/dev/sr0	/media/cdrom0	udf,iso9660	ro,user,noauto,unhide	0	0[/COLOR]**

Once **fstab** is saved, it should work immediately (at least once any disc in the drive is ejected and mounted again). And in case you're wondering if the "**ro**" (read-only) option is suitable for rewritable drives, don't worry, it's a standard way of mounting disc drives, and erasing and writing data to RWs is not affected.

Anyway, I've seen quite a few people asking how to turn off automounting, or at least how to set a permanent mount point for their optical drives, so hopefully this helps someone out there! Cheers.

---

### Post by cariboo on 2010-07-15
This thread really doesn't have anything to do with security, moved to General help so that others may benefit from your experience.

---

### Post by OzzyFrank on 2010-07-15
> **cariboo907 said:**
> This thread really doesn't have anything to do with security, moved to General help so that others may benefit from your experience.

Yeah, considering I marked this as Multimedia, I have no idea how it end up in Security!

---

### Post by mc4man on 2010-07-15
I've been using this for fstab in lucid and now maverick, also gets around the security bit policy for the rare disk that has  an .exe on it.
(obviously the mount point(s) need to exist

```
/dev/sr0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sr1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
```

It's also worth reviewing your /etc/udev/rules.d/70-persistent-cd.rules file for how your /dev/dvd, /dev/cdrom, /dev/dvd1, /dev/cdrom1, ect. links are set up

(I like the sr0 drive to get the /dev/dvd and /dev/cdrom links. 
 - plus in maverick it's possible that the rules file will be wrong if you have 2 or more cd/dvd drives and install from a livecd.

---

### Post by OzzyFrank on 2010-07-16
Thanks for the tip. But what is the security issue concerning discs with .EXEs on them, as I've personally never had any hassles (but truth be told, it's not like I stick in Windows software discs that often, hehe)? Anyway, great that you put that info there for those who need it.

As for /etc/udev/rules.d/70-persistent-cd.rules, mine appears OK (I assume):

SUBSYSTEM=="block", ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.5-scsi-1:0:0:0", SYMLINK+="cdrom", ENV{GENERATED}="1"
SUBSYSTEM=="block", ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.5-scsi-1:0:0:0", SYMLINK+="cdrw", ENV{GENERATED}="1"
SUBSYSTEM=="block", ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.5-scsi-1:0:0:0", SYMLINK+="dvd", ENV{GENERATED}="1"
SUBSYSTEM=="block", ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.5-scsi-1:0:0:0", SYMLINK+="dvdrw", ENV{GENERATED}="1"

... but I actually have little idea what this file does (or what editing it achieves). Had some issues in my old system and editing this file didn't seem to do anything. Actually, it was trying various tips on how to get the drive recognised as "dvdrw" for programs that use that instead of mount points like /media/cdrom0. So any info on useful editing of this file would be appreciated.

---

### Post by mc4man on 2010-07-16
> mine appears OK (I assume):

It's fine - the only times it may be an issue is when you have 2 drives - sometimes you may want one drive to get the lower /dev links 
(some apps will default to /dev/dvd or /dev/cdrom

Also sometimes when replacing a drive you may get bumped up /dev links (not sr0 or scd0

Ex. here 
> # DVD-ROM_GDR8164B (pci-0000:00:1f.1-scsi-1:0:0:0)
SUBSYSTEM=="block", ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.1-scsi-1:0:0:0", SYMLINK+="cdrom1", ENV{GENERATED}="1"
SUBSYSTEM=="block", ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.1-scsi-1:0:0:0", SYMLINK+="dvd1", ENV{GENERATED}="1"

# DVD_A_DH20A4P (pci-0000:00:1f.1-scsi-0:0:0:0)
SUBSYSTEM=="block", ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.1-scsi-0:0:0:0", SYMLINK+="cdrom", ENV{GENERATED}="1"
SUBSYSTEM=="block", ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.1-scsi-0:0:0:0", SYMLINK+="cdrw", ENV{GENERATED}="1"
SUBSYSTEM=="block", ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.1-scsi-0:0:0:0", SYMLINK+="dvd", ENV{GENERATED}="1"
SUBSYSTEM=="block", ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.1-scsi-0:0:0:0", SYMLINK+="dvdrw", ENV{GENERATED}="1"

# Cruzer (pci-0000:00:1d.0-usb-0:1.3:1.0-scsi-0:0:0:1)
SUBSYSTEM=="block", ENV{ID_CDROM}=="?*", ENV{ID_SERIAL}=="SanDisk_Cruzer_3512930F6200FB4E-0:1", SYMLINK+="cdrom2", ENV{GENERATED}="1"

Initially DH20A4P was given /dev/dvd1 and /dev/cdrom1, and GDR8164B was given /dev/dvd and /dev/cdrom.
So I switched them, one because I use DH20A4P more and it's easier to remember /dev/sr0 has /dev/dvd and /dev/cdrom, /dev/sr1 has /dev/dvd1, /dev/cdrom1

The sr0, sr1 ect. are not switch-able - the optical drive you can boot from - as set in bios, always gets sr0 (scd0

Now if I was to connect an external cd/dvd drive it would get links after the sandisk flash drive which would make it a little confusing.
(/dev/sr3, /dev/cdrom3, /dev/dev2, so before doing so the first time I'd delete the sandisk entry, reboot and  connect the external. Then it would be more logical - /dev/sr2, /dev/cdrom2, /dev/dvd2

---

