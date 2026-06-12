---
title: "Error while copying file (Error splicing file: Input/output error)"
date: 2010-06-03
forum: General Help
---

### Post by tyliew333 on 2010-06-03
Hi, 

When I try to copy PDF files from one folder to another folder, it give me this error:

"*Error while copying "2004-SNUG-Europe-paper_...log_DPI_with_SystemC.pdf". There was an error copying the file into /media/CCDCE66BDCE64F70/Backup Master/Heterogeneous_cosimulation/Documentation*"
"Error splicing file: Input/output error"

What is the reason of this error and how can this be fixed?

thanks,
ty6

---

### Post by civ247 on 2010-06-12
Bump.

I get this quite often as well. Mostly when copying data to/from external HD.

---

### Post by Stoneface on 2010-06-14
I think it can be caused by a scratched DVD like I have right now. I am trying to salvage the data by copying it and get the same error:

"Error while copying "VTS_01_0.VOB".

Error splicing file: Input/output error"

I think these dmesg error are connected to it:

```
[173159.276747] Buffer I/O error on device sr1, logical block 404
[173159.276751] Buffer I/O error on device sr1, logical block 405
[173159.276755] Buffer I/O error on device sr1, logical block 406
[173159.276758] Buffer I/O error on device sr1, logical block 407
[173159.276760] Buffer I/O error on device sr1, logical block 408
[173159.276763] Buffer I/O error on device sr1, logical block 409
[173159.276765] Buffer I/O error on device sr1, logical block 410
[173159.276767] Buffer I/O error on device sr1, logical block 411
[173159.276769] Buffer I/O error on device sr1, logical block 412
[173159.276771] Buffer I/O error on device sr1, logical block 413

```

 Any tips?

---

### Post by damontallen on 2010-06-18
> **civ247 said:**
> Bump.

I get this quite often as well. Mostly when copying data to/from external HD.

I was having this problem transferring data from my old computer to my new one through an esata external drive.  My old computer had an esata card (6 months old.  Rosewill RC-210 Silicon Image External eSATA $19.99 at Newegg) and once I swapped the card from my old computer to my new one I didn't have any problems reading the card.  My new computer has a esata port on the motherboard (ASUS M4A78T-E AM3 AMD 790GX) but it kept giving my the "Error splicing file: Input/output error" on certain files.  I don't know if this will fix your problems but it fixed mine.

---

### Post by AgentY on 2010-06-24
I'm having the same problem on with an avi file;

I downloaded a 700mb avi - MOVED it to an external hdd. - (Error splicing file: Input/output error)
This file then dissapeared from both drives - no idea where it went...

I re-downloaded the exact same file - COPIED it to the same external hdd - (Error splicing file: Input/output error)

I can copy other files fine so this one is begging to bug me. I might try to do this in Windows shortly if i still have no luck.. 

If any one has any ideas I'd be very greatful...

Thanks

Y.

(Ubuntu 10.04 LTS)


(Update)
I've also just noticed that once i hit one of the options after the error (cancel, skip, skip all) the external drives unmounts itself / no longer visible unless its removed from USB port and plugged in again.


*** FIX / Work-around***

OK, it was this simple for me..

Renamed the folder "moivename [year]" to "moviename[year]" and it copied over first time! (deleted all spaces from the folder and file names).

Hope this helps anyone else that has been annoyed by this error. It may also work just renaming the files to anything other than what it errored with but the above worked for me so unable to test!

---

### Post by ttocScott on 2010-06-29
If any of you earlier posters see this, are you using EXT4 by chance? I'm having issues with moving files over from a drive with EXT4 to another drive (with EXT3), and the reason I am moving the files is because I want to reformat the drive and also put it back to EXT3. I can move some folders, but if I try to move a file that is too big, I get that error. Then I have to reboot to reset everything, and I can start the process over until it happens again, and I have to reboot again. 
Scott

---

### Post by kob0724 on 2010-07-10
I'm getting the exact same issue when copying data from one of my external hard drives to another. Anybody have any idea as to what is going on here?

Just a little more information.
External Hard Drive 1:
A RAID box with Software RAID 5. 4x1.5 TB hard drives. Connected via eSATA.
FileSystem: XFS

External Hard Drive 2:
1.5 TB hard drive with NTFS. Connected via USB.

---

### Post by rakeshbabugr on 2010-07-14
I am facing the same problem while trying to copy a file from external hard disk (WD P/N: WD2500ME-00 4408A S/N WXE208MX8278 R/N A7B) .

I have to try it to copy in Windows and see if it works.

---

### Post by jatoo on 2010-07-15
I am having this problem copying from a CD to an ext4 drive.

---

### Post by rakeshbabugr on 2010-07-15
Well, the  similar issue I faced was because of a defective file I think, because I couldn't copy in Windows XP either.

---

### Post by kob0724 on 2010-07-17
After my external crashed again, I unplugged it, plugged it back in, and tried to mount it. There was an error. I ran dmesg | tail and got this:
[75935.353345] scsi 3:0:0:0: Direct-Access     ATA      eSATA-2 External 0    PQ: 0 ANSI: 5
[75935.353508] sd 3:0:0:0: Attached scsi generic sg2 type 0
[75935.353613] sd 3:0:0:0: [sdd] 8790531504 512-byte logical blocks: (4.50 TB/4.09 TiB)
[75935.353658] sd 3:0:0:0: [sdd] Write Protect is off
[75935.353661] sd 3:0:0:0: [sdd] Mode Sense: 00 3a 00 00
[75935.353685] sd 3:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[75935.354343]  sdd: sdd1
[75936.054487] sd 3:0:0:0: [sdd] Attached SCSI disk
[75941.965574] XFS: Filesystem sdd1 has duplicate UUID - can't mount
[75963.280011] Filesystem "sdb1": xfs_log_force: error 5 returned.


-Kurtis

---

### Post by B-Con on 2010-07-22
I'm having the same problem, both reading from and writing to various files. I re-formatted the external USB drive and it took a couple tries before succeeding. At first I thought it was a bad drive/interface, but I'm not sure now. I've not seen the error before.

> **ttocScott said:**
> If any of you earlier posters see this, are you using EXT4 by chance? I'm having issues with moving files over from a drive with EXT4 to another drive (with EXT3), and the reason I am moving the files is because I want to reformat the drive and also put it back to EXT3. I can move some folders, but if I try to move a file that is too big, I get that error. Then I have to reboot to reset everything, and I can start the process over until it happens again, and I have to reboot again. 
Scott

Yep. I'm running on ext4, trying to copy to an external NTFS.

And renaming the folder I was trying to copy over to no longer include spaces worked for me too. Very weird.

---

### Post by ignotus666 on 2010-07-28
I have the same error too (error while copying file (Error splicing file: Input/output error)) when trying to copy files from a brand-new pc to a usb storage device. I've tried reformatting the usb device (ext3, ext4, FAT), renaming the file to be copied so it doesn't have spaces; I even created a new partition on my pc hard drive using ext3 (it was originally ext4 and thought it might be that) and I still can't copy large files to the usb device - files smaller than 600mb will copy (very slowly though), but larger ones won't. This problem is really annoying. Like someone else on this thread said, after the error message the usb device unmounts itself and when I plug it in again, suddenly it's read-only. There's nothing wrong with the usb device or the file either as they do the same process fine with my laptop (I have lucid on both computers).

Any suggestions?

---

### Post by B-Con on 2010-07-28
Well, I think I fixed the problem, sort of. That same external drive I was copying to was having problems in Windows as well. Opening the files or listing the directories on the drive in Windows caused Windows Explorer to hang, sometimes indefinitely.

I had two identical external hard drive enclosures, so I took the drive out of the first and put it in the second one. It seemed like all my problems disappeared. Windows was able to read from the drive perfectly and I was able to copy data to it with no splicing errors under Linux.

So, it looks like my problem was fixed by changing hard drive enclosures, implying that it was the enclosure that was the problem. However, considering that so many other people report a similar problem makes me skeptical. All I can say is that it worked fine under my limited tests, I'll report anything else of interest if I find it.

---

### Post by tontaube on 2010-08-14
Hello,

i get this error when I try to copy a folder from a VCD (internal DVD-RW drive) to a NTFS folder.
When I copy the same in WinXP it works flawlessly.

Ubuntu 10.04 Lucid Lynx 32bit



This issue with copying VCD seems to be a general problem. I've tried on several computers with different hardware running Ubuntu Lucid to copy a VCD (to ext3 and NTFS) and always got this error - so I'm sure that this exludes possible hardware issues.

---

### Post by djmac on 2010-09-10
Hi, also getting the same problem. I am moving files from a fat32 partition to a fat32 partition. Didn't seem to have problems going ext3 to fat32, or vice versa. 

Thanks.

---

### Post by stkrzysiak on 2010-09-18
Same issue here, started seeing it when I started using ext4 on my home partition.  The external I am transferring to is ntfs, so it appears the common denominator is ext4.  I had transferred about 290 gigs(different ubuntu distro, pre 10.04, & ext3) prior to ext4 without ever seeing this error :/

---

### Post by chocolateboy on 2010-09-19
I had the same problem copying a 700 MB file to a USB flash drive. It would consistently crash with this error, whether copying from NTFS or ext3.

The solution that worked for me was to plug the drive into one of the USB ports at the **back** of the computer rather than the front.

I'm not sure if this is a power issue or a USB 1.x vs USB 2.0 issue, but I've seen external USB drive manuals explicitly suggest/require the use of the rear ports, and it worked in this case.

---

### Post by Ripfox on 2010-09-20
Yea, this is super not cool man. I am trying to move a 4.2 GB file on to an 8gb flash drive and crashing every time with this error in every USB port.

---

### Post by sderose on 2010-09-22
Same problem here, copying from a CD. Turned out to be a fingerprint on the CD. Wiped it off and the error went away.

:)

---

### Post by hugo_koopmans on 2010-10-12
same here, trying to copy a vm disk file.

dmesg | til gives:

hugo@vaio:~$ dmesg|tail
[33533.104863] sd 8:0:0:0: [sdc] CDB: Read(10): 28 00 0a 54 89 8f 00 00 08 00
[33533.104886] end_request: I/O error, dev sdc, sector 173312399
[33533.104898] Buffer I/O error on device sdc1, logical block 21664042
[33537.204190] sd 8:0:0:0: [sdc] Unhandled sense code
[33537.204198] sd 8:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[33537.204208] sd 8:0:0:0: [sdc] Sense Key : Medium Error [current] 
[33537.204219] sd 8:0:0:0: [sdc] Add. Sense: Unrecovered read error
[33537.204230] sd 8:0:0:0: [sdc] CDB: Read(10): 28 00 0a 54 89 8f 00 00 08 00
[33537.204253] end_request: I/O error, dev sdc, sector 173312399
[33537.204265] Buffer I/O error on device sdc1, logical block 21664042
hugo@vaio:~$ 

something about an unhandled sense code ... any suggestions?

hugo

---

### Post by issis on 2010-10-16
Guys,

I'm having the same error on Lucid 10.04. I'm trying to copy a 2.5 GB file to my external hard drive and it gets stuck on reaching 811MB. It's really frustrating....:mad:

I get the following message report on doing a "dmesg | tail"

[ 6560.252506] sd 0:0:0:0: [sda] Unhandled sense code
[ 6560.252511] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 6560.252518] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[ 6560.252527] Descriptor sense data with sense descriptors (in hex):
[ 6560.252532]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[ 6560.252550]         00 68 96 68 
[ 6560.252558] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[ 6560.252569] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 00 68 95 e0 00 01 00 00
[ 6560.252587] end_request: I/O error, dev sda, sector 6854248
[ 6560.252623] ata1: EH complete

I'm using ext4 as my file system on my desktop while my external hard drive has NTFS.

Is this a known issue with **ext4**. Has anyone tried copying large files in excess of 4GB successfully on **ext3** drives? 

Thanks!

---

### Post by Youcandoit! on 2010-11-17
For me it seemed to be some kind of USB power issue. I tried to copy a file less than 130mb from my ext4 hard disk to fat32 USB flash drive. I had the splice error until I connected my USB directly to usb port in the back of my computer. Now I am transferring files without any problems.

---

### Post by ben2talk on 2010-11-18
No -  I'm getting it trying to copy files back from a CD to an NTFS partition - unless my ext4 home partition is playing a part in this...

Maybe I'll fire up a virtualbox and try to get the files off disk that way.

Okay - didn't work. I think it's a problem with disks (I had many errors writing discs with Ubuntu - sometimes with no warning - so these files which took me a week to dribble on torrent have now gone).

---

### Post by Alabaster on 2010-11-18
I'm having a very similar issue, I'm trying to copy a 4.2 gb tar.gz file on to a NTFS eSATA dirve tho, from ext4 (lucid)

---

### Post by wdiz on 2010-11-19
Got the same problem copying from internal SSD (ext4 Home partition) to internal Datas hard drive with NTFS

---

### Post by eundas on 2010-11-19
I'm having the same annoying problem. A temporary fix I found was to install a USB hub. If I attach the external disk directly to one of the computer's ports, then using the disk becomes impossible. Attaching the disk to the hub makes it usable again.

Eduardo

---

### Post by morsch on 2010-11-24
Thanks Eduardo - yes, connecting the USB drive to a USB hub rather than connecting directly DOES WORK. Unbelievable. I am curious to know why :-)

I [described my success on qompute]("http://www.qompute.net/2010/11/ubuntu-copying-from-one-media-to.html"), though no more info, than simply stating that the solution by Eduardo works :-)

---

### Post by BobTheMailMan on 2010-12-13
I am having same problem.

Using External Rosewell With a ESATA connection

Copying 219.6gb of files and it is one movie file, ~700.mb avi. 

Copying From HFS+ Journaled volume to a Ubuntu Software raid 0 ext 4 volume, while in ubuntu 10.10 under the root superuser login. 



Some of you might want to try under root in case its a permissions issue, I thought i was having problems with HFS+ and permissions but it seamed i fixed those. 


Similarities seem to include media files? ext4? external hard drives via usb and esata? and yea. 

the movie files plays just fine it seams and if I try and copy it by itself it gets about 100mb in to the copy and then brings up the error.

---

### Post by aeklabunde on 2010-12-28
I have the same I/O error trying to copy media from DVD to my hard drive. Worked once, and then never again.  First workaround was to compress, and then unpack into the located I wanted the media.  That also worked just once, then the I/O error for subsequent atttempts.  The next two media DVD's I saved as ISO's, and that is still working for now! Only problem is that when I unpack the ISO to make it media player friendly (though the ISO file will play just fine on both VLC and XBMC, but not Movie Player) and restore the normal directory structure, the characters ";1" are added to the end of each VOB, BUP and IFO file.  I then have to rename the files to remove the additional characters or only VLC can play the media.  Crazy the workarounds we have to come up with to get around to a common problem.

---

### Post by gandonov on 2010-12-29
I have the same problem. I tried all suggestions from this thread, but with no success.

I have no solution, but I have a workaround. ;) / *Sorry for my English* /

I think that **the root of the the problem is that write operations (for USB memory) are too slow, and Ubuntu can not *sync* all writes.**

So, I split [FONT="Courier New"]THE_BIG_FILE[/FONT] (~8GB) into small pieces ([FONT="Courier New"]xaa, xab, xac, ...[/FONT]), and I copy them one by one to the USB device.
The tricky moment is that I **[FONT="Courier New"]sync[/FONT] all changes after every appended piece!**

I write a small bash script for this:
```

echo "Splitting into 40MB pieces."
split -b 41943040 THE_BIG_FILE

echo "Just to be sure that the destination file not exist."
rm /media/VOLUME/THE_BIG_FILE

echo "Let the show go on."
for file in x* ; do
	echo "Appending $file"
	cat $file >> /media/VOLUME/THE_BIG_FILE
	echo "**Sync...**"
	sync
done
```

---

### Post by lduperval on 2011-01-03
So, could it be that every n minutes, ext4 syncs and since you are copying very large files, the sync takes too long and give the splicing error?

Wondering because I get the same issue on an external iomega drive, copying large file from the ext4-formatted hdd to my internal hdd.

L

---

### Post by phatqao on 2011-01-10
I'm having the same issue copying .m4a files from an HFS+ partition on a WD 250 GB drive

---

### Post by sailors on 2011-01-12
Error splicing file: Input/output error 

I have that error on all my ubuntu's computer....... (since a long time)
copy any cd from external via USB 
I can read the directory but can not copy..

this is the only reason, why i still have Windows.
Because there it works !!!!!

---

### Post by Zuuperman on 2011-01-27
ok last night I reformatted my hard drive.. reinstalled Ubuntu 10.4
Now I am able to copy the files off the drive without a problem. 

However, I did find some bad sectors on my hard drive. It may be that those sectors are what caused the I/O error. I'm going to let my hard drive fill up again and see if it happens again. 

Tiny bit of detail: I didn't install any updates, dangerous, but I wonder if it's an update that might have caused the issue..

Let me know what you did to get around this...

---

### Post by dexterchief on 2011-01-28
I am getting this error as well. Both on my laptop (Dell XPS 1530) and my computer at work (an unknown Dell Desktop) both running Mav. These issues are recent for me, within the last few months.

---

### Post by khopek on 2011-01-31
I am getting this error whenever I try to copy 720p movies. I'm going to go ahead and blame it on the external being a FAT32 partition as I never had this problem with the NTFS formatted external [Seagate Free Agent].

My 1.5 NTFS external died so I bought a new 1.5TB drive and stuck it in the Seagate casing. I tried using Ubuntu to format as NTFS as it gave me the option; however, it wouldn't work so I opted for FAT32 since this drive is often used between Ubuntu and XP...

And now I can't copy...

---

### Post by Zuuperman on 2011-02-01
Yes I have issues copying big files to a fat32 formatted drive. Unfortunately, FAT32 is the format required by xbox to play media :(

Not had an issue copying to the NTFS drive since I reinstalled Ubuntu 10.4.. then again  I've been avoiding updates like a plague (just in case one of them caused me the pain last time)

---

### Post by Zuuperman on 2011-02-08
Ok in my case, I think I've seen the same error caused by two different conditions.. First that my usb flash drive is not supported.. always fails to copy big files to it..

the second is that I'm convinced that bad clusters on my primary hard drive allow data not to be read from it. Reason I'm convinced of this.. the problem only occurs when there is only 25gig of space remaining.. perhaps this is when the bad sectors begin to be used.. At this point I cannot copy to a drive which earlier I was able to copy the files to.. I can't make a copy of the file to the same drive.. something fishy with the drive...

I've completely reinstalled ubuntu 10.4 32bit and intentionally have not applied any updates.. and the error still occurs so the theory that an update may have caused this goes down the drain! I shall no longer be holding back from applying the updates...

Though i think the USB issue still somehow is going to be a bug.. I completely reformatted my USB stick and the error still occurs when copying a file to it...

---

### Post by The other One on 2011-02-09
I don't have a solution to this problem, but I did find a pretty easy work around.

I was having the same problem as everyone else whilst trying to copy 2 video files (~150MB and ~350MB each) from an NTFS partition to an EXT3 shared folder.

Over breakfast - where I do my best thinking - I decided to try putting the 2 files into a tar.gz file. They went into the archive fine, the archive file copied fine, and they were then successfully extracted onto the EXT3 partition.

I hope this helps some of you.

---

### Post by albertnet on 2011-02-10
Ok guys, here are my 2 cents.
I've never had any problems copying any kind of file but just started a couple hours ago and my symptoms and characteristics prior to the error:

Machine Specs:
Internal sata seagate 1Tb
Internal sata Seagate 2Tb
Internal Sata Maxtor 160Gb
OS running within SSD 30Gb
Phenom X4
4 Gb 1066 SDRAM2

Symptoms:
Recently (about 1 month) fresh install of maverick meerkat 10.10
Today an update came, something about flash and another which never read what it was about and both were 7Mb at most.
A few days ago I remember not seeing files from one of my folders and though someone erased my data!, rebooted and voila! there it was again.
Today, after the update, installing another virtual machine on VBox my iso image wasn't there, after freaking out I remembered and rebooted, yes, there was again the file, tried to run this iso but the virtual machine hanged so I decided to copy it to the current SSD to run it from there and this is when the error ocurred. 
I then unmounted my 160Gb HDD and it disapeared from the Media folder. As we speak I unpluged the sata connector from my mobo and reinserted it, copying from HDD to HDD, or HDD to SSD won't generate the error.
I'm quite confused and am pretty sure this error will strike again.

Any help from you guys will be much appreciated.

---

### Post by eric489 on 2011-02-12
I'm also having this error.

I was trying to send a file from my WD external HD to my newly bought pristine INTENSO HD... :(

Any ideas what might cause this ?

---

### Post by caterpillar on 2011-02-23
The file may be corrupted.

To narrow it own to THAT particular file, try copying other files from the source to a different drive on your local machine, or network share or removable medium. 

I have had this problem after I stored a collection of known good files on an ext4 partition. Seems like ext4 has issues with data corruption. I'm sticking with ext3 as I've never had any trouble with it... yet.

As for the corrupted files... well, I'm still looking for ways to repair them.

---

### Post by focaccio on 2011-02-28
I had the same problem when trying to copy a 2.1G vmdk from DVD to the system SATA HDD.  I tried two different exact burn copies of the DVD and the error occurred at the exact same point of data transfer for both: at about 480 meg of transfer.  I think there is definitely a bug/problem.  This occurred on a bare-metal install of x86_64 ubuntu 10.10 running on i7-870/DP55KG that is less than a week old.

My work around was FTP, since the file was on another machine in the same LAN. FTP transferred the file no problem!

---

### Post by hopelessone on 2011-03-05
Same problem...
Im going back to ext3 stuff ext4 i have a 2tb hdd full of movies approx 2gb each and when it was full movies paused and couldn't play any of them anymore.... ran fsck with a bunch of errors...can't move files off the hdd so going to try to compress them and move them and re-format back to ext3...

hope helps

---

### Post by twoboots on 2011-03-13
I get this error when trying to copy a very large batch of files (2.5 Gb )  from an 8G USB 2.0 flashdrive (Kingston Data Traveller) over to a new Ubuntu 10.10 installation. I have worked around this by transferring the files through my Windows XP install and then copying them from the NTFS volume over to the Linux installation. However..I'd really like to avoid this runaround.

---

### Post by nocco on 2011-03-24
Same problem... I have ext4..
it doesn't copy more than 320 MB..
:mad:

---

### Post by digitography on 2011-03-31
I'm getting this error when copying or writing a large file, such as a virtual machine export.

I have experienced this with external USB drives and memory sticks

Running 10.10

---

### Post by DanRichNC on 2011-03-31
I experienced the same error while copying a dvd to an external hd... AFTER I had already done it the day before. First thought was that the disk was dirty, then I thought the drive might be malfunctioning...
Most of the other post relating to this error seemed to point me in that direction, but the disk was clean and the drive is new and reads well.

After I retraced my steps, I (painstakingly) found a solution that works for me.

For some reason the error goes away IF I open the dvd with VLC media player briefly before trying to copy the data.

If I try to copy the files first, I get the error, and have to re-mount the disk.

Not sure why this fix works, but it has on two separate machines using a customized USB boot drive running Lucid.  Hope it works for you.

BTW, I got the error on EXT4, FAT, and EXT3 file systems.

---

### Post by Progreso on 2011-04-13
I am having the same error, copying from an external 150GB to a 1TB backup, on 10.04, the amount of the copied is about 60GB. I repeated the procedure with Krusader, and the error went away. :popcorn:

---

### Post by aMovieMan on 2011-04-14
I suspect I just have a dodgy drive, because I simply copied to my other drive and it was fine.

---

### Post by Orange Kingdom on 2011-04-17
Same here  full of errors while coping a 30mb!  file.

What a big fail! Ubuntu cant copying files to an ext. hd drive.
Well, must go to Windows to perform the operation  (again).


[30999.556802] usb 1-1.1: reset high speed USB device using ehci_hcd and address 23
[31000.027708] sd 27:0:0:0: Device offlined - not ready after error recovery
[31000.027718] sd 27:0:0:0: [sdh] Unhandled error code
[31000.027721] sd 27:0:0:0: [sdh] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK
[31000.027727] sd 27:0:0:0: [sdh] CDB: Read(10): 28 00 74 70 6c a8 00 00 08 00
[31000.027739] end_request: I/O error, dev sdh, sector 1953524904
[31000.027744] Buffer I/O error on device sdh, logical block 244190613
[31000.027803] sd 27:0:0:0: rejecting I/O to offline device
[31000.027876] sd 27:0:0:0: rejecting I/O to offline device
[31000.027894] sd 27:0:0:0: rejecting I/O to offline device
[31000.027934] sd 27:0:0:0: rejecting I/O to offline device
[31000.027949] sd 27:0:0:0: rejecting I/O to offline device
[31000.027978] sd 27:0:0:0: rejecting I/O to offline device
[31000.027996] sd 27:0:0:0: rejecting I/O to offline device
[31000.028019] sd 27:0:0:0: rejecting I/O to offline device
[31000.028036] sd 27:0:0:0: rejecting I/O to offline device
[31000.028054] sd 27:0:0:0: rejecting I/O to offline device
[31000.028071] sd 27:0:0:0: rejecting I/O to offline device

---

### Post by zambizzi on 2011-05-03
I'm getting this, whether I copy to a Fat32 thumb drive or an NTFS-formatted external hard drive - both of which aren't corrupt or problematic in any way, when used with Windows.

It's got to be EXT4 vs "everything else" - which begs the question; would this happen if copying to external EXT4-formatted drives?  I'm guessing...no.

Big, big, sloppy FAIL.  I now can't backup tons of files and am stuck.  Back to Win 7...see ya next year, Ubuntu.

---

### Post by niharthekadi on 2011-05-17
we have an Ubuntu 10.10 disk, it is showing error that either the CD or hard-disk error in my and my friends' computers.

The problem is we can not use md5 checksum as we deleted an iso file from which we created the disk.

but still it shows (while live session):
--------------------------------
ubuntu@ubuntu:~$ cd /cdrom 
ubuntu@ubuntu:/cdrom$ md5sum -c md5sum.txt | grep -vi 'OK$' 
./casper/filesystem.squashfs: FAILED 
md5sum: WARNING: 1 of 66 computed checksums did NOT match 
ubuntu@ubuntu:/cdrom$  
----------------------------------------------------------------------------------------------------
also the nero disk info:
================
Nero CD-DVD Speed: Disc Info 
Basic Information 
 Disc type: : CD-ROM 
 Capacity:  : 78:51.71 
            : 693 MB 
            : 726827008 bytes 
Extended Information 
Tracks      : 1 (0 audio, 1 data) 
Sessions    : 1 
---------------------------------------------------------------------------------------------------
i'm also attaching a surface scan report i hope it can help some one to identify the error
the report shows just two cells (the last two) as bad sectors (that's not even 1%) and others are good. so, is it possible to change just one file or we have to download the whole ISO again.
--------------------------------------------------------------------------------------------------
more over while starting live session it asked only for either try or install,
it does like give option for "check disk for errors" like before

---

### Post by SuperMau on 2011-05-25
Ok, this is annoying! I was getting the same error trying to copy a 700MB video file from a DVD to my hard disk (I got similar errors in Windows XP by the way). I ended up copying the file with ddrescue with excellent results:

```
sudo apt-get install gddrescue
ddrescue /media/dcrom/VoyagerS01E01.avi foo.avi foo.log
```I hope this helps...

Cheers :P

---

### Post by huwjenjinn on 2011-05-29
> **SuperMau said:**
> Ok, this is annoying! I was getting the same error trying to copy a 700MB video file from a DVD to my hard disk (I got similar errors in Windows XP by the way). I ended up copying the file with ddrescue with excellent results:

```
sudo apt-get install gddrescue
ddrescue /media/dcrom/VoyagerS01E01.avi foo.avi foo.log
```I hope this helps...

Cheers :P

Many thanks.

Allowed me to copy a DVD onto the local disk (10.04 with ext4) , with a few errors, then transform to MPG replete with artefacts! But it worked.

Cheers.
 PS Never had this problem before with any DVD so it's an odd problem. Only thing different was it was a DVD created from a Harddisk recorder and I've never copied one of those. All other DVDs were originals.

The DVD played perfectly in both my SONY Blu-ray and SONY DVD players. 

Odd.

---

### Post by felixq78 on 2011-06-28
Error splicing file: Input/output error
I get the same issue occasionally. I just downloaded it again directly onto the Hard Drive where it's to stay.

---

### Post by DawieS on 2011-07-06
Hi guys,
I have seen this error a few times in the last couple of weeks when copying large volumes of large files between disks. In my case it is not exactly repeatable, and a retry of the copy always succeeds. Also, every time at least one external eSata drive was suddenly unmounted and went off-line (powered off by software) in the middle of the copy. I had to flick the power switch off, and back on again to be able to remount the drive. This behaviour cannot be good for the drive, and may cause loss of data and damage to the disk surface.

Now if we want to get to the bottom cause of this behaviour, all of us will have to provide more information, to be able to find common features in a process of elimination. It may even be possible that there may be a bug in the power saving module of Ubuntu, spinning down the drive while (erroneously) thinking it has been idle for long enough.

I therefor recommend that all posters who had this file splicing error while copying, edit their posts, and provide their information under the following headings:

[B]Operating System
Source Drive Type
Source File System
Target Drive Type
Target File System
Approximate Total Copy Size (GB)
Approximate Average File Size (MB)
Approximate Copy Speed (MB/s)
Spin Down Hard Disks When Possible (Power Management Setting)
Error Repeated On Retry?
Additional Remarks[/B]

Please feel free to add additional headings if you feel it may be appropriate.:smile:

---

### Post by DawieS on 2011-07-06
Here is my info:
**Operating System**
Ubuntu 10.04
**Source Drive Type**
External, eSata 2TB Seagate Eco green 5900 rpm
**Source File System**
ext4
**Target Drive Type**
Internal, 1.5 TB Seagate Barracuda 7200 rpm
**Target File System**
ext3
**Approximate Total Copy Size (GB)**
200
**Approximate Average File Size (MB)**
600
**Approximate Copy Speed (MB/s)**
70
**Spin Down Hard Disks When Possible (Power Management Setting)**
Enabled
**Error Repeated On Retry?**
No
**Additional Remarks**
Source drive was off-lined by software during copy. All file-systems checked good after error. Retry copy was successful.

---

### Post by DawieS on 2011-07-13
**Operating System**
Ubuntu 10.04
**Source Drive Type**
External, eSata 1TB Seagate Barracuda 7200 rpm
**Source File System**
ext3
**Target Drive Type**
Internal, old slow 40 GB Seagate Barracuda
**Target File System**
ext4
**Approximate Total Copy Size (GB)**
0.7
**Approximate Average File Size (MB)**
700
**Approximate Copy Speed (MB/s)**
0.1
**Spin Down Hard Disks When Possible (Power Management Setting)**
Disabled
**Error Repeated On Retry?**
Yes
**Additional Remarks**](*,)
I have been hit again by this problem, only different this time. I was watching a video from an eSata drive, when **VLC** got stuck. After a restart, it would play for only about 2 minutes further, and freeze again. After a few repeated restarts, I decided to copy the file to the desktop to check it. The copy would start very slowly, (+- 100 KB/s), and then abort with the "**File Splicing Error** **(Input/Output Error)**" message. I then tried a few other files on the disk, with the same results. Only small fragments of the files would end up on the Desktop.

When checking the 2 partitions on the external disk with **Disk Utility**, it was reported as NOT clean, even the first (spare) Ubuntu partition, which I have not touched since the last check. It then displayed both partitions as "unknown". The log files then showed that the drive was off-lined.

I decided to restart, to see if it will bring the drive back up again. However, a message popped up saying that the **Power Manager** is busy, and gave me the choice to **Cancel**, or **Restart Anyway**. I waited a while, then restarted anyway. The external drive would only come back to life if switched off, and back on (after waiting a bit). The restart was NOT normal, and the top panel would only show up, about half a minute after the boot was completed. When checking with **Disk Utility**, both partitions were clean. However, when trying to copy ANY file from the disk, the same process would be repeated, with errors from File Splicing Error to busy Power Manager and abnormal boot-up.

I have concluded that my Ubuntu installation and/or external disk must have become corrupted for some reason, when at some point I switched off my Epson 915 printer, that suddenly reverted everything back to normal, with no error messages or abnormal boot-ups. All copies from the disk were good and went at full speed.

The Epson printer was the only USB device connected to my PC for the last couple of years, and was always left on, without problems. Now what does a printer have to do with the Power Manager? When looking at the printer, it struck me that it has a SD slot at the front, that used to show up in Win XP as a Mass Storage Device a few years ago (when I was still using XP).

I have only recently installed Swap Partitions, and never had this error before that, but had the Power Manager disabled. This time round, I had the down-spin of disks disabled (enabled with previous events), but the problem still struck again, only more persistent.

I am fairly convinced that the Power Manager is in some way or another responsible for this error. I just cannot make a good estimate at the required conditions to trigger the event.

I will now disable the Power Manager at startup, and see how it runs. If I have no problems in 2 months, the probability that the Power Manager contains the responsible bug will be +95%.

---

### Post by ellaivarios on 2011-07-15
I have the same problem copying a 6GB virtual Box file to an 8GB Flashdrive - it just crashes near the end. This is ridiculous!!!

For the love of God, ever since I switched to Linux all I have done is learn learn learn and learn how to tweak and customize things to get around issues. Can't it just work at least for simple things?

This is why I still have a dual boot with Windows. It copied the file just fine. This is retarded!

---

### Post by quatoria on 2011-07-16
I have the same issue, sadly, since I have this issue on my windows 7 machine (I can't quite get myself away from MS totally.)

[http://social.technet.microsoft.com/Forums/en-US/w7itprohardware/thread/38f25c1d-de67-4c74-8845-2cd3a15d8e41/](http://social.technet.microsoft.com/Forums/en-US/w7itprohardware/thread/38f25c1d-de67-4c74-8845-2cd3a15d8e41/)

And that problem means exactly the same thing on my other machine, I can't copy large files.

I am shocked no one in Ubuntu land thought of this when creating ext4. Very sad day, and together with the other silly changes in 11.04, I am more and more wanting to go back to 9.04.

Operating System - ubuntu 11.04
Source Drive Type - western digital
Source File System - ext4
Target Drive Type - usb flash drive fro mSD
Target File System - fat32
Approximate Total Copy Size (GB) - tried lots but around 4GB needed.
Approximate Average File Size (MB) - mostly mp3's, so 3-5MB
Approximate Copy Speed (MB/s) - I think it reaches about 2MBs via usb before crashing.
Spin Down Hard Disks When Possible (Power Management Setting)
Error Repeated On Retry? - tried on 4 different SD cards many tims in different sized chunks (600MB, couple of gig etc)
Additional Remarks

---

### Post by ellaivarios on 2011-07-16
I apologize for the bitterness I spewed earlier, but I was and still am truly bitter!

The 8GB flash drive was formatted with the NTFS. There's no reason why it wouldn't be able to carry a large file, be it 6GB or 7.9 GB. I ended up transferring the fie over a network - it took ages.

Then I tried again using a second, larger usb stick (10GB), and the problem repeated!

After looking into the matter more carefully, I found that they both contained multiple copies of the trash folder within the trash folder, within the trash folder, within the trash folder, within the trash folder... you get the idea, and would cause the machine to slow down. You could say I had a virus, but nah, I don't buy it. This was a clean install, and I've hardly used the Internet. 

The trash folder  contained files with really weird jarbled up filenames. Every time I  detelete these, they reappeared. and reappeared and reappeared! Even with Shift+Delete. The folder .Trash-1000 contained infinite copies of itself, again and again and again!

I tried:
 	 	rm -rf * 
but to no avail. I tried taking ownership of the folder, I tried removing the read-only permissions, nothing! Sudo this sudo that, still nothing! I was at my wit's end! The trash folder with these weird properties would remain there/reappear even after I formatted the Flash drives!! I formatted the drives, again and again, but it was still acting wonky, same behavior!! 

Meanwhile, transferring the same file on a large 500GB external USB-powered disk, was fine! (I still wanted to try it even though we had transferred the file over a network, just to see what the hell is going on!)

I even formatted one of the USB flash drives and deleted the partition and then left it with unpartitioned space, and LOL when I went into windows, it told me it was formatted FAT32, and empty, and I could put files in it Just fine. I used chkdsk in Windows, and  still it found no problems. I checked it for errors with other programs in both Linux and Windows and IT APPEARED PERFECT! Both Flash drives.

so weird!

So, before throwing the two USB flash drives out,
I used TestDisk on my 8GB flash drive, and found that I had a corrupt partition table. What was happening is that the Volume label (specificaclly the name of the drive I had given it) was different in Windows and different in Ubuntu!!!! In Windows explorer it appeared as JamesUSB (the old name) and in Linux it appeared as James8GB. Renaming the disk or placing information on it in either Operating System would result in neither the label nor the data placed in the disk to be retained in any of the Operating Systems! Each Operating System would "see" whatever changes were made to the drive in its own environment!! I have never seen such erratic behavior before. Mind you I'm not a complete noob. 

TestDisk cleaned the drive, and helped me erase all the information on it. I also went into Windows and formatted the drive in full (Performing a Full Format, not a Quick Format), which took a couple of hours. The first time I formatted the drive, it didn't work!! So I thought the drive was fried! 

Then I did it again, and Voila! It started acting normal again! Volume labels are retained across Operating systems, as well as the data on the stick, and the partition tables are safe and sound and the same in all operating systems. Weirdest thing ever! 

The second USB stick was fixed in the same way.

It got me thinking: First time I formatted the drives I was using an allocation unit of 512Kb, then 2048Kb and finally 4096Kb. Perhaps flash drives only like to be formatted to their default values? Im not sure.

In any case. That's my story. in case it adds any value, or merely entertains.

---

### Post by metrodream on 2011-08-04
i have the same problem. ubuntu 1104 with this input/output error while copying...

it seems there is no solution so far...:(

---

### Post by rpremk24 on 2011-08-11
> **metrodream said:**
> i have the same problem. ubuntu 1104 with this input/output error while copying...

it seems there is no solution so far...:(


Hey ppl out there..its due to missing fragments of that specific file...I got this error wen i downloaded a movie  n tried to move it to my HD..so i just verified my downloaded data with Transmission..i found out dat few fragments were not downloaded..so i just downloaded it n it works fine now..:D There's no need to check all ur configs...Just try to download the file completely...Cheers..!!:P:):lolflag:

---

### Post by jayar323 on 2011-09-02
**Operating System**
ubuntu lucid 10.4
**Source Drive Type **
excelstor 80gb internal hdd
**Source File System**
ext4
**Target Drive Type**
wd elements external 320gb
**Target File System**
ntfs
**Approximate Total Copy Size (GB)**
2.2gb
**Approximate Average File Size (MB)**
182mb
**Approximate Copy Speed (MB/s)**
not sure..maybe 14mb/s
**Spin Down Hard Disks When Possible (Power Management Setting)**
no
**Error Repeated On Retry?**
yes
**Additional Remarks**
problem occured after my external hdd suddenly got unmounted while i was copying to my external drive.

hope ubuntu post or finds a fix on this..:(

---

### Post by imwithid on 2011-09-12
This is the first time I've encountered this problem.

To those who are trying to copy to FAT32 file systems (usually USB drives), [you will not be able to copy files greater than approximately 4 GB]("http://en.wikipedia.org/wiki/File_Allocation_Table#FAT32").

I find it odd as originally, it was a 6.5 GB file that was copied from my local drive to my external eSATA drive. I wanted to copy it back and I cannot do it. It was copied while I ran my external drive's copy of Ubuntu 10.04.3 x86 version. Now using my local version of Ubuntu 10.04.3 x64, I cannot copy from the external drive to my local drive. I'm going to restart and boot into the x86 system and see if it works. Both source and destination partitions are NTFS, however, the external drive's partition was made using FDISK whereas I cannot recall how the local drive was partitioned (probably via GParted). I'm not sure if this makes a significant difference.

Failing that, I'll boot into Windows XP x64 and see if I can use that. Perhaps it is  a file fragmentation problem or the disk requires a file system repair. I doubt that it's a bad sector problem (although I'm not going to discount it) as the hard drive is about a week old.

I'll report back within a couple of hours with the results.

---

### Post by imwithid on 2011-09-12
Update

Both attempts at using Ubuntu failed.
Windows XP x64 returned a CRC failure.

I then tried the standard fix via Windows:```
chkdsk x: /f
```This may take a while. As soon as it is done, I'll try to copy the file again.

Failing a repair, defragment and no physical disk error (I'll check SMART), I will try it on another computer. If the problem remains, it will narrow it down to the hard drive or the enclosure. I'll then try a different enclosure and a direct wiring. I'm going to get to the bottom of this problem.

[Edit]
Although difficult to believe, it was a bad sector. This drive is only a week old, however, these things happen and the threshold for bad sectors is about 120.

Getting to the file transfer, it worked, well and fast via Windows XP x64. I will try via Ubuntu and I predict all will be okay. I should have figured it was a bad sector (only 3.1 GB was transferring instead of the 4 GB threshold of 32-bit addressing).

I don't know if my experience has helped anyone.

---

### Post by DawieS on 2011-09-30
In my case, the problem was caused by the Power Manager, which had some weird interaction with my Epson 915 printer, connected on USB. It seems as if the Power Manager wants to spin down disks, and then run into problems when "spinning down" the SD card slot on the printer. Whenever the machine was left on for a prolonged period (+10 hours), I sometimes had the following symptoms:
- Random freeze/hang-up.
- File Splicing error (Input/Output error) when reading from disks, then mark all partitions as bad, and off-line the disk.
- Some charge build-up on USB ports, causing a hard reset when plugging in a (grounded) external disk.

Three months ago, I removed the Swap partition, and disabled the Power Manager from starting up. The machine is running rock-solid ever since, with none of the above-mentioned symptoms. The only disadvantage is that there is no hibernating ability.

I will now file a bug report, including the log files (pointing to the Power Manager). Since I had several updates since disabling the Power Manager, I will first re-enable it, and check for the re-occurrence of the symptoms, before filing the bug report.

---

### Post by tomkat3 on 2011-10-16
[B]Operating System
[/B]Xubuntu 11.04[B]
Source Drive Type
[/B]Samsung 120gb internal hard drive
[B] Source File System
[/B]ext4
[B] Target Drive Type
[/B]Same as the source, I was copy/pasting from one folder to another
[B] Target File System
[/B]Same as the source, I was copy/pasting from one folder to another
[B] Approximate Total Copy Size (GB)
[/B]0.7MB
[B] Approximate Average File Size (MB)
[/B]0.7MB, one file
[B] Approximate Copy Speed (MB/s)
[/B]24?
[B] Spin Down Hard Disks When Possible (Power Management Setting)
[/B]no
[B] Error Repeated On Retry?
[/B]yep
[B] Additional Remarks
[/B]I'm copying this .avi file from one folder to another. It gets about 5 seconds in and copies 128MB (hence the copy speed) and spits out the splicing file error.

Edit: I should also say that a few weeks ago I accidentally deleted all of my hard drive partitions before screwing around with testdisk long enough to recover everything.

What's the problem? Is there something wrong with the file or my hard drive?

A file is just a bunch of data right? What would ever stop a computer from moving it around?

---

### Post by imwithid on 2011-10-18
> **tomkat3 said:**
> [B]Operating System
[/B]Xubuntu 11.04[B]
Source Drive Type
[/B]Samsung 120gb internal hard drive
[B] Source File System
[/B]ext4
[B] Target Drive Type
[/B]Same as the source, I was copy/pasting from one folder to another
[B] Target File System
[/B]Same as the source, I was copy/pasting from one folder to another
[B] Approximate Total Copy Size (GB)
[/B]0.7MB
[B] Approximate Average File Size (MB)
[/B]0.7MB, one file
[B] Approximate Copy Speed (MB/s)
[/B]24?
[B] Spin Down Hard Disks When Possible (Power Management Setting)
[/B]no
[B] Error Repeated On Retry?
[/B]yep
[B] Additional Remarks
[/B]I'm copying this .avi file from one folder to another. It gets about 5 seconds in and copies 128MB (hence the copy speed) and spits out the splicing file error.

Edit: I should also say that a few weeks ago I accidentally deleted all of my hard drive partitions before screwing around with testdisk long enough to recover everything.

What's the problem? Is there something wrong with the file or my hard drive?

A file is just a bunch of data right? What would ever stop a computer from moving it around?

I would begin with the drive itself. Start with the usual indicators (e.g. Disk Utility or smartmontools (gsmartcontrol if you want the GUI frontend)). If all seems clear (i.e. Reallocated Sector Count or Currently Pending Sector Count are both zero) then it is likely  that your attempts at data recovery were not complete.

---

### Post by donicaben on 2011-10-18
> **B-Con said:**
> Well, I think I fixed the problem, sort of. That same external drive I was copying to was having problems in Windows as well. Opening the files or listing the directories on the drive in Windows caused Windows Explorer to hang, sometimes indefinitely.

I had two identical external hard drive enclosures, so I took the drive out of the first and put it in the second one. It seemed like all my problems disappeared. Windows was able to read from the drive perfectly and I was able to copy data to it with no splicing errors under Linux.

So, it looks like my problem was fixed by changing hard drive enclosures, implying that it was the enclosure that was the problem. However, considering that so many other people report a similar problem makes me skeptical. All I can say is that it worked fine under my limited tests, I'll report anything else of interest if I find it.

Thank you!  I bought an external off of Craigslist that had a dent in the case.  It was only $10, so no super big loss, but loosening case worked.  Thanks!  :-)

---

### Post by Andreawws on 2011-12-14
Ok... this thread isn't that old and it hasn't helped me... yet. (So thus I shall post!)
[B]Operating System
[/B]ubuntu 11.04[B]
Source Drive Type
[/B]CD
[B] Source File System
[/B]CD...
[B] Target Drive Type
[/B]80 hdd.... no memory whatsoever what the brand is and I don't feel like checking **been a long day**
[B] Target File System
[/B]ext4
[B] Approximate Total Copy Size (GB)
[/B]Less than one (1) GB
[B] Approximate Average File Size (MB)
[/B]~900mb (two files)
[B] Approximate Copy Speed (MB/s)
[/B]less than ~1MB/s 
[B] Spin Down Hard Disks When Possible (Power Management Setting)
[/B]no
[B] Error Repeated On Retry?
[/B]yep (tried 5 times... well actually 6... (though the sixth time was just for collecting data,,,, write speed and similar) :/ )
** Additional Remarks**

Additional Remarks. The CD gives a similar error in windows. (something about the checksum.... CRC [something] circular redundancy check or something like that,.....)

But when checking in Ubuntu the checksum is reported to be correct. (And as a fact, The Discs are supposed to work. :/ 
**They do work on my friends computer, I was there when he tested them!**)

Errors:

Error splicing file: Input/output error <---copying file from the cd(s).


tar: star wars cd1/RZR-KTR1.BIN: File shrank by 262566064 bytes; padding with zeros
tar: star wars cd1/rzr-ktr.nfo: Read error at byte 0, while reading 5300 bytes: Input/output error
tar: Exiting with failure status due to previous errors

^
||
||
when compressing said CD(s)

let's see.... that should be about it :D


EDIT:
Forgot some significant data!
The file system I am copying to is @ 45GB, the HDD has 2 damaged sectors and there is 10GB of free space on the file system.

that should be all :D

---

### Post by dirtyhabanero on 2011-12-15
Well I thought that this error was just an issue with my external HDD, but now I've also been getting this issue when trying to copy files to the 32GB microSD on my Samsung GS2 phone. Here are the specs for the phone issue:[B]

Operating System
[/B]Ubuntu 11.10[B]
Source Drive Type
[/B]Computer HDD
[B] Source File System
[/B]NTFS (for dual boot system)
[B]Target Drive Type
[/B]32GB microSD card in phone - works, borrowing from my housemate 8-)
[B] Target File System
[/B]Fat32 (Can't change this...)
[B] Approximate Total Copy Size (GB)
[/B]4.3GB
[B] Approximate Average File Size (MB)
[/B]5MB (songs)
[B] Approximate Copy Speed (MB/s)
[/B]less than 2.4MB/s (but I'm certain it's been faster)
[B] Spin Down Hard Disks When Possible (Power Management Setting)
[/B]No
[B] Error Repeated On Retry?
[/B]Yes :( - even when using nautilus with sudo. 
[B] Additional Remarks

[/B]Gets about half way through and then gives the error. At first I thought that it didn't want to copy RHCP tracks, but that can't be it :lolflag:. 

dmesg | tail straight after the first error gave this:
```
$ dmesg | tail
[49933.401790] cdc_acm 2-3:1.1: ttyACM0: USB ACM device
[49933.524105] usb 2-3: reset high speed USB device number 15 using ehci_hcd
[49933.658033] cdc_acm 2-3:1.1: This device cannot do calls on its own. It is not a modem.
[49933.658175] cdc_acm 2-3:1.1: ttyACM0: USB ACM device
[49933.660879] VFS: busy inodes on changed media or resized disk sdd
[49933.661888] sd 22:0:0:0: [sdd] 24133632 512-byte logical blocks: (12.3 GB/11.5 GiB)
[49934.816153] sd 22:0:0:1: rejecting I/O to offline device
[49934.816180] FAT-fs (sde): unable to read inode block for updating (i_pos 60951126)
[49934.816203] sd 22:0:0:1: rejecting I/O to offline device
[49934.816212] FAT-fs (sde): unable to read inode block for updating (i_pos 60951184)
```And after I pressed "Skip All", I get another error, dmesg tail as follows:
```
$ dmesg | tail
[49967.225100] sd 22:0:0:1: rejecting I/O to offline device
[49967.225107] FAT-fs (sde): Directory bread(block 3809454) failed
[49967.225115] sd 22:0:0:1: rejecting I/O to offline device
[49967.225122] FAT-fs (sde): Directory bread(block 3809455) failed
[49967.225130] sd 22:0:0:1: rejecting I/O to offline device
[49967.225136] FAT-fs (sde): Directory bread(block 3809456) failed
[49967.225145] sd 22:0:0:1: rejecting I/O to offline device
[49967.225151] FAT-fs (sde): Directory bread(block 3809457) failed
[49967.225201] sd 22:0:0:1: rejecting I/O to offline device
[49967.225208] FAT-fs (sde): FAT read failed (blocknr 534)
```Orange Kingdom appears to have posted something similar, hopefully I don't get binned for dbl posting. Will keep at it.

---

### Post by image28 on 2012-01-08
I recently installed ubuntu on a new computer on the 24th of December, worked great for a few days, but recently I get the splicing input/output error when copying to any of 3 usb hard-drives, and one 16gb usb key. Occasionally one file will copy, but most will not. The 3 hard-drives (usb 2.0 ) are plugged into a usb 3.0/2.0 combination hub, and I plug the usb key into a different usb 2.0 hub, but have tried switching the plugs around without any luck.

---

### Post by Whatzit on 2012-02-18
> **SuperMau said:**
> Ok, this is annoying! I was getting the same error trying to copy a 700MB video file from a DVD to my hard disk (I got similar errors in Windows XP by the way). I ended up copying the file with ddrescue with excellent results:

```
sudo apt-get install gddrescue
ddrescue /media/dcrom/VoyagerS01E01.avi foo.avi foo.log
```I hope this helps...

Cheers :P

Thank you for this! You're the man!

My hdd had bad sectors and ddrescue is exactly what I needed to recover those files that would not copy over.

---

### Post by Marran77 on 2012-03-01
This problem made me almost rip my hair out. I could not copy files from my ext4 internal harddrive to my new Xtreamer Sidewinder 2 with an internal 320 gb harddrive. I tried to format the Sidewinder-harddrive several times from Ubuntu using disktool and Gparted (to ntfs, fat and ext3) and always got some kind of error. Then I read here in the forum that some people got rid of the problem using either an USB-hub or plugging the external harddrive in the back of the computer. I tried the latest first, and now, as I'm typing this, I'm transfering 150 gb of movies to my Sidewinder-harddrive:D I'm so lucky:D:D:D:D:D

So, if you haven't tried it yet, plug the USB-harddrive in the back of the computer first!

---

### Post by oleander on 2012-03-05
Hi, everyone, I think I have a solution!

I just had this problem on Xubuntu 11.10 running from a Live CD while trying to transfer files from an EXT3 partition to a FAT32 partition to back them up. I've actually had this problem before (while not using a Live CD) and it's ridiculously annoying and limiting!

What I had tried first was to drag & drop the files using Thunar. I then tried the Ctrl+c, Ctrl+v copying and pasting using Thunar. When both gave me issues, I tried using Alt+F2 and then ran "gksu thunar" and repeated the same actions, thinking that it was a problem of privileges. No such luck -- if you're reading this, you may have tried these things too (whether with Thunar or some other file manager).

After all that long waiting and disappointment, I tried the command-line program 'dd' and it worked -- I verified the results by running 'md5sum' on both files and problem solved! :D 

Here's what I did, step-by-step:

1. Open the terminal. (if you don't know how or aren't sure what it is, see here: [https://help.ubuntu.com/community/UsingTheTerminal]("https://help.ubuntu.com/community/UsingTheTerminal"))

2. Navigate to the location of the document you'd like to copy/transfer by using the 'cd' and 'ls' commands. (again, if you haven't the faintest idea what I'm talking about, see the above link and this one: [http://afrodita.rcub.bg.ac.rs/~ivica/nlm/part1/cd_ls.html]("http://afrodita.rcub.bg.ac.rs/~ivica/nlm/part1/cd_ls.html"))

3. Use the 'dd' command to make a copy of the file in the desired directory. Here's an example:

Say I'm in some directory and want to copy Xubuntu.iso to /media/Backup, this is what I'd do:
```
dd if=Xubuntu.iso of=/media/Backup/Xubuntu.iso
```

As always, if you're confused about how to run a program, type in "man programName" into the terminal and hit [Enter] to see a bit of an explanation -- aka the "man pages" or manual. In this case, if you're confused about 'dd' you could type in 'man dd' and hit [Enter] for more info. 

***I'd also suggest using 'md5sum' to check that the file is correct and wasn't incorrectly copied before deleting the original -- which you'll have to do since 'dd' makes copies, it's not like cutting and pasting (it doesn't delete the original or move it). Here's some info on 'md5sum' to get you started: [http://linux.about.com/library/cmd/blcmdl1_md5sum.htm]("http://linux.about.com/library/cmd/blcmdl1_md5sum.htm")

Though this problem really shouldn't exist (the whole error splicing file issue), using 'dd' should at least help everyone to transfer their files while this problem is hopefully being solved by the developers. :)

Hope this helps everyone!
~Oleander

**Edit:** Just to add, I had trouble after posting this with moving a file with 'dd' which was 4GB+. According to this thread: [http://forums.fedoraforum.org/showthread.php?t=206928]("http://forums.fedoraforum.org/showthread.php?t=206928"), files of a certain size are not permitted in certain file systems. After compressing the file I wanted to move with 'dd' it did work. I imagine you can also split a file into several archives if you'd prefer to work it that way. In either case, the archive can be later compressed by a file system that allows larger file sizes.

---

### Post by CarolDenny on 2012-03-05
hey there and thank you for your information – I’ve definitely picked up something new from right here. I did however expertise several technical issues using this website, as I experienced to reload the website a lot of times previous to I could get it to load properly. I had been wondering if your web host is OK? Not that I am complaining, but sluggish loading instances times will often affect your placement in google and can damage your quality score if ads and marketing with Adwords. Anyway I’m adding this RSS to my email and could look out for a lot more of your respective interesting content. Make sure you update this again very soon.

---

### Post by oleander on 2012-03-05
In response to both CarolDenny and henrydoown:

**(Quite Technical Approach)**
I personally haven't had any problems using this forum today at all. If you have problems accessing a website, it can be any number of things. Normally, the first thing I do when I have a problem accessing one or more websites is flush my DNS resolver cache. This cache stores information about web pages on your computer and if incorrect/incomplete information is stored, it can bring up error pages and create other issues for you alone even if others in the same household (but on a different computer) experience no issues. This website talks about the DNS resolver cache and installing/using it on Ubuntu: [http://embraceubuntu.com/2006/08/02/local-dns-cache-for-faster-browsing/]("http://embraceubuntu.com/2006/08/02/local-dns-cache-for-faster-browsing/")

**(Not-So-Technical Approach)**
Another thing to do (and I know this sounds ridiculous) is just delete cookies/data from your computer and restart your browser. Sometimes programs get buggy and have issues of their own going on. You can do this in Firefox by going to [Tools]>[Clear Recent History] choose [Clear Everything] in the dropdown menu and then click [Clear Now]. This will cause problems if you save login information but this is what I'd personally do myself if encountering a problem with loading websites. 

**(Moderately Technical Approach)**
A more technical approach is to use 'ping'. You'd go to the terminal and enter something like: 
```
ping -c 10 ubuntuforums.org
```
It will spit out something like this:
```

PING ubuntuforums.org (91.189.94.12) 56(84) bytes of data.
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_req=1 ttl=49 time=92.2 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_req=2 ttl=49 time=97.8 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_req=3 ttl=49 time=93.1 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_req=4 ttl=49 time=93.8 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_req=5 ttl=49 time=93.2 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_req=6 ttl=49 time=94.9 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_req=7 ttl=49 time=94.1 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_req=8 ttl=49 time=93.6 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_req=9 ttl=49 time=94.1 ms
64 bytes from feijoa.canonical.com (91.189.94.12): icmp_req=10 ttl=49 time=93.8 ms

--- ubuntuforums.org ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 9012ms
rtt min/avg/max/mdev = 92.214/94.099/97.877/1.470 ms

```

Since it says "0% packet loss" you at least know your computer can communicate with the server at ubuntuforums.org.

Then there's the customer support methods which will require you to reboot everything...restart various electronics like your computer and router, unplug and plug in everything. If all else fails, I usually resort to what I like to call the "caveman method" -- smack it. Yes...smack it. Sometimes this actually works (no, I'm not kidding)...I just make sure to do it in a way that doesn't require me to buy any new electronic equipment (if anyone else tries this, I'd suggest they do the same and be violent in a *gentle* way...oh, and do so **at your own risk** <insert long, generic disclaimer here>).

I hope the problem clears up soon! :)
~Oleander

---

### Post by Sand3r on 2012-03-19
Just a very late reply to AgentY on page 1, he solved my problem regarding the Error splicing file: Input/output error. His solution when copying large files to a disk was to create a directory without spaces on the external hard drive.

For some reason, that works for me! Thanks!

I'm repeating that here after almost 1,5 years, because someone __might still be helped with this solution ;)

---

### Post by VaZia on 2012-07-04
Hi. I am trying to copy large file 5.9 GB to the FLASH drive sized 8 GB and get same error. "File to large"

---

### Post by steeldriver on 2012-07-04
> **VaZia said:**
> Hi. I am trying to copy large file 5.9 GB to the FLASH drive sized 8 GB and get same error. "File to large"

What filesystem is on the flash drive? if it is FAT32 then the maximum individual file size is 4GB

[http://en.wikipedia.org/wiki/File_Allocation_Table#FAT32](http://en.wikipedia.org/wiki/File_Allocation_Table#FAT32)

BTW you should probably have started your own thread for this instead of bumping an old one which may not have anything to do with your issue

---

### Post by mikevikki on 2012-07-31
I had this issue and fixed it as follows (please note data on the drive will be lost):-

1. Start your PC
2. Plug in the external USA or other external drive.
3. Goto Linux disk utility
4. Locate the relevant USB normally near the bottom on the left.
5. Make sure the drive is not mounted. If it is press the unmouth button
6. Press the format button just above the big bar that represents the drive.
7. From the drop down select "dont partition" and press ok.
8. When 7 is done press the format button below the big bar representing the drive.
9. Select NTFS and press format.
10. Remount the drive by pressing the Mount Button.

Note FAT formats will only support files upto 4Gig

NTFS is best as external drives can then be read by either Linux or windows. For me EXT4 on USB drives never seems to work as it creates the Lost+Found on the external drive. I think (i dont know) that linux thinks your external drive is internal.

Hope this helps let me know.

---

### Post by knowledgeispower on 2012-08-04
Fixed for me.... 

Hi Friends, 


I found something new, even i use to get the same error while copying files from my hard disk to the external hard-disk.

I have observed the CPU utilization while performing the copy, which was going upto 100%, that is not because of this copy, it is because of the other application running on my PC. 

so, I closed other application and brought my PC to low utilization, then copied... 

it is successful.  :)

---

### Post by mayankraipure on 2012-08-19
I got the same problem after 4 gb copied i got splicing file: iinput/output : file to large 

possible solution could be changing the file system of pendrive from fat32 to NTFS then try to copy .

---

### Post by Sambol on 2013-02-04
This is my first time posting, so woo hoo! :D

Anyways,

I consistently ran into an input/output error when trying to cp/mv/dd anything (regardless of size or format) off of my external hard drive after upgrading to 12.04 LTS. The drive mounted, and I had no trouble accessing the directories and viewing their contents. I tried several of the fixes proposed on this forum, to no avail. I then plugged the drive into a Windows 7 computer, which displayed similar behaviour.

In desperation, I stumbled into the Ubuntu Disk Utility and clicked on «Check Filesystem», which solved the problem in 30s. Now I can cp/mv files back and forth from my external without any error.

 Hope it helps!

---

### Post by isa.dsouza on 2013-02-18
both partitions ext 4 formatted and ntfs formatted display this error. No back up of Ripped DVD now. Any answers?

---

### Post by mcneelymj on 2014-01-05
I ran into this problem while copying a large file from one external drive to another. I worked around it by copying the file onto my internal drive first and then copying that file to the second external drive. I'm not sure what exactly was causing the problem, but I suspect it was a hardware/firmware issue since I am able to copy large files between the same external hard drives using a different computer running the same version of Ubuntu (12.04).

---

### Post by zackery2 on 2014-05-21
I've had the same issue with different versions with Linux as well

---

### Post by syntaxerror74 on 2014-06-07
Any yet another one with the same problem.

HOWEVER...I noticed that the problem will minimize by using console and not PCManFM. It might even be a bug in one (or several) file managers, which apparently do something questionable in accessing the file(s) from time to time.

I had this problem a dozen times when copying stuff from NTFS to ext4 with a certain ST drive. Although it might be that this drive has at least a knack (albeit a neglectable one), there were never any kinds of these errors (Error splicing file: Read-only file system) when copying on console.
And that PCManFM respectively libmanfm is buggy in many ways, is an open secret.

> **Sambol said:**
> In desperation, I stumbled into the Ubuntu Disk Utility and clicked on «Check Filesystem», which solved the  problem in 30s. Now I can cp/mv files back and forth from my external  without any error.
Heh - that almost sounds like voodoo magic.
Since even though I don't know about this utility's inner workings, I would bet my life on it that "Check Filesystem" is nothing but a frontend, simply performing a **fsck** under the hood.

---

### Post by peter-ludwig on 2015-04-11
> **syntaxerror74 said:**
> 
Since even though I don't know about this utility's inner workings, I would bet my life on it that "Check Filesystem" is nothing but a frontend, simply performing a **fsck** under the hood.


This little fsck / chkdsk util is your friend. Solving *almost* all Problems concerning "Error 5" messages.

I analysed the problem a wee bit more. Here my results:

a) the problem can occur having a CD / DVD with scratches or fingerprints on it
b) the problem can occur by trying to copy files which are already corrupt due to a damaged media underneath. (This can be a usb stick, micro sd-card or similar)
c) the problem can occur due to a corrup filesystem.
d) the problem can occur due to forbidden characters in the filename => ":" ">" "/" "\" and others.

Test: The problem occurs on other operating systems as well

Symptoms/Reasons: 

1) The filename is corrupt. (the name is composed of funny characters) (Bad Sign)
2) The file type icon has changed. Songs do not any more have a "song-typical" icon but a for example text icon. (Bad Sign)
3) The file-size has changed. (much smaller than the oiginal one) (Source = Bad Sign / target = keep on copying)
4) The file size is 0 (Source = Bad Sign / target = keep on copying)
5) The cd / DVD is scratched (cleaning)
6) The SD Card / USB Stick is damaged (fell down, became too hot, washing mashine ... ) (repair??? / bin)

Workarounds:

1) Try to keep on copying the file over an over again. If you check the filesize while copying I noticed that sometimes the copying goes on and finishes in the end. (after the 10th try) But this does *not* mean that the file is healthy. Chances are 50:50. But chances not too bad if the type icon is still correct. 

=> there is a good tool that might jump in handy: "unstoppable file copier"
[http://www.roadkil.net/program.php/P29/Unstoppable%20Copier](http://www.roadkil.net/program.php/P29/Unstoppable%20Copier)

2) Try cleaning the cd with dishwashing liquid and a clean soft cotton wool towel.

3) Rename the file. (without special characters)

4) Copy the files one by one. Sounds funny but this seemed to work sometimes better than copying complete folders.


Good Luck!

---

### Post by oldos2er on 2015-04-11
Old thread closed.

---

