---
title: "Help Adding a Second Hard Drive"
date: 2006-03-17
forum: General Help
---

### Post by peter1632 on 2006-03-17
I need some help adding a second drive to my system.  This second drive, hdb, is 300g, intended for mythtv use (225g) and the balance for other storage needs.  Thus, I’d like to format the[FONT="Courier New"] /myth[/FONT] partition as [FONT="Courier New"]xfs[/FONT], and the other [FONT="Courier New"]/backup[/FONT] partition as [FONT="Courier New"]ext3[/FONT].  I had some success using [FONT="Courier New"]mkfs.xfs[/FONT] but df does recognize the drive (so not really much success, eh?).  Assuming I need to start back with [FONT="Courier New"]fdisk[/FONT], how do I correctly format, create these two partitions, and then modify my fstab so things will mount when I boot the system.  Thanks….

[SIZE="1"]cpu: athlon 1830mhz
mem: 1g mushkin memory
mobo: shuttle an35
vid: geforce n6600
hda: wd 120gb
hdb: maxtor 300gb
dvd: asus drw-1608ps
kernel 2.612-10
both ubuntu and kubuntu installed[/SIZE]

---

### Post by TLE on 2006-03-17
Can't you use the graphical partition maneger, it looks pretty easy, it under system - adminestration - discs      at least for the partitioninig, then we can figure out the fstab stuff later, or you can search the forum

---

### Post by peter1632 on 2006-03-17
I had tried QTPARTED... just tried again.  OK, now I seem to have partitioned the drive and QTPARTED shows the first ext3 partition and the second hdb2 partitionas xfs.  I edited the fstab and rebooted.  I see a "Failed" during boot when trying to mount the local file systems.  I invoke DiskManager and it sees the partitions, but tells me they are Inaccessible.  I'm now searching for info on fstab... must be doing it wrong.

[COLOR="Navy"]UPDATE:  OK, I had neglected to issue a chmod for each of the new directories.  So I issued
   chmod 777 /mnt/storage      [this is the ext3 drive]
   chmod 777 /mnt/mythtv       [this is the xfs drive]

Now the drives show up in QTPARTED and in the drive utilities.  I'd like the folders to show up
in the file system ... and I find that I cannot save to the drives yet.  Thoughts?[/COLOR]

---

### Post by z-vet on 2006-03-18
You don't need to reboot after repartitioning of harddrive since it's unmounted when you partition it. Just mount it with "mount" command from Konsole or whatever terminal. It's better because you can see an error messages if something goes wrong. 
Anyway, post here your /etc/fstab.

---

### Post by peter1632 on 2006-03-18
[QUOTE=z-vet]...Anyway, post here your /etc/fstab.[/QUOTE]


fstab file:

[FONT="Courier New"]
[SIZE="2"]#
proc /proc               proc       defaults    0      0
/dev/hda1   /                     ext3       defalts,errors=remount -ro  0  1
/dev/hda5   none                swap      sw           0      0
/dev/hdc     /media/cdrom0   udf,iso9660 user,noauto 0     0
#
[COLOR="Green"]/dev/hdb1    /mnt/storage     ext3    defaults       0    0
/deb/hdb2    /mnt/mythtv        xfs      defaults   0  0[/COLOR]
#
[/SIZE][/FONT]

---

### Post by five40i on 2006-03-18
I am going to ask a stupid question. Did you create the directories in /mnt ??
The reason I ask is, I added a new hard drive and forgot about creating the directory....Just a suggestion.

Good luck..

---

### Post by five40i on 2006-03-18
I looked at the previous posts and that was a stupid question....I don't know what the hell I was thinking????:(

---

### Post by z-vet on 2006-03-19
Try to modify an entries in /etc/fstab like this:
```

/dev/hdb1 /mnt/storage ext3 auto,users,exec 0 2
/dev/hdb2 /mnt/mythtv xfs auto,users,exec 0 2

```
Remove this # at the end of the file (if it exists). Note that you must to have an empty line at the end of /etc/fstab, e.g. hit return twice. Then do 
```

cd /mnt
sudo chown user:group storage 
sudo chown user:group mythtv
mount storage
mount mythtv

```
Hope it helps...

---

### Post by peter1632 on 2006-03-19
YES!  it worked.  I invoked

[FONT="Courier New"]sudo chown peter storage
sudo chown peter mythtv
and was able to write to the drives.[/FONT]

Thankyou.

---

