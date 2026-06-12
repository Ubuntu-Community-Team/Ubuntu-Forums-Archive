---
title: "File recovery after formatting wrong partition"
date: 2012-02-14
forum: General Help
---

### Post by du3113 on 2012-02-14
Hi,yesterday I made a mistake, that I try to resolve now. Instead of formatting the partition of my old OS, I formatted a data partition (which was ntfs before formatting) with ext4 file system and installed an OS (xubuntu). Unfortunately after having installed it, I found out that I had made a mistake... :(



The first step I took was making an image of that partition using (g)ddrescue. Then I let testdisk analyze it, but it couldn't find ntfs headers - so it failed to recover any data.



Unfortunately the series of my(?) fails continues:
I just don't know why (because I did never intend to do so) my encrypted LUKS-partition on the same drive (located at the end of the volume) was displayed with a size of 8MB (of once 3xx GB) and the rest of the space till the end of the volume is displayed as "free" now. As I did not do anything intentionally to do so, I hope that just the partition table is damaged.
After remarking the resized partition I took another ddrescue image of the whole drive.
So I can use the drive to install the software and use the images to recover the data afterwards, am I right?


Would you recommend to keep the drive as is or are the images enough to recover data? I don't really need all data of both volumes - but to get even some of that data would be great.




Best wishes
 duelle

---

### Post by winh8r on 2012-02-14
It is always safer to work on images of the drive when recovering data, that way you will always have the original in the state it was when you started.

If you make a mistake on an image of the disk then you have not lost everything.


I would suggest that you spend a little time reading up on what would be best for you before trying anything else though.


the fact that you formatted an ntfs drive to ext4 then installed an OS on it may well have rendered the data on the ntfs unrecoverable, without going into extremely low level forensic recovery which is really a specialist job and consequently very expensive to have done.



If you run Photorec (part of the testdisk suite) on one of the images you may well get some data back.

There is a step by step guide to using the program available at


[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step]("http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step")

there is useful info here also:

[extundelete.sourceforge.net]("extundelete.sourceforge.net")


I hope this is of some help to you.

---

### Post by Mark Phelps on 2012-02-14
If you have access to an MS Windows PC, and you can attached the formatted drive to that PC ... and ... are willing to spend some money, you may be able to recover that data using MS Window apps.

If interested, read on ...

In my experience, Windows filesystem utilities have been best at recovering data from former Windows partitions; Linux filesystem utilities have been best at recovering data from former Linux partitions.

Since your data was on a Windows partition, based on my experience at doing this successfully, my suggestions are the following:
[NOTE: If your PC has a working copy of MS Windows on it, skip to step 4]
1) Find someone with a working MS Windows PC
2) Remove your drive from this PC.
3) Connect your old drive to the MS Windows PC.
4) Download and install the trial version of GetDataBack for NTFS from Runtime Software in MS Windows.
5) Run GetDataBack and select the option to find Deleted files.
6) When done, browse the filesystem in the app to see if your directories and files were found.  If so, view some to confirm the contents are intact.
7) If they are, you will have to purchase GetDataBack to do the actual recovery. You won't have to reinstall it; instead, they will email you an activation code which you can use to turn on the recovery feature.

And, last time I checked, GetDataBack for NTFS was $80, USD.

There's also a FREE MS Windows file system recovery app known as Recuva.  You could try that first -- but my experience in MS Windows is you get what you pay for.

Your data ... your money ... your choice.

---

### Post by shanky2345 on 2013-01-29
Hi,

Don’t worry; it is easy to recover data lost due to accidentally formatting of hard drive partition. Few days back, even I had accidentally formatted wrong partitions and lost some of my important business documents. At that time unformat partition software really helped me to [recover partition after format]("http://www.unformatpartition.com/"). I was very happy when I got all my lost data back. So even you can give a [try]("http://www.unformatpartition.com/download/unformatpartition-windows.exe") to recover your lost data from formatted hard drive partition.

Good luck,
Shanky Jacob

---

