---
title: "My 160Gb HDD shows only 6Gb after using gParted"
date: 2012-09-02
forum: General Help
---

### Post by corowakid on 2012-09-02
Hi all,

I don't com here often, as my use of buntu has always gone OK. But I've got a problem that stumps me entirely. I have an Aspire One netbook, previously using Win XP. I used gParted to remove the NTFS partition, and installed Ubuntu only. Things have gone great, but yesterday I decided to use another OS, and again used gParted and wiped the disk. Things went as normal, but when the work had been done, I had 1 6Gb NTFS partition - no unallocated space, no other partition, zilch.

Now, I KNOW I shouldn't have been playing around where I knew nothing, and I've been everywhere to see if there's a way to grow the hDD size to its original size. But I'm getting nowhere, except finding detauls on recovering unallocated space. All I see is 1 partition, 6Gb, formatted NTFS, and nothing else.

I've been trying for a week to find out what happened, and is it possible to recover the space. I'm limited in help, as I live in a small country town, no computer shops, and 60kms away are only a selection of retail stores - no help.

Can anyone reading this post suggest what I've done wrong? Can I get the space back? I have the System Rescue Disk (not much help, the command line is a total mystery to me), and gParted.

As always, these forums provide great help to us newbies. Can someone help me? Any comments or methods would be greatly appreciated. TIA

Barrie

---

### Post by Bashing-om on 2012-09-03
corowakid;

 There is a possible solution, entailing the use of the dd comand to zero out the drive and re-format from scratch to re-partition. This is what I would do.

  However, let's wait a bit and see what others suggest for a solution.


[INDENT]regards <==BDQ

[/INDENT]

---

### Post by corowakid on 2012-09-03
> **Bashing-om said:**
> corowakid;

 There is a possible solution, entailing the use of the dd comand to zero out the drive and re-format from scratch to re-partition. This is what I would do.

  However, let's wait a bit and see what others suggest for a solution.


[INDENT]regards <==BDQ

[/INDENT]

Many thanks for responding; typical Ubuntu help. I just Googled DD, and you are right; a bit more information than I can handle. I may add I'm 77, so learning new tricks takes a lot more effort than before.

If I may, I'll wait until others might respond, and if eventually your solution is the most appropriate, can you help me with the command line instructions.

Again, thanks a lot for the prompt reply.

Regards

Barrie

---

### Post by Bashing-om on 2012-09-03
corowakid;

  You are welcome (glad to see you took the initiative to research the dd command, very awesome in it's power and destructive abilities).

I will monitor this thread and take action as needed.

By the way..... age is no hindrance, desire overcomes many things! You are entering a great world ..and more power to you.

[INDENT]regards <==BDQ

[/INDENT]

---

### Post by coffeecat on 2012-09-03
@corowakid, I'm presuming you were using Gparted from the live Ubuntu session, from a live USB. If you have a live Ubuntu usb, boot up with it, go to the live desktop and open a terminal. Now run these two commands:

```
sudo fdisk -lu
sudo parted -l
```

They don't do anything except give you some useful output which may help us to see what has gone wrong. Post the output of the two commands and we can go from there. You can paste the output by highlighting it with the mouse, right-clicking -> copy and then paste into your post. When you do post the output, please post it between [noparse]```
 and 
```[/noparse] tags to preserve formatting and for clarity. The simplest way of doing this is to highlight the output and then click on the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the message toolbar.

---

### Post by corowakid on 2012-09-03
> **coffeecat said:**
> @corowakid, I'm presuming you were using Gparted from the live Ubuntu session, from a live USB. If you have a live Ubuntu usb, boot up with it, go to the live desktop and open a terminal. Now run these two commands:

```
sudo fdisk -lu
sudo parted -l
```

They don't do anything except give you some useful output which may help us to see what has gone wrong. Post the output of the two commands and we can go from there. You can paste the output by highlighting it with the mouse, right-clicking -> copy and then paste into your post. When you do post the output, please post it between [noparse]```
 and 
```[/noparse] tags to preserve formatting and for clarity. The simplest way of doing this is to highlight the output and then click on the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the message toolbar.

Well, here goes. 1st time I've done this, and just couldn't get my head around it. I tried saving in LibreOffice, then made a folder and tried to paste it there, then gave up, and went back to your post, followed your instructions, and here it is:
```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 8069 MB, 8069677056 bytes
255 heads, 63 sectors/track, 981 cylinders, total 15761088 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003d8cf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    15759764     7879851    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 4009 MB, 4009754624 bytes
128 heads, 22 sectors/track, 2781 cylinders, total 7831552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           8     7831551     3915772    b  W95 FAT32

Disk /dev/sdc: 32.0 GB, 32023511040 bytes
25 heads, 25 sectors/track, 100073 cylinders, total 62545920 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            8064    62545919    31268928    c  W95 FAT32 (LBA)
ubuntu@ubuntu:~$ sudo parted -l
Model: ATA P-SSD1800 (scsi)
Disk /dev/sda: 8070MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  8069MB  8069MB  primary  ntfs


```

 Hope this makes sense, very much appreciate your time in helping me. Regards Barrie

---

### Post by oldfred on 2012-09-04
You are showing a 8GB, 4GB & 32GB drives. Which one is the 160GB drive? 

What does BIOS show. It should show drive & model number for each device it finds.
This should show same list of drives:
sudo lshw -class disk

You may be able to find old partitions on drive with testdisk. Testdisk is in the repository and you can download it into the liveCD or USB. Most repairCDs include testdisk.

repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition]("https://help.ubuntu.com/community/DataRecovery#Lost%20Partition")

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by coffeecat on 2012-09-04
@corowakid, your outputs tell us the following:

sda is an 8GB drive with a single 8GB NTFS partition. Googling the "Model: ATA P-SSD1800 (scsi)" from the parted output suggest that this is an 8GB SSD (solid state drive), and some of the google hits mention the Acer Aspire One. Are you sure that your Aspire One didn't originally come with only an 8GB SSD drive? I must admit that 8GB for Windows XP sounds insufficient, but sda is usually (but not always - depends on the BIOS) the first internal drive and with a netbook you should only have one internal drive. Indeed [this wikipedia article]("http://en.wikipedia.org/wiki/Acer_Aspire_One") says that Acer Aspire Ones came with either a SSD of 8 or 16GB **or** a conventional hard drive of between 120-500GB.

sdb is a 4GB drive formatted FAT32. I'm guessing that this could be your live USB, but you omitted to include the parted output for sdb. Is your live USB a 4GB one?

sdc is a 32GB device formatted FAT32. Did you have a second USB drive, or SD card, plugged in when you ran these two commands? Again, the parted output for sdc is missing which might be useful.

---

### Post by corowakid on 2012-09-05
> **oldfred said:**
> You are showing a 8GB, 4GB & 32GB drives. Which one is the 160GB drive? 

What does BIOS show. It should show drive & model number for each device it finds.
This should show same list of drives:
sudo lshw -class disk

You may be able to find old partitions on drive with testdisk. Testdisk is in the repository and you can download it into the liveCD or USB. Most repairCDs include testdisk.

repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition]("https://help.ubuntu.com/community/DataRecovery#Lost%20Partition")

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)


Thanks for the comment. Below is the output of the LSHW query. Means nothing to me, newbie that I am. Perhaps you could comment?

I accessed the Boot Options screen, and HDD is classed as 8Gb only. Can't make sense of the info provided - should I transcribe it and present it? Appreciate your reply.
```
ubuntu@ubuntu:~$ sudo lshw -class disk
  *-disk                  
       description: ATA Disk
       product: P-SSD1800
       physical id: 0.0.0
       bus info: scsi@1:0.0.0
       logical name: /dev/sda
       version: Ver2
       serial: 0208286007427
       size: 7695MiB (8069MB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=0003d8cf
  *-disk
       description: SCSI Disk
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/sdb
       size: 3824MiB (4009MB)
       capabilities: partitioned partitioned:dos
       configuration: signature=c3072e18
```

---

### Post by corowakid on 2012-09-05
> **coffeecat said:**
> @corowakid, your outputs tell us the following:

sda is an 8GB drive with a single 8GB NTFS partition. Googling the "Model: ATA P-SSD1800 (scsi)" from the parted output suggest that this is an 8GB SSD (solid state drive), and some of the google hits mention the Acer Aspire One. Are you sure that your Aspire One didn't originally come with only an 8GB SSD drive? I must admit that 8GB for Windows XP sounds insufficient, but sda is usually (but not always - depends on the BIOS) the first internal drive and with a netbook you should only have one internal drive. Indeed [this wikipedia article]("http://en.wikipedia.org/wiki/Acer_Aspire_One") says that Acer Aspire Ones came with either a SSD of 8 or 16GB **or** a conventional hard drive of between 120-500GB.

sdb is a 4GB drive formatted FAT32. I'm guessing that this could be your live USB, but you omitted to include the parted output for sdb. Is your live USB a 4GB one?

sdc is a 32GB device formatted FAT32. Did you have a second USB drive, or SD card, plugged in when you ran these two commands? Again, the parted output for sdc is missing which might be useful.

It is (was?) 160Gb HDD, up until I did whatever I did to turn it into an 8Gb. I used gParted as I have usually done when reformatting Linux systems ( I have 2), and things have always gone OK. But somehow I got the commands wrong, hence the reduction of HDD available. I'm happy to ditch the Aspire - its not worth the hassles. I've got a Toshiba NB200 that will do fine. 

The 4Gb USB contains the Live Linux Install. The 32Gb was the USB stick I tried to save the output of Terminal (dumb that I am).

I appreciate everyone's input, but it looks like I can kiss off the netbook. I'll probably buy the Rikomagic MK102 Android and have a play. If its possible to get the Aspire back to where it was before I played, that would be great. But no big deal if it will require the helpful people to go to a lot of research. I do appreciate everyone's assistance so far. I'll wait for comment before I decide what I do. Needless to say it doesn't in any way affect my affection for Ubuntu - it will always be part of my computing experience. Thanks.

---

### Post by Bashing-om on 2012-09-05
Barrie;

  Lets not get to hasty here, Consider that the drives have windows formating.
As a rule, Use windows tools to deal with windows problems, Linux tools to cope with ubuntu situations. That said, how 'bout looking/repartitioning with the window's disk utilities.... (if worse does come to worse, and you have backed up important data, and do not mind loosing all else; we can run the "dd" command to zero out the disk and perhaps reclaim the lost space ????

[INDENT]just bidding my time <==BDQ
[/INDENT]

---

### Post by corowakid on 2012-09-05
Thanks for the response. I probably didn't outline what I did originally. I had Ubuntu 12.04 blissfully working away and all was good. I decided to change back to Win XP, as I had some music I wanted to have on my iPod. So, use gParted, delete the SDA partition, create a new NTFS partition for XP, saw that only 8Gb was being formatted, and thought this was strange, but I'd come back and revisit it when XP was on. Still showing 8Gb, and absolutely no other space showing. I realised I should have used the ms-sys --mbr /dev/sda command. Tried to do that using System Restore Disk, but no dice. After that I realised that I had no knowledge to allow me to go forward. I'm typing this on Ubuntu 12.04 reinstalled, works a charm, but shows only 8Gb on HDD.

So, I'm up for trying any fix, on the basis that the computer has limited attraction as it is, and if it can't be set right I'll dice it and use one of the others. But by going forward, a fix, in whatever form, will grow my limited Ubuntu knowledge, so that I will be able to recognise and possibly fix a similar occurence. I await any further asistance. Regards.

---

### Post by Bashing-om on 2012-09-05
Barrie;
  with no further ado, here we are:
```

sudo dd if=/dev/zero of=/dev/sda bs=1M

```  This code zeros out the disk, in this case sda ... which I expect to be the only disk in use.
run this command from the live cd (sda can not be mounted to accomplish this, running from live cd insures disk is not mounted) Strongly advise that you remove from the system all other drives and disk devices(prevents overwriting a good disk in the event of "some error") [IF you know for CERTAIN the disk is in fact sda then no harm will entail].
  What I expect to happen is dd wipes out all the meta data embedded onto the disk thus enabling to format and partition the disk.

  When you run this code ....there is no output to the screen until the process is completed; A method to obtain a status is below. It Will take some time to complete. On my 500 gig drives it takes 2 hours per disk (see I have had hands- on-experience) to complete.
to obtain a status:
open another terminal session (tty2), in tty2 enter:
```
ps -ef | grep dd
```in the output look for the process dd; note the number in the first column (pick the process of dd, not the process of grep for dd, both will be displayed.
With the number from this code do this code in tty2:
```
sudo kill SIGUSR1 <insert dd's number>
```as in :```
sudo kill SIGUSR1 1234
```OK ? ...The system will crunch the numbers for a bit ...and directly will have output in tty1. Enter the kill code in tty2 as often as you want to get a status on dd's progress.
 All we are doing here is finding the process indentification (PID) of all process and using grep to only show that of dd.
I will leave it to you as an exercise to determine why SIGUSR1 performs the display function !

  I hope it works .. I have known of some cases even dd could not write to. Let us know how it works out.[INDENT]regards <==BDQ
[/INDENT]

---

### Post by corowakid on 2012-09-06
Well, to everyone who responded, this my mea culpa. I thought of leaving town, changing my logon details, foregoing Ubuntu, but I figured it was better to take the music for my idiocy. My HDD IS NOT 160Gb - it is an 8Gb SSD, as one of the posters mentioned. I was too focused on WHAT I knew, rather than getting the box it came in and looking at the specs. Sure enough, there it is in cold letters, 8Gb.

So, I apologise totally for wasting the time of the friendly posters who must have had thoughts of whether I really knew. I am embarrassed, and I apologise for taking your valuable time.

I'll fly below the radar for a while now - it will be think first, post last. Hopefully, if I do post again, I trust you will ignore this saga I caused.

Thanks for everything.

---

### Post by oldfred on 2012-09-06
Sometimes we need a mistake to learn even more. Glad it is solved.

---

### Post by Bashing-om on 2012-09-06
+1 oldfred ... A learning experience for all ... With this wonderful operating system, it is rare indeed a day goes by I do not learn more.

[INDENT]enjoy <==BDQ

[/INDENT]

---

### Post by dwashere on 2013-07-31
Now to be found here: [http://ubuntuforums.org/showthread.php?t=2164446](http://ubuntuforums.org/showthread.php?t=2164446)

Sorry for posting it first here!

---

