---
title: "Filesystem is NOT clean"
date: 2010-11-28
forum: General Help
---

### Post by pyromidget on 2010-11-28
So I went away for a few days but left my computer on to seed torrents.  I come back today to find that my flatmate decided to have a tidy up, unplugging my computer and external HDD in the process...

I set my computer back up but now my external drive is refusing to mount.  This drive has EVERYTHING on it - about 5 years worth of music & video d/ls plus a lot of important documents so I'm praying that it isn't wrecked.

That I know of, the drive was mounted but not in use when the power was pulled. The disk utility recognises its there and SMART-healthy, but claims "Filesystem is NOT clean" and won't mount it.

Can anyone help? :-(

---

### Post by carl4926 on 2010-11-28
What file system is it - ie: ntfs, ext4...?

---

### Post by pyromidget on 2010-11-28
Sorry, forgot to put that in.  Its got a single 1TB FAT32 partition on it.

---

### Post by I'mGeorge on 2010-11-28
when you left your computer to download, was that in windows or in linux ?

---

### Post by Chronon on 2010-11-28
fsck.vfat should help.  I usually run with "-a" to have it automatically fix errors it finds.  You may wish to consult the man page for other options first.

---

### Post by pyromidget on 2010-11-28
Linux - wiped my dual-boot when maverick came out.

---

### Post by pyromidget on 2010-11-28
Chronon:

```
martin@beliskner:~$ sudo fsck -t vfat /dev/sdb
[sudo] password for martin: 
fsck from util-linux-ng 2.17.2
dosfsck 3.0.9, 31 Jan 2010, FAT32, LFN
Currently, only 1 or 2 FATs are supported, not 251.
```

---

### Post by I'mGeorge on 2010-11-28
the solution as your hdd has a windows file system on it would be to let windows make it's cache disk run on it, after that you should be able to mount it easily.

---

### Post by pyromidget on 2010-11-28
Unfortunately i no longer have access to windows - i wiped it from both my machines when 10.10 was released.

---

### Post by davec64 on 2010-11-28
As a suggestion you could try forcing the mount:

```
sudo mount /dev/src /mnt/dst -o force
```

change the source and destination locations to your set up.

If you wean to read up on it first, have a look at:

```
man mount
```

Hope that helps!

---

### Post by carl4926 on 2010-11-28
Parted magic
And use Test Disk

Google should help you

Or find a mate with a windows machine and connect it up (probably the best option IMO)

---

### Post by I'mGeorge on 2010-11-28
yeah force mount could work, this it's why I've asked you if you left your PC downloading in Windows. If your computer was shut down out of the sudden, window flags the drive's file system so it would know it wasn't shut downed normally and perform a check disk next time you boot in. This also prevents the hard disk to be normally mounted in linux and using the -o force mount options could work. 

But i don't know what to say 'cause usually if your computer, hdd were shut down while in linux this inconvenience shouldn't occur. But it could happen.

---

### Post by Ceyx on 2010-11-28
You may also want to boot your system with a Live CD, and run gparted to have a look.....

---

### Post by pyromidget on 2010-11-28
davec64:

```
martin@beliskner:~$ sudo mount -t vfat /dev/sdb /media -o force
[sudo] password for martin: 
mount: wrong fs type, bad option, bad superblock on /dev/sdb,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

martin@beliskner:~$ dmesg | tail
[  585.772653] sd 5:0:0:0: Attached scsi generic sg1 type 0
[  585.777979] sd 5:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[  585.780098] sd 5:0:0:0: [sdb] Write Protect is off
[  585.780110] sd 5:0:0:0: [sdb] Mode Sense: 28 00 00 00
[  585.780116] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[  585.782331] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[  585.782364]  sdb: sdb1
[  585.800245] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[  585.800272] sd 5:0:0:0: [sdb] Attached SCSI disk
[ 5736.090432] FAT: Unrecognized mount option "force" or missing value
martin@beliskner:~$
```

---

### Post by pyromidget on 2010-11-28
The computer wasn't shut down AFAIK - just unplugged suddenly.  I'll try out gparted etc and post back.  thanks for the help so far folks!

---

### Post by pyromidget on 2010-11-28
okay, so gparted keeps crashing halfway through checking/repairing filesystem... any more ideas?

---

### Post by davec64 on 2010-11-28
> **pyromidget said:**
> davec64:

```
martin@beliskner:~$ sudo mount -t vfat /dev/sdb /media -o force
[sudo] password for martin: 
mount: wrong fs type, bad option, bad superblock on /dev/sdb,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

martin@beliskner:~$ dmesg | tail
[  585.772653] sd 5:0:0:0: Attached scsi generic sg1 type 0
[  585.777979] sd 5:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[  585.780098] sd 5:0:0:0: [sdb] Write Protect is off
[  585.780110] sd 5:0:0:0: [sdb] Mode Sense: 28 00 00 00
[  585.780116] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[  585.782331] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[  585.782364]  sdb: sdb1
[  585.800245] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[  585.800272] sd 5:0:0:0: [sdb] Attached SCSI disk
[ 5736.090432] FAT: Unrecognized mount option "force" or missing value
martin@beliskner:~$
```

I don't thin you need the -y vfat, try:

```
sudo mount /dev/sdb /media -o force
```
If that's where you want it mounted.

---

### Post by pyromidget on 2010-11-28
```
martin@beliskner:~$ sudo mount /dev/sdb /media -o force
[sudo] password for martin: 
mount: you must specify the filesystem type
martin@beliskner:~$ 

```

This is starting to go a bit catch-22 on us i think...

---

### Post by davec64 on 2010-11-28
I think you can safely say force isn't the answer!
Sorry I don't know what else to suggest.

---

### Post by pyromidget on 2010-11-28
no worries - thanks anyway!

Anyone else want to take up the challenge? :p

---

### Post by Bitrate on 2010-11-28
If you've got access to a Windows XP installation CD try booting off the CD and going into recovery console mode and typing CHKDSK x: /F /R  (where x: is your hard drive to be checked). If you don't have an XP boot disk then try obtaining a system rescue disk like BartPE.

---

### Post by Ceyx on 2010-11-28
> **pyromidget said:**
> okay, so gparted keeps crashing halfway through checking/repairing filesystem... any more ideas?


Make sure you have the right support within Gparted for Fat 32.  Check Gparted > View > File system Support.

Also, I presume this is a USB Drive.  I have experienced many problems with USB drives on one particular computer I have - try another computer's usb port with a Live CD... and also perhaps disable USB 2.0 in Ubuntu.


Ciao !

---

### Post by pyromidget on 2010-11-28
> **Bitrate said:**
> If you've got access to a Windows XP installation CD try booting off the CD and going into recovery console mode and typing CHKDSK x: /F /R  (where x: is your hard drive to be checked). If you don't have an XP boot disk then try obtaining a system rescue disk like BartPE.
don't have xp but might have 2k kicking around. will that do?

Ceyx:  full fat32 support in gparted.  i'll give the others a try when i get a chance

---

### Post by pyromidget on 2010-11-29
Bit of an update:  Got hold of a vista comp for a few minutes and tried plugging in the hard drive - worked perfectly.  tried it back in my 10.10 box, nothing.  Ran chkdsk on the drive too and it claimed to have fixed errors on the filesystem, but still no joy trying it back on linux.

Also, managed to borrow another 1tb external, so if i can somehow get access to the data, i can at least copy everything over, reformat my own drive to ext4 and put everything back.  all dependant on actually getting to the data though :(

---

### Post by carl4926 on 2010-11-29
It's essential to safely remove the disk from windows

---

### Post by pyromidget on 2010-11-29
> **carl4926 said:**
> It's essential to safely remove the disk from windows

i made a point of doing that.  Somehow the drive has randomly started working again - i have no idea why but now its a race against time to get everything copied off of it!

---

### Post by SeijiSensei on 2010-11-29
The syntax in the fsck and mount commands above is generally wrong unless there's something unusual about how FAT32 devices are referenced.  Something like "mount /dev/sdb" or "fsck /dev/sdb" applies the command to the *device*,  not to one of the filesystems on it.  If it has just one partition, that is referenced as /dev/sdb_1_, so try running

```
sudo fsck -t vfat /dev/sdb1
```

and see what happens.

Forcing a mount is an absolute last-ditch effort.

---

### Post by pyromidget on 2010-11-30
partial success!  managed to somehow mount the dodgy drive and copy the contents onto another.  One problem has cropped up though - somewhere in the transfer, i've lost about 2 gig of data.

i tried the solution here to no avail:

[http://ubuntuforums.org/showthread.php?t=1525613](http://ubuntuforums.org/showthread.php?t=1525613)

does anyone know of another way to compare contents and transfer the missing files?

---

