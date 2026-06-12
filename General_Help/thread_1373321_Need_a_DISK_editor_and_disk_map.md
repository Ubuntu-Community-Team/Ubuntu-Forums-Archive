---
title: "Need a DISK editor and disk map"
date: 2010-01-05
forum: General Help
---

### Post by Silvernail on 2010-01-05
I have several hard drives that have failed over the last few years that I would like to recover some data from.

What I want to do.
Back in the early 80's I was using an operating system named OS9 put out by Microware in De Moines Iowa.

Somehow my hard drive got a scratch and failed on boot. The very first sector on the drive contained the bytes that said where to find the, file allocation table, root directory, and file descriptors.

Byte 9 A B held the address of the root directory. So if I looked there I could now jump straight to the root directory and read the address of the file descriptor which held the address of the data  that I wanted to recover.  ( This is a somewhat simplified version of the procedure. )

Can someone point me to a [COLOR="Red"]disk editor [/COLOR] that I can use to open the drive in raw mode and  change the bytes on it? Or read the data on it?  I have not been able to figure how to use 'hexedit' for this.

So that I will know what I am reading on the drive, is there a map of the how the drive is layout?

If anyone can help I will appreciate it.
TIA
Dave

---

### Post by SecretCode on 2010-01-05
Are these internal drives that you will plug in with IDE/SCSI/SATA/... cables? As long as you can get them to appear in /dev (check /dev/disk/by-path/) you will be able to work on them with dd.

I'm not sure if you can use hexedit directly on a disk device, but you can extract parts using dd and then write them back.

Supposing your disk is at /dev/sdd, and also supposing that you know that [COLOR="Red"]by accidentally writing to the wrong disk, or with the wrong offset or count, you could destroy all your data[/COLOR]:
```
sudo dd if=/dev/sdd of=somediskcontents bs=512 skip=63 count=1
hexedit somediskcontents
sudo dd if=somediskcontents of=/dev/sdd bs=512 seek=63 count=1
```... would edit sector 63.

Look at man dd to understand the bs, count, skip and seek options.

To understand the layout of the drives, study [http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record) and so on.


Somebody else may have better advice than this!

---

