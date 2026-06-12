---
title: "Error copying from CD-ROM - Error splicing file: Input/output error"
date: 2012-01-01
forum: General Help
---

### Post by AD-RS1600i on 2012-01-01
Hello Everyone,

On logging onto the forum today it says the last time I visited was July 31st 2007 - blimey - where does time go?! And wow, how everything has moved on, the latest version of Ubuntu with the Unity desktop absolutely **rocks!!**:D It will not be so long next time as I feel I am mature enough now to battle on with Linux with my personal struggles with it adapting from a MS world.. as the rewards are well worth it.

Everything installed beautifully with my new system, the only glitch I am suffering with is my DVD-ROM drive when on attempting to copy large files circa 100mb+ the process fails with the following error:-

**Error while copying "PAK0.PK3". **(loading PK3 files for IOQuake:) )[B]
There was an error copying the file into /home/adrian/Desktop.
Error splicing file: Input/output error[/B]

Using the following command 'lshw -C disk' - I get the following information concerning my drive:-

[B]*-cdrom
       description: DVD writer
       product: DVD+-RW GSA-H53N
       vendor: HL-DT-ST
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       logical name: /media/Quake3
       version: B104
       serial: [
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500 state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
          logical name: /media/Quake3
          capabilities: partitioned partitioned:mac
          configuration: mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500 state=mounted[/B]

Within the /var/kern.log:-

[B]Jan  1 16:20:54 adrian-G41MT-S2PT kernel: [ 5800.424369] sr 1:0:0:0: [sr0] Unhandled sense code
Jan  1 16:20:54 adrian-G41MT-S2PT kernel: [ 5800.424372] sr 1:0:0:0: [sr0]  Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Jan  1 16:20:54 adrian-G41MT-S2PT kernel: [ 5800.424375] sr 1:0:0:0: [sr0]  Sense Key : Hardware Error [current] 
Jan  1 16:20:54 adrian-G41MT-S2PT kernel: [ 5800.424378] sr 1:0:0:0: [sr0]  Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
Jan  1 16:20:54 adrian-G41MT-S2PT kernel: [ 5800.424382] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 02 4b 5f 00 00 40 00
Jan  1 16:20:54 adrian-G41MT-S2PT kernel: [ 5800.424389] end_request: I/O error, dev sr0, sector 601468
Jan  1 16:20:54 adrian-G41MT-S2PT kernel: [ 5800.424394] quiet_error: 732 callbacks suppressed
Jan  1 16:20:54 adrian-G41MT-S2PT kernel: [ 5800.424396] Buffer I/O error on device sr0, logical block 150367
Jan  1 16:20:54 adrian-G41MT-S2PT kernel: [ 5800.424402] Buffer I/O error on device sr0, logical block 150368
Jan  1 16:20:54 adrian-G41MT-S2PT kernel: [ 5800.424408] Buffer I/O error on device sr0, logical block 150369
Jan  1 16:20:54 adrian-G41MT-S2PT kernel: [ 5800.424411] Buffer I/O error on device sr0, logical block 150370
Jan  1 16:20:54 adrian-G41MT-S2PT kernel: [ 5800.424414] Buffer I/O error on device sr0, logical block 150371
Jan  1 16:20:54 adrian-G41MT-S2PT kernel: [ 5800.424416] Buffer I/O error on device sr0, logical block 150372
Jan  1 16:20:54 adrian-G41MT-S2PT kernel: [ 5800.424418] Buffer I/O error on device sr0, logical block 150373
Jan  1 16:20:54 adrian-G41MT-S2PT kernel: [ 5800.424420] Buffer I/O error on device sr0, logical block 150374
Jan  1 16:20:54 adrian-G41MT-S2PT kernel: [ 5800.424422] Buffer I/O error on device sr0, logical block 150375
Jan  1 16:20:54 adrian-G41MT-S2PT kernel: [ 5800.424424] Buffer I/O error on device sr0, logical block 150376[/B]

The annoying thing is, on my Windows partition the drive works without issue. I also think the original Linux drivers used with the drive must have been good as obviously my Ubuntu installation installed without issue.

I strongly suspect I am going to need to buy a new drive - checking the excellent [http://linuxhcl.com/](http://linuxhcl.com/) hardware page for a suitable replacement. Worked a treat when picking a new wireless dongle..! :)

Just thought I would double check with the forums first as I hate wasting materials and obviously adding another drive to the land fill.. :(

Many many thanks in advanced, and sorry it has been a while:D

Adrian

PS - Happy New Year Ubuntu Forum :)

---

### Post by AD-RS1600i on 2012-01-01
I justed tested a spare CD-ROM drive I had using the same IDE cable & interface etc. and it worked ok.. 

I suspect it is just a strange quirk on a cheap OEM DVD drive..

Should I give up on it and buy another?

Thanks in advanced,

Adrian

---

### Post by gordintoronto on 2012-01-01
Sometimes a drive will just have a problem with the occasional disc. Where did the disc come from? If it was created on that drive, I would dump the drive. Have you tried it with other discs, such as watching a commercial DVD?

---

### Post by AD-RS1600i on 2012-01-02
Thanks for your input guys really appreciate it :)

Yeah, the CD is a bog standard original Quake 3 Arena disk.. Tried a OEM XP disk as well, same result when attempting to build a Virtualbox machine using it..

I am soooooooooooooooo lucky I decided to install Quake 3 because if I had not of done that I would have been left assuming there was a underling issue with Virtualbox and installing from CD etc.

On playing audio CDs it also makes a strange 'corrupted' sound betweens tracks etc.

But, like I say on Windows it is happy - I'm guessing the drive manufacturer cut a few corners with the operation of the drive knowing how Windows works, but deviating away from the standards for creating such drives which obviously the Linux developers would adhere to strictly which is why it does not work properly on Linux.

I have so much admiration for all the open source developers out there - what you guys have created with all the various flavours of Linux is nothing short of outstanding :D

---

