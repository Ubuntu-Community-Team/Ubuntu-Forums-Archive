---
title: "Folder Recovery Needed"
date: 2012-02-04
forum: General Help
---

### Post by sibleytr on 2012-02-04
I need to recover a folder off of a EXT4 RAID1 partition.

In the process of reinstalling 11.10 Alt I realized that my backup process was missing a key folder. Unfortunately I was already in the process of partition modifications. The original configuration consisted of 3 raid 1 partitions. 2 x 500 gb hd's for root (ext4) and swap and 2 x 1 tb hd's for a Vol1 (ext4). I had just deleted the RAIDs when I realized I was at condition FUBAR. Installation was immediately aborted at this point.

Being unable to boot, I placed a 11.10 live in the system and tried to access the drives. The needed folder is on the root raid (500 gb). However when I attempt to mount with Disk Utility,...

Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sda1, missing codepage or helper program, or other error

HELP!

---

### Post by winh8r on 2012-02-07
First thing to do is avoid using the disk. That way you will have a better chance of recovery.

You can try this:

[http://extundelete.sourceforge.net/]("http://extundelete.sourceforge.net/")

or  get testdisk from the repositories and use it from another drive to recover from the "mistake" drive.

It helps if you know the file types you are looking for when using testdisk as you can specify them in the options menu, but the default setting will recover everything from the drive, so you will need a drive of appropriate size to recover to.

Hope this helps

Good Luck



edit. possibly better solution since you have enough large capacity drives, is to use ddrescue to take a disk image from the 500Gb disk and recover your files from that, that way you will still have the original if anything goes wrong during the recovery.

---

### Post by sibleytr on 2012-02-08
I was able to locate testdisk and use photorec to recover my missing files. Unfortunately the files were recovered as:

ff#######.(ext)

Better to have an rename then to not have at all.

Will try the aforementioned extundelete to see if it gives me any better naming options.

Thanks for the info.

---

### Post by sibleytr on 2012-02-08
Having trouble mounting the raid drive.

Drive shows as Linux RAID autodetect (0xfd)
Device: /dev/sde1

Can't seem to use extundelete until I can mount

---

### Post by winh8r on 2012-02-09
> **sibleytr said:**
> I was able to locate testdisk and use photorec to recover my missing files. Unfortunately the files were recovered as:

ff#######.(ext)

Better to have an rename then to not have at all.

Will try the aforementioned extundelete to see if it gives me any better naming options.

Thanks for the info.

Glad you were able to get them back, the recovery process assumes that you are willing to put up with the hassle of renaming the files, it has done its thing by getting them back for you, what happens after recovery is a matter of personal choice.

use a tool like mrename (in the repositories) for batch renaming.

at least you are smiling again!!!

---

