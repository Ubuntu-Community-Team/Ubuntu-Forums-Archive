---
title: "Problem burning iso"
date: 2010-08-10
forum: General Help
---

### Post by Austin25 on 2010-08-10
I'm trying to burn a live iso with Brasero, and it fails before it really burns anything. If I put  it back in after it ejects it, it still says it's blank. When it crashes, it asked me to save the log:
```
Checking session consistency (brasero_burn_check_session_consistency brasero-burn.c:1741)
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_set_output_size_for_current_track
BraseroBurnURI stopping
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_session_output_size
BraseroBurnURI output set (IMAGE) image = /tmp/brasero_tmp_5TGLHV.bin toc = none
BraseroBurnURI called brasero_job_get_session_output_size
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
BraseroLocalTrack output set (IMAGE) image = /tmp/brasero_tmp_8NHLHV.bin toc = none
BraseroLocalTrack called brasero_job_get_session_output_size
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_current_track
BraseroLocalTrack no remote URIs
BraseroLocalTrack stopping
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
    speed=24
    fs=16m
    -data
    -nopad
    /home/austin/Downloads/ubuntu-10.04-desktop-i386.iso
BraseroWodim Launching command
BraseroWodim called brasero_job_get_fd_out
BraseroWodim called brasero_job_get_fd_in
BraseroWodim called brasero_job_get_fd_out
BraseroWodim stderr: wodim: No write mode specified.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: Assuming -tao mode.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: Future versions of wodim may have different drive dependent defaults.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: scsidev: '/dev/sr0'
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: devname: '/dev/sr0'
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: scsibus: -2 target: -2 lun: -2
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Linux sg driver version: 3.5.27
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Wodim version: 1.1.10
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: SCSI buffer size: 64512
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: communication breaks or freezes immediately after that.
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: TOC Type: 1 = CD-ROM
BraseroWodim stdout: Device type    : Removable CD-ROM
BraseroWodim stdout: Version        : 5
BraseroWodim stdout: Response Format: 2
BraseroWodim stdout: Capabilities   : 
BraseroWodim stdout: Vendor_info    : 'TSSTcorp'
BraseroWodim stdout: Identification : 'CDDVDW TS-L633M '
BraseroWodim stdout: Revision       : '0200'
BraseroWodim stdout: Device seems to be: Generic mmc2 DVD-R/DVD-RW.
BraseroWodim stdout: Current: 0x0009 (CD-R)
BraseroWodim stdout: Profile: 0x0015 (DVD-R/DL sequential recording) 
BraseroWodim stdout: Profile: 0x0016 (DVD-R/DL layer jump recording) 
BraseroWodim stdout: Profile: 0x002B (DVD+R/DL) 
BraseroWodim stdout: Profile: 0x001B (DVD+R) 
BraseroWodim stdout: Profile: 0x001A (DVD+RW) 
BraseroWodim stdout: Profile: 0x0014 (DVD-RW sequential recording) 
BraseroWodim stdout: Profile: 0x0013 (DVD-RW restricted overwrite) 
BraseroWodim stdout: Profile: 0x0012 (DVD-RAM) 
BraseroWodim stdout: Profile: 0x0011 (DVD-R sequential recording) 
BraseroWodim stdout: Profile: 0x0010 (DVD-ROM) 
BraseroWodim stdout: Profile: 0x000A (CD-RW) 
BraseroWodim stdout: Profile: 0x0009 (CD-R) (current)
BraseroWodim stdout: Profile: 0x0008 (CD-ROM) 
BraseroWodim stdout: Profile: 0x0002 (Removable disk) 
BraseroWodim stdout: Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
BraseroWodim stdout: Driver flags   : MMC-3 SWABAUDIO BURNFREE 
BraseroWodim stdout: Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
BraseroWodim stdout: Drive buf size : 1962752 = 1916 KB
BraseroWodim stdout: FIFO size      : 16777216 = 16384 KB
BraseroWodim stderr: Speed set to 4234 KB/s
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Track 01: data   699 MB        
BraseroWodim stdout: Total size:      803 MB (79:34.89) = 358117 sectors
BraseroWodim stdout: Lout start:      803 MB (79:36/67) = 358117 sectors
BraseroWodim stdout: Current Secsize: 2048
BraseroWodim stdout: ATIP info from disk:
BraseroWodim stdout:   Indicated writing power: 5
BraseroWodim stdout:   Is unrestricted
BraseroWodim stdout:   Is not erasable
BraseroWodim stdout:   Disk sub type: Medium Type A, high Beta category (A+) (3)
BraseroWodim stdout:   ATIP start of lead in:  -11839 (97:24/11)
BraseroWodim stdout:   ATIP start of lead out: 359849 (79:59/74)
BraseroWodim stdout: Disk type:    Long strategy type (Cyanine, AZO or similar)
BraseroWodim stdout: Manuf. index: 24
BraseroWodim stdout: Manufacturer: SONY Corporation
BraseroWodim stdout: Blocks total: 359849 Blocks current: 359849 Blocks remaining: 1732
BraseroWodim stdout: Starting to write CD/DVD at speed  24.0 in real TAO mode for single session.
BraseroWodim stdout: Last chance to quit, starting real write in    4 seconds.
BraseroWodim called brasero_job_set_dangerous
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout:    3 seconds.
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout:    2 seconds.
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout:    1 seconds.   0 seconds. Operation starts.
BraseroWodim stdout: Waiting for reader process to fill input buffer ... input buffer ready.
BraseroWodim stdout: Performing OPC...
BraseroWodim stderr: Errno: 5 (Input/output error), send opc scsi sendcmd: no error
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: CDB:  54 01 00 00 00 00 00 00 00 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Writing  time:   63.163s
BraseroWodim stderr: status: 0x2 (CHECK CONDITION)
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: BURN-Free was never needed.
BraseroWodim stderr: Sense Bytes: 72 0B 00 00 00 00 00 0E 09 0C 00 00 00 03 00 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Key: 0x0 No Additional Sense, Segment 11
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Code: 0x00 Qual 0x03 (setmark detected) Fru 0x0
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense flags: Blk 0 (not valid) 
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: cmd finished after 63.123s timeout 60s
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: OPC failed.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: fifo had 255 puts and 0 gets.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: fifo was 0 times empty and 0 times full, min fill was 100%.
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: HUP
BraseroWodim stderr: HUP
BraseroWodim process finished with status 255
BraseroWodim called brasero_job_error
BraseroWodim finished with an error
BraseroWodim asked to stop because of an error
    error        = 0
    message    = "no message"
BraseroWodim stopping
Session error : unknown (brasero_burn_record brasero-burn.c:2842)
```Any ideas?

---

### Post by Quackers on 2010-08-10
Are you selecting the "Burn Image" option?

---

### Post by Austin25 on 2010-08-10
yes.

---

### Post by yunone on 2010-08-10
have you restarted?
tried another blank disc?


just the basics

---

### Post by Austin25 on 2010-08-10
yes, I even tried a different program, and it gave the same error.
Oh, and yes, it was the right kind of drive.

---

### Post by Austin25 on 2010-08-10
Ok, I tried burn and it didn't work either.

---

### Post by bobcollard on 2010-08-10
Try unetbooten with a thumb drive.

---

### Post by Austin25 on 2010-08-10
I would use unetbootin, but it's for a computer with older bios.
It seems to fail at OPC.
Do you think I could use unetbootin on a cd?

---

### Post by -kg- on 2010-08-10
I have heard that some people have been having trouble with burning DVDs with Brasero lately.  I almost never use Brasero for anything...I just heard.

Have you tried using K3B?  K3B always works flawlessly for me.

---

### Post by bobcollard on 2010-08-10
> **Austin25 said:**
> I would use unetbootin, but it's for a computer with older bios.
It seems to fail at OPC.
Do you think I could use unetbootin on a cd?
Unetbooten, up to date, comes in many different systems including Windows.  It is basically used on USB Drives and I have used it extensively without any bugs.  Home page here:
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by Austin25 on 2010-08-10
I know, I use unetbootin all the time, and I guess it doesn't work on cds with the "show all drives" option.
I'll try K3B.

---

### Post by Austin25 on 2010-08-10
K3B failed.
that means:
4 programs
3 cds
an update
a restart.

---

### Post by bobcollard on 2010-08-10
> **Austin25 said:**
> K#B failed.
that means:
4 programs
3 cds
an update
a restart.
An Alternative from the Home page:.
> UNetbootin can create a bootable Live USB drive, [COLOR=Red]or it can make a  "frugal install" on your local hard disk[/COLOR] if you don't have a USB drive.

---

### Post by Austin25 on 2010-08-10
> **bobcollard said:**
> An Alternative from the Home page:.
Yes, I know, but I'm using that now, and I use Ubuntu a lot, so I'd like to have a CD.

I think I know the answers to these, but I'd like to get them out of the way because I might be wrong, and it could be the problem:
Do CD-Rs expire, or any other way a CD could go bad over time before being used?
Can I burn CDs in a DVD burner.
Are there CDs (possibly the ones I have) that only work for audio?
How much tolerance is there for a CD being offset?
How is Sony's reputation for CDs?
Is there any way to test if it's my drive that's broken?

---

### Post by bobcollard on 2010-08-10
> **Austin25 said:**
> Yes, I know, but I'm using that now, and I use Ubuntu a lot, so I'd like to have a CD.

I think I know the answers to these, but I'd like to get them out of the way because I might be wrong, and it could be the problem:
Do CD-Rs expire, or any other way a CD could go bad over time before being used?
Can I burn CDs in a DVD burner.
Are there CDs (possibly the ones I have) that only work for audio?
How much tolerance is there for a CD being offset?
How is Sony's reputation for CDs?
Is there any way to test if it's my drive that's broken?
1. they do not Expire.
2. yes
3. data is data, as long as there is enough room on the disk it should work
4. the head should pick up where it begins.
5. Since they helped invent then, go figure.
6. yes, a system check might do it and there are applications but I don't know the names.

---

### Post by Austin25 on 2010-08-10
System check?

---

### Post by bobcollard on 2010-08-10
> **Austin25 said:**
> System check?
Depends on your System and applications.Systemtap, system tools etc.

---

### Post by Austin25 on 2010-08-10
Well, I put in a DVD, and although it was not able to read the codec,(curse proprietary encrypted dvds)  it was able to copy the raw files off of it.

---

### Post by bobcollard on 2010-08-10
> **Austin25 said:**
> Well, I put in a DVD, and although it was not able to read the codec,(curse proprietary encrypted dvds)  it was able to copy the raw files off of it.
Install the libdvdcss2 using Terminal for the main codec or install gnome restricted  packages through Synaptic Package Manager.

---

### Post by Austin25 on 2010-08-10
nah, all I did that for was to test the drives functionality, and now I'm pretty sure it works.
I'm going to try reinstalling Brasero through synaptic, as well as anything that might help.

And that didn't help.

---

### Post by Austin25 on 2010-08-10
Well it won't burn Audio either.

---

### Post by bobcollard on 2010-08-10
> **Austin25 said:**
> nah, all I did that for was to test the drives functionality, and now I'm pretty sure it works.
I'm going to try reinstalling Brasero through synaptic, as well as anything that might help.

And that didn't help.
Reading and writing are two different things, good luck.

---

### Post by Austin25 on 2010-08-10
yeah, I'm thinking there is probably something's wrong with writing. I don't know if it's drivers, hardware or the CDs.

---

### Post by bobcollard on 2010-08-10
> **Austin25 said:**
> yeah, I'm thinking there is probably something's wrong with writing. I don't know if it's drivers, hardware or the CDs.
Have you tried varying the speed of the burn?  3x is best.

---

### Post by Austin25 on 2010-08-10
It seems the slowest brasero will let me go is 10x.

---

### Post by Austin25 on 2010-08-10
Here's the output from burn:
```
austin@austin-laptop0:~/Downloads$ sudo burn -I -n ubuntu-10.04-desktop-i386.isoBurn v.0.4.5  Written by Gaetano Paolone.
Burn until recorded, now!
This software comes with absolutely no warranty! Use at your own risk!
Burn is free software.
See software updates at <URL:http://www.bigpaul.org/burn/>.

Iso-CD...


To be burned:              699 Mb
Disk space needed:          0 Mb
Media capacity:          700 Mb

Do you want to see image's contents before proceeding (yes/no) [yes]? yes


Please choose:

1. Print every file with path
2. Print directory tree structure
3. Ok, finished... Let's burn
> ^CTraceback (most recent call last):
  File "<string>", line 1, in <module>
  File "/usr/lib/pymodules/python2.6/burnlib/burn.py", line 809, in main
    cdrom.iso.ask_mount(options.iso_name)
  File "/usr/lib/pymodules/python2.6/burnlib/burn.py", line 277, in ask_mount
    self.mount(image)
  File "/usr/lib/pymodules/python2.6/burnlib/burn.py", line 295, in mount
    self.ask_after_mount(self.mount_dir)
  File "/usr/lib/pymodules/python2.6/burnlib/burn.py", line 310, in ask_after_mount
    mount_choice = raw_input(prompt)
KeyboardInterrupt
austin@austin-laptop0:~/Downloads$ sudo burn -I -n ubuntu-10.04-desktop-i386.isoBurn v.0.4.5  Written by Gaetano Paolone.
Burn until recorded, now!
This software comes with absolutely no warranty! Use at your own risk!
Burn is free software.
See software updates at <URL:http://www.bigpaul.org/burn/>.

Iso-CD...


To be burned:              699 Mb
Disk space needed:          0 Mb
Media capacity:          700 Mb

Do you want to see image's contents before proceeding (yes/no) [yes]? no

Press a key to begin recording...
Please wait...
/usr/bin/wodim: No write mode specified.
/usr/bin/wodim: Assuming -tao mode.
/usr/bin/wodim: Future versions of wodim may have different drive dependent defaults.
TOC Type: 1 = CD-ROM
scsidev: '/dev/cdrom'
devname: '/dev/cdrom'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.10
Driveropts: 'burnfree'
SCSI buffer size: 64512
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'TSSTcorp'
Identification : 'CDDVDW TS-L633M '
Revision       : '0200'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0009 (CD-R)
Profile: 0x0015 (DVD-R/DL sequential recording) 
Profile: 0x0016 (DVD-R/DL layer jump recording) 
Profile: 0x002B (DVD+R/DL) 
Profile: 0x001B (DVD+R) 
Profile: 0x001A (DVD+RW) 
Profile: 0x0014 (DVD-RW sequential recording) 
Profile: 0x0013 (DVD-RW restricted overwrite) 
Profile: 0x0012 (DVD-RAM) 
Profile: 0x0011 (DVD-R sequential recording) 
Profile: 0x0010 (DVD-ROM) 
Profile: 0x000A (CD-RW) 
Profile: 0x0009 (CD-R) (current)
Profile: 0x0008 (CD-ROM) 
Profile: 0x0002 (Removable disk) 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1962752 = 1916 KB
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
FIFO size      : 12582912 = 12288 KB
Track 01: data   699 MB         padsize:   30 KB
Total size:      803 MB (79:35.09) = 358132 sectors
Lout start:      803 MB (79:37/07) = 358132 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 5
  Is unrestricted
  Is not erasable
  Disk sub type: Medium Type A, high Beta category (A+) (3)
  ATIP start of lead in:  -11839 (97:24/11)
  ATIP start of lead out: 359849 (79:59/74)
Disk type:    Long strategy type (Cyanine, AZO or similar)
Manuf. index: 24
Manufacturer: SONY Corporation
Blocks total: 359849 Blocks current: 359849 Blocks remaining: 1717
Speed set to 1764 KB/s
Starting to write CD/DVD at speed  10.0 in real TAO mode for single session.
Last chance to quit, starting real write in    0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Errno: 5 (Input/output error), send opc scsi sendcmd: no error
CDB:  54 01 00 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 72 0B 00 00 00 00 00 0E 09 0C 00 00 00 03 00 00
Sense Key: 0x0 No Additional Sense, Segment 11
Sense Code: 0x00 Qual 0x03 (setmark detected) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 62.411s timeout 60s
/usr/bin/wodim: OPC failed.
Writing  time:   62.451s
BURN-Free was never needed.
/usr/bin/wodim: fifo had 191 puts and 0 gets.
/usr/bin/wodim: fifo was 0 times empty and 0 times full, min fill was 100%.

ubuntu-10.04-desktop-i386.iso  is the image file created...
Do you want me to remove it (yes/no) [no]? no
Do you want to use this image to make another copy now? (yes/no) [no]? no

```

---

### Post by bobcollard on 2010-08-10
> **Austin25 said:**
> It seems the slowest brasero will let me go is 10x.
Probably for CDs, the last thing I burned I used a DVD-RW, like I said I use USB Thumb drives to save money in the long run.  I have only been using Sabayon for a few weeks, before that it was all Ubuntu of one flavor or other.  Well, sorry I could not help further.

---

### Post by bobcollard on 2010-08-10
699MB ???  You are pushing the envelope and should use a DVD instead.

---

### Post by Austin25 on 2010-08-10
I don't have a dvd, I only have CDs, but I could use the other iso I need burned, which happens to be smaller.

---

### Post by bobcollard on 2010-08-10
> **Austin25 said:**
> I don't have a dvd, I only have CDs, but I could use the other iso I need burned, which happens to be smaller.
Remember your list?  
3. data is data, as long as there is enough room on the disk it should work
Try the smaller ISO

---

### Post by Austin25 on 2010-08-10
Still didn't work. I don't think this is a user error anymore.

---

### Post by Austin25 on 2010-08-11
Maybe this is a conspiracy so we have to BUY the live CDs.
Well, I tried it again, and I KNOW it wrote something, as I can see it on it, but I think something went wrong as it finalized. I hope this works eventually, but for now, I guess I don't have much of a choice over unetbootin.

---

### Post by Austin25 on 2010-10-10
I have deduce that it is a software problem. I can burn a CD if I boot from an Ubuntu live USB drive.
edit: Sorry, no I can't. I hope it's the CDs I'm using.

---

