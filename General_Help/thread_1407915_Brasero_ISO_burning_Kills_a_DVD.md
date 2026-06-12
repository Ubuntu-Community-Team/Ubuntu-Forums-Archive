---
title: "Brasero ISO burning: Kills a DVD"
date: 2010-02-15
forum: General Help
---

### Post by Steel-Bunz on 2010-02-15
I tried burning Kubuntu 10.04 Alpha 2 ISO image into a DVD (because it was too big for a CD :(). "A writing error occured" and the DVD is dead now. Could somebody through some light on this issue? I have burned CDs in my HP laptop successfully in the past...

Here is the log... And Thank you...

```
Checking session consistency (brasero_burn_check_session_consistency burn.c:1905)
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_set_output_size_for_current_track
BraseroBurnURI stopping
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_session_output_size
BraseroBurnURI output set (IMAGE) image = /tmp/brasero_tmp_JZFV7U.bin toc = none
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_current_track
BraseroBurnURI called brasero_job_get_input_type
BraseroBurnURI burn:// URI found burn:///lucid-desktop-i386.iso
BraseroBurnURI called brasero_job_set_current_action
BraseroBurnURI called brasero_job_get_current_track
BraseroBurnURI called brasero_job_add_track
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI Finished track successfully
BraseroBurnURI stopping
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
	speed=8
	driveropts=burnfree
	-dao
	fs=16m
	-data
	-nopad
	/home/gosa/Desktop/lucid-desktop-i386.iso
BraseroWodim Launching command
BraseroWodim called brasero_job_get_fd_out
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
BraseroWodim stdout: Vendor_info    : 'Slimtype'
BraseroWodim stdout: Identification : 'DVD A  DS8A1H   '
BraseroWodim stdout: Revision       : 'WH66'
BraseroWodim stdout: Device seems to be: Generic mmc2 DVD-R/DVD-RW.
BraseroWodim stdout: Current: 0x0011 (DVD-R sequential recording)
BraseroWodim stdout: Profile: 0x002B (DVD+R/DL) 
BraseroWodim stdout: Profile: 0x001B (DVD+R) 
BraseroWodim stdout: Profile: 0x001A (DVD+RW) 
BraseroWodim stdout: Profile: 0x0016 (DVD-R/DL layer jump recording) 
BraseroWodim stdout: Profile: 0x0015 (DVD-R/DL sequential recording) 
BraseroWodim stdout: Profile: 0x0014 (DVD-RW sequential recording) 
BraseroWodim stdout: Profile: 0x0013 (DVD-RW restricted overwrite) 
BraseroWodim stdout: Profile: 0x0012 (DVD-RAM) 
BraseroWodim stdout: Profile: 0x0011 (DVD-R sequential recording) (current)
BraseroWodim stdout: Profile: 0x0010 (DVD-ROM) 
BraseroWodim stdout: Profile: 0x000A (CD-RW) 
BraseroWodim stdout: Profile: 0x0009 (CD-R) 
BraseroWodim stdout: Profile: 0x0008 (CD-ROM) 
BraseroWodim stdout: Profile: 0x0002 (Removable disk) 
BraseroWodim stdout: Using generic SCSI-3/mmc DVD-R(W) driver (mmc_mdvd).
BraseroWodim stdout: Driver flags   : SWABAUDIO BURNFREE 
BraseroWodim stdout: Supported modes: PACKET SAO
BraseroWodim stdout: Drive buf size : 1182464 = 1154 KB
BraseroWodim stdout: FIFO size      : 16777216 = 16384 KB
BraseroWodim stderr: Speed set to 11080 KB/s
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Track 01: data   715 MB        
BraseroWodim stdout: Total size:      821 MB (81:26.01) = 366451 sectors
BraseroWodim stdout: Lout start:      822 MB (81:28/01) = 366451 sectors
BraseroWodim stdout: Current Secsize: 2048
BraseroWodim stdout: HINT: use dvd+rw-mediainfo from dvd+rw-tools for information extraction.
BraseroWodim stdout: Blocks total: 2298496 Blocks current: 2298496 Blocks remaining: 1932045
BraseroWodim stdout: Starting to write CD/DVD at speed   8.0 in real SAO mode for single session.
BraseroWodim stdout: Last chance to quit, starting real write in    4 seconds.
BraseroWodim called brasero_job_set_dangerous
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout:    3 seconds.
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout:    2 seconds.
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout:    1 seconds.   0 seconds. Operation starts.
BraseroWodim stdout: Waiting for reader process to fill input buffer ... input buffer ready.
BraseroWodim stdout: Performing OPC...
BraseroWodim stdout: Sending CUE sheet...
BraseroWodim called brasero_job_get_input_type
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Starting new track at sector: 0
BraseroWodim stdout: 
BraseroWodim stderr: Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: CDB:  2A 00 00 00 00 1F 00 00 1F 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: status: 0x2 (CHECK CONDITION)
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Bytes: 71 00 03 00 00 00 00 0A 00 00 00 00 0C 00 00 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Key: 0x3 Medium Error, deferred error, Segment 0
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Code: 0x0C Qual 0x00 (write error) Fru 0x0
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense flags: Blk 0 (not valid) 
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: cmd finished after 0.312s timeout 200s
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: A write error occured.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: Please properly read the error message above.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Errno: 5 (Input/output error), test unit ready scsi sendcmd: no error
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Track 01:    0 of  715 MB written.
BraseroWodim stderr: CDB:  00 00 00 00 00 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: write track data: error after 63488 bytes
BraseroWodim stderr: status: 0x2 (CHECK CONDITION)
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Writing  time:  263.217s
BraseroWodim stderr: Sense Bytes: 70 00 02 00 00 00 00 0A 00 00 00 00 04 08 00 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Average write speed   3.5x.
BraseroWodim stderr: Sense Key: 0x2 Not Ready, Segment 0
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Fixating...
BraseroWodim called brasero_job_set_current_action
BraseroWodim stderr: Sense Code: 0x04 Qual 0x08 (logical unit not ready, long write in progress) Fru 0x0
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense flags: Blk 0 (not valid) 
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: cmd finished after 0.568s timeout 200s
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Errno: 5 (Input/output error), flush cache scsi sendcmd: no error
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Trouble flushing the cache
BraseroWodim stderr: CDB:  35 00 00 00 00 00 00 00 00 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Fixating time:    0.653s
BraseroWodim stderr: status: 0x2 (CHECK CONDITION)
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Bytes: 70 00 02 00 00 00 00 0A 00 00 00 00 04 08 00 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Key: 0x2 Not Ready, Segment 0
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Code: 0x04 Qual 0x08 (logical unit not ready, long write in progress) Fru 0x0
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense flags: Blk 0 (not valid) 
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: cmd finished after 0.653s timeout 200s
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: Cannot fixate disk.
BraseroWodim called brasero_job_get_flags
BraseroWodim called brasero_job_error
BraseroWodim finished with an error
BraseroWodim asked to stop because of an error
	error		= 12
	message	= "An error occured while writing to disc"
BraseroWodim stopping
BraseroWodim got killed
Session error : An error occured while writing to disc (brasero_burn_record burn.c:2599)
```

---

### Post by switch10 on 2010-02-15
I have to burn DVD's at the lowest possible speed with my laptop burner, or I will get that error.

Try lowering the speed.

---

### Post by Steel-Bunz on 2010-02-15
Thank you Switch,
I am going to use it as a last option. Until I clearly understand what the bug is, I don't want to waste another DVD... I am still searching through various forums and zeroing in on the error "wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.scsidev: '/dev/sr0'". Some forums have suggested running the program as root, but, I am not sure yet.

There was a page in Ubuntu archives where someone said it is actually a feature. :D Wish I can talk to someone who coded wodim :-)

---

### Post by Steel-Bunz on 2010-02-16
I am almost convinced that wodim is the culprit. There are many bug reports and discussions in Gnome, Fedora, ArchLinux and other forums. But no solutions so far.
 
Could someone please suggest a DVD burning application that doesn't use wodim in the background?

---

### Post by Steel-Bunz on 2010-02-17
Bump...
 
Did anyone successfully manage to burn an ISO image to DVD using any of the DVD burners? Please let me know the applications to try out. Both k3b and Brasero failed for me.

---

### Post by mk1w86 on 2010-02-17
It might not fix your problem but if you want to try another application have a look at GnomeBaker.

---

### Post by arthur.afarias on 2010-04-04
I'm having the same problem as you [Steel-Bunz]("http://ubuntuforums.org/member.php?u=923267"). I tried burn my image in GnomeBaker and I'm still getting error messages:

> 
[U][U]Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
CDB:  2A 00 00 02 63 A5 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: F1 00 04 00 02 61 37 0A 00 32 00 10 03 01 00 00
Sense Key: 0x4 Hardware Error, deferred error, Segment 0
Sense Code: 0x03 Qual 0x01 (no write current) Fru 0x0
Sense flags: Blk 155959 (valid) 
cmd finished after 0.045s timeout 40s
wodim: A write error occured.
wodim: Please properly read the error message above.

write track data: error after 320677888 bytes
Writing  time:  549.468s
Average write speed   9.0x.
Min drive buffer fill was 97%
Fixating...
Errno: 5 (Input/output error), close track/session scsi sendcmd: no error
CDB:  5B 00 02 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 03 00 00 00 00 0A 00 00 15 12 73 03 00 00
Sense Key: 0x3 Medium Error, Segment 0
Sense Code: 0x73 Qual 0x03 (power calibration area error) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 26.060s timeout 480s
cmd finished after 26.060s timeout 480s
Fixating time:   26.090s
wodim: Cannot fixate disk.
BURN-Free was never needed.
wodim: fifo had 5243 puts and 5052 gets.
wodim: fifo was 0 times empty and 5039 times full, min fill was 96%.[/U][/U]


---

### Post by orkyahaalhai on 2010-04-06
or u can try one dvd with puppy linux via pburn .i am having same kinda problem in  ubuntu . so when i need to burn a dvd ,i just pop in a puppy linux linux cd in dvd drive , when it loads in ram removess it and put a blank one and lo ,i am burning at lighting speed!!

---

### Post by orkyahaalhai on 2010-04-06
waiting for pburn or alike app on ubuntu!

---

### Post by steviefordi on 2010-04-06
Slowing down your burn speed to at least half that of the discs maximum may solve your problem. I will add this into your thoughts though...

Have you recently bought some new blank discs? My opinoin is it is most likely a disc problem.

There are two possible problems:

Firmware - Ensure your DVD writers firmware is up-to-date as this tells the drive how to write to the disc based on the discs media code. Media codes not recognised by the firmware will cause problems.

Dodgy discs - I think it's only worth buying TY's or Verbatim. If you've bought cheap media poor manufacturing quality is quite likely your problem.

I've done many successful burns with Brassero, and also wodim directly from the command line and never had any problems. I may be wrong but I don't think this software, anyways hope you get this sorted soon.

---

### Post by Abhinav K Sahdev on 2010-04-21
SAME PROBLEM HERE.  SAME ERROR . I tried with minimum speed with my dvd drive on a cd.  Almost 4 out of 5 mb was written . then i got this error.

---

### Post by shurenste on 2010-06-20
I have the same problem. Burned DVD with Brasero or K3b cannot be played and they are full of errors.
I m sure that it is not media dependant.

---

### Post by mk1w86 on 2010-06-20
> **shurenste said:**
> I have the same problem. Burned DVD with Brasero or K3b cannot be played and they are full of errors.
I m sure that it is not media dependant.

Does this happen with every disk you burn or is it a particular iso?

If it is a particular iso, is it a Ubuntu iso or something else?

---

### Post by jaksun5 on 2010-06-21
**Re: burner error**             
                                                                I also have  this problem. I'm quite new to Ubuntu (4 months since it's been my  primary system at home). I'm mostly happy, usually it only takes me a  few hours to knock off any setup issue. I have been troubleshooting this  issue for some time now though with no luck. I can't burn a dvd of  assorted video files nor a cd of mp3s or CD tracks. Here's my system:

OS: Ubuntu Jaunty Jackalope 9.04 (I'm using this version becuase it's  the only one that seems to work with my network card upon installation,  and I'm not fussed about flashy desktops)
Notebook: HP NX7010
DVD Burner: TEAC DV-W24EW C.0D
Brasero Version is 2.26.1
Kernel: 2.6.28.19 generic

Tried the following: (for many different reasons, mostly because ppl on  the forums reported success doing something or other)

sudo apt-get update
Installing k3b (also didn't work or I'd be using that)
added ubuntu restricted extras (which had to remove libavcodec52 and  libavutil49)

Didn't try:
disabling udev: many other posts advise against this
sudo apt-get upgrade (I was worried that this would upgrade ubuntu 9.04  to 10.04 and break something)
Don't know how to upgrade the kernel without risking some other major  issue

I'm really stumped, even though I can find other issues online that  appear to look like mine. In this case I'm hoping someone somewhere will  be able to give me some definitive advice (apart from go back to  Windows! :sad:

Should also mention that it happens with CDs and DVDs with any type of recording (data dvd or data cd or music cd)

---

### Post by Linuxforall on 2010-06-21
wodim is definitely the culprit here as from what I read at Arch, Ubuntu, Fedora forums but here is the strange part. Ripping an ISO is no issue with my SONY Opticarc but it fails with my LG DVD so I also suspect its a drive specific issue and most likely command and firmware related as well.

---

### Post by jaksun5 on 2011-02-09
OK I've now also tested with an external lite-on burner and it works like a charm, so yes it's definitely drive specific. Surely there should be either a driver or firmware update that fixes this? The drive was used in HPNX7010 and also Fujitsu Lifebook S7025 and Toshiba Satellite A60. Surely all these people can't be doing without?

---

### Post by Frantique on 2011-02-25
Nope, actually it is making the same error independent of machine. I have tested on HP, DELL, Lenovo, (older) IBM laptops, beside this on DELL and IBM desktops.
I have burned 30 disks in total, containing random data (selecting few images, music, etc.), the result is 30 broken disks. Something it is written on the disk through, I can copy the content with dd, just the format is unrecognized.
The first lines of the dump contains the file names burned. 
Really strange...

---

### Post by johnaaronrose on 2012-03-23
I'm trying to burn a CD from the iso for Ubuntu 10.04.4. 

I've tried cdrecord -fix -dev=/dev/dvdrw, cdrecord -fix -dev=/dev/cdrw  & cdrecord -fix -dev=/dev/cdrom. They all give 'Error trying to open  /dev/cdrom exclusively (Device or resource busy)... retrying in 1  second.' (or similar) repeatedly. Any ideas?

PS I looked on Launchpad bugs & there's a 2010 bug about brasero & wodim: if I understand it correctly, the problem is with wodim.

---

