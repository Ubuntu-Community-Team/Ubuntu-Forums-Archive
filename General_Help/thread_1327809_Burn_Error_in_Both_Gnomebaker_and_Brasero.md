---
title: "Burn Error in Both Gnomebaker and Brasero"
date: 2009-11-15
forum: General Help
---

### Post by somking95 on 2009-11-15
I have a clean install of 9.10. Sata DVD Burner. I can not burn a data dvd. I have tried both Brasero and Gnome Baker. Any help would be greatly appreciated.

*Brasero Error Message*
> BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr: /dev/sr0: "Current Write Speed" is 16.4x1352KBps.
BraseroGrowisofs stderr: :-[ WRITE@LBA=f0h failed with SK=5h/INVALID ADDRESS FOR WRITE]: Invalid argument
BraseroGrowisofs stderr: :-( write failed: Invalid argument
BraseroGrowisofs stderr: /dev/sr0: flushing cache
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr: /dev/sr0: updating RMA
BraseroGrowisofs stderr: /dev/sr0: closing disc
BraseroGrowisofs stderr: HUP
BraseroGrowisofs stdout: HUP
BraseroGrowisofs process finished with status 22
BraseroGrowisofs called brasero_job_error
BraseroGrowisofs finished with an error
BraseroGrowisofs asked to stop because of an error
rror		= 0
	message	= "no message"
BraseroGrowisofs stopping
BraseroGrowisofs got killed
Session error : unknown (brasero_burn_record brasero-burn.c:2811)

*Gnomebaker Output*
> Executing 'genisoimage -gui -V ufc-105 -A GnomeBaker -p MyUname -iso-level 3 -l -r -hide-rr-moved -J -joliet-long -graft-points --path-list /tmp/GnomeBaker-MyUname/gnomebaker-ACYT3U | builtin_dd of=/dev/sr0 obs=32k seek=0'
I: -input-charset not specified, using utf-8 (detected in locale settings)
/dev/sr0: "Current Write Speed" is 8.2x1352KBps.
:-[ WRITE@LBA=f0h failed with SK=5h/INVALID ADDRESS FOR WRITE]: Invalid argument
:-( write failed: Invalid argument
/dev/sr0: flushing cache
/dev/sr0: updating RMA
/dev/sr0: closing session

*Gnome Baker Pop Up Message*
> DBus error org.gtk.Private.RemoteVolumeMonitor.NotFound: The given volume was not found

The common denominator seems to be:
> :-[ WRITE@LBA=f0h failed with SK=5h/INVALID ADDRESS FOR WRITE]: Invalid argument

??????

---

### Post by Sin@Sin-Sacrifice on 2009-11-15
From what I've read it looks like either the disk is bad or the drive may be bad. I also say another post about changing the block size from 512 bytes to 256 bytes but that page was for writing HUGE files to a tape drive in Unix. I would say try another disk... if you get the same error perhaps check other kinds of mediums and in other OSs. In this you can see if it is the medium, the drive, or the software. Once you have it cornered you may be able to find more information.

---

### Post by somking95 on 2009-11-15
I have tired some other dvd's from the same box but still have problems. I will get some new ones and try them. I noticed on one of the failed dvds, the file is burnt on the dvd but its just not completed. The burn process seems to fail at the end.

I can burn cd's no problem.

---

### Post by Sin@Sin-Sacrifice on 2009-11-15
This guy solved it but I don't think this is a good answer. [http://ubuntuforums.org/archive/index.php/t-1253058](http://ubuntuforums.org/archive/index.php/t-1253058)

As it were... I guess this is tied to this [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/130200](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/130200) bug and will not be fixed. I guess it's the difference between how those programs understand base 10 and base 2 math. Is the disk a 4.7 GB?

---

### Post by somking95 on 2009-11-15
> **Sin@Sin-Sacrifice said:**
> This guy solved it but I don't think this is a good answer. [http://ubuntuforums.org/archive/index.php/t-1253058](http://ubuntuforums.org/archive/index.php/t-1253058)

As it were... I guess this is tied to this [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/130200](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/130200) bug and will not be fixed. I guess it's the difference between how those programs understand base 10 and base 2 math. Is the disk a 4.7 GB?

Yeah, its a 4.7 disk. Should I try a different size?

I did not understand how creating a 20 gig swap partition helped him and I really don't want to have to run a windows program to burn dvd's.

I wonder why I am having the problems but not everyone else does.

---

### Post by Sin@Sin-Sacrifice on 2009-11-15
That's what I took from the sites and posts I read. I don't entirely understand it myself. I get bits and pieces... I'm going to try and burn something on a 4.7 DVD-RW I have here. Let you know what happens.

---

### Post by Sin@Sin-Sacrifice on 2009-11-16
Well... I can burn with no problems at all. I just burnt my backup of a Stargate DVD 4.02 GB to a RW and it works as well as the original DVD. I did find this though. [http://ubuntuforums.org/showthread.php?t=369198](http://ubuntuforums.org/showthread.php?t=369198) Let me know if you need help with making aliases.

---

### Post by missmoondog on 2009-11-16
use k3b for burning, it works correctly. 
just don't forget to grab the extracodecs package along with it, when installing through synaptic.

brasero stinks!!

---

### Post by somking95 on 2009-11-22
> **Sin@Sin-Sacrifice said:**
> Well... I can burn with no problems at all. I just burnt my backup of a Stargate DVD 4.02 GB to a RW and it works as well as the original DVD. I did find this though. [http://ubuntuforums.org/showthread.php?t=369198](http://ubuntuforums.org/showthread.php?t=369198) Let me know if you need help with making aliases.

thanks for the help
I am going to buy some more blanks and try one first and if the problem still occurs then I am going to start trying some of the suggestions.

---

### Post by phatcartoon on 2009-11-22
This isn't exactly what you are talking about, but I was having a problem with Brasero.  No matter what I tried burning, it would always hang at..  "preparing to write"  I looked for solutions and found none.  I also tried Gnome CD master and that wouldn't even find my CD drive.   The closest thing I could find to a solution was to install "K3B".   That seemed to do the job.  Everything burns just fine now.  I wish you luck.


My results. . .

Brasero=fail
Gnome CD master=fail
K3b=  :)

---

### Post by somking95 on 2009-11-22
K3b = Success!

I have always loved K3b but I wanted to try and use all Gnome apps. After hearing so many suggestions for K3b and I used it and it worked.

---

### Post by mattman on 2009-11-22
I've had trouble with Brasero ever since upgrading to Karmic. Switched to k3b and it works fine.

---

### Post by lifmnt on 2009-11-23
I have the same error here
**"DBus error org.gtk.Private.RemoteVolumeMonitor.NotFound: The given volume was not found**"

It happens when I try to burn a dvd image (.iso).
I tried to use brasero, gnomebaker and now k3b.

I already ruined 2 blank dvds, and now the 3rd one is stuck on the drive, the led is flashing, and I've already got the error message. (used k3b this time)

What is wrong? how to fix this problem, since k3b doesn't work either?

I'm using ubuntu 9.10, clean install

---

### Post by paultrafalgar on 2009-12-06
First post on this forum so gently!
I have endlessly wrecked DVDs with gnomebaker. Being a fully paid up card carrying paranoid, I believe it to be Digital  Rights Nazism. However, the point is: I have a workaround. It's tedious but seems to do the trick. When you want to burn an iso with gnomebaker first shut your machine down, take out the power lead and remove the battery for 10 seconds. (Yes, you heard). Reinstall the battery and connect the power lead (I'm using a  laptop here - Asus Eee). Put the blank disc in the drive, plug the drive in (USB lead) and connect it to the laptop. All this before you boot up. As you boot up the drive is searched in case it is a bootable cd. Run gnomebaker, select the iso you want to burn and proceed to burn.
I am not sure why this works but what I suspect is that the fact that the drive is mounted to search for bootableness when rebooting means that is "registered" whereas if you don't register it, it is somehow marked as unmountable.
By the way, you will need to do this rebooting BETWEEN EVERY INSTANCE OF BURNING which makes it a real pain if you are making several copies.
I hope this works for you.

---

### Post by zasq on 2009-12-10
Hi! 
I also ruined several DVDs trying to burn data on them with brasero. DVD+RW and CD worked fine, but burning on DVD-RW resulted in a "burn error" just a second before finishing the job. I could even see the files in the file manager but not open them.
Then, I tried to burn the data on the DVD-RW out of nautilus file manager and - it worked! Even though nautilus uses brasero to do this. Strange thing, but it helps at least for Data-DVD.
Anyway, I hope someone will find a better solution for this bug...

---

### Post by Ron_ on 2009-12-17
Because misery loves company... add me to the list of folks who have trashed media trying both Brasero and GnomeBaker on Ubuntu 9.10.  I have a new low-end HP desktop with [SIZE=-1][FONT=Helvetica, Arial, sans-serif]a 16x DVD-/+RW drive, and I am using DVD-R media. I am just trying to burn 1 large (4GB) file to a data DVD.  I have tried 16x and 4x.  The message I get  from both apps is: 

:-[ WRITE@LBA=e0h failed with SK=5h/INVALID ADDRESS FOR WRITE]: Invalid argument
:-[ write failed: Invalid argument



[/FONT][/SIZE]

---

### Post by xerman on 2009-12-18
Hello there,

I've been having weird issues with Brasero, Gnomebaker and the Nautilus Burn thing. The point is that I by any means can burn a DVD, and CDs I can burn some if the size of the contents is small.

If size of contents is around 20 MB, 50 MB, it seems ok, if the size of contents extends 100 MB then have problems burning:

```
BraseroWodim stdout: Track 01:    0 of  197 MB written.
BraseroGenisoimage stderr:   4.94% done, estimate finish Fri Dec 18 18:23:12 2009
BraseroWodim stdout: Track 01:    1 of  197 MB written (fifo  99%) [buf  99%]  21.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    2 of  197 MB written (fifo 100%) [buf  99%]  21.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    3 of  197 MB written (fifo 100%) [buf  99%]  22.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    4 of  197 MB written (fifo 100%) [buf  99%]  21.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stderr: Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: CDB:  2A 00 00 00 0A E6 00 00 1F 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: status: 0x2 (CHECK CONDITION)
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Bytes: 70 00 04 00 00 00 00 0A E8 C7 1A 80 08 03 00 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Key: 0x4 Hardware Error, Segment 0
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Code: 0x08 Qual 0x03 (logical unit communication crc error (ultra-dma/32)) Fru 0x0
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense flags: Blk 0 (not valid) 
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: cmd finished after 0.020s timeout 200s
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: A write error occured.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: Please properly read the error message above.
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Track 01:    5 of  197 MB written (fifo  99%) [buf 100%]  22.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: write track data: error after 5713920 bytes
BraseroWodim stdout: Writing  time:   23.168s
BraseroWodim stdout: Average write speed  58.4x.
BraseroWodim stdout: Min drive buffer fill was 99%
BraseroWodim stdout: Fixating...
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Fixating time:    5.534s
BraseroWodim stderr: wodim: fifo had 234 puts and 91 gets.
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: HUP
BraseroWodim stderr: wodim: fifo was 0 times empty and 79 times full, min fill was 95%.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: HUP
BraseroWodim process finished with status 254
BraseroWodim called brasero_job_error
BraseroWodim finished with an error
BraseroWodim asked to stop because of an error
	error		= 0
	message	= "no message"
BraseroGenisoimage stopping
BraseroGenisoimage got killed
BraseroGenisoimage disconnecting BraseroGenisoimage from BraseroWodim
BraseroWodim stopping
BraseroWodim got killed
BraseroWodim closing connection for BraseroWodim
Session error : unknown (brasero_burn_record burn.c:2602)
```

The thing is weird, because some CD's Burn and some don't, but DVD, none... 

K3B also can not burn CD. Even more weird....

When I try to simulate first the recording Any program, K3B, Brasero, Xfburn, can reach to record 9 MB, while when not simulating, just reached 5 MB. Lowering burning speed does nothing. No good...

Even More, on the Desktop there is still the Icon that the Blank CD-R is mounted when there is no CD in the Writer. If I eject that cd, the cd tray opens with no cd in. Then I close the CD tray, but the Cd is still mounted and with those 5 MB of info recorded in there.

Thanks a lot and hope this will also help.
Best regards....

Xermán

---

### Post by AkiraBergman on 2009-12-20
I also wasted quite a few CDs and DVDs with Brasero in Ubuntu 9.10 AMD64. K3B works fine.

---

### Post by jamesobooth on 2009-12-26
I'm seriously considering going back to Windows just cause of this.  I haven't been able to successfully burn a CD or DVD since going to Linux.  I've tried Ubuntu 9.04, 9.10, and Mint 8.  I know it's not hardware cause Winders burns just fine.  Suck!

Here's a log if it helps anyone else at all:
```

Checking session consistency (brasero_burn_check_session_consistency brasero-burn.c:1848) 
BraseroBurnURI called brasero_job_get_action 
BraseroBurnURI called brasero_job_get_action 
BraseroBurnURI called brasero_job_set_output_size_for_current_track 
BraseroBurnURI stopping 
BraseroBurnURI called brasero_job_get_action 
BraseroBurnURI called brasero_job_get_session_output_size 
BraseroBurnURI output set (IMAGE) image = /tmp/brasero_tmp_1GP34U.bin toc = none 
BraseroBurnURI called brasero_job_get_action 
BraseroBurnURI called brasero_job_get_current_track 
BraseroBurnURI no burn:// URI found 
BraseroBurnURI stopping 
BraseroLocalTrack called brasero_job_get_action 
BraseroLocalTrack called brasero_job_get_action 
BraseroLocalTrack called brasero_job_set_output_size_for_current_track 
BraseroLocalTrack stopping 
BraseroLocalTrack called brasero_job_get_action 
BraseroLocalTrack called brasero_job_get_session_output_size 
BraseroLocalTrack output set (IMAGE) image = /tmp/brasero_tmp_3WP34U.bin toc = none 
BraseroLocalTrack called brasero_job_get_action 
BraseroLocalTrack called brasero_job_get_current_track 
BraseroLocalTrack no remote URIs 
BraseroLocalTrack stopping 
BraseroChecksumImage called brasero_job_get_current_track 
BraseroChecksumImage called brasero_job_get_action 
BraseroChecksumImage called brasero_job_get_flags 
BraseroChecksumImage called brasero_job_get_action 
BraseroChecksumImage called brasero_job_get_action 
BraseroChecksumImage called brasero_job_get_fd_in 
BraseroChecksumImage called brasero_job_set_output_size_for_current_track 
BraseroChecksumImage stopping 
BraseroChecksumImage called brasero_job_get_current_track 
BraseroChecksumImage called brasero_job_get_action 
BraseroChecksumImage There is a checksum already 0 
BraseroWodim called brasero_job_get_action 
BraseroWodim getting varg 
BraseroWodim called brasero_job_get_action 
BraseroWodim got varg: 
BraseroWodim deactivating 
BraseroWodim called brasero_job_get_action 
BraseroWodim getting varg 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_get_device 
BraseroWodim called brasero_job_get_flags 
BraseroWodim called brasero_job_get_speed 
BraseroWodim called brasero_job_get_flags 
BraseroWodim called brasero_job_get_input_type 
BraseroWodim called brasero_job_get_fd_in 
BraseroWodim called brasero_job_get_current_track 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim got varg: 
	wodim 
	-v 
	dev=/dev/sr0 
	speed=4 
	driveropts=burnfree 
	fs=16m 
	-data 
	-nopad 
	/home/james/Downloads/LinuxMint-8.iso 
BraseroWodim Launching command 
BraseroWodim called brasero_job_get_fd_out 
BraseroWodim stderr: wodim: No write mode specified. 
BraseroWodim called brasero_job_get_flags 
BraseroWodim stderr: wodim: Asuming -tao mode. 
BraseroWodim called brasero_job_get_flags 
BraseroWodim stderr: wodim: Future versions of wodim may have different drive dependent defaults. 
BraseroWodim called brasero_job_get_flags 
BraseroWodim stderr: wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.scsidev: '/dev/sr0' 
BraseroWodim called brasero_job_get_flags 
BraseroWodim stderr: devname: '/dev/sr0' 
BraseroWodim called brasero_job_get_flags 
BraseroWodim stderr: scsibus: -2 target: -2 lun: -2 
BraseroWodim called brasero_job_get_flags 
BraseroWodim stderr: Linux sg driver version: 3.5.27 
BraseroWodim called brasero_job_get_flags 
BraseroWodim stderr: Wodim version: 1.1.9 
BraseroWodim called brasero_job_get_flags 
BraseroWodim stderr: SCSI buffer size: 64512 
BraseroWodim called brasero_job_get_flags 
BraseroWodim stderr: Beginning DMA speed test. Set CDR_NODMATEST environment variable if device 
BraseroWodim called brasero_job_get_flags 
BraseroWodim stderr: communication breaks or freezes immediately after that. 
BraseroWodim called brasero_job_get_flags 
BraseroWodim stdout: TOC Type: 1 = CD-ROM 
BraseroWodim stdout: Driveropts: 'burnfree' 
BraseroWodim stdout: Device type    : Removable CD-ROM 
BraseroWodim stdout: Version        : 5 
BraseroWodim stdout: Response Format: 2 
BraseroWodim stdout: Capabilities   : 
BraseroWodim stdout: Vendor_info    : 'MATSHITA' 
BraseroWodim stdout: Identification : 'DVD-RAM UJ-862  ' 
BraseroWodim stdout: Revision       : 'RB01' 
BraseroWodim stdout: Device seems to be: Generic mmc2 DVD-R/DVD-RW. 
BraseroWodim stdout: Current: 0x000A (CD-RW) 
BraseroWodim stdout: Profile: 0x0012 (DVD-RAM) 
BraseroWodim stdout: Profile: 0x002B (DVD+R/DL) 
BraseroWodim stdout: Profile: 0x001B (DVD+R) 
BraseroWodim stdout: Profile: 0x001A (DVD+RW) 
BraseroWodim stdout: Profile: 0x0016 (DVD-R/DL layer jump recording) 
BraseroWodim stdout: Profile: 0x0015 (DVD-R/DL sequential recording) 
BraseroWodim stdout: Profile: 0x0013 (DVD-RW restricted overwrite) 
BraseroWodim stdout: Profile: 0x0014 (DVD-RW sequential recording) 
BraseroWodim stdout: Profile: 0x0011 (DVD-R sequential recording) 
BraseroWodim stdout: Profile: 0x0010 (DVD-ROM) 
BraseroWodim stdout: Profile: 0x000A (CD-RW) (current) 
BraseroWodim stdout: Profile: 0x0009 (CD-R) 
BraseroWodim stdout: Profile: 0x0008 (CD-ROM) 
BraseroWodim stdout: Profile: 0x0002 (Removable disk) 
BraseroWodim stdout: Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr). 
BraseroWodim stdout: Driver flags   : MMC-3 SWABAUDIO BURNFREE 
BraseroWodim stdout: Supported modes: TAO PACKET SAO 
BraseroWodim stdout: Drive buf size : 1310720 = 1280 KB 
BraseroWodim stdout: FIFO size      : 16777216 = 16384 KB 
BraseroWodim stderr: Speed set to 706 KB/s 
BraseroWodim called brasero_job_get_flags 
BraseroWodim stdout: Track 01: data   688 MB        
BraseroWodim stdout: Total size:      790 MB (78:17.77) = 352333 sectors 
BraseroWodim stdout: Lout start:      790 MB (78:19/58) = 352333 sectors 
BraseroWodim stdout: Current Secsize: 2048 
BraseroWodim stdout: ATIP info from disk: 
BraseroWodim stdout:   Indicated writing power: 6 
BraseroWodim stdout:   Reference speed: 2 
BraseroWodim stdout:   Is not unrestricted 
BraseroWodim stdout:   Is erasable 
BraseroWodim stdout:   ATIP start of lead in:  -11078 (97:34/22) 
BraseroWodim stdout:   ATIP start of lead out: 359849 (79:59/74) 
BraseroWodim stdout:   1T speed low:  0 (reserved val  0) 1T speed high:  4 
BraseroWodim stdout:   2T speed low:  0 (reserved val  5) 2T speed high:  0 (reserved val 12) 
BraseroWodim stdout:   power mult factor: 3 5 
BraseroWodim stdout:   recommended erase/write power: 3 
BraseroWodim stdout:   A1 values: 02 3A B0 
BraseroWodim stdout:   A2 values: 5C C6 26 
BraseroWodim stdout: Disk type:    Phase change 
BraseroWodim stdout: Manuf. index: 11 
BraseroWodim stdout: Manufacturer: Mitsubishi Chemical Corporation 
BraseroWodim stdout: Blocks total: 359849 Blocks current: 359849 Blocks remaining: 7516 
BraseroWodim stdout: Starting to write CD/DVD at speed   4.0 in real TAO mode for single session. 
BraseroWodim stdout: Last chance to quit, starting real write in    4 seconds.# 
BraseroWodim called brasero_job_set_dangerous 
BraseroWodim stdout: # 
BraseroWodim stdout: # 
BraseroWodim stdout: # 
BraseroWodim stdout: # 
BraseroWodim stdout: # 
BraseroWodim stdout: # 
BraseroWodim stdout: # 
BraseroWodim stdout: # 
BraseroWodim stdout: # 
BraseroWodim stdout: # 
BraseroWodim stdout: # 
BraseroWodim stdout: # 
BraseroWodim stdout:    3 seconds.# 
BraseroWodim stdout: # 
BraseroWodim stdout: # 
BraseroWodim stdout: # 
BraseroWodim stdout: # 
BraseroWodim stdout: # 
BraseroWodim stdout: # 
BraseroWodim stdout: # 
BraseroWodim stdout: # 
BraseroWodim stdout: # 
BraseroWodim stdout: # 
BraseroWodim stdout: # 
BraseroWodim stdout: # 
BraseroWodim stdout:    2 seconds.# 
BraseroWodim stdout: # 
BraseroWodim stdout: # 
BraseroWodim stdout: # 
BraseroWodim stdout: # 
BraseroWodim stdout: # 
BraseroWodim stdout: # 
BraseroWodim stdout: # 
BraseroWodim stdout: # 
BraseroWodim stdout: # 
BraseroWodim stdout: # 
BraseroWodim stdout: # 
BraseroWodim stdout: # 
BraseroWodim stdout:    1 seconds.#############   0 seconds. Operation starts. 
BraseroWodim stdout: Waiting for reader process to fill input buffer ... input buffer ready. 
BraseroWodim stdout: Performing OPC... 
BraseroWodim stdout: Starting new track at sector: 0 
BraseroWodim stdout: 
BraseroWodim stdout: Track 01:    0 of  688 MB written. 
BraseroWodim stdout: Track 01:    1 of  688 MB written (fifo 100%) [buf  99%]   6.4x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:    2 of  688 MB written (fifo 100%) [buf 100%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:    3 of  688 MB written (fifo 100%) [buf 100%]   4.3x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:    4 of  688 MB written (fifo 100%) [buf  99%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:    5 of  688 MB written (fifo 100%) [buf  99%]   4.3x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:    6 of  688 MB written (fifo 100%) [buf 100%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:    7 of  688 MB written (fifo 100%) [buf 100%]   4.3x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:    8 of  688 MB written (fifo 100%) [buf  99%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:    9 of  688 MB written (fifo 100%) [buf  99%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:   10 of  688 MB written (fifo 100%) [buf 100%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:   11 of  688 MB written (fifo 100%) [buf 100%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:   12 of  688 MB written (fifo 100%) [buf  99%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:   13 of  688 MB written (fifo 100%) [buf  99%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:   14 of  688 MB written (fifo 100%) [buf 100%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:   15 of  688 MB written (fifo 100%) [buf 100%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:   16 of  688 MB written (fifo 100%) [buf  99%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:   17 of  688 MB written (fifo 100%) [buf  99%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:   18 of  688 MB written (fifo 100%) [buf 100%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:   19 of  688 MB written (fifo 100%) [buf 100%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:   20 of  688 MB written (fifo 100%) [buf  99%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:   21 of  688 MB written (fifo 100%) [buf  99%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:   22 of  688 MB written (fifo 100%) [buf 100%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:   23 of  688 MB written (fifo 100%) [buf 100%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:   24 of  688 MB written (fifo 100%) [buf  99%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:   25 of  688 MB written (fifo 100%) [buf  99%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:   26 of  688 MB written (fifo 100%) [buf 100%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:   27 of  688 MB written (fifo 100%) [buf 100%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:   28 of  688 MB written (fifo 100%) [buf  99%]   4.0x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:   29 of  688 MB written (fifo 100%) [buf  99%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:   30 of  688 MB written (fifo 100%) [buf 100%]   4.0x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:   31 of  688 MB written (fifo 100%) [buf 100%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:   32 of  688 MB written (fifo 100%) [buf  99%]   4.0x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:   33 of  688 MB written (fifo 100%) [buf 100%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:   34 of  688 MB written (fifo 100%) [buf 100%]   4.3x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:   35 of  688 MB written (fifo 100%) [buf  99%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:   36 of  688 MB written (fifo 100%) [buf  99%]   4.3x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:   37 of  688 MB written (fifo 100%) [buf 100%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:   38 of  688 MB written (fifo 100%) [buf 100%]   4.3x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:   39 of  688 MB written (fifo 100%) [buf  99%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:   40 of  688 MB written (fifo 100%) [buf  99%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:   41 of  688 MB written (fifo 100%) [buf 100%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:   42 of  688 MB written (fifo 100%) [buf 100%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:   43 of  688 MB written (fifo 100%) [buf  99%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:   44 of  688 MB written (fifo 100%) [buf  99%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:   45 of  688 MB written (fifo 100%) [buf 100%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:   46 of  688 MB written (fifo 100%) [buf 100%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:   47 of  688 MB written (fifo 100%) [buf  99%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:   48 of  688 MB written (fifo 100%) [buf  99%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:   49 of  688 MB written (fifo 100%) [buf 100%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:   50 of  688 MB written (fifo 100%) [buf 100%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:   51 of  688 MB written (fifo 100%) [buf  99%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:   52 of  688 MB written (fifo 100%) [buf  99%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:   53 of  688 MB written (fifo 100%) [buf 100%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:   54 of  688 MB written (fifo 100%) [buf 100%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:   55 of  688 MB written (fifo 100%) [buf  99%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:   56 of  688 MB written (fifo 100%) [buf  99%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:   57 of  688 MB written (fifo 100%) [buf 100%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:   58 of  688 MB written (fifo 100%) [buf 100%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:   59 of  688 MB written (fifo 100%) [buf  99%]   4.0x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:   60 of  688 MB written (fifo 100%) [buf  99%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:   61 of  688 MB written (fifo 100%) [buf 100%]   4.0x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:   62 of  688 MB written (fifo 100%) [buf 100%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:   63 of  688 MB written (fifo 100%) [buf  99%]   4.0x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:   64 of  688 MB written (fifo 100%) [buf 100%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:   65 of  688 MB written (fifo 100%) [buf 100%]   4.3x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:   66 of  688 MB written (fifo 100%) [buf  99%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:   67 of  688 MB written (fifo 100%) [buf  99%]   4.3x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:   68 of  688 MB written (fifo 100%) [buf 100%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:   69 of  688 MB written (fifo 100%) [buf 100%]   4.3x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:   70 of  688 MB written (fifo 100%) [buf  99%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:   71 of  688 MB written (fifo 100%) [buf  99%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:   72 of  688 MB written (fifo 100%) [buf 100%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:   73 of  688 MB written (fifo 100%) [buf 100%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:   74 of  688 MB written (fifo 100%) [buf  99%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:   75 of  688 MB written (fifo 100%) [buf  99%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:   76 of  688 MB written (fifo 100%) [buf 100%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:   77 of  688 MB written (fifo 100%) [buf 100%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:   78 of  688 MB written (fifo 100%) [buf  99%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:   79 of  688 MB written (fifo 100%) [buf  99%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:   80 of  688 MB written (fifo 100%) [buf 100%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:   81 of  688 MB written (fifo 100%) [buf 100%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:   82 of  688 MB written (fifo 100%) [buf  99%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:   83 of  688 MB written (fifo 100%) [buf  99%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:   84 of  688 MB written (fifo 100%) [buf 100%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:   85 of  688 MB written (fifo 100%) [buf 100%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:   86 of  688 MB written (fifo 100%) [buf  99%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:   87 of  688 MB written (fifo 100%) [buf  99%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:   88 of  688 MB written (fifo 100%) [buf 100%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:   89 of  688 MB written (fifo 100%) [buf 100%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:   90 of  688 MB written (fifo 100%) [buf  99%]   4.0x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:   91 of  688 MB written (fifo 100%) [buf  99%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:   92 of  688 MB written (fifo 100%) [buf 100%]   4.0x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:   93 of  688 MB written (fifo 100%) [buf 100%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:   94 of  688 MB written (fifo 100%) [buf  99%]   4.0x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:   95 of  688 MB written (fifo 100%) [buf 100%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:   96 of  688 MB written (fifo 100%) [buf 100%]   4.3x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:   97 of  688 MB written (fifo 100%) [buf  99%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:   98 of  688 MB written (fifo 100%) [buf  99%]   4.3x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:   99 of  688 MB written (fifo 100%) [buf 100%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  100 of  688 MB written (fifo 100%) [buf 100%]   4.3x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  101 of  688 MB written (fifo 100%) [buf  99%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  102 of  688 MB written (fifo 100%) [buf  99%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  103 of  688 MB written (fifo 100%) [buf 100%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  104 of  688 MB written (fifo 100%) [buf 100%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  105 of  688 MB written (fifo 100%) [buf  99%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  106 of  688 MB written (fifo 100%) [buf  99%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  107 of  688 MB written (fifo 100%) [buf 100%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  108 of  688 MB written (fifo 100%) [buf 100%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  109 of  688 MB written (fifo 100%) [buf  99%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  110 of  688 MB written (fifo 100%) [buf  99%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  111 of  688 MB written (fifo 100%) [buf 100%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  112 of  688 MB written (fifo 100%) [buf 100%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  113 of  688 MB written (fifo 100%) [buf  99%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  114 of  688 MB written (fifo 100%) [buf  99%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  115 of  688 MB written (fifo 100%) [buf 100%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  116 of  688 MB written (fifo 100%) [buf 100%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  117 of  688 MB written (fifo 100%) [buf  99%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  118 of  688 MB written (fifo 100%) [buf  99%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  119 of  688 MB written (fifo 100%) [buf 100%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  120 of  688 MB written (fifo 100%) [buf 100%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  121 of  688 MB written (fifo 100%) [buf  99%]   4.0x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  122 of  688 MB written (fifo 100%) [buf  99%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  123 of  688 MB written (fifo 100%) [buf 100%]   4.0x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  124 of  688 MB written (fifo 100%) [buf 100%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  125 of  688 MB written (fifo 100%) [buf  99%]   4.0x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  126 of  688 MB written (fifo 100%) [buf 100%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  127 of  688 MB written (fifo 100%) [buf 100%]   4.3x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  128 of  688 MB written (fifo 100%) [buf  99%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  129 of  688 MB written (fifo 100%) [buf  99%]   4.3x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  130 of  688 MB written (fifo 100%) [buf 100%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  131 of  688 MB written (fifo 100%) [buf 100%]   4.3x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  132 of  688 MB written (fifo 100%) [buf  99%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  133 of  688 MB written (fifo 100%) [buf  99%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  134 of  688 MB written (fifo 100%) [buf 100%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  135 of  688 MB written (fifo 100%) [buf 100%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  136 of  688 MB written (fifo 100%) [buf  99%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  137 of  688 MB written (fifo 100%) [buf  99%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  138 of  688 MB written (fifo 100%) [buf 100%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  139 of  688 MB written (fifo 100%) [buf 100%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  140 of  688 MB written (fifo 100%) [buf  99%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  141 of  688 MB written (fifo 100%) [buf  99%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  142 of  688 MB written (fifo 100%) [buf 100%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  143 of  688 MB written (fifo 100%) [buf 100%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  144 of  688 MB written (fifo 100%) [buf  99%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  145 of  688 MB written (fifo 100%) [buf  99%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  146 of  688 MB written (fifo 100%) [buf 100%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  147 of  688 MB written (fifo 100%) [buf 100%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  148 of  688 MB written (fifo 100%) [buf  99%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  149 of  688 MB written (fifo 100%) [buf  99%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  150 of  688 MB written (fifo 100%) [buf 100%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  151 of  688 MB written (fifo 100%) [buf 100%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  152 of  688 MB written (fifo 100%) [buf  99%]   4.0x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  153 of  688 MB written (fifo 100%) [buf  99%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  154 of  688 MB written (fifo 100%) [buf 100%]   4.0x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  155 of  688 MB written (fifo 100%) [buf 100%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  156 of  688 MB written (fifo 100%) [buf  99%]   4.0x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  157 of  688 MB written (fifo 100%) [buf 100%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  158 of  688 MB written (fifo 100%) [buf 100%]   4.3x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  159 of  688 MB written (fifo 100%) [buf  99%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  160 of  688 MB written (fifo 100%) [buf  99%]   4.3x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  161 of  688 MB written (fifo 100%) [buf 100%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  162 of  688 MB written (fifo 100%) [buf 100%]   4.3x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  163 of  688 MB written (fifo 100%) [buf  99%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  164 of  688 MB written (fifo 100%) [buf  99%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  165 of  688 MB written (fifo 100%) [buf 100%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  166 of  688 MB written (fifo 100%) [buf 100%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  167 of  688 MB written (fifo 100%) [buf  99%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  168 of  688 MB written (fifo 100%) [buf  99%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  169 of  688 MB written (fifo 100%) [buf 100%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  170 of  688 MB written (fifo 100%) [buf 100%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  171 of  688 MB written (fifo 100%) [buf  99%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  172 of  688 MB written (fifo 100%) [buf  99%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  173 of  688 MB written (fifo 100%) [buf 100%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  174 of  688 MB written (fifo 100%) [buf 100%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  175 of  688 MB written (fifo 100%) [buf  99%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  176 of  688 MB written (fifo 100%) [buf  99%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  177 of  688 MB written (fifo 100%) [buf 100%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  178 of  688 MB written (fifo 100%) [buf 100%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  179 of  688 MB written (fifo 100%) [buf  99%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  180 of  688 MB written (fifo 100%) [buf  99%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  181 of  688 MB written (fifo 100%) [buf 100%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  182 of  688 MB written (fifo 100%) [buf 100%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  183 of  688 MB written (fifo 100%) [buf  99%]   4.0x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  184 of  688 MB written (fifo 100%) [buf  99%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  185 of  688 MB written (fifo 100%) [buf 100%]   4.0x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  186 of  688 MB written (fifo 100%) [buf 100%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  187 of  688 MB written (fifo 100%) [buf  99%]   4.0x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  188 of  688 MB written (fifo 100%) [buf 100%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  189 of  688 MB written (fifo 100%) [buf 100%]   4.3x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  190 of  688 MB written (fifo 100%) [buf  99%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  191 of  688 MB written (fifo 100%) [buf  99%]   4.3x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  192 of  688 MB written (fifo 100%) [buf 100%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  193 of  688 MB written (fifo 100%) [buf 100%]   4.3x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  194 of  688 MB written (fifo 100%) [buf  99%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  195 of  688 MB written (fifo 100%) [buf  99%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  196 of  688 MB written (fifo 100%) [buf 100%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  197 of  688 MB written (fifo 100%) [buf 100%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  198 of  688 MB written (fifo 100%) [buf  99%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  199 of  688 MB written (fifo 100%) [buf  99%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  200 of  688 MB written (fifo 100%) [buf 100%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  201 of  688 MB written (fifo 100%) [buf 100%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  202 of  688 MB written (fifo 100%) [buf  99%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  203 of  688 MB written (fifo 100%) [buf  99%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  204 of  688 MB written (fifo 100%) [buf 100%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  205 of  688 MB written (fifo 100%) [buf 100%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  206 of  688 MB written (fifo 100%) [buf  99%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  207 of  688 MB written (fifo 100%) [buf  99%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  208 of  688 MB written (fifo 100%) [buf 100%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  209 of  688 MB written (fifo 100%) [buf 100%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  210 of  688 MB written (fifo 100%) [buf  99%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  211 of  688 MB written (fifo 100%) [buf  99%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  212 of  688 MB written (fifo 100%) [buf 100%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  213 of  688 MB written (fifo 100%) [buf 100%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  214 of  688 MB written (fifo 100%) [buf  99%]   4.0x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  215 of  688 MB written (fifo 100%) [buf  99%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  216 of  688 MB written (fifo 100%) [buf 100%]   4.0x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  217 of  688 MB written (fifo 100%) [buf 100%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  218 of  688 MB written (fifo 100%) [buf  99%]   4.0x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  219 of  688 MB written (fifo 100%) [buf 100%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  220 of  688 MB written (fifo 100%) [buf 100%]   4.3x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  221 of  688 MB written (fifo 100%) [buf  99%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  222 of  688 MB written (fifo 100%) [buf  99%]   4.3x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  223 of  688 MB written (fifo 100%) [buf 100%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  224 of  688 MB written (fifo 100%) [buf 100%]   4.3x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  225 of  688 MB written (fifo 100%) [buf  99%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  226 of  688 MB written (fifo 100%) [buf  99%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  227 of  688 MB written (fifo 100%) [buf 100%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  228 of  688 MB written (fifo 100%) [buf 100%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  229 of  688 MB written (fifo 100%) [buf  99%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  230 of  688 MB written (fifo 100%) [buf  99%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  231 of  688 MB written (fifo 100%) [buf 100%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  232 of  688 MB written (fifo 100%) [buf 100%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  233 of  688 MB written (fifo 100%) [buf  99%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  234 of  688 MB written (fifo 100%) [buf  99%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  235 of  688 MB written (fifo 100%) [buf 100%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  236 of  688 MB written (fifo 100%) [buf 100%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  237 of  688 MB written (fifo 100%) [buf  99%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  238 of  688 MB written (fifo 100%) [buf  99%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  239 of  688 MB written (fifo 100%) [buf 100%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  240 of  688 MB written (fifo 100%) [buf 100%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  241 of  688 MB written (fifo 100%) [buf  99%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  242 of  688 MB written (fifo 100%) [buf  99%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  243 of  688 MB written (fifo 100%) [buf 100%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  244 of  688 MB written (fifo 100%) [buf 100%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  245 of  688 MB written (fifo 100%) [buf  99%]   4.0x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  246 of  688 MB written (fifo 100%) [buf  99%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  247 of  688 MB written (fifo 100%) [buf 100%]   4.0x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  248 of  688 MB written (fifo 100%) [buf 100%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  249 of  688 MB written (fifo 100%) [buf  99%]   4.0x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  250 of  688 MB written (fifo 100%) [buf 100%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  251 of  688 MB written (fifo 100%) [buf 100%]   4.3x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  252 of  688 MB written (fifo 100%) [buf  99%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  253 of  688 MB written (fifo 100%) [buf  99%]   4.3x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  254 of  688 MB written (fifo 100%) [buf 100%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  255 of  688 MB written (fifo 100%) [buf 100%]   4.3x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  256 of  688 MB written (fifo 100%) [buf  99%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  257 of  688 MB written (fifo 100%) [buf  99%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  258 of  688 MB written (fifo 100%) [buf 100%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  259 of  688 MB written (fifo 100%) [buf 100%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  260 of  688 MB written (fifo 100%) [buf  99%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  261 of  688 MB written (fifo 100%) [buf  99%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  262 of  688 MB written (fifo 100%) [buf 100%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  263 of  688 MB written (fifo 100%) [buf 100%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  264 of  688 MB written (fifo 100%) [buf  99%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  265 of  688 MB written (fifo 100%) [buf  99%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  266 of  688 MB written (fifo 100%) [buf 100%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  267 of  688 MB written (fifo 100%) [buf 100%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  268 of  688 MB written (fifo 100%) [buf  99%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  269 of  688 MB written (fifo 100%) [buf  99%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  270 of  688 MB written (fifo 100%) [buf 100%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  271 of  688 MB written (fifo 100%) [buf 100%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  272 of  688 MB written (fifo 100%) [buf  99%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  273 of  688 MB written (fifo 100%) [buf  99%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  274 of  688 MB written (fifo 100%) [buf 100%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  275 of  688 MB written (fifo 100%) [buf 100%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  276 of  688 MB written (fifo 100%) [buf  99%]   4.0x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  277 of  688 MB written (fifo 100%) [buf  99%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  278 of  688 MB written (fifo 100%) [buf 100%]   4.0x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  279 of  688 MB written (fifo 100%) [buf 100%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  280 of  688 MB written (fifo 100%) [buf  99%]   4.0x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  281 of  688 MB written (fifo 100%) [buf 100%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  282 of  688 MB written (fifo 100%) [buf 100%]   4.3x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  283 of  688 MB written (fifo 100%) [buf  99%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  284 of  688 MB written (fifo 100%) [buf  99%]   4.3x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  285 of  688 MB written (fifo 100%) [buf 100%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  286 of  688 MB written (fifo 100%) [buf 100%]   4.3x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  287 of  688 MB written (fifo 100%) [buf  99%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  288 of  688 MB written (fifo 100%) [buf  99%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  289 of  688 MB written (fifo 100%) [buf 100%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  290 of  688 MB written (fifo 100%) [buf 100%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  291 of  688 MB written (fifo 100%) [buf  99%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  292 of  688 MB written (fifo 100%) [buf  99%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  293 of  688 MB written (fifo 100%) [buf 100%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  294 of  688 MB written (fifo 100%) [buf 100%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  295 of  688 MB written (fifo 100%) [buf  99%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  296 of  688 MB written (fifo 100%) [buf  99%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  297 of  688 MB written (fifo 100%) [buf 100%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  298 of  688 MB written (fifo 100%) [buf 100%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  299 of  688 MB written (fifo 100%) [buf  99%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  300 of  688 MB written (fifo 100%) [buf  99%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  301 of  688 MB written (fifo 100%) [buf 100%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  302 of  688 MB written (fifo 100%) [buf 100%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  303 of  688 MB written (fifo 100%) [buf  99%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  304 of  688 MB written (fifo 100%) [buf  99%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  305 of  688 MB written (fifo 100%) [buf 100%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  306 of  688 MB written (fifo 100%) [buf 100%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  307 of  688 MB written (fifo 100%) [buf  99%]   4.0x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  308 of  688 MB written (fifo 100%) [buf  99%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  309 of  688 MB written (fifo 100%) [buf 100%]   4.0x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  310 of  688 MB written (fifo 100%) [buf 100%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  311 of  688 MB written (fifo 100%) [buf  99%]   4.0x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  312 of  688 MB written (fifo 100%) [buf 100%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  313 of  688 MB written (fifo 100%) [buf 100%]   4.3x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  314 of  688 MB written (fifo 100%) [buf  99%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  315 of  688 MB written (fifo 100%) [buf  99%]   4.3x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  316 of  688 MB written (fifo 100%) [buf 100%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  317 of  688 MB written (fifo 100%) [buf 100%]   4.3x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  318 of  688 MB written (fifo 100%) [buf  99%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  319 of  688 MB written (fifo 100%) [buf  99%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  320 of  688 MB written (fifo 100%) [buf 100%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  321 of  688 MB written (fifo 100%) [buf 100%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  322 of  688 MB written (fifo 100%) [buf  99%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  323 of  688 MB written (fifo 100%) [buf  99%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  324 of  688 MB written (fifo 100%) [buf 100%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  325 of  688 MB written (fifo 100%) [buf 100%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  326 of  688 MB written (fifo 100%) [buf  99%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  327 of  688 MB written (fifo 100%) [buf  99%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  328 of  688 MB written (fifo 100%) [buf 100%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  329 of  688 MB written (fifo 100%) [buf 100%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  330 of  688 MB written (fifo 100%) [buf  99%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  331 of  688 MB written (fifo 100%) [buf  99%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  332 of  688 MB written (fifo 100%) [buf 100%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  333 of  688 MB written (fifo 100%) [buf 100%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  334 of  688 MB written (fifo 100%) [buf  99%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  335 of  688 MB written (fifo 100%) [buf  99%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  336 of  688 MB written (fifo 100%) [buf 100%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  337 of  688 MB written (fifo 100%) [buf 100%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  338 of  688 MB written (fifo 100%) [buf  99%]   4.0x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  339 of  688 MB written (fifo 100%) [buf  99%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  340 of  688 MB written (fifo 100%) [buf 100%]   4.0x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  341 of  688 MB written (fifo 100%) [buf 100%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  342 of  688 MB written (fifo 100%) [buf  99%]   4.0x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  343 of  688 MB written (fifo 100%) [buf 100%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  344 of  688 MB written (fifo 100%) [buf 100%]   4.3x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  345 of  688 MB written (fifo 100%) [buf  99%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  346 of  688 MB written (fifo 100%) [buf  99%]   4.3x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  347 of  688 MB written (fifo 100%) [buf 100%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  348 of  688 MB written (fifo 100%) [buf 100%]   4.3x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  349 of  688 MB written (fifo 100%) [buf  99%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  350 of  688 MB written (fifo 100%) [buf  99%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  351 of  688 MB written (fifo 100%) [buf 100%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  352 of  688 MB written (fifo 100%) [buf 100%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  353 of  688 MB written (fifo 100%) [buf  99%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  354 of  688 MB written (fifo 100%) [buf  99%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  355 of  688 MB written (fifo 100%) [buf 100%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  356 of  688 MB written (fifo 100%) [buf 100%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  357 of  688 MB written (fifo 100%) [buf  99%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  358 of  688 MB written (fifo 100%) [buf  99%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  359 of  688 MB written (fifo 100%) [buf 100%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  360 of  688 MB written (fifo 100%) [buf 100%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  361 of  688 MB written (fifo 100%) [buf  99%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  362 of  688 MB written (fifo 100%) [buf  99%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  363 of  688 MB written (fifo 100%) [buf 100%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Track 01:  364 of  688 MB written (fifo 100%) [buf 100%]   4.2x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stderr: Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error 
BraseroWodim called brasero_job_get_flags 
BraseroWodim stderr: CDB:  2A 00 00 02 DB 0B 00 00 1F 00 
BraseroWodim called brasero_job_get_flags 
BraseroWodim stderr: status: 0x2 (CHECK CONDITION) 
BraseroWodim called brasero_job_get_flags 
BraseroWodim stderr: Sense Bytes: F1 00 03 00 02 D8 9E 0A 00 13 00 00 10 00 00 00 
BraseroWodim called brasero_job_get_flags 
BraseroWodim stderr: Sense Key: 0x3 Medium Error, deferred error, Segment 0 
BraseroWodim called brasero_job_get_flags 
BraseroWodim stderr: Sense Code: 0x10 Qual 0x00 (id crc or ecc error) Fru 0x0 
BraseroWodim called brasero_job_get_flags 
BraseroWodim stderr: Sense flags: Blk 186526 (valid) 
BraseroWodim called brasero_job_get_flags 
BraseroWodim stderr: cmd finished after 0.072s timeout 40s 
BraseroWodim called brasero_job_get_flags 
BraseroWodim stderr: wodim: A write error occured. 
BraseroWodim called brasero_job_get_flags 
BraseroWodim stderr: wodim: Please properly read the error message above. 
BraseroWodim called brasero_job_get_flags 
BraseroWodim stdout: Track 01:  365 of  688 MB written (fifo 100%) [buf  99%]   4.1x. 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: write track data: error after 383277056 bytes 
BraseroWodim stdout: Writing  time:  633.778s 
BraseroWodim stdout: Average write speed   7.5x. 
BraseroWodim stdout: Min drive buffer fill was 99% 
BraseroWodim stdout: Fixating... 
BraseroWodim called brasero_job_get_action 
BraseroWodim called brasero_job_set_current_action 
BraseroWodim stdout: Fixating time:   78.814s 
BraseroWodim stderr: wodim: fifo had 6292 puts and 6038 gets. 
BraseroWodim called brasero_job_get_flags 
BraseroWodim stdout: BURN-Free was never needed. 
BraseroWodim stderr: wodim: fifo was 0 times empty and 6025 times full, min fill was 97%. 
BraseroWodim called brasero_job_get_flags 
BraseroWodim stdout: HUP 
BraseroWodim stderr: HUP 
BraseroWodim process finished with status 254 
BraseroWodim called brasero_job_error 
BraseroWodim finished with an error 
BraseroWodim asked to stop because of an error 
	error		= 0 
	message	= "no message" 
BraseroWodim stopping 
BraseroWodim got killed 
Session error : unknown (brasero_burn_record brasero-burn.c:2811) ntuforumsw.o
```

---

### Post by AkiraBergman on 2009-12-26
Use K3B.

---

### Post by marcellux on 2010-02-06
I have exactly the same issue; can burn music, data, image cd's, but no dvd's! brasero, gnomebaker or K3b with extracodecs packages! I am using Ubuntu 9.10 karmic Koala. with 9.04 had no problem!!!


"  p, li { white-space: pre-wrap; }  [FONT=DejaVu Sans Mono]Devices[/FONT]
 [FONT=DejaVu Sans Mono]-----------------------[/FONT]
 [FONT=DejaVu Sans Mono]Slimtype DVD A  DS8A1P CA11 (/dev/sr0, CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL) [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump] [%7][/FONT]
 [FONT=DejaVu Sans Mono][/FONT]
 [FONT=DejaVu Sans Mono]System[/FONT]
 [FONT=DejaVu Sans Mono]-----------------------[/FONT]
 [FONT=DejaVu Sans Mono]K3b Version: 1.68.0[/FONT]
 [FONT=DejaVu Sans Mono]KDE Version: 4.3.5 (KDE 4.3.5)[/FONT]
 [FONT=DejaVu Sans Mono]QT Version:  4.5.2[/FONT]
 [FONT=DejaVu Sans Mono]Kernel:      2.6.31-19-generic[/FONT]
 [FONT=DejaVu Sans Mono][/FONT]
 [FONT=DejaVu Sans Mono]Used versions[/FONT]
 [FONT=DejaVu Sans Mono]-----------------------[/FONT]
 [FONT=DejaVu Sans Mono]cdrecord: 1.1.9[/FONT]
 [FONT=DejaVu Sans Mono][/FONT]
 [FONT=DejaVu Sans Mono]cdrecord[/FONT]
 [FONT=DejaVu Sans Mono]-----------------------[/FONT]
 [FONT=DejaVu Sans Mono]/usr/bin/wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.[/FONT]
 [FONT=DejaVu Sans Mono]scsidev: '/dev/sr0'[/FONT]
 [FONT=DejaVu Sans Mono]devname: '/dev/sr0'[/FONT]
 [FONT=DejaVu Sans Mono]scsibus: -2 target: -2 lun: -2[/FONT]
 [FONT=DejaVu Sans Mono]Linux sg driver version: 3.5.27[/FONT]
 [FONT=DejaVu Sans Mono]Wodim version: 1.1.9[/FONT]
 [FONT=DejaVu Sans Mono]SCSI buffer size: 64512[/FONT]
 [FONT=DejaVu Sans Mono]Beginning DMA speed test. Set CDR_NODMATEST environment variable if device[/FONT]
 [FONT=DejaVu Sans Mono]communication breaks or freezes immediately after that.[/FONT]
 [FONT=DejaVu Sans Mono]TOC Type: 1 = CD-ROM[/FONT]
 [FONT=DejaVu Sans Mono]Driveropts: 'burnfree'[/FONT]
 [FONT=DejaVu Sans Mono]Device type    : Removable CD-ROM[/FONT]
 [FONT=DejaVu Sans Mono]Version        : 5[/FONT]
 [FONT=DejaVu Sans Mono]Response Format: 2[/FONT]
 [FONT=DejaVu Sans Mono]Capabilities   : [/FONT]
 [FONT=DejaVu Sans Mono]Vendor_info    : 'Slimtype'[/FONT]
 [FONT=DejaVu Sans Mono]Identification : 'DVD A  DS8A1P   '[/FONT]
 [FONT=DejaVu Sans Mono]Revision       : 'CA11'[/FONT]
 [FONT=DejaVu Sans Mono]Device seems to be: Generic mmc2 DVD-R/DVD-RW.[/FONT]
 [FONT=DejaVu Sans Mono]Current: 0x001B (DVD+R)[/FONT]
 [FONT=DejaVu Sans Mono]Profile: 0x002B (DVD+R/DL) [/FONT]
 [FONT=DejaVu Sans Mono]Profile: 0x001B (DVD+R) (current)[/FONT]
 [FONT=DejaVu Sans Mono]Profile: 0x001A (DVD+RW) [/FONT]
 [FONT=DejaVu Sans Mono]Profile: 0x0016 (DVD-R/DL layer jump recording) [/FONT]
 [FONT=DejaVu Sans Mono]Profile: 0x0015 (DVD-R/DL sequential recording) [/FONT]
 [FONT=DejaVu Sans Mono]Profile: 0x0014 (DVD-RW sequential recording) [/FONT]
 [FONT=DejaVu Sans Mono]Profile: 0x0013 (DVD-RW restricted overwrite) [/FONT]
 [FONT=DejaVu Sans Mono]Profile: 0x0012 (DVD-RAM) [/FONT]
 [FONT=DejaVu Sans Mono]Profile: 0x0011 (DVD-R sequential recording) [/FONT]
 [FONT=DejaVu Sans Mono]Profile: 0x0010 (DVD-ROM) [/FONT]
 [FONT=DejaVu Sans Mono]Profile: 0x000A (CD-RW) [/FONT]
 [FONT=DejaVu Sans Mono]Profile: 0x0009 (CD-R) [/FONT]
 [FONT=DejaVu Sans Mono]Profile: 0x0008 (CD-ROM) [/FONT]
 [FONT=DejaVu Sans Mono]Profile: 0x0002 (Removable disk) [/FONT]
 [FONT=DejaVu Sans Mono]Using generic SCSI-3/mmc DVD-R(W) driver (mmc_mdvd).[/FONT]
 [FONT=DejaVu Sans Mono]Driver flags   : SWABAUDIO BURNFREE [/FONT]
 [FONT=DejaVu Sans Mono]Supported modes: PACKET SAO[/FONT]
 [FONT=DejaVu Sans Mono]Drive buf size : 1029888 = 1005 KB[/FONT]
 [FONT=DejaVu Sans Mono]FIFO size      : 12582912 = 12288 KB[/FONT]
 [FONT=DejaVu Sans Mono]Speed set to 11080 KB/s[/FONT]
 [FONT=DejaVu Sans Mono]Track 01: data  1497 MB        [/FONT]
 [FONT=DejaVu Sans Mono]Total size:     1719 MB (170:20.16) = 766512 sectors[/FONT]
 [FONT=DejaVu Sans Mono]Lout start:     1719 MB (170:22/12) = 766512 sectors[/FONT]
 [FONT=DejaVu Sans Mono]Current Secsize: 2048[/FONT]
 [FONT=DejaVu Sans Mono]HINT: use dvd+rw-mediainfo from dvd+rw-tools for information extraction.[/FONT]
 [FONT=DejaVu Sans Mono]Blocks total: 2295104 Blocks current: 2295104 Blocks remaining: 1528592[/FONT]
 [FONT=DejaVu Sans Mono]Starting to write CD/DVD at speed   8.0 in real SAO mode for single session.[/FONT]
 [FONT=DejaVu Sans Mono]Last chance to quit, starting real write in    2 seconds.[/FONT]
 [FONT=DejaVu Sans Mono]   1 seconds.[/FONT]
 [FONT=DejaVu Sans Mono]   0 seconds. Operation starts.[/FONT]
 [FONT=DejaVu Sans Mono]Waiting for reader process to fill input buffer ... Errno: 5 (Input/output error), reserve track scsi sendcmd: no error[/FONT]
 [FONT=DejaVu Sans Mono]CDB:  53 00 00 00 00 00 0B B2 30 00[/FONT]
 [FONT=DejaVu Sans Mono]status: 0x2 (CHECK CONDITION)[/FONT]
 [FONT=DejaVu Sans Mono]Sense Bytes: 70 00 03 00 00 00 00 0A 00 00 00 00 73 03 00 00[/FONT]
 [FONT=DejaVu Sans Mono]Sense Key: 0x3 Medium Error, Segment 0[/FONT]
 [FONT=DejaVu Sans Mono]Sense Code: 0x73 Qual 0x03 (power calibration area error) Fru 0x0[/FONT]
 [FONT=DejaVu Sans Mono]Sense flags: Blk 0 (not valid) [/FONT]
 [FONT=DejaVu Sans Mono]cmd finished after 35.345s timeout 200s[/FONT]
 [FONT=DejaVu Sans Mono]/usr/bin/wodim: Cannot open new session.[/FONT]
 [FONT=DejaVu Sans Mono]input buffer ready.[/FONT]
 [FONT=DejaVu Sans Mono]Writing  time:   35.408s[/FONT]
 [FONT=DejaVu Sans Mono]/usr/bin/wodim: fifo had 192 puts and 0 gets.[/FONT]
 [FONT=DejaVu Sans Mono]/usr/bin/wodim: fifo was 0 times empty and 0 times full, min fill was 100%.[/FONT]
 [FONT=DejaVu Sans Mono][/FONT]
 [FONT=DejaVu Sans Mono]cdrecord command:[/FONT]
 [FONT=DejaVu Sans Mono]-----------------------[/FONT]
 [FONT=DejaVu Sans Mono]/usr/bin/wodim -v gracetime=2 dev=/dev/sr0 speed=8 -sao driveropts=burnfree -data -tsize=766512s -"[/FONT]
 [FONT=DejaVu Sans Mono][/FONT]

---

### Post by marcellux on 2010-02-06
I had the same problem with brasero, gnomebaker and k3b! "FAILED".

As default, the speed is set to "auto". I set the speed to burn at 2X... and it works fine now!!!

---

### Post by marcellux on 2010-02-06
By the way! I am using K3b! 

the log now looks like this;

Devices
-----------------------
Slimtype DVD A  DS8A1P CA11 (/dev/sr0, CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL) [DVD-ROM, DVD-R Sequential, DVD-R Dual Layer Sequential, DVD-R Dual Layer Jump, DVD-RAM, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, DVD+R Dual Layer, CD-ROM, CD-R, CD-RW] [SAO, TAO, RAW, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Restricted Overwrite, Layer Jump] [%7]

System
-----------------------
K3b Version: 1.68.0
KDE Version: 4.3.5 (KDE 4.3.5)
QT Version:  4.5.2
Kernel:      2.6.31-19-generic

Used versions
-----------------------
cdrecord: 1.1.9

cdrecord
-----------------------
/usr/bin/wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.scsidev: '/dev/sr0'
devname: '/dev/sr0'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.9
SCSI buffer size: 64512
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
TOC Type: 1 = CD-ROM
Driveropts: 'burnfree'
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'Slimtype'
Identification : 'DVD A  DS8A1P   '
Revision       : 'CA11'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x001B (DVD+R)
Profile: 0x002B (DVD+R/DL) 
Profile: 0x001B (DVD+R) (current)
Profile: 0x001A (DVD+RW) 
Profile: 0x0016 (DVD-R/DL layer jump recording) 
Profile: 0x0015 (DVD-R/DL sequential recording) 
Profile: 0x0014 (DVD-RW sequential recording) 
Profile: 0x0013 (DVD-RW restricted overwrite) 
Profile: 0x0012 (DVD-RAM) 
Profile: 0x0011 (DVD-R sequential recording) 
Profile: 0x0010 (DVD-ROM) 
Profile: 0x000A (CD-RW) 
Profile: 0x0009 (CD-R) 
Profile: 0x0008 (CD-ROM) 
Profile: 0x0002 (Removable disk) 
Using generic SCSI-3/mmc DVD-R(W) driver (mmc_mdvd).
Driver flags   : SWABAUDIO BURNFREE 
Supported modes: PACKET SAO
Drive buf size : 1029888 = 1005 KB
FIFO size      : 12582912 = 12288 KB
Speed set to 3324 KB/s
Track 01: data  1497 MB        
Total size:     1719 MB (170:20.16) = 766512 sectors
Lout start:     1719 MB (170:22/12) = 766512 sectors
Current Secsize: 2048
HINT: use dvd+rw-mediainfo from dvd+rw-tools for information extraction.
Blocks total: 2295104 Blocks current: 2295104 Blocks remaining: 1528592
Starting to write CD/DVD at speed   2.0 in real SAO mode for single session.
Last chance to quit, starting real write in    2 seconds.
   1 seconds.
   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Sending CUE sheet...
Starting new track at sector: 0
Track 01:    0 of 1497 MB written.
Track 01:    1 of 1497 MB written (fifo 100%) [buf  99%]   0.4x.
Track 01:    2 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:    3 of 1497 MB written (fifo 100%) [buf  96%]   2.7x.
Track 01:    4 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:    5 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:    6 of 1497 MB written (fifo 100%) [buf  98%]   2.6x.
Track 01:    7 of 1497 MB written (fifo  99%) [buf  99%]   2.8x.
Track 01:    8 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:    9 of 1497 MB written (fifo 100%) [buf  98%]   2.7x.
Track 01:   10 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:   11 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:   12 of 1497 MB written (fifo  99%) [buf  99%]   2.6x.
Track 01:   13 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:   14 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:   15 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:   16 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:   17 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01:   18 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:   19 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:   20 of 1497 MB written (fifo 100%) [buf  96%]   2.6x.
Track 01:   21 of 1497 MB written (fifo 100%) [buf  98%]   2.7x.
Track 01:   22 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:   23 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:   24 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:   25 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:   26 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:   27 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:   28 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:   29 of 1497 MB written (fifo 100%) [buf  97%]   2.6x.
Track 01:   30 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01:   31 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:   32 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:   33 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01:   34 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01:   35 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01:   36 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01:   37 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:   38 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:   39 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:   40 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:   41 of 1497 MB written (fifo  99%) [buf  99%]   2.6x.
Track 01:   42 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:   43 of 1497 MB written (fifo  98%) [buf  99%]   2.6x.
Track 01:   44 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:   45 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:   46 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:   47 of 1497 MB written (fifo  99%) [buf  99%]   2.6x.
Track 01:   48 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:   49 of 1497 MB written (fifo  99%) [buf  96%]   2.6x.
Track 01:   50 of 1497 MB written (fifo  99%) [buf  99%]   2.8x.
Track 01:   51 of 1497 MB written (fifo  99%) [buf  98%]   2.6x.
Track 01:   52 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:   53 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:   54 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:   55 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:   56 of 1497 MB written (fifo 100%) [buf  97%]   2.6x.
Track 01:   57 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:   58 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01:   59 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:   60 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:   61 of 1497 MB written (fifo 100%) [buf  98%]   2.6x.
Track 01:   62 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:   63 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:   64 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01:   65 of 1497 MB written (fifo 100%) [buf  96%]   2.7x.
Track 01:   66 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:   67 of 1497 MB written (fifo 100%) [buf  97%]   2.7x.
Track 01:   68 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01:   69 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01:   70 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:   71 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:   72 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:   73 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01:   74 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:   75 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:   76 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:   77 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:   78 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:   79 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:   80 of 1497 MB written (fifo  99%) [buf  99%]   2.6x.
Track 01:   81 of 1497 MB written (fifo 100%) [buf  96%]   2.6x.
Track 01:   82 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:   83 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:   84 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:   85 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01:   86 of 1497 MB written (fifo 100%) [buf  98%]   2.6x.
Track 01:   87 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:   88 of 1497 MB written (fifo  98%) [buf  99%]   2.6x.
Track 01:   89 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:   90 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:   91 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01:   92 of 1497 MB written (fifo  99%) [buf  99%]   2.6x.
Track 01:   93 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:   94 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:   95 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01:   96 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:   97 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:   98 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:   99 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  100 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01:  101 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  102 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  103 of 1497 MB written (fifo  99%) [buf  99%]   2.6x.
Track 01:  104 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  105 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  106 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  107 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  108 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  109 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  110 of 1497 MB written (fifo 100%) [buf  96%]   2.6x.
Track 01:  111 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01:  112 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  113 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  114 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  115 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  116 of 1497 MB written (fifo 100%) [buf  98%]   2.7x.
Track 01:  117 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  118 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  119 of 1497 MB written (fifo  99%) [buf  99%]   2.6x.
Track 01:  120 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  121 of 1497 MB written (fifo  99%) [buf  99%]   2.6x.
Track 01:  122 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01:  123 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  124 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  125 of 1497 MB written (fifo  99%) [buf  99%]   2.6x.
Track 01:  126 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01:  127 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  128 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  129 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  130 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01:  131 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  132 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  133 of 1497 MB written (fifo 100%) [buf  96%]   2.7x.
Track 01:  134 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  135 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  136 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  137 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  138 of 1497 MB written (fifo  99%) [buf  99%]   2.6x.
Track 01:  139 of 1497 MB written (fifo 100%) [buf  98%]   2.7x.
Track 01:  140 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  141 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  142 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  143 of 1497 MB written (fifo  99%) [buf  97%]   2.7x.
Track 01:  144 of 1497 MB written (fifo  98%) [buf  97%]   2.6x.
Track 01:  145 of 1497 MB written (fifo 100%) [buf  99%]   2.8x.
Track 01:  146 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  147 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01:  148 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  149 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01:  150 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  151 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  152 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  153 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  154 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  155 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  156 of 1497 MB written (fifo  99%) [buf  99%]   2.6x.
Track 01:  157 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01:  158 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  159 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  160 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  161 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  162 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  163 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  164 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  165 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  166 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  167 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  168 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01:  169 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  170 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  171 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  172 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  173 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  174 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  175 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  176 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  177 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  178 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  179 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  180 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  181 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  182 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  183 of 1497 MB written (fifo  99%) [buf  99%]   2.6x.
Track 01:  184 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  185 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  186 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  187 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  188 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  189 of 1497 MB written (fifo 100%) [buf  99%]   2.8x.
Track 01:  190 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  191 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  192 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  193 of 1497 MB written (fifo  99%) [buf  94%]   2.6x.
Track 01:  194 of 1497 MB written (fifo 100%) [buf  99%]   2.8x.
Track 01:  195 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01:  196 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  197 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  198 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  199 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  200 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  201 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  202 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  203 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  204 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  205 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  206 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  207 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01:  208 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  209 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  210 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  211 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  212 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  213 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  214 of 1497 MB written (fifo  99%) [buf  98%]   2.6x.
Track 01:  215 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  216 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  217 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  218 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  219 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01:  220 of 1497 MB written (fifo  99%) [buf  99%]   2.8x.
Track 01:  221 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  222 of 1497 MB written (fifo 100%) [buf  98%]   2.7x.
Track 01:  223 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  224 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  225 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  226 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  227 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  228 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01:  229 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  230 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  231 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  232 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  233 of 1497 MB written (fifo  99%) [buf  99%]   2.6x.
Track 01:  234 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  235 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  236 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  237 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  238 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  239 of 1497 MB written (fifo  99%) [buf  99%]   2.6x.
Track 01:  240 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01:  241 of 1497 MB written (fifo  99%) [buf  99%]   2.6x.
Track 01:  242 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  243 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  244 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  245 of 1497 MB written (fifo 100%) [buf  98%]   2.6x.
Track 01:  246 of 1497 MB written (fifo 100%) [buf  97%]   2.6x.
Track 01:  247 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  248 of 1497 MB written (fifo 100%) [buf  98%]   2.7x.
Track 01:  249 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  250 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  251 of 1497 MB written (fifo  99%) [buf  99%]   2.8x.
Track 01:  252 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  253 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  254 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  255 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  256 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  257 of 1497 MB written (fifo 100%) [buf  98%]   2.7x.
Track 01:  258 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  259 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  260 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  261 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  262 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  263 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  264 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  265 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  266 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  267 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  268 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  269 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01:  270 of 1497 MB written (fifo  99%) [buf  99%]   2.6x.
Track 01:  271 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  272 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  273 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  274 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  275 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  276 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  277 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  278 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  279 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  280 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  281 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  282 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  283 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  284 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  285 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01:  286 of 1497 MB written (fifo 100%) [buf  98%]   2.7x.
Track 01:  287 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  288 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  289 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  290 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  291 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  292 of 1497 MB written (fifo 100%) [buf  97%]   2.7x.
Track 01:  293 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  294 of 1497 MB written (fifo 100%) [buf  98%]   2.7x.
Track 01:  295 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  296 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01:  297 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  298 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  299 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  300 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  301 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  302 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  303 of 1497 MB written (fifo 100%) [buf  97%]   2.6x.
Track 01:  304 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01:  305 of 1497 MB written (fifo  99%) [buf  99%]   2.6x.
Track 01:  306 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  307 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  308 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01:  309 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  310 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  311 of 1497 MB written (fifo  99%) [buf  98%]   2.6x.
Track 01:  312 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  313 of 1497 MB written (fifo 100%) [buf  99%]   2.8x.
Track 01:  314 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  315 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01:  316 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01:  317 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  318 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  319 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  320 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  321 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  322 of 1497 MB written (fifo  99%) [buf  99%]   2.6x.
Track 01:  323 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  324 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  325 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  326 of 1497 MB written (fifo  99%) [buf  99%]   2.6x.
Track 01:  327 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  328 of 1497 MB written (fifo 100%) [buf  98%]   2.6x.
Track 01:  329 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  330 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  331 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  332 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  333 of 1497 MB written (fifo 100%) [buf  98%]   2.7x.
Track 01:  334 of 1497 MB written (fifo  99%) [buf  99%]   2.6x.
Track 01:  335 of 1497 MB written (fifo 100%) [buf  96%]   2.6x.
Track 01:  336 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  337 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  338 of 1497 MB written (fifo  99%) [buf  99%]   2.6x.
Track 01:  339 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  340 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  341 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01:  342 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  343 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01:  344 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  345 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  346 of 1497 MB written (fifo 100%) [buf  99%]   2.8x.
Track 01:  347 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  348 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  349 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  350 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  351 of 1497 MB written (fifo  99%) [buf  99%]   2.6x.
Track 01:  352 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  353 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  354 of 1497 MB written (fifo 100%) [buf  98%]   2.7x.
Track 01:  355 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  356 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  357 of 1497 MB written (fifo  99%) [buf  99%]   2.6x.
Track 01:  358 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  359 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  360 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  361 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  362 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01:  363 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  364 of 1497 MB written (fifo  98%) [buf  99%]   2.7x.
Track 01:  365 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  366 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  367 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  368 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  369 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  370 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  371 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  372 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  373 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  374 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  375 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  376 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  377 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  378 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  379 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  380 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  381 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01:  382 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  383 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  384 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  385 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01:  386 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  387 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  388 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  389 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  390 of 1497 MB written (fifo 100%) [buf  98%]   2.6x.
Track 01:  391 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  392 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  393 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  394 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  395 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  396 of 1497 MB written (fifo  99%) [buf  99%]   2.6x.
Track 01:  397 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  398 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  399 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  400 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  401 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  402 of 1497 MB written (fifo  99%) [buf  99%]   2.6x.
Track 01:  403 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  404 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  405 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  406 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01:  407 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01:  408 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  409 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01:  410 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  411 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  412 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  413 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  414 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  415 of 1497 MB written (fifo  99%) [buf  98%]   2.6x.
Track 01:  416 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  417 of 1497 MB written (fifo 100%) [buf  98%]   2.6x.
Track 01:  418 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  419 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  420 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  421 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  422 of 1497 MB written (fifo 100%) [buf  98%]   2.7x.
Track 01:  423 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01:  424 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  425 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  426 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  427 of 1497 MB written (fifo  99%) [buf  99%]   2.6x.
Track 01:  428 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  429 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  430 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  431 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  432 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  433 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  434 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01:  435 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  436 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01:  437 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  438 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  439 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  440 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  441 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  442 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01:  443 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  444 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  445 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  446 of 1497 MB written (fifo 100%) [buf  93%]   2.5x.
Track 01:  447 of 1497 MB written (fifo  99%) [buf  99%]   2.9x.
Track 01:  448 of 1497 MB written (fifo 100%) [buf  98%]   2.6x.
Track 01:  449 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  450 of 1497 MB written (fifo  99%) [buf  99%]   2.6x.
Track 01:  451 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01:  452 of 1497 MB written (fifo  98%) [buf  99%]   2.6x.
Track 01:  453 of 1497 MB written (fifo 100%) [buf  90%]   2.5x.
Track 01:  454 of 1497 MB written (fifo 100%) [buf  99%]   2.8x.
Track 01:  455 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  456 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  457 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01:  458 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  459 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  460 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  461 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  462 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  463 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  464 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  465 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  466 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  467 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  468 of 1497 MB written (fifo 100%) [buf  99%]   2.8x.
Track 01:  469 of 1497 MB written (fifo 100%) [buf  98%]   2.6x.
Track 01:  470 of 1497 MB written (fifo 100%) [buf  99%]   2.8x.
Track 01:  471 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  472 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  473 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  474 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  475 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  476 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  477 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  478 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  479 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  480 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  481 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  482 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  483 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  484 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  485 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  486 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  487 of 1497 MB written (fifo  99%) [buf  99%]   2.6x.
Track 01:  488 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01:  489 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  490 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  491 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  492 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  493 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  494 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  495 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  496 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  497 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  498 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  499 of 1497 MB written (fifo 100%) [buf  98%]   2.7x.
Track 01:  500 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  501 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01:  502 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  503 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  504 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  505 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  506 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  507 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  508 of 1497 MB written (fifo  99%) [buf  99%]   2.6x.
Track 01:  509 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  510 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  511 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  512 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  513 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  514 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  515 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  516 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  517 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  518 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  519 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  520 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  521 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  522 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  523 of 1497 MB written (fifo 100%) [buf  97%]   2.6x.
Track 01:  524 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  525 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  526 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  527 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01:  528 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  529 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  530 of 1497 MB written (fifo 100%) [buf  99%]   2.8x.
Track 01:  531 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  532 of 1497 MB written (fifo 100%) [buf  99%]   2.8x.
Track 01:  533 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01:  534 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  535 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  536 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  537 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  538 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  539 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  540 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01:  541 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  542 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  543 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  544 of 1497 MB written (fifo 100%) [buf  98%]   2.7x.
Track 01:  545 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  546 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  547 of 1497 MB written (fifo 100%) [buf  97%]   2.6x.
Track 01:  548 of 1497 MB written (fifo 100%) [buf  99%]   2.8x.
Track 01:  549 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  550 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01:  551 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  552 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  553 of 1497 MB written (fifo  99%) [buf  99%]   2.6x.
Track 01:  554 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  555 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  556 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  557 of 1497 MB written (fifo  99%) [buf  99%]   2.6x.
Track 01:  558 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01:  559 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  560 of 1497 MB written (fifo 100%) [buf  98%]   2.6x.
Track 01:  561 of 1497 MB written (fifo 100%) [buf  99%]   2.8x.
Track 01:  562 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  563 of 1497 MB written (fifo 100%) [buf  99%]   2.8x.
Track 01:  564 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  565 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  566 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  567 of 1497 MB written (fifo 100%) [buf  98%]   2.7x.
Track 01:  568 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  569 of 1497 MB written (fifo 100%) [buf  96%]   2.6x.
Track 01:  570 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  571 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  572 of 1497 MB written (fifo 100%) [buf  98%]   2.6x.
Track 01:  573 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  574 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  575 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  576 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  577 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01:  578 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  579 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01:  580 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  581 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  582 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  583 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  584 of 1497 MB written (fifo  99%) [buf  99%]   2.6x.
Track 01:  585 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01:  586 of 1497 MB written (fifo  99%) [buf  99%]   2.6x.
Track 01:  587 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  588 of 1497 MB written (fifo  99%) [buf  99%]   2.6x.
Track 01:  589 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  590 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  591 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01:  592 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  593 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  594 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  595 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01:  596 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  597 of 1497 MB written (fifo 100%) [buf  98%]   2.6x.
Track 01:  598 of 1497 MB written (fifo 100%) [buf  99%]   2.8x.
Track 01:  599 of 1497 MB written (fifo 100%) [buf  98%]   2.6x.
Track 01:  600 of 1497 MB written (fifo 100%) [buf  99%]   2.8x.
Track 01:  601 of 1497 MB written (fifo 100%) [buf  92%]   2.6x.
Track 01:  602 of 1497 MB written (fifo 100%) [buf  98%]   2.8x.
Track 01:  603 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  604 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  605 of 1497 MB written (fifo 100%) [buf  98%]   2.6x.
Track 01:  606 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  607 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  608 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  609 of 1497 MB written (fifo  99%) [buf  99%]   2.6x.
Track 01:  610 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  611 of 1497 MB written (fifo 100%) [buf  96%]   2.6x.
Track 01:  612 of 1497 MB written (fifo 100%) [buf  99%]   2.8x.
Track 01:  613 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  614 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  615 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  616 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  617 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  618 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  619 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  620 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  621 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  622 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  623 of 1497 MB written (fifo 100%) [buf  98%]   2.7x.
Track 01:  624 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  625 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  626 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  627 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  628 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  629 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  630 of 1497 MB written (fifo 100%) [buf  97%]   2.6x.
Track 01:  631 of 1497 MB written (fifo 100%) [buf  99%]   2.8x.
Track 01:  632 of 1497 MB written (fifo  99%) [buf  99%]   2.6x.
Track 01:  633 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  634 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  635 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01:  636 of 1497 MB written (fifo  99%) [buf  99%]   2.6x.
Track 01:  637 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  638 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  639 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  640 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  641 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  642 of 1497 MB written (fifo  99%) [buf  99%]   2.6x.
Track 01:  643 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01:  644 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  645 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  646 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  647 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  648 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  649 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  650 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  651 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  652 of 1497 MB written (fifo  99%) [buf  99%]   2.6x.
Track 01:  653 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  654 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01:  655 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  656 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01:  657 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  658 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01:  659 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  660 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  661 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  662 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  663 of 1497 MB written (fifo  99%) [buf  99%]   2.6x.
Track 01:  664 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  665 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01:  666 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  667 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  668 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01:  669 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  670 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01:  671 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  672 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  673 of 1497 MB written (fifo  99%) [buf  99%]   2.6x.
Track 01:  674 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  675 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  676 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  677 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  678 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  679 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  680 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  681 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  682 of 1497 MB written (fifo 100%) [buf  96%]   2.7x.
Track 01:  683 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  684 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  685 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  686 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  687 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  688 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  689 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  690 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  691 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  692 of 1497 MB written (fifo  99%) [buf  99%]   2.6x.
Track 01:  693 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  694 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  695 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  696 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  697 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  698 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  699 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  700 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  701 of 1497 MB written (fifo 100%) [buf  98%]   2.7x.
Track 01:  702 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  703 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  704 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  705 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  706 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  707 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  708 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  709 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01:  710 of 1497 MB written (fifo  99%) [buf  99%]   2.6x.
Track 01:  711 of 1497 MB written (fifo 100%) [buf  97%]   2.6x.
Track 01:  712 of 1497 MB written (fifo 100%) [buf  98%]   2.6x.
Track 01:  713 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  714 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  715 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  716 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  717 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  718 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  719 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  720 of 1497 MB written (fifo 100%) [buf  98%]   2.7x.
Track 01:  721 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  722 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  723 of 1497 MB written (fifo 100%) [buf  95%]   2.6x.
Track 01:  724 of 1497 MB written (fifo  99%) [buf  99%]   2.8x.
Track 01:  725 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  726 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  727 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  728 of 1497 MB written (fifo 100%) [buf  98%]   2.7x.
Track 01:  729 of 1497 MB written (fifo 100%) [buf  98%]   2.6x.
Track 01:  730 of 1497 MB written (fifo 100%) [buf  99%]   2.8x.
Track 01:  731 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  732 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  733 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  734 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  735 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  736 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  737 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  738 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  739 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  740 of 1497 MB written (fifo  98%) [buf  99%]   2.7x.
Track 01:  741 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  742 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01:  743 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  744 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  745 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  746 of 1497 MB written (fifo 100%) [buf  97%]   2.6x.
Track 01:  747 of 1497 MB written (fifo 100%) [buf  99%]   2.8x.
Track 01:  748 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  749 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  750 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01:  751 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  752 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  753 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01:  754 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  755 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  756 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  757 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01:  758 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  759 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01:  760 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  761 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  762 of 1497 MB written (fifo  99%) [buf  99%]   2.6x.
Track 01:  763 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  764 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  765 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  766 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  767 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  768 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  769 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  770 of 1497 MB written (fifo 100%) [buf  97%]   2.6x.
Track 01:  771 of 1497 MB written (fifo 100%) [buf  96%]   2.6x.
Track 01:  772 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  773 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  774 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  775 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  776 of 1497 MB written (fifo  99%) [buf  99%]   2.6x.
Track 01:  777 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  778 of 1497 MB written (fifo 100%) [buf  99%]   2.8x.
Track 01:  779 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  780 of 1497 MB written (fifo 100%) [buf  99%]   2.8x.
Track 01:  781 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  782 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  783 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  784 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  785 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  786 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  787 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  788 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  789 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  790 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  791 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  792 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  793 of 1497 MB written (fifo 100%) [buf  98%]   2.6x.
Track 01:  794 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01:  795 of 1497 MB written (fifo  99%) [buf  99%]   2.6x.
Track 01:  796 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  797 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  798 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  799 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  800 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  801 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  802 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  803 of 1497 MB written (fifo  99%) [buf  99%]   2.6x.
Track 01:  804 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  805 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  806 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  807 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  808 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  809 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  810 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  811 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  812 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  813 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  814 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01:  815 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  816 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  817 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  818 of 1497 MB written (fifo  99%) [buf  99%]   2.6x.
Track 01:  819 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  820 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  821 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  822 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  823 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  824 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  825 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  826 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  827 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  828 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  829 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01:  830 of 1497 MB written (fifo  99%) [buf  99%]   2.6x.
Track 01:  831 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  832 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  833 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  834 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  835 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  836 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  837 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  838 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  839 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  840 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  841 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01:  842 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  843 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01:  844 of 1497 MB written (fifo  99%) [buf  97%]   2.7x.
Track 01:  845 of 1497 MB written (fifo 100%) [buf  98%]   2.7x.
Track 01:  846 of 1497 MB written (fifo  99%) [buf  99%]   2.8x.
Track 01:  847 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  848 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01:  849 of 1497 MB written (fifo  99%) [buf  99%]   2.6x.
Track 01:  850 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  851 of 1497 MB written (fifo  99%) [buf  99%]   2.6x.
Track 01:  852 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  853 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  854 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01:  855 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  856 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  857 of 1497 MB written (fifo  99%) [buf  99%]   2.6x.
Track 01:  858 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  859 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  860 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  861 of 1497 MB written (fifo  99%) [buf  97%]   2.6x.
Track 01:  862 of 1497 MB written (fifo 100%) [buf  99%]   2.8x.
Track 01:  863 of 1497 MB written (fifo  99%) [buf  99%]   2.6x.
Track 01:  864 of 1497 MB written (fifo 100%) [buf  90%]   2.5x.
Track 01:  865 of 1497 MB written (fifo 100%) [buf  99%]   2.8x.
Track 01:  866 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01:  867 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  868 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  869 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  870 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  871 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  872 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  873 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  874 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  875 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  876 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  877 of 1497 MB written (fifo 100%) [buf  98%]   2.7x.
Track 01:  878 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  879 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  880 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  881 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  882 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  883 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  884 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  885 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  886 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  887 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  888 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  889 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  890 of 1497 MB written (fifo 100%) [buf  98%]   2.6x.
Track 01:  891 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  892 of 1497 MB written (fifo  99%) [buf  99%]   2.6x.
Track 01:  893 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  894 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  895 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01:  896 of 1497 MB written (fifo  99%) [buf  99%]   2.6x.
Track 01:  897 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  898 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  899 of 1497 MB written (fifo 100%) [buf  96%]   2.6x.
Track 01:  900 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  901 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01:  902 of 1497 MB written (fifo 100%) [buf  99%]   2.8x.
Track 01:  903 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  904 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  905 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01:  906 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01:  907 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  908 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  909 of 1497 MB written (fifo  99%) [buf  99%]   2.6x.
Track 01:  910 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  911 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  912 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  913 of 1497 MB written (fifo 100%) [buf  98%]   2.6x.
Track 01:  914 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  915 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  916 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  917 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  918 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  919 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  920 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  921 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  922 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  923 of 1497 MB written (fifo 100%) [buf  98%]   2.6x.
Track 01:  924 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  925 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  926 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  927 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  928 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  929 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  930 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01:  931 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  932 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  933 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  934 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  935 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  936 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01:  937 of 1497 MB written (fifo 100%) [buf  98%]   2.7x.
Track 01:  938 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  939 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  940 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  941 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01:  942 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  943 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  944 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  945 of 1497 MB written (fifo 100%) [buf  95%]   2.6x.
Track 01:  946 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  947 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  948 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  949 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01:  950 of 1497 MB written (fifo 100%) [buf  98%]   2.6x.
Track 01:  951 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01:  952 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  953 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  954 of 1497 MB written (fifo  99%) [buf  99%]   2.6x.
Track 01:  955 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  956 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  957 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  958 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  959 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  960 of 1497 MB written (fifo 100%) [buf  98%]   2.6x.
Track 01:  961 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  962 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  963 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  964 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  965 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01:  966 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  967 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  968 of 1497 MB written (fifo 100%) [buf  99%]   2.8x.
Track 01:  969 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  970 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  971 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  972 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01:  973 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  974 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  975 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  976 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01:  977 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  978 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  979 of 1497 MB written (fifo  99%) [buf  99%]   2.6x.
Track 01:  980 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  981 of 1497 MB written (fifo 100%) [buf  97%]   2.6x.
Track 01:  982 of 1497 MB written (fifo  99%) [buf  99%]   2.8x.
Track 01:  983 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  984 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  985 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  986 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  987 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  988 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  989 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  990 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  991 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  992 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  993 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  994 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  995 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  996 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  997 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01:  998 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01:  999 of 1497 MB written (fifo 100%) [buf  99%]   2.8x.
Track 01: 1000 of 1497 MB written (fifo 100%) [buf  98%]   2.6x.
Track 01: 1001 of 1497 MB written (fifo 100%) [buf  99%]   2.8x.
Track 01: 1002 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1003 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1004 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1005 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1006 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1007 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1008 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1009 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1010 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1011 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01: 1012 of 1497 MB written (fifo 100%) [buf  98%]   2.6x.
Track 01: 1013 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1014 of 1497 MB written (fifo  99%) [buf  99%]   2.6x.
Track 01: 1015 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1016 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1017 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01: 1018 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1019 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1020 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1021 of 1497 MB written (fifo 100%) [buf  98%]   2.7x.
Track 01: 1022 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1023 of 1497 MB written (fifo 100%) [buf  98%]   2.6x.
Track 01: 1024 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1025 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01: 1026 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1027 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1028 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1029 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1030 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1031 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01: 1032 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1033 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1034 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1035 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1036 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1037 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1038 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1039 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1040 of 1497 MB written (fifo 100%) [buf  98%]   2.7x.
Track 01: 1041 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1042 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1043 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1044 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1045 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1046 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1047 of 1497 MB written (fifo 100%) [buf  98%]   2.6x.
Track 01: 1048 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01: 1049 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1050 of 1497 MB written (fifo 100%) [buf  98%]   2.7x.
Track 01: 1051 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1052 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01: 1053 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1054 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1055 of 1497 MB written (fifo  99%) [buf  99%]   2.6x.
Track 01: 1056 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1057 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01: 1058 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1059 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1060 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1061 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1062 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1063 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1064 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01: 1065 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1066 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1067 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1068 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1069 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1070 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1071 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1072 of 1497 MB written (fifo 100%) [buf  98%]   2.6x.
Track 01: 1073 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1074 of 1497 MB written (fifo  99%) [buf  99%]   2.6x.
Track 01: 1075 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1076 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1077 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1078 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1079 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1080 of 1497 MB written (fifo  99%) [buf  99%]   2.6x.
Track 01: 1081 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1082 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1083 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1084 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1085 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1086 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1087 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1088 of 1497 MB written (fifo 100%) [buf  99%]   2.8x.
Track 01: 1089 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1090 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1091 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1092 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1093 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1094 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1095 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1096 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1097 of 1497 MB written (fifo  99%) [buf  99%]   2.6x.
Track 01: 1098 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1099 of 1497 MB written (fifo  99%) [buf  99%]   2.6x.
Track 01: 1100 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1101 of 1497 MB written (fifo  99%) [buf  99%]   2.6x.
Track 01: 1102 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1103 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1104 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1105 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1106 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1107 of 1497 MB written (fifo 100%) [buf  98%]   2.6x.
Track 01: 1108 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1109 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1110 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1111 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1112 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1113 of 1497 MB written (fifo  99%) [buf  99%]   2.6x.
Track 01: 1114 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1115 of 1497 MB written (fifo  99%) [buf  99%]   2.6x.
Track 01: 1116 of 1497 MB written (fifo  98%) [buf  99%]   2.7x.
Track 01: 1117 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1118 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1119 of 1497 MB written (fifo 100%) [buf  98%]   2.7x.
Track 01: 1120 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01: 1121 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1122 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1123 of 1497 MB written (fifo 100%) [buf  94%]   2.6x.
Track 01: 1124 of 1497 MB written (fifo 100%) [buf  99%]   2.8x.
Track 01: 1125 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1126 of 1497 MB written (fifo  99%) [buf  99%]   2.6x.
Track 01: 1127 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1128 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1129 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1130 of 1497 MB written (fifo  99%) [buf  99%]   2.6x.
Track 01: 1131 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1132 of 1497 MB written (fifo  99%) [buf  99%]   2.6x.
Track 01: 1133 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1134 of 1497 MB written (fifo  99%) [buf  99%]   2.6x.
Track 01: 1135 of 1497 MB written (fifo 100%) [buf  97%]   2.7x.
Track 01: 1136 of 1497 MB written (fifo  99%) [buf  97%]   2.6x.
Track 01: 1137 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01: 1138 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1139 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1140 of 1497 MB written (fifo  99%) [buf  99%]   2.6x.
Track 01: 1141 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1142 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1143 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1144 of 1497 MB written (fifo 100%) [buf  97%]   2.6x.
Track 01: 1145 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1146 of 1497 MB written (fifo 100%) [buf  98%]   2.6x.
Track 01: 1147 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1148 of 1497 MB written (fifo 100%) [buf  98%]   2.6x.
Track 01: 1149 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1150 of 1497 MB written (fifo 100%) [buf  99%]   2.8x.
Track 01: 1151 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1152 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01: 1153 of 1497 MB written (fifo 100%) [buf  95%]   2.6x.
Track 01: 1154 of 1497 MB written (fifo 100%) [buf  99%]   2.9x.
Track 01: 1155 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01: 1156 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1157 of 1497 MB written (fifo 100%) [buf  98%]   2.6x.
Track 01: 1158 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1159 of 1497 MB written (fifo 100%) [buf  98%]   2.6x.
Track 01: 1160 of 1497 MB written (fifo  99%) [buf  99%]   2.8x.
Track 01: 1161 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1162 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1163 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1164 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1165 of 1497 MB written (fifo 100%) [buf  98%]   2.6x.
Track 01: 1166 of 1497 MB written (fifo 100%) [buf  98%]   2.7x.
Track 01: 1167 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1168 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1169 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1170 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1171 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1172 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1173 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1174 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1175 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1176 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1177 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1178 of 1497 MB written (fifo 100%) [buf  98%]   2.6x.
Track 01: 1179 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1180 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1181 of 1497 MB written (fifo 100%) [buf  99%]   2.8x.
Track 01: 1182 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1183 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1184 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1185 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01: 1186 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01: 1187 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1188 of 1497 MB written (fifo 100%) [buf  98%]   2.6x.
Track 01: 1189 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1190 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1191 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1192 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1193 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1194 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1195 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1196 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1197 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1198 of 1497 MB written (fifo  99%) [buf  99%]   2.6x.
Track 01: 1199 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1200 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1201 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1202 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1203 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1204 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1205 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1206 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1207 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1208 of 1497 MB written (fifo 100%) [buf  98%]   2.6x.
Track 01: 1209 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01: 1210 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1211 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1212 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01: 1213 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1214 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01: 1215 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1216 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1217 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1218 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1219 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1220 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1221 of 1497 MB written (fifo  99%) [buf  99%]   2.6x.
Track 01: 1222 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01: 1223 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1224 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1225 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1226 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1227 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1228 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01: 1229 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1230 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1231 of 1497 MB written (fifo  99%) [buf  97%]   2.6x.
Track 01: 1232 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1233 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1234 of 1497 MB written (fifo 100%) [buf  98%]   2.7x.
Track 01: 1235 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1236 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1237 of 1497 MB written (fifo  99%) [buf  99%]   2.6x.
Track 01: 1238 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1239 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1240 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1241 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1242 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1243 of 1497 MB written (fifo 100%) [buf  98%]   2.7x.
Track 01: 1244 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1245 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1246 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01: 1247 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01: 1248 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01: 1249 of 1497 MB written (fifo 100%) [buf  98%]   2.7x.
Track 01: 1250 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1251 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1252 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1253 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1254 of 1497 MB written (fifo  99%) [buf  99%]   2.6x.
Track 01: 1255 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1256 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1257 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01: 1258 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1259 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01: 1260 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1261 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1262 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1263 of 1497 MB written (fifo 100%) [buf  97%]   2.6x.
Track 01: 1264 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1265 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1266 of 1497 MB written (fifo 100%) [buf  98%]   2.6x.
Track 01: 1267 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1268 of 1497 MB written (fifo  99%) [buf  99%]   2.6x.
Track 01: 1269 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1270 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1271 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1272 of 1497 MB written (fifo 100%) [buf  92%]   2.4x.
Track 01: 1273 of 1497 MB written (fifo 100%) [buf  99%]   2.8x.
Track 01: 1274 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01: 1275 of 1497 MB written (fifo  99%) [buf  98%]   2.6x.
Track 01: 1276 of 1497 MB written (fifo 100%) [buf  98%]   2.8x.
Track 01: 1277 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1278 of 1497 MB written (fifo 100%) [buf  98%]   2.7x.
Track 01: 1279 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1280 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1281 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1282 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1283 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1284 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1285 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1286 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1287 of 1497 MB written (fifo 100%) [buf  96%]   2.6x.
Track 01: 1288 of 1497 MB written (fifo 100%) [buf  99%]   2.8x.
Track 01: 1289 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1290 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1291 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1292 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01: 1293 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1294 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1295 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1296 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1297 of 1497 MB written (fifo  99%) [buf  99%]   2.6x.
Track 01: 1298 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1299 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1300 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1301 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1302 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01: 1303 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1304 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1305 of 1497 MB written (fifo 100%) [buf  99%]   2.8x.
Track 01: 1306 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1307 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1308 of 1497 MB written (fifo 100%) [buf  98%]   2.6x.
Track 01: 1309 of 1497 MB written (fifo  99%) [buf  99%]   2.8x.
Track 01: 1310 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1311 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1312 of 1497 MB written (fifo 100%) [buf  96%]   2.6x.
Track 01: 1313 of 1497 MB written (fifo  99%) [buf  99%]   2.8x.
Track 01: 1314 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1315 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1316 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1317 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1318 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1319 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1320 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1321 of 1497 MB written (fifo 100%) [buf  95%]   2.6x.
Track 01: 1322 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1323 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1324 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1325 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1326 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1327 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01: 1328 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1329 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1330 of 1497 MB written (fifo  99%) [buf  99%]   2.6x.
Track 01: 1331 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1332 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1333 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1334 of 1497 MB written (fifo 100%) [buf  98%]   2.6x.
Track 01: 1335 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1336 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1337 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01: 1338 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1339 of 1497 MB written (fifo 100%) [buf  98%]   2.6x.
Track 01: 1340 of 1497 MB written (fifo  99%) [buf  99%]   2.8x.
Track 01: 1341 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01: 1342 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1343 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1344 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01: 1345 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1346 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1347 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1348 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1349 of 1497 MB written (fifo  99%) [buf  99%]   2.6x.
Track 01: 1350 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1351 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1352 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01: 1353 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1354 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01: 1355 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1356 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1357 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1358 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1359 of 1497 MB written (fifo  99%) [buf  99%]   2.6x.
Track 01: 1360 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1361 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1362 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01: 1363 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1364 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1365 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1366 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1367 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1368 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1369 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01: 1370 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01: 1371 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1372 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1373 of 1497 MB written (fifo 100%) [buf  97%]   2.7x.
Track 01: 1374 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1375 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1376 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1377 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1378 of 1497 MB written (fifo 100%) [buf  98%]   2.6x.
Track 01: 1379 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1380 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1381 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1382 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1383 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1384 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1385 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1386 of 1497 MB written (fifo 100%) [buf  98%]   2.6x.
Track 01: 1387 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1388 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1389 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1390 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1391 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1392 of 1497 MB written (fifo  99%) [buf  99%]   2.6x.
Track 01: 1393 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1394 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1395 of 1497 MB written (fifo 100%) [buf  98%]   2.7x.
Track 01: 1396 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1397 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1398 of 1497 MB written (fifo  99%) [buf  98%]   2.7x.
Track 01: 1399 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1400 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1401 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01: 1402 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1403 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1404 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1405 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1406 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01: 1407 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1408 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1409 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1410 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1411 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1412 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01: 1413 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1414 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1415 of 1497 MB written (fifo  99%) [buf  99%]   2.6x.
Track 01: 1416 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1417 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1418 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01: 1419 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1420 of 1497 MB written (fifo  99%) [buf  98%]   2.7x.
Track 01: 1421 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1422 of 1497 MB written (fifo 100%) [buf  97%]   2.6x.
Track 01: 1423 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1424 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1425 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1426 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01: 1427 of 1497 MB written (fifo  99%) [buf  99%]   2.6x.
Track 01: 1428 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1429 of 1497 MB written (fifo 100%) [buf  98%]   2.7x.
Track 01: 1430 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1431 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1432 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01: 1433 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1434 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1435 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1436 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1437 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1438 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1439 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1440 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1441 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1442 of 1497 MB written (fifo 100%) [buf  98%]   2.6x.
Track 01: 1443 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1444 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1445 of 1497 MB written (fifo 100%) [buf  98%]   2.7x.
Track 01: 1446 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1447 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1448 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1449 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1450 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1451 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01: 1452 of 1497 MB written (fifo  99%) [buf  99%]   2.6x.
Track 01: 1453 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1454 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1455 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1456 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1457 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1458 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1459 of 1497 MB written (fifo 100%) [buf  98%]   2.7x.
Track 01: 1460 of 1497 MB written (fifo 100%) [buf  99%]   2.8x.
Track 01: 1461 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1462 of 1497 MB written (fifo 100%) [buf  98%]   2.7x.
Track 01: 1463 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1464 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1465 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01: 1466 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1467 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1468 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1469 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1470 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1471 of 1497 MB written (fifo  99%) [buf  99%]   2.6x.
Track 01: 1472 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1473 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1474 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1475 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1476 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1477 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1478 of 1497 MB written (fifo  99%) [buf  99%]   2.7x.
Track 01: 1479 of 1497 MB written (fifo  99%) [buf  99%]   2.6x.
Track 01: 1480 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1481 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1482 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1483 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1484 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1485 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1486 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1487 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1488 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1489 of 1497 MB written (fifo 100%) [buf  99%]   2.6x.
Track 01: 1490 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1491 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1492 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1493 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1494 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1495 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1496 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: 1497 of 1497 MB written (fifo 100%) [buf  99%]   2.7x.
Track 01: Total bytes read/written: 1569816576/1569816576 (766512 sectors).
Writing  time:  470.245s
Average write speed   2.6x.
Min drive buffer fill was 90%
Fixating...
Fixating time:   51.543s
/usr/bin/wodim: fifo had 24727 puts and 24727 gets.
/usr/bin/wodim: fifo was 0 times empty and 20532 times full, min fill was 97%.

cdrecord command:
-----------------------
/usr/bin/wodim -v gracetime=2 dev=/dev/sr0 speed=2 -sao driveropts=burnfree -data -tsize=766512s -


FIXED

---

### Post by Grandma_DOG on 2010-03-13
I can confirm my problem is Karmic upgrade issue.  
I upgraded yesterday and now I can't burn DVDs like I could last week. Just hangs.
Has someone listed it as an official upgrade bug yet?

---

### Post by eclebowsky on 2010-03-14
I have the same problem with Ubuntu 9.10 64bit, Kernel 2.6.31-20. 
Burner is HL-DT-ST DVD+/-RW GS20N on a brand new Dell notebook. With Win7 (in dual boot) I can burn flawless CD/DVD.
Brasero, k3b, gnomebaker, nero-linux all FAIL.
I also noticed that during the tentative writing the icon "Empty CD/DVD" disappears from the Desktop. (why??)

Hope someone can help fix this issue.

---

### Post by emptythevoid on 2010-03-18
Same problem, same drive:  HL-DT-ST DVD+-RW GS20N on a Dell Precision M6500, clean install of Ubuntu 32-bit

---

### Post by Glugglug on 2010-03-31
Its not a bad disk or hardware fault   same machine running both 9.04 and 9.10 .

9.04 works  9.10 doesn't.


on another machine  same  problem  stuck at preparing to write   

9.10 doesn't work   Mint 8 works  and mint uses brasero as well.

---

### Post by Munschy_00 on 2012-08-03
sudo apt-get install libbrasero-media3-dev


on ubuntu 12.04

brasero doesn't come dvd ready
worked for me

---

### Post by wildmanne39 on 2012-08-03
Thanks for sharing and please do not post in threads that have not had activity for a year or longer, since this is an old thread it has been closed.

---

