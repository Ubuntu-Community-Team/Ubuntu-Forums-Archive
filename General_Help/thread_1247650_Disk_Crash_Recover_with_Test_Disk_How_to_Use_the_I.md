---
title: "Disk Crash Recover with Test Disk How to Use the Image.dd file"
date: 2009-08-23
forum: General Help
---

### Post by SneakPeak on 2009-08-23
[Solved] Edit:

I never did figure out how to work with the image.dd file but it turned out not to be necessary.  Testdisk seems to have fixed the drive.  I am not sure exactly what did the trick but I re-wrote the partition table using Testdisk and then re-wrote the boot using Testdisk.  Interestingly this gives 1234F when one boots and (although I never tested it becasue by the time I figured out what this means I had already fixed my grub) this is a boot menu created by Testdisk indicating fisrt partition, second partition.. floppy!  Anyway I think that is what it is and this info may help someone faced with 1234F and not knowing what it is.

Finally look at post number 5 for fixing grub! 

Hi,

I have 9.04 installed on an external USB hard drive.  Today it just crashed.  One minute it was working the next minute not. I got a pop up window where one would normally see an error message but it was just filled with little rectangular blocks.

The disk won't boot and I can't access it from a different Linux box which I used to be able to do.

I have run test disk and re-written the partition table and the boot information (I think) but this has not helped.  Now I am using test disk to create a file Image.dd of the disk.  The question is how can I do anything useful with Image.dd?  How do I access it and how do I retrieve the data from it?

Thanks

Sneaks

---

### Post by aysiu on 2009-08-24
If you already have *testdisk* installed, just run the command ```
sudo photorec
``` from the terminal to try to recover the deleted data.

---

### Post by SneakPeak on 2009-08-24
Hi 

Problem sort of solved.  After playing around with testdisk for a while including writing an image and writing the partition table the disk was suddenly available again.  It would not boot but I could see all the files and I could copy them accross to a backup disk.  I wish I could be more specific about what had "solved" the problem but unfortunately I don't know what did the trick.  

The disk still does not boot and I have tried writing the boot information using testdisk and I have used fsck via gparted but I still can't get the disk to boot.  My plan now that I have recovered my data is to repartition and reformat the disk and start with a clean installation.

Thanks for the suggestion.

Sneaks

---

### Post by P4man on 2009-08-24
to make it boot again, you may just have to reinstall grub on it. That said, be careful with that drive, I would no longer trust it. Perhaps you can test it for harware defects using ultimatebootcd.

---

### Post by SneakPeak on 2009-08-24
Thanks P4Man

Supergrub booted my system no problem.  I then fixed it with these commands:

sudo grub
find /boot/grub/stage1
root (hd#,#)
setup (hd#)

I want to now do a hardware check on the drive to check if there are any problems.  The "UltimateBootCD" has a lot of stuff but I don't want to use something that is going to potentially cause damage.  Any recommendations on a hardware testing tool?

Cheers

Sneaks

---

### Post by P4man on 2009-08-24
you need the tool from your harddisk vendor to do a really good test. Do you know the brand of harddisk ? I only recommended ultimate boot cd cause it has ALL tools on one convenient disk.

---

### Post by louieb on 2009-08-24
> **SneakPeak said:**
>   Any recommendations on a hardware testing tool?
```
sudo apt-get install smartmontools
```> 
control and monitor storage systems using S.M.A.R.T. 
The smartmontools package contains two utility programs (smartctl and smartd)
to control and monitor storage systems using the Self-Monitoring, Analysis and
Reporting Technology System (S.M.A.R.T.) built into most modern ATA and SCSI
hard disks. It is derived from the smartsuite package, and includes support
for ATA/ATAPI-5 disks. It should run on any modern Linux system.
Pretty nice. Command line only at this time. But coming with v9.10 is a graphical front end Gsmartcontrol.  BTW the [PartedMagicCD]("http://partedmagic.com/wiki/PartedMagic.php?n=Main.PartedMagic")  has the GsmartControl front end if want to check it out.

---

### Post by SneakPeak on 2009-08-25
Thanks for the advice Louieb

My drive is an **external Fujitsu Siemens USB **drive.  I set up my bios to boot first from USB and in this way I can run a complete Ubuntu machine on my work laptop without distrubing any of the work stuff on the internal hard drive.  When I did the install I just removed the laptop internal drive temporarily. 

Will smartmontools work on an external USB interface?  I have been advised that it won't?

Thanks

Adrian

---

### Post by P4man on 2009-08-25
> **SneakPeak said:**
> Thanks for the advice Louieb

My drive is an **external Fujitsu Siemens USB **drive.  I set up my bios to boot first from USB and in this way I can run a complete Ubuntu machine on my work laptop without distrubing any of the work stuff on the internal hard drive.  When I did the install I just removed the laptop internal drive temporarily. 

Will smartmontools work on an external USB interface?  I have been advised that it won't?

Thanks

Adrian

AFAIK, smart won't work over an USB interface. Im not even sure if any diagnostics program can. Most are DOS based and might have trouble finding it on a USB bus. If there are any, its probably gonna be a windows program.

Still, try the ultimate bootcd, see if there is anyting for fujitsu and if it can detect the usb drive. (Although actually its not even guaranteed there is a fujitsu drive inside that enclosure:) )

Other solution is taking the drive out of the enclosure and connect it to a desktop.

---

### Post by P4man on 2009-08-25
actually, found something that would work with USB enclosures. Never tried it, so i cant vouch for it, and its for windows.. but have a look at this perhaps:

[http://hddguru.com/content/en/software/2006.01.22-HDDScan/](http://hddguru.com/content/en/software/2006.01.22-HDDScan/)

---

### Post by SneakPeak on 2009-08-25
> **P4man said:**
> actually, found something that would work with USB enclosures. Never tried it, so i cant vouch for it, and its for windows.. but have a look at this perhaps:

[http://hddguru.com/content/en/software/2006.01.22-HDDScan/](http://hddguru.com/content/en/software/2006.01.22-HDDScan/)

Thanks P4man

One last question.  If this is a windows tool what are the chances of it properly recognizing ext3 partitions and not messing them up?  I don't want the diagnostic tool to screw up my drive by scanning and trying to do something crazy like convert to FAT or NTFS?

Thanks again

Sneaks

---

### Post by P4man on 2009-08-25
> **SneakPeak said:**
> Thanks P4man

One last question.  If this is a windows tool what are the chances of it properly recognizing ext3 partitions and not messing them up?  I don't want the diagnostic tool to screw up my drive by scanning and trying to do something crazy like convert to FAT or NTFS?

Thanks again

Sneaks

A proper diagnostics tool should be oblivious about filesystems. It doesnt care about files or partitions or how the disk is organized or whats on it; it would read or read/write sectors, and whether the data on those represent an Ext or NTFS file system, or just random bits doesn't matter. Its a bit like dd being able to copy  regardless of filesystems or partitions, as it just ignores them and copies sectors blindly. It doesn't have to understand them. A photocopier can copy pages of chinese without knowing any chinese :)

That said, I dont know if that program can do a write test without destroying the drive contents, but Im fairly certain it will give you a warning before erasing the drive :)

---

### Post by SneakPeak on 2009-08-25
Thanks P4man,

I think I am going to go the conservative route and just backup daily and see how my drive performs.  If it crashes, so be it, but I don't want to risk breaking it with the diagnostic tool.  

I'll run the diagnostics after the crash or hopefully never! 

Cheers

Sneaks

---

### Post by P4man on 2009-08-25
You chicken :D (Or would that be ostrich ? :p )

here, I glanced over this page:

[http://hddguru.com/content/en/software/2006.01.22-HDDScan/](http://hddguru.com/content/en/software/2006.01.22-HDDScan/)

Except for the erase option (obviously), noting is destructive. It only reads. It can do a lot of nifty things, including a full smart analysis. No reason I can see not to try it. Unless you prefer not to know your disk is perhaps dying :)

---

### Post by SneakPeak on 2009-08-25
All right you have convinced me

I'll give it a try and post the results here.

Cheers

Chicken Man.....

---

### Post by SneakPeak on 2009-08-25
Ok so I tried this software:

[http://hddguru.com/content/en/softwa...01.22-HDDScan/](http://hddguru.com/content/en/softwa...01.22-HDDScan/)

In the documentation it says that S.M.A.R.T testing is possible for compatible / recognized USB drives.  Mine is not one of those so I could only run the read tests.  I ran the "Read" test which takes forever.  I left it running and went to bed.  When I got up the status showed "Finished"  There were no error messages and I couldn't find a log file or anything like that showing a report.

So I guess as far as "Read" goes the drive is ok.

I will go back to regular backup and see what happens.

Those who have recognized / compatible external drives my get more value from this tool.

Cheers

Sneaks

---

