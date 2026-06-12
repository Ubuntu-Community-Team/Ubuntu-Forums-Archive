---
title: "One more user with &quot;CAN'T BURN CDs&quot; problem...."
date: 2010-02-03
forum: General Help
---

### Post by jl2035 on 2010-02-03
I guess many bugs have been reported about this issue, and also I'm not the first who is talking about this on forums. I just can't burn CD using any tool. First the Brasero error log: [http://pastebin.com/f3f9f1e34](http://pastebin.com/f3f9f1e34)

Than I tried to use K3B who saved my *** once before(on some other machine). But this time I got this error:
```
Unable to mount Blank Optical Disc
DBus error org.gtk.Private.RemoteVolumeMonitor.NotFound: The given volume was not found
```

After asking on Ubuntu IRC Chat channel I installed GnomeBaker. This tool doesn't report any error it just destroys the CD. I mean it says that burning process is finished but: if I put it in the other machine I actualy see files I tried to burn but I can't access them. If I try to copy something it says "The parameter is incorrect."

If I try to burn from the terminal, I get GUI dialog saying the same msg as K3B. The terminal output is here:
[http://pastebin.com/f3aedf9ac](http://pastebin.com/f3aedf9ac)

Please help me - I really need to burn a CD from time to time...

---

### Post by Sarnix on 2010-02-07
I have the same problem. I just installed a new dvd-burner and I tried to burn an iso using Nero.
```
Linux (Ubuntu 9.10 'karmic') 2.6.31-19-generic (x86_64)
Nero API version: 9.7.0.132
Using interface version: 9.0.1.4
Installed in: /usr/lib64/nero/
Application: Nero AG\Nero Linux
Internal Version: 9, 7, 0, 132

Recorder:             <HL-DT-ST DVDRAM GH22NS40>Version: NL02 - HA 3 TA 0 - 0.0.0.0
 Adapter driver:      <ahci>                    HA 3
 Drive buffer  :      2048kB
 Bus Type      :      via Inquiry data
Excluded drive IDs: 
WriteBufferSize: 83886080 (0) Byte
BUFE           : 0
Physical memory     : 3962MB (4058040kB)
Free physical memory: 2191MB (2244304kB)
Memory in use       : 44 %
Uncached PFiles: 0x0
Global Bus Type: default (0)
Check supported media : Disabled (0) 

7.2.2010
NeroAPI
01:34:03 PM	#1 Text 0 File DlgWaitCD.cpp, Line 294
	Medium type in the drive: CD-RW High Speed
	Lowest/Highest CLV write speed:         4x/10x
	Recorder min/max supported write speed: 10x/10x
	
01:34:03 PM	#2 Text 0 File DlgWaitCD.cpp, Line 313
	Last possible write address on media:   359846
	Last address to be written:                634
	
01:34:03 PM	#3 Text 0 File DlgWaitCD.cpp, Line 325
	Write in overburning mode: NO
	
01:34:03 PM	#4 Text 0 File DlgWaitCD.cpp, Line 2856
	Recorder: HL-DT-ST DVDRAM GH22NS40;
	   CDRW code: 00 97 22 60; OSJ entry from: Daxon Technology, Inc.
	   ATIP Data:
	     Special    Info [hex] 1: B3 00 CE, 2: 61 16 3C (LI 97:22.60), 3: 4F 3B 4A (LO 79:59.74)
	     Additional Info [hex] 1: 24 1A D8, 2: 26 B2 4A, 3: 00 00 00 (invalid)
	
01:34:03 PM	#5 Text 0 File DlgWaitCD.cpp, Line 500
	>>> Protocol of DlgWaitCD activities: <<<
	=========================================
	This disc is not empty.
		(Medium in drive: CD-RW. Medium required by compilation: CD-R/RW.)
	Accessing disc...
		(Medium in drive: CD-RW. Medium required by compilation: CD-R/RW.)
	
01:34:03 PM	#6 Text 0 File ThreadedTransferInterface.cpp, Line 734
	Setup items (after recorder preparation)
	 0: TRM_DATA_MODE1 ()
	    2 indices, index0 (150) not provided
	    original disc pos #0 + 635 (635) = #635/0:8.35
	    relocatable, disc pos for caching/writing not required/ required
	    -> TRM_DATA_MODE1, 2048, config 0, wanted index0 0 blocks, length 635 blocks [HL-DT-ST DVDRAM GH22NS40 (H:3 T:0)]
	--------------------------------------------------------------
	
01:34:03 PM	#7 Text 0 File ThreadedTransferInterface.cpp, Line 936
	Prepare [HL-DT-ST DVDRAM GH22NS40 (H:3 T:0)] for write in CUE-sheet-DAO
	DAO infos:
	==========
	 MCN: ""
	 TOCType: 0x00; Session Closed, disc not fixated
	 Tracks 1 to 1:                                  Idx 0         Idx 1      Next Trk
	   1: TRM_DATA_MODE1, 2048/0x00, FilePos             0        307200       1607680, ISRC ""
	DAO layout:
	===========
	 ___Start_|____Track_|_Idx_|_CtrlAdr_|_____Size_|______NWA_|_RecDep__________
	     -150 |  lead-in |   0 |    0x41 |        0 |        0 | 0x00
	     -150 |        1 |   0 |    0x41 |        0 |        0 | 0x00
	        0 |        1 |   1 |    0x41 |      635 |        0 | 0x00
	      635 | lead-out |   1 |    0x41 |        0 |        0 | 0x00
	
01:34:03 PM	#8 Text 0 File Burncd.cpp, Line 4354
	Caching options: cache CDRom or Network-No, small files-Yes (<32KB)
	
01:34:03 PM	#9 Phase 24 File ExtendedProgress.cpp, Line 537
	Caching of files started
	
01:34:03 PM	#10 Text 0 File Burncd.cpp, Line 4476
	Cache writing successful.
	
01:34:03 PM	#11 Phase 25 File ExtendedProgress.cpp, Line 537
	Caching of files completed
	
01:34:03 PM	#12 Phase 36 File ExtendedProgress.cpp, Line 537
	Burn process started at 10x (1500 KB/s)
	
01:34:03 PM	#13 Text 0 File ThreadedTransferInterface.cpp, Line 2690
	Verifying disc position of item 0 (relocatable, disc pos, no patch infos, orig at #0): write at #0
	
01:34:03 PM	#14 Text 0 File MMC.cpp, Line 17580
	StartDAO : CD-Text - Off
	
01:34:03 PM	#15 Text 0 File MMC.cpp, Line 21804
	Set BUFE: Buffer underrun protection -> ON 
	
01:34:03 PM	#16 Text 0 File MMC.cpp, Line 17808
	CueData, Len=32
	41 00 00 14 00 00 00 00 
	41 01 00 10 00 00 00 00 
	41 01 01 10 00 00 02 00 
	41 aa 01 14 00 00 0a 23 
	
01:34:03 PM	#17 Text 0 File ThreadedTransfer.cpp, Line 273
	Pipe memory size 83836800
	
01:34:20 PM	#18 Text 0 File Cdrdrv.cpp, Line 1273
	13:34:20 - HL-DT-ST DVDRAM GH22NS40 (H:3 T:0) : Queue again later
	
01:34:39 PM	#19 SCSI -1064 File SCSIInterface.cpp, Line 624
	SCSI Exec, HA 3, TA 0, LUN 0, buffer 0x0x7f3f7b09f2c0
	Status:     0x04 (0x01, SCSI_ERR)
	HA-Status   0x00 (0x00, OK)
	TA-Status   0x05 (0x0B, SCSI_TASTATUS_FAILED)
	Sense Key:  0x05 (KEY_ILLEGAL_REQUEST)
	Sense Code: 0x21
	Sense Qual: 0x02
	CDB Data:   0x2A 0x00 0x00 0x00 0x01 0x40 0x00 0x00 0x20 0x00 0x00 0x00 
	Sense Data: 0x70 0x00 0x05 0x00 0x00 0x00 0x00 0x0A 
	            0x2A 0x30 0x07 0x90 0x21 0x02 
	
01:34:39 PM	#20 CDR -1064 File Writer.cpp, Line 306
	Invalid block address
	HL-DT-ST DVDRAM GH22NS40 (H:3 T:0)
	
01:34:39 PM	#21 Text 0 File DVDPlusDualLayer.cpp, Line 1455
	SetDriveCaps: Set LAST LBA of layer 1 to 0
	
01:34:39 PM	#22 Phase 38 File ExtendedProgress.cpp, Line 537
	Burn process failed at 10x (1500 KB/s)
	
```

---

### Post by Kopachris on 2010-02-07
Ditto.  Brand new system (Athlon II X4, 4GB RAM, LG super-multi drive...).  Trying to burn an Ubuntu x64 disk to dual-boot with and an Ubuntu x86 Server disk for my other computer.  I get the exact same log file from Brasero.

---

### Post by jl2035 on 2010-02-07
I think I started this thread in the wrong category. There are to many of them in the 'General help', and it's kinda' lost...

I guess you two also have 9.10 installed?

---

### Post by Sarnix on 2010-02-08
Yes, 9.10 and almost the same configuration as Kopachris.

I did a complete reinstall, because things were so messed up. At first I tried to install Windows 7, which failed. Bad copy or something. Then installed ubuntu, then added the dvd-burner.
Now I did it in the right sequence. The dvd-burner inside, then install windows, then install ubuntu and i just burned a pdf-file to a cd-rw, which succeeded and was a problem before. Haven't tried burning an iso though.

---

### Post by sleepee on 2010-02-09
hey, just wondering if anybody's found a solution to this problem... without having to reinstall of course.

i'm also having problems burning...well, pretty much anything, with pretty much any program (brasero, k3b, etc).  i don't feel like starting a new thread to possibly the same problem, so i thought i'd ask first...

---

### Post by jl2035 on 2010-02-15
I really want to solve this too...but I'm afraid nobody sees this thread anymore. I wanted to report a bug... but I think you have to be in a Bug Squad for this.

---

### Post by bkline on 2010-03-03
> **jl2035 said:**
> I really want to solve this too...but I'm afraid nobody sees this thread anymore. I wanted to report a bug... but I think you have to be in a Bug Squad for this.

I've been having the same problem since installing karmic.  You don't need to be in any special group to report bugs.  Just navigate to [https://bugs.launchpad.net/ubuntu/]("https://bugs.launchpad.net/ubuntu/") and register.  Unfortunately, the most common response by the Ubuntu team to bug reports is to ignore them.  Then 6 months or a year later you'll get an automated message telling you there hasn't been any activity on this issue for a long time (as if you didn't already know) and asking you to let them know if the problem has gone away so they can close the bug.  Sometimes you get lucky, though, so by all means go ahead and file a report.

---

### Post by bkline on 2010-03-03
Looks like the bug (which is apparently in the kernel) has been filed already, assuming it's the same one reported in this thread.  See [https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/405544]("https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/405544").  Lots of activity in the issue up until the end of January, after which it goes dead (without a fix).

---

### Post by deadlockedgamer on 2010-03-03
Did you try double clicking the iso? I have had this issue burning iso files unless I do it this way! As far as other files go just because your cd says 700mb does not mean it is actually 700mb. make sure your file is a couple megabytes smaller. Ubuntu Iso would fit of course. I have always found burning in Ubuntu easier. I have a friend who bought a new laptop with vista and had the same problem. Try inserting a different burner and see if it works (eliminate hardware defect!). Don't know what to say just giving it a shot!

---

### Post by Kopachris on 2010-03-04
Did some more testing, I can't burn data CDs either.  I tried installing and using K3b, but that didn't help.  K3b kept giving me a buffer underrun error--though I turned up the software buffer as high as I thought I could and tried burning at a much slower speed.  The drive is supposed to go up to 48x speed for burning CDs.
> Did you try double clicking the iso? I have had this issue burning iso files unless I do it this way! As far as other files go just because your cd says 700mb does not mean it is actually 700mb. make sure your file is a couple megabytes smaller. Ubuntu Iso would fit of course. I have always found burning in Ubuntu easier. I have a friend who bought a new laptop with vista and had the same problem. Try inserting a different burner and see if it works (eliminate hardware defect!). Don't know what to say just giving it a shot!Yes, I tried double clicking the iso.  I also made sure the stuff to write was smaller than the disk by several megabytes at least (it's an Ubuntu iso, I don't think they'd make an iso they thought people couldn't write).  No, I can't insert a different burner.  This is my only SATA burner, and the only IDE port on my mobo is being used by two harddrives (one for root (two partitions: one 64-bit, other 32-bit), one for /home).

---

### Post by jl2035 on 2010-03-04
I repored a new bug: [https://bugs.launchpad.net/ubuntu/+source/cdrtools/+bug/531901](https://bugs.launchpad.net/ubuntu/+source/cdrtools/+bug/531901)

---

### Post by NewDisciple on 2010-03-04
Same problem, but I fixed it with additional plugins.  Can't tell you what they were as it has been some time since this occurred.  Just check synaptic for them is all I can tell you.

---

### Post by jl2035 on 2010-03-16
I'm not saying "the problem is solved", but I successfully burned an iso image. I added -raw96r option to cdrecord. Burning from Brasero or other tool still doesn't work. 

Check out the bug thred: [https://bugs.launchpad.net/ubuntu/+source/cdrtools/+bug/531901](https://bugs.launchpad.net/ubuntu/+source/cdrtools/+bug/531901)

---

### Post by bkline on 2010-05-01
I seems that lucid has come very close to solving this problem (for me, at least).  I can now burn backup DVDs without having to move the tar files to an older Ubuntu system which wasn't plagued by the burning bugs.  Only remaining problem is that Brasero complains that it can't eject the DVD when the burning is done (see attached screenshot).  The user is told to eject the DVD by hand.  This instruction is given in a modal dialog window whose only button says "Cancel" (which seems bizarre since I don't want to cancel the burn, which has completed anyway).  Compared to the inability of karmic to burn backup DVDs at all, I can live with this residual silliness.

---

### Post by jl2035 on 2010-08-04
I have the exact same issue in Lucid... but I can live whit that.

---

### Post by bkline on 2010-08-04
Funny thing is, it no longer happens all the time.  Just most of the time, though sometimes it figures out how to eject the burned disc itself.

---

### Post by digitography on 2010-08-07
If this can't be solved can anyone suggest another cd burning package?

I use Infrarecord in W! and that works fine, if Ubuntu think the masses are going to swithch to this OS with bugs like this that are not being resolved they really are living in cloud cuckoo land.

I don't have the time to mess around with this I need it to work.
Bit of a rant there, so I'll get mi coat :D

---

