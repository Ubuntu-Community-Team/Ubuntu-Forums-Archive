---
title: "Raid 0 / XFS Problems / Missing Partition"
date: 2012-05-31
forum: General Help
---

### Post by prosonik on 2012-05-31
Hi,



I think I've got my self into self raid0 problems. I'm hoping somebody can offer some advice that I haven't been able to find with the 5-10 hours of googling i've done.

To start off with, on an old 780G motherboard using the latest Ubuntu 12.04, I had a raid0 setup  for my mythbox. About a week ago, a drive disappeared and broke the raid array. I tracked it down to either a bad cable or
sata connection, as the bios no longer detected it. 

It prompted to do a desired upgrade, I switch the motherboard to slightly newer am3 based processor/mobo combo.

However, it would not rebuild the array using the standard:

```
mdadm --assemble --scan
```

An inspection of the drives using --examine it appeared that the Raid version was unknown. After many hours of googling, I ended up (and this was my mistake) doing a mdadm --create. 

So I have the array back up, however the partion table has been destroyed. My only hint is Dmesg displays:

```
  573.701922] md: md0 stopped.
[  573.707732] md: bind<sdc5>
[  573.716369] md: bind<sdd5>
[  573.716540] md: bind<sde5>
[  573.740643] md: bind<sdb6>
[  573.754121] md/raid0:md0: md_size is 7792575488 sectors.
[  573.754125] md: RAID0 configuration for md0 - 2 zones
[  573.754127] md: zone0=[sdb6/sdc5/sdd5/sde5]
[  573.754131]       zone-offset=         0KB, device-offset=         0KB, size=3864045568KB
[  573.754133] md: zone1=[sdc5/sdd5/sde5]
[  573.754136]       zone-offset=3864045568KB, device-offset= 966011392KB, size=  32242176KB
[  573.754138]
[  573.754157] md0: detected capacity change from 0 to 3989798649856
[  573.789121]  md0: unknown partition table
[  613.211459] XFS (md0): bad magic number
[  613.211465] XFS (md0): SB validate failed
[33865.128940] md0: detected capacity change from 3989798649856 to 0
[33865.128950] md: md0 stopped.
[33865.128959] md: unbind<sdb6>
[33865.144028] md: export_rdev(sdb6)
[33865.144381] md: unbind<sde5>
[33865.160057] md: export_rdev(sde5)
[33865.160277] md: unbind<sdd5>
[33865.176022] md: export_rdev(sdd5)
[33865.176193] md: unbind<sdc5>
[33865.176272] md: export_rdev(sdc5)
[33868.901090] md: md0 stopped.
[33868.905656] md: bind<sdc5>
[33868.905825] md: bind<sdd5>
[33868.905979] md: bind<sde5>
[33868.906137] md: bind<sdb6>
[33868.913736] md/raid0:md0: md_size is 7792575488 sectors.
[33868.913742] md: RAID0 configuration for md0 - 2 zones
[33868.913745] md: zone0=[sdb6/sdc5/sdd5/sde5]
[33868.913754]       zone-offset=         0KB, device-offset=         0KB, size=3864045568KB
[33868.913757] md: zone1=[sdc5/sdd5/sde5]
[33868.913764]       zone-offset=3864045568KB, device-offset= 966011392KB, size=  32242176KB
[33868.913784]
[33868.913809] md0: detected capacity change from 0 to 3989798649856
[33868.931731]  md0: unknown partition table
[34308.177586] XFS (md0): bad magic number
[34308.177592] XFS (md0): SB validate failed
```


I known any fdisk commands will destroy any remaining data. Is there anything I can do to get the data back? I'm okay with mounting it read-only and copying the data to a 3rd drive. Really, I'd like to move the drives to raid 5 or 1+0, whatever would be better for mythtv.

Ian

---

### Post by Cheesemill on 2012-05-31
It's going to be a lot quicker and easier to just create a new array and restore your data from your most recent backup rather than trying to recover from your existing situation.

---

### Post by strask on 2012-05-31
> **prosonik said:**
> I known any fdisk commands will destroy any remaining data. Is there anything I can do to get the data back?

My first approach would be to see if testdisk can help you: [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

I've never used it myself so pointing you towards the software and documentation there is all I can do. Best luck to you.

---

### Post by prosonik on 2012-05-31
That would be nice, if this wasn't my backup solution. However, I have the really important stuff mostly in the cloud. I was the process of backing up my photos etc.  But the vast majority of this is video and mythtv recordings, thus the big-honking 4 gig drive.  


> **Cheesemill said:**
> It's going to be a lot quicker and easier to just create a new array and restore your data from your most recent backup rather than trying to recover from your existing situation.

---

### Post by Cheesemill on 2012-05-31
> That would be nice, if this wasn't my backup solution.Sorry to be the bearer of bad news but for future reference RAID is never a backup solution, it's only a business continuity plan. There are several situations which don't involve a drive dying that can wipe out a RAID array such as controller malfunction, write hole data corruption, application errors and user error (for example accidentally deleting data).

Even if you do use RAID you should always have a backup solution in place as well.

Worse than that RAID0 doesn't provide any redundancy at all, if 1 drive in a RAID0 array fails you lose **all** of your data. RAID0 should only ever be used to get increased performance from drives, never for any other reason. With a RAID0 you actually increase your risk of data loss over using single drives.

---

### Post by prosonik on 2012-06-02
Unfortunately, I'm well aware of the downfalls of raid0. I used to go with LVM over raid0. The drives were stripped together to create a massive storage unit for Mythtv/Video. Overtime, it became a dumping ground for all things digital. I have other storage units on the network. I just never got around to setting up an Rsync solution. 

That said, it's crashed. I'm geek. I like to give it a go and see what I can recover. I was hopping somebody had some advice that I hadn't found in googling. I'm currently working with Testdesk but so far no luck.


> **Cheesemill said:**
> Sorry to be the bearer of bad news but for future reference RAID is never a backup solution, it's only a business continuity plan. There are several situations which don't involve a drive dying that can wipe out a RAID array such as controller malfunction, write hole data corruption, application errors and user error (for example accidlly deleting data).

Even if you do use RAID you should always have a backup solution in place as well.

Worse than that RAID0 doesn't provide any redundancy at all, if 1 drive in a RAID0 array fails you lose **all** of your data. RAID0 should only ever be used to get increased performance from drives, never for any other reason. With a RAID0 you actually increase your risk of data loss over using single drives.

---

### Post by prosonik on 2012-06-03
Update:

I didn't have any luck with Testdisk, but it's brother product PhotoRec has done a very good job at finding and recovering the files. I did the recovery on the the drive themselves, not the RAID volume. My photos and mythtv mpegs are in good condition, but the mp3's aren't. Really, the only thing important are the photos.

From what I remember, Photorec is installed when you in install testdisk. Both are found in the ubuntu repos..



> 
I known any fdisk commands will destroy any remaining data. Is there anything I can do to get the data back? I'm okay with mounting it read-only and copying the data to a 3rd drive. Really, I'd like to move the drives to raid 5 or 1+0, whatever would be better for mythtv.

Ian

---

### Post by prosonik on 2012-06-03
Testdisk, not so much. Photorec seems to have done the task of recovery. Thanks!

> **strask said:**
> My first approach would be to see if testdisk can help you: [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

I've never used it myself so pointing you towards the software and documentation there is all I can do. Best luck to you.

---

