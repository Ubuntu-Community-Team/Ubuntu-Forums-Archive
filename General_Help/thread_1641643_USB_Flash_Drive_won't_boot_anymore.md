---
title: "USB Flash Drive won't boot anymore"
date: 2010-12-09
forum: General Help
---

### Post by joehoward on 2010-12-09
Hi Everyone

I recently installed Ubuntu Netbook Edition 10.10 on a flash drive so I could use my own customized OS on school netbooks.  It has worked very well to date.
However, I forgot to plug the flash drive back into the machine before I woke it up and it froze.  I've accidentally done this before, and normally, I can go back into the OS with a simple reboot.  Now, it displays the splash screen for a little, but I get an error message:

```
initramfs mount: mounting /dev/loop1 on /cow failed: invalid argument
```

I'm no expert, but it sounds like the /cow directory is messed up, it can't create a virtual drive in the Ram

I can easily re-install the OS on the flash drive, but it took me almost a week to get the necessary drivers the first time, and i _really_ don't want to go that route unless _absolutely_ nessesary.

Can someone help me get my flash drive boot disk running again?  I am rather new to linux, but am not afraid to play with code.

Thanks in advance

---

### Post by C.S.Cameron on 2010-12-10
What method did you use to install to the flash drive? Full install? Persistent install?

If persistent install everything is saved in the file casper-rw.
You can back up this file on another drive reinstall Ubuntu to the USB drive and overwrite the new casper-rw with the old one.
If casper-rw is full you can mount it on another drive and delete unnecessary stuff from it.

If you did a Full install to it, you might be able to copy the home folder, (resync), and paste it back into a new install.

---

### Post by joehoward on 2010-12-11
I did a Persistent install because there is a casper-rw file on the drive.

I copied the Casper file onto my external HD, reinstalled the OS onto my flash drive, and replaced the new Casper file with the one I backed up, as you suggested.
However, when I tried to boot, I got the exact same error message as before.

I just tried to mount my old Casper file using the directions found  [here]("http://ubuntuforums.org/showthread.php?t=1028564"), but I got this error message:

```
ubuntu@ubuntu:/media/Expansion Drive$ sudo mount -o loop casper-rw /media/casper1/
mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

So then used the dmesg command as it suggested and got this:
```
ubuntu@ubuntu:/media/Expansion Drive$ dmesg | tail
[16137.798721] sd 7:0:0:0: [sdg] Assuming drive cache: write through
[16137.798725] sd 7:0:0:0: [sdg] Attached SCSI removable disk
[16165.341978] sd 7:0:0:0: [sdg] Assuming drive cache: write through
[16165.341983]  sdg: unknown partition table
[16166.977228] sd 7:0:0:0: [sdg] Assuming drive cache: write through
[16166.977233]  sdg:
[25280.204553] journal_bmap: journal block not found at offset 11635 on loop1
[25280.204557] JBD: bad block at offset 11635
[25280.204560] JBD: recovery failed
[25280.204561] EXT3-fs: error loading journal.
```

the 3rd to last part about "bad block at offset 11635" makes me think that the Casper file got messed up when I woke up the machine.  This would also explain why the problem happened again on the fresh install.

so i guess my next question is this:  Is there any way to recover the casper-rw file?

---

### Post by C.S.Cameron on 2010-12-11
Sounds to me like the casper-rw file has been corrupted.
I have not heard of a way to fix one.
Sorry.

Next time you could try using a ext3 casper-rw partition.
I think these are a little harder to corrupt as all files are kept individual.

---

### Post by warfacegod on 2010-12-11
> **C.S.Cameron said:**
> Sounds to me like the casper-rw file has been corrupted.
I have not heard of a way to fix one.
Sorry.

Next time you could try using a ext3 casper-rw partition.
I think these are a little harder to corrupt as all files are kept individual.

Why can't you replace that file?

---

### Post by wilee-nilee on 2010-12-11
> **warfacegod said:**
> Why can't you replace that file?

> **joehoward said:**
> 
I'm no expert, but it sounds like the /cow directory is messed up, it can't create a virtual drive in the Ram

**I can easily re-install the OS on the flash drive, but it took me almost a week to get the necessary drivers the first time, and i _really_ don't want to go that route unless _absolutely_ nessesary.**


Thanks in advance

Probably, just trying to follow this information.

---

### Post by warfacegod on 2010-12-11
Sorry. More than a few to the wind. Should have seen/connected that.  Oops!

---

### Post by joehoward on 2010-12-12
Well, guess I'd better start looking for those drivers again

Thanks for trying anyways.

---

