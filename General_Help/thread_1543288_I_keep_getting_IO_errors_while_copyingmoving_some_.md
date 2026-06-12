---
title: "I keep getting I/O errors while copying/moving some files."
date: 2010-07-31
forum: General Help
---

### Post by Mr_VeRiTy on 2010-07-31
Hi, Recently whenever I copy (or move) files from one place on my hd to another One or two of them dont copy, and I get an error similar to "```
There was an error copying the file into [location].

Show more details>

      Error splicing file: Input/output error.
```
The file is always an .avi file and always between 600MB and 1.4GB in size, how can I fix this problem?

---

### Post by Mr_VeRiTy on 2010-08-02
*Bump*

---

### Post by P4man on 2010-08-02
Probably something wrong with the files; filesystem or drive (/controller). Well, i guess that covers it all lol. Perhaps you can check the output of
```

tail /var/log/messages
```

after this happens. But i suspect this is not something you can solve other than by replacing the drive or ide/sata/usb cable.

---

### Post by Mr_VeRiTy on 2010-08-02
> **P4man said:**
> Probably something wrong with the files; filesystem or drive (/controller). Well, i guess that covers it all lol. Perhaps you can check the output of
```

tail /var/log/messages
```

after this happens. But i suspect this is not something you can solve other than by replacing the drive or ide/sata/usb cable.
The output of 
```

tail /var/log/messages
```

was:
```

luke@computer:~$ tail /var/log/messages
Aug  3 00:16:46 computer kernel: [107260.385338] ata1.00: configured for UDMA/100
Aug  3 00:16:46 computer kernel: [107260.385363] sd 0:0:0:0: [sda] Unhandled sense code
Aug  3 00:16:46 computer kernel: [107260.385367] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Aug  3 00:16:46 computer kernel: [107260.385373] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Aug  3 00:16:46 computer kernel: [107260.385381] Descriptor sense data with sense descriptors (in hex):
Aug  3 00:16:46 computer kernel: [107260.385384]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
Aug  3 00:16:46 computer kernel: [107260.385402]         39 c2 4f 37 
Aug  3 00:16:46 computer kernel: [107260.385409] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
Aug  3 00:16:46 computer kernel: [107260.385418] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 39 c2 4f 00 00 00 80 00
Aug  3 00:16:46 computer kernel: [107260.385456] ata1: EH complete
luke@computer:~$ 

```
Of course, I have no idea what any of that means :)

---

### Post by CharlesA on 2010-08-02
Try running fsck from a livecd and see if it finds any file system corruption.

My bet is the hard drive is failing.

---

### Post by Mr_VeRiTy on 2010-08-02
> **CharlesA said:**
> Try running fsck from a livecd and see if it finds any file system corruption.

My bet is the hard drive is failing.

The hard drive shouldn't be failing, as I only bought it in December 2009, but if it is failing, what is the best backup tool for Ubuntu?

---

### Post by CharlesA on 2010-08-02
Not sure of a backup tool, but you can normally just copy the home directory and be ok.

Also download the diagnostics from the manufacturer and run them to make sure the drive is ok.

---

### Post by Mr_VeRiTy on 2010-08-02
> **CharlesA said:**
> Not sure of a backup tool, but you can normally just copy the home directory and be ok.

Also download the diagnostics from the manufacturer and run them to make sure the drive is ok.
Sorry to be newbie-ish but how do I run fsck on an ext4 filesystem?

When I boot up my live CD and type fsck into the terminal It just says
```
ubuntu@ubuntu:~$ fsck
fsck from util-linux-ng 2.17.2
```

---

### Post by CharlesA on 2010-08-02
> **Mr_VeRiTy said:**
> Sorry to be newbie-ish but how do I run fsck on an ext4 filesystem?

When I boot up my live CD and type fsck into the terminal It just says
```
ubuntu@ubuntu:~$ fsck
fsck from util-linux-ng 2.17.2
```
Same way as you run fsck on ext2 or ext3.

```
sudo fsck -C /dev/sdxy
```

Where x is a, b, c, etc
Where y is 1, 2, 3, etc

---

### Post by Mr_VeRiTy on 2010-08-02
The output of fsck on sda1 was
```
ubuntu@ubuntu:~$ sudo fsck -C /dev/sda1
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
Alpha: clean, 351667/27713536 files, 13650479/110839040 blocks

```

And my second partition, sda4 (which I *think *is the only one that has had the errors)
```
ubuntu@ubuntu:~$ sudo fsck -C /dev/sda4
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
Beta: clean, 50/2387392 files, 5608671/9547776 blocks (check in 3  mounts)

```

Also, I looked, and I don't think toshiba (my hdd's manufacturer) have a diagnostic tool that runs on ubuntu, on their website.

---

### Post by CharlesA on 2010-08-02
You'd probably want to run fsck with the -f option to force it to run.

Also, most HDD diagnostics utilities boot from cd, so they have full access to the hardware.

---

### Post by P4man on 2010-08-03
The logfile definitely shows a harddrive error. Looks like a bad drive or a bad IDE (/sata) cable. 

Running a diagnostics is a good idea, but what does palimpsest say? System >adminstration > disk utility. Select your drive and go to SMART status. If its not enabled, then enable it in the bios.

---

### Post by Mr_VeRiTy on 2010-08-04
> **P4man said:**
> The logfile definitely shows a harddrive error. Looks like a bad drive or a bad IDE (/sata) cable. 

Running a diagnostics is a good idea, but what does palimpsest say? System >adminstration > disk utility. Select your drive and go to SMART status. If its not enabled, then enable it in the bios.
Disk utility's S.M.A.R.T. status shows that most things are either "good" or "N/A" but Reallocated Sector Count's status is "warning" with a value of 1143 Reallocated Sectors

one other warning is "Current Pending Sector Count" who's status is also "Warning" and has a value of 37, I tried checking the smart status yesterday but for some reason it wouldn't let me until I installed smartmontools, would the output of smartctl help?

Currently I'm doing a long self test, but the short self test's say that the hdd is fine, as part of the output of smartctl was ```
SMART overall-health self-assessment test result: PASSED
```

---

### Post by Mr_VeRiTy on 2010-08-04
> **P4man said:**
> The logfile definitely shows a harddrive error. Looks like a bad drive or a bad IDE (/sata) cable. 

Running a diagnostics is a good idea, but what does palimpsest say? System >adminstration > disk utility. Select your drive and go to SMART status. If its not enabled, then enable it in the bios.

Also I don't think I can change the sata/IDE cable as it is a laptop hdd, don't know if that changes anything. 

Btw If my drive is called sda1 does that mean it is solid state? 'cos I thought hda# was hard disk and sda# was solid state.

---

### Post by P4man on 2010-08-04
Looks like your drive is about to die or suffered a head crash (any chance you bumped the drive or laptop while it was on?). Those pending sectors are sectors that the drive has trouble reading or writing to. It should be zero on a good drive. They will be remapped to spare ones (apparently you still have some) but if those files you are trying to copy reside partly on those sectors, you might get what you are experiencing.

As for it being called sda.. any drive is called sdx, wether it is a sata or pata drive, ssd or magnetic.

---

### Post by Mr_VeRiTy on 2010-08-04
> **P4man said:**
> Looks like your drive is about to die or suffered a head crash (any chance you bumped the drive or laptop while it was on?). Those pending sectors are sectors that the drive has trouble reading or writing to. It should be zero on a good drive. They will be remapped to spare ones (apparently you still have some) but if those files you are trying to copy reside partly on those sectors, you might get what you are experiencing.

As for it being called sda.. any drive is called sdx, wether it is a sata or pata drive, ssd or magnetic.
I don't remember ever dropping my laptop... and The reallocated sector count has been that high for as long as I've had this laptop (late december 2009)

In the meantime is there any way to prevent the hard drive from writing to the bad area of the drive?
 
Would formatting it help?

---

### Post by P4man on 2010-08-04
> **Mr_VeRiTy said:**
> I don't remember ever dropping my laptop... and The reallocated sector count has been that high for as long as I've had this laptop (late december 2009)

In the meantime is there any way to prevent the hard drive from writing to the bad area of the drive?
 
Would formatting it help?

The drive will automatically avoid using the bad sectors. But there is still data on it that it can not relocate because it has trouble reading it. It will only relocate those pending sectors if you try and write other data to it, so it can discard the now unreadable data in those bad sectors and use other (spare) sector instead. All of this is invisible to the OS, has nothing to do with the filesystem as its the drive controller doing this.

There is nothing you can or should do. You can trigger this by zero filling your drive, and that will result in no "pending sectors" and a higher relocated count, but not do anything useful really. (quick) formatting the drive will do nothing unless by a huge coincidence those pending sectors hold partition data that gets written to during a quick format, but thats highly unlikely. Full format will do the same as the zero filling.

You could just as well delete the problematic files. new files occupating the "same" sectors will end up on healthy parts of the drive.

---

### Post by Mr_VeRiTy on 2010-08-04
So I am definitely going to have to buy a new drive?

Is there any way to save the files in the bad sectors?

---

### Post by P4man on 2010-08-04
No. If indeed the problematic sector count remains stable, then it may well have been a head crash in the past killing a few 100 sectors but otherwise the drive could be healthy. If you see that number go up, then you will most likely have to replace the drive at some point.

edit: and no, its highly unlikely you can save those files. You can try with testdisk but its unlikely to work.

---

### Post by Mr_VeRiTy on 2010-08-04
> **P4man said:**
> No. If indeed the problematic sector count remains stable, then it may well have been a head crash in the past killing a few 100 sectors but otherwise the drive could be healthy. If you see that number go up, then you will most likely have to replace the drive at some point.

edit: and no, its highly unlikely you can save those files. You can try with testdisk but its unlikely to work.
Thanks for your help, I will have to keep an eye on the drive.

---

