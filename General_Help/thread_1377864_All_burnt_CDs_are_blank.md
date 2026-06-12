---
title: "All burnt CDs are blank"
date: 2010-01-10
forum: General Help
---

### Post by darkwish_ on 2010-01-10
After i burn CD with Imgburn, Gnomebaker or brasero all disc are bkank.
If it can help, log from imgburn, there are some errors:
```

I 01:41:21 ImgBurn Version 2.5.0.0 started!
I 01:41:21 Microsoft Windows XP Professional (5.1, Build 2600 : Service Pack 3)
I 01:41:21 Total Physical Memory: 3,096,648 KB  -  Available: 1,613,644 KB
I 01:41:21 Initialising SPTI...
I 01:41:21 Searching for SCSI / ATAPI devices...
I 01:41:24 Found 1 DVD±RW/RAM!
I 01:42:10 Operation Started!
I 01:42:10 Building Image Tree...
I 01:42:30 Checking Directory Depth...
I 01:42:30 Calculating Totals...
I 01:42:30 Preparing Image...
I 01:42:31 Checking Path Length...
I 01:42:31 Contents: 4 Files, 0 Folders
I 01:42:31 Content Type: Data
I 01:42:31 Data Type: MODE1/2048
I 01:42:31 File System(s): ISO9660, UDF (1.02)
I 01:42:31 Volume Label: Desktop
I 01:42:31 Size: 232,806 bytes
I 01:42:31 Sectors: 116
I 01:42:31 Image Size: 1,245,184 bytes
I 01:42:31 Image Sectors: 608
I 01:42:36 Operation Successfully Completed! - Duration: 00:00:25
I 01:42:36 Operation Started!
I 01:42:36 Source File: -==/\/[BUILD IMAGE]\/\==-
I 01:42:36 Source File Sectors: 608 (MODE1/2048)
I 01:42:36 Source File Size: 1,245,184 bytes
I 01:42:36 Source File Volume Identifier: Desktop
I 01:42:36 Source File Application Identifier: IMGBURN V2.5.0.0 - THE ULTIMATE IMAGE BURNER!
I 01:42:36 Source File Implementation Identifier: ImgBurn
I 01:42:36 Source File File System(s): ISO9660, UDF (1.02)
I 01:42:36 Destination Device: [2:0:0] TSSTcorp CDDVDW TS-L632H AS02 (E:)
I 01:42:36 Destination Media Type: CD-R (Disc ID: 97m27s18f, Plasmon Data Systems) (Speeds: 10x, 16x, 20x, 24x)
I 01:42:36 Destination Media Sectors: 359,847
I 01:42:36 Write Mode: CD
I 01:42:36 Write Type: SAO
I 01:42:36 Write Speed: MAX
I 01:42:37 Lock Volume: Yes
I 01:42:37 Test Mode: No
I 01:42:37 OPC: No
I 01:42:37 BURN-Proof: Enabled
W 01:42:37 DeviceIoControl(IOCTL_STORAGE_MCN_CONTROL) Failed! - Media change notification has NOT been disabled.
I 01:42:39 Filling Buffer... (40 MB)
I 01:42:39 Writing LeadIn...
I 01:43:01 Writing Session 1 of 1... (1 Track, LBA: 0 - 607)
I 01:43:01 Writing Track 1 of 1... (MODE1/2048, LBA: 0 - 607)
I 01:43:02 Synchronising Cache...
I 01:43:31 Exporting Graph Data...
I 01:43:31 Graph Data File: C:\users\mengzk\Application Data\ImgBurn\Graph Data Files\TSSTcorp_CDDVDW_TS-L632H_AS02_MONDAY-JANUARY-11-2010_1-42_AM_97m27s18f_MAX.ibg
I 01:43:31 Export Successfully Completed!
I 01:43:32 Operation Successfully Completed! - Duration: 00:00:55
I 01:43:32 Average Write Rate: N/A - Maximum Write Rate: N/A
I 01:43:32 Cycling Tray before Verify...
I 01:44:02 Device Ready!
I 01:44:02 Operation Started!
I 01:44:02 Source Device: [2:0:0] TSSTcorp CDDVDW TS-L632H AS02 (E:)
I 01:44:02 Source Media Type: CD-R (Disc ID: 97m27s18f) (Speeds: 10x, 16x, 20x, 24x)
I 01:44:02 Image File: -==/\/[BUILD IMAGE]\/\==-
I 01:44:02 Image File Sectors: 608 (MODE1/2048)
I 01:44:02 Image File Size: 1,245,184 bytes
I 01:44:02 Image File Volume Identifier: Desktop
I 01:44:02 Image File Application Identifier: IMGBURN V2.5.0.0 - THE ULTIMATE IMAGE BURNER!
I 01:44:02 Image File Implementation Identifier: ImgBurn
I 01:44:02 Image File File System(s): ISO9660, UDF (1.02)
I 01:44:02 Read Speed (Data/Audio): MAX / MAX
E 01:44:02 Session 1, Track 1 is smaller on the disc than it is in the image file.
E 01:44:03 Disc's Track Sectors: 0 (TOC Sectors: 0)
E 01:44:03 Image File's Track Sectors: 608 (TOC Sectors: 608)
E 01:44:03 Operation Failed! - Duration: 00:00:00
I 01:44:03 Average Verify Rate: N/A - Maximum Verify Rate: N/A
```

---

### Post by ankspo71 on 2010-01-10
Hi, me too.
Is that a log file from using imgburn in XP pro, or from running imgburn in wine?
How old is your cd burning drive?

I have a similar problem with burning in Ubuntu 9.10 (off and on) and in 10.04 (test release). I've tried xfburn, brasero, gnomebaker, and k3b, no luck. I have this problem with 2 different internal dvd burners (both still young in age, Samsung and Adaptec), but the dvd burners work well in XP-Pro/MCE and Ubuntu 9.04 and earlier. Since then I came across a cheap deal for an external USB dvd burner and it works. I know this is not a solution, but it's what I'm doing now to burn cd/dvds.

Sorry I can't be of much help.

---

### Post by darkwish_ on 2010-01-11
hi, this log from imgburn in wine. in vista home premium it works well and also can blank discs in ubuntu 9.10, but not write =/
i am using notebook Asus M51SE: [http://www.asus.com/product.aspx?P_ID=XJ9Cvqsb6mwKnqYp](http://www.asus.com/product.aspx?P_ID=XJ9Cvqsb6mwKnqYp)

---

### Post by garvinrick4 on 2010-01-11
Should be no reason why you cannot take a .iso file of Ubuntu around 692 to 698 meg and
BURN a Live CD. I notice you are working at 24 times speed, Why not try 8x or so to get a nice
clean burn. Make sure the .iso file when in properties is right Megs. 
Try it one more time nice and slow and check to make sure things are looking right.

---

### Post by Sef on 2010-01-11
If it is speed, then 4x or less is best.

---

### Post by darkwish_ on 2010-01-11
thanks, i put speed to 4x and it burn well:
```
I 10:56:37 Average Write Rate: 5,208 KB/s (3.8x) - Maximum Write Rate: 5,671 KB/s (4.1x)
I 10:56:37 Cycling Tray before Verify...
W 10:56:52 Waiting for device to become ready...
I 10:57:19 Device Ready!
I 10:57:22 Operation Started!
I 10:57:22 Source Device: [2:0:0] TSSTcorp CDDVDW TS-L632H AS02 (E:)
I 10:57:22 Source Media Type: DVD-R (Book Type: DVD-R) (Disc ID: RITEKG05) (Speeds: 3x, 4x, 6x, 8x)
I 10:57:22 Image File: -==/\/[BUILD IMAGE]\/\==-
I 10:57:22 Image File Sectors: 1,523,632 (MODE1/2048)
I 10:57:22 Image File Size: 3,120,398,336 bytes
I 10:57:22 Image File Volume Identifier: Apocalyptica
...
...
I 11:04:34 Export Successfully Completed!
I 11:04:34 Operation Successfully Completed! - Duration: 00:07:12
I 11:04:34 Average Verify Rate: 7,053 KB/s (5.1x) - Maximum Verify Rate: 10,048 KB/s (7.3x)

```
i checked disc, all files were written.

---

### Post by llawwehttam on 2010-01-11
> **Sef said:**
> If it is speed, then 4x or less is best.

I agree with this. I never burn a live cd above 4X.

---

### Post by linuxcss on 2010-01-11
speed does not always fix the problem,
this has been frustrating ... just in the last 2 days (Jan 2010), 
I had thought to have burnt a few dvd+rw only to reinsert them
and find them blank ... I attempted to burn these with gnomebaker under
karmic

---

### Post by ankspo71 on 2010-01-11
To linuxcss,
If you have tried a few burning application already, all I can suggest is to dual boot with another linux distro that can burn... like what I was doing before I picked up a usb drive. In my case, Ubuntu 9.04 or CrunchBang 9.04 was what I needed to dual boot with.

Here's my original thread. Maybe something someone said in that thread can be useful to you.
[**I was able to burn CD's in Karmic RC, but not in KK final**]("http://ubuntuforums.org/showthread.php?t=1305501")

---

### Post by garvinrick4 on 2010-01-11
It is not the .iso you are getting from Ubuntu that is bad! Look for user error or a bad piece of hardware or software. Figure it out, why let something as simple as BURNING a Live CD beat you.

---

### Post by ankspo71 on 2010-01-11
Hi, 
Do you mean me?   ;-)
I agree, most of the time hardware problems can be traced back to errors or user errors, or even burn speed. On the other hand... there are no errors in my case. My bad burns were reported as successful burns, even launching the burning apps by terminal reported no errors. The problem has to be with my particular motherboard, or the drivers the latest Ubuntu(s) or Linux kernel ships with I'm afraid. The motherboard is a Biostar p4900-m4. The drives tested are two completely different DVD-RAM drives that still work like new in different OSes and distributions. The only thing I didn't try was buy higher quality cables (if quality matters). Instead of that I bought a Lite-On EZ-Dub and now I have something to burn with (and it's also portable and it says dual-layer capable, so that kind of makes up for the tiny loss that I had to invest). Like I said though, I agree with what you said about giving up too soon. ;-)

---

