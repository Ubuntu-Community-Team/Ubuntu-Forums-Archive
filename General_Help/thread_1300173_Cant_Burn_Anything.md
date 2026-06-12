---
title: "Cant Burn Anything"
date: 2009-10-24
forum: General Help
---

### Post by bigpond on 2009-10-24
hey guys, im using ubuntu 9.04 and everytime i try to burn something on a cd it fails and ejects the cd.

```
Checking session consistency (brasero_burn_check_session_consistency burn.c:1905)
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_set_output_size_for_current_track
BraseroBurnURI stopping
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_session_output_size
BraseroBurnURI output set (IMAGE) image = /tmp/brasero_tmp_3NQG2U.bin toc = none
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_current_track
BraseroBurnURI called brasero_job_get_input_type
BraseroBurnURI no burn:// URI found
BraseroBurnURI stopping
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_set_output_size_for_current_track
BraseroLocalTrack stopping
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_session_output_size
BraseroLocalTrack output set (IMAGE) image = /tmp/brasero_tmp_YF3G2U.bin toc = none
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_current_track
BraseroLocalTrack called brasero_job_get_input_type
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
BraseroChecksumImage called brasero_job_get_flags
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_session_output_size
BraseroChecksumImage output set (IMAGE) image = /tmp/brasero_tmp_YG5G2U.bin toc = none
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_input_type
BraseroChecksumImage called brasero_job_set_current_action
BraseroChecksumImage called brasero_job_get_fd_in
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage Starting checksuming file /home/dwaque/Documents/LinuxMint-7/LinuxMint-7.iso (size = 731021312)
BraseroChecksumImage called brasero_job_get_fd_out
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage Setting new checksum (type = 2) 64e2a290fb51f8e7a9d058355fe93d0e ( before)
BraseroChecksumImage Finished track successfully
BraseroChecksumImage stopping
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
    driveropts=burnfree
    -dao
    fs=16m
    -data
    -nopad
    /home/dwaque/Documents/LinuxMint-7/LinuxMint-7.iso
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
BraseroWodim stdout: Vendor_info    : 'HL-DT-ST'
BraseroWodim stdout: Identification : 'DVD+-RW GA11N   '
BraseroWodim stdout: Revision       : 'A101'
BraseroWodim stdout: Device seems to be: Generic mmc2 DVD-R/DVD-RW.
BraseroWodim stdout: Current: 0x0009 (CD-R)
BraseroWodim stdout: Profile: 0x0012 (DVD-RAM) 
BraseroWodim stdout: Profile: 0x0011 (DVD-R sequential recording) 
BraseroWodim stdout: Profile: 0x0015 (DVD-R/DL sequential recording) 
BraseroWodim stdout: Profile: 0x0014 (DVD-RW sequential recording) 
BraseroWodim stdout: Profile: 0x0013 (DVD-RW restricted overwrite) 
BraseroWodim stdout: Profile: 0x001A (DVD+RW) 
BraseroWodim stdout: Profile: 0x001B (DVD+R) 
BraseroWodim stdout: Profile: 0x002B (DVD+R/DL) 
BraseroWodim stdout: Profile: 0x0010 (DVD-ROM) 
BraseroWodim stdout: Profile: 0x0009 (CD-R) (current)
BraseroWodim stdout: Profile: 0x000A (CD-RW) 
BraseroWodim stdout: Profile: 0x0008 (CD-ROM) 
BraseroWodim stdout: Profile: 0x0002 (Removable disk) 
BraseroWodim stdout: Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
BraseroWodim stdout: Driver flags   : MMC-3 SWABAUDIO BURNFREE 
BraseroWodim stdout: Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
BraseroWodim stdout: Drive buf size : 1053696 = 1029 KB
BraseroWodim stdout: Drive DMA Speed: 15002 kB/s 85x CD 10x DVD
BraseroWodim stdout: FIFO size      : 16777216 = 16384 KB
BraseroWodim stderr: Speed set to 4234 KB/s
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Track 01: data   697 MB        
BraseroWodim stdout: Total size:      800 MB (79:19.25) = 356944 sectors
BraseroWodim stdout: Lout start:      800 MB (79:21/19) = 356944 sectors
BraseroWodim stdout: Current Secsize: 2048
BraseroWodim stdout: ATIP info from disk:
BraseroWodim stdout:   Indicated writing power: 4
BraseroWodim stdout:   Is not unrestricted
BraseroWodim stdout:   Is not erasable
BraseroWodim stdout:   Disk sub type: Medium Type A, low Beta category (A-) (2)
BraseroWodim stdout:   ATIP start of lead in:  -12508 (97:15/17)
BraseroWodim stdout:   ATIP start of lead out: 359845 (79:59/70)
BraseroWodim stdout: Disk type:    Short strategy type (Phthalocyanine or similar)
BraseroWodim stdout: Manuf. index: 22
BraseroWodim stdout: Manufacturer: Ritek Co.
BraseroWodim stdout: Blocks total: 359845 Blocks current: 359845 Blocks remaining: 2901
BraseroWodim stdout: Starting to write CD/DVD at speed  24.0 in real SAO mode for single session.
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
BraseroWodim stdout: Sending CUE sheet...
BraseroWodim called brasero_job_get_input_type
BraseroWodim called brasero_job_set_current_action
BraseroWodim stderr: Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: CDB:  2A 00 FF FF FF 6A 00 00 1F 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Writing pregap for track 1 at -150
BraseroWodim stderr: status: 0x2 (CHECK CONDITION)
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: write track pad data: error after 0 bytes
BraseroWodim stderr: Sense Bytes: 70 00 05 00 00 00 00 0A 2A 00 00 80 30 05 00 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: BFree: 1029 K BSize: 1029 K
BraseroWodim stderr: Sense Key: 0x5 Illegal Request, Segment 0
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Starting new track at sector: 0
BraseroWodim stderr: Sense Code: 0x30 Qual 0x05 (cannot write medium - incompatible format) Fru 0x0
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: 
BraseroWodim stderr: Sense flags: Blk 0 (not valid) 
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: cmd finished after 0.003s timeout 200s
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: CDB:  2A 00 00 00 00 00 00 00 1F 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: status: 0x2 (CHECK CONDITION)
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Bytes: 70 00 05 00 00 00 00 0A 2A 00 00 80 30 05 00 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Key: 0x5 Illegal Request, Segment 0
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Code: 0x30 Qual 0x05 (cannot write medium - incompatible format) Fru 0x0
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense flags: Blk 0 (not valid) 
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: cmd finished after 0.004s timeout 200s
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: A write error occured.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: Please properly read the error message above.
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Track 01:    0 of  697 MB written.
BraseroWodim stdout: write track data: error after 0 bytes
BraseroWodim stdout: Writing  time:   42.613s
BraseroWodim stdout: Average write speed 111.8x.
BraseroWodim stdout: Fixating...
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Fixating time:    0.004s
BraseroWodim stderr: wodim: fifo had 255 puts and 1 gets.
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: HUP
BraseroWodim stderr: wodim: fifo was 0 times empty and 0 times full, min fill was 100%.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: HUP
BraseroWodim process finished with status 254
BraseroWodim called brasero_job_error
BraseroWodim finished with an error
BraseroWodim asked to stop because of an error
    error        = 0
    message    = "no message"
BraseroWodim stopping
BraseroWodim got killed
Session error : unknown (brasero_burn_record burn.c:2602)

```i know its not my hardware because i burned isos and everything on vista.
any help would be greatly appreciated!

thanks :)

---

### Post by bigpond on 2009-10-25
any help?

---

### Post by jmszr on 2009-10-25
bigpond,

I would suggest that you install k3b - I've never had a problem burning a CD with it. It will install some KDE files with it (all told about 130 mb).

Go to Applications > Accessories > Terminal and copy & paste:

```
sudo apt-get install k3b
```

into it and then press Enter. It will ask for your password - type it in (it will not be visible-security) and again press Enter. It will then be under Applications > Sound & Video.

Hope that helps.

Edit: Small "k" in k3b

---

### Post by DaJL on 2009-11-26
Did you ever get this burner to work?  I have the same problem with the exact same burner.

'HL-DT-ST' 'DVD+-RW GA11N   ' 'A101' 

I'm in karmic  and it doesn't work any better with k3b

---

### Post by Entropy512 on 2009-12-24
I am having the same problem, even burning an image to CD-R media directly with cdrecord (actually it looks like it is an alias to wodim on this system?)

I had similar problems with DVD-R media.

```

adodd@andysg51:~$ sudo cdrecord -v speed=4 dev=/dev/dvdrw driveropts=burnfree fs=64M -dao Documents/ubuntu-9.10-desktop-i386.iso                                                                                                     
TOC Type: 1 = CD-ROM                                                                                             
scsidev: '/dev/dvdrw'                                                                                            
devname: '/dev/dvdrw'                                                                                            
scsibus: -2 target: -2 lun: -2                                                                                   
Linux sg driver version: 3.5.27                                                                                  
Wodim version: 1.1.9                                                                                             
Driveropts: 'burnfree'                                                                                           
SCSI buffer size: 64512                                                                                          
Device type    : Removable CD-ROM                                                                                
Version        : 5                                                                                               
Response Format: 2                                                                                               
Capabilities   :                                                                                                 
Vendor_info    : 'HL-DT-ST'                                                                                      
Identification : 'DVDRAM GSA-T50N '                                                                              
Revision       : 'RR09'                                                                                          
Device seems to be: Generic mmc2 DVD-R/DVD-RW.                                                                   
Current: 0x0009 (CD-R)                                                                                           
Profile: 0x0012 (DVD-RAM)                                                                                        
Profile: 0x0011 (DVD-R sequential recording)                                                                     
Profile: 0x0015 (DVD-R/DL sequential recording)                                                                  
Profile: 0x0016 (DVD-R/DL layer jump recording)                                                                  
Profile: 0x0014 (DVD-RW sequential recording)                                                                    
Profile: 0x0013 (DVD-RW restricted overwrite)                                                                    
Profile: 0x001A (DVD+RW)                                                                                         
Profile: 0x001B (DVD+R)                                                                                          
Profile: 0x002B (DVD+R/DL)                                                                                       
Profile: 0x0010 (DVD-ROM)                                                                                        
Profile: 0x0009 (CD-R) (current)                                                                                 
Profile: 0x000A (CD-RW)                                                                                          
Profile: 0x0008 (CD-ROM)                                                                                         
Profile: 0x0002 (Removable disk)                                                                                 
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).                                                          
Driver flags   : MMC-3 SWABAUDIO BURNFREE                                                                        
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R                                      
Drive buf size : 1053696 = 1029 KB                                                                               
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device                                       
communication breaks or freezes immediately after that.                                                          
Drive DMA Speed: 14728 kB/s 83x CD 10x DVD                                                                       
FIFO size      : 67108864 = 65536 KB                                                                             
Track 01: data   689 MB                                                                                          
Total size:      792 MB (78:30.21) = 353266 sectors                                                              
Lout start:      792 MB (78:32/16) = 353266 sectors                                                              
Current Secsize: 2048                                                                                            
ATIP info from disk:                                                                                             
  Indicated writing power: 5                                                                                     
  Is not unrestricted                                                                                            
  Is not erasable                                                                                                
  Disk sub type: Medium Type C, low Beta category (C-) (6)                                                       
  ATIP start of lead in:  -11640 (97:26/60)                                                                      
  ATIP start of lead out: 359849 (79:59/74)                                                                      
Disk type:    Long strategy type (Cyanine, AZO or similar)                                                       
Manuf. index: 3                                                                                                  
Manufacturer: CMC Magnetics Corporation                                                                          
Blocks total: 359849 Blocks current: 359849 Blocks remaining: 6583                                               
Speed set to 1764 KB/s                                                                                           
Starting to write CD/DVD at speed  10.0 in real SAO mode for single session.                                     
Last chance to quit, starting real write in    0 seconds. Operation starts.                                      
Waiting for reader process to fill input buffer ... input buffer ready.                                          
Performing OPC...                                                                                                
Sending CUE sheet...                                                                                             
Writing pregap for track 1 at -150                                                                               
Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error                                                   
CDB:  2A 00 FF FF FF 6A 00 00 1F 00                                                                              
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 2A 00 00 80 30 05 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x30 Qual 0x05 (cannot write medium - incompatible format) Fru 0x0
Sense flags: Blk 0 (not valid)
cmd finished after 0.002s timeout 200s
write track pad data: error after 0 bytes
BFree: 1029 K BSize: 1029 K
Starting new track at sector: 0
Track 01:    0 of  689 MB written.Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
CDB:  2A 00 00 00 00 00 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 2A 00 00 80 30 05 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x30 Qual 0x05 (cannot write medium - incompatible format) Fru 0x0
Sense flags: Blk 0 (not valid)
cmd finished after 0.004s timeout 200s

write track data: error after 0 bytes
wodim: A write error occured.
wodim: Please properly read the error message above.
Writing  time:   36.861s
Average write speed 128.0x.
Fixating...
Fixating time:    0.004s
wodim: fifo had 1023 puts and 1 gets.
wodim: fifo was 0 times empty and 0 times full, min fill was 100%.

```

---

### Post by duffydack on 2009-12-26
Ubuntu 9.10 / HL-DT-ST DVD+-RW GA11N v102 and same burning woes.  Brasero will write but at a pathetic 0.3x speed and k3b gives an error..  (i had to run permissions setup in k3b to fix permissions first).  Imgburn in wine (using aspi, as SPTI fails to detect a writer) does the same as brasero, at 0.3x

---

### Post by surfed on 2010-01-21
It seems to be a firmware issue with this drive. Googled drive and model and lots of people on Dells and Macs have this issue

---

### Post by duffydack on 2010-01-23
How can it be a firmware issue or issue of any kind with this drive when it runs flawlessly in windows.  
It does blank rewritables fine ive found, but cant get past lead-in for writing....well not quite true.. I have had it write 1 disc from a whole pack of dvd+r, using the same command ive used before when its failed and I used the command after successful write but never worked again..
This is a linux/ubuntu issue.

---

### Post by surfed on 2010-01-23
> **duffydack said:**
> How can it be a firmware issue or issue of any kind with this drive when it runs flawlessly in windows.  
It does blank rewritables fine ive found, but cant get past lead-in for writing....well not quite true.. I have had it write 1 disc from a whole pack of dvd+r, using the same command ive used before when its failed and I used the command after successful write but never worked again..
This is a linux/ubuntu issue.


because with the previous firmware it would work in linux but not win7. This is not the first time that i hear about firmware issues in drives. Google the drive model and you will come across lots of people with similar issues.

---

### Post by duffydack on 2010-01-26
Do you know what version firmware it was that worked in linux?  Mine came with A102 (dell), but the only one available for download from dell is A101 (odd)
It says it fixes it for Win7 anyway so that wont be any good downgrading to that..I assume.

---

### Post by surfed on 2010-01-26
Mine came with A102 but i have read about others using A101 with same problem. I ended up getting this:
[http://www.eeshops.com/sony-nec-bdr-bluray-sata-dvd-drive-burner-bc5600s-p-368.html](http://www.eeshops.com/sony-nec-bdr-bluray-sata-dvd-drive-burner-bc5600s-p-368.html)
Dell lists them in their Driver Firmware page for the XPS1645 so i know it will fit. I will report back in a couple of weeks (still has not arrived) if this drive works but i googled and found nobody with any issues.

---

### Post by surfed on 2010-01-28
The actual problem for me was device-manager-plasmoid 1.1.1, replacing it with device-notifier everything works again.

---

### Post by pstickar on 2010-01-29
@surfed: could I ask you what packages contain "device-notifier"? Is it specific of a particular installation or is it also available for the standard & plain ubuntu (karmic)?

I have the same problem with a

vendor= hp
Identification= DVDRAM GSA-U20N 
Revision= HC11
Device seems to be: Generic mmc2 DVD-R/DVD-RW

---

### Post by surfed on 2010-01-29
> **pstickar said:**
> @surfed: could I ask you what packages contain "device-notifier"? Is it specific of a particular installation or is it also available for the standard & plain ubuntu (karmic)?

I have the same problem with a

vendor= hp
Identification= DVDRAM GSA-U20N 
Revision= HC11
Device seems to be: Generic mmc2 DVD-R/DVD-RW

Its a 3rd party app i got from kdelook.org
To find out if another program is causing issues, boot into single user mode and burn a disk from there. If it works you have another program causing issues by accessing the disk.

---

### Post by pous on 2010-03-01
could you explain again in plain english?
i've got to admit i'm quite new to linux, and have a similar problem wit my burner, it worked fine in windows, but in ubuntu i cant get it to copy anything yet... thanks!

forgot to mention (if it makes any difference) i now run 9.10...

---

### Post by surfed on 2010-03-01
> **pous said:**
> could you explain again in plain english?
i've got to admit i'm quite new to linux, and have a similar problem wit my burner, it worked fine in windows, but in ubuntu i cant get it to copy anything yet... thanks!

forgot to mention (if it makes any difference) i now run 9.10...

Post more details on your error / messages so we can pinpoint your particular issue. In my case it ended up being a compatibility issue with my drives firmware and Linux. An easy way to verify if thats an issue is to insert an blank cd and the in a terminal type dmesg. If you get sence errors than you might have this problem but more likely its just a setup problem.

---

### Post by duffydack on 2010-03-02
I get those sense errors in dmesg when i insert a disc...  I did actually get it to burn ONCE a while after I first got laptop.. I was in irc askin for help on it, and I went to the shell to run the same command Ive run a dozen times, to get the error message, and it burned...and hasnt burned since... weird.

---

### Post by surfed on 2010-03-02
> **duffydack said:**
> I get those sense errors in dmesg when i insert a disc...  I did actually get it to burn ONCE a while after I first got laptop.. I was in irc askin for help on it, and I went to the shell to run the same command Ive run a dozen times, to get the error message, and it burned...and hasnt burned since... weird.

Same for me, its a drive issue, not much you can do except get a different drive. There is a long conversation by me with thomas from the devburn-devel mailing list on the issue and basically we gave up on getting this drive / firmware combo to work. One thing we did not try as i ended up getting another drive and selling this one is downgrading the firmware to A101.

---

### Post by duffydack on 2010-03-03
> **surfed said:**
> Same for me, its a drive issue, not much you can do except get a different drive. There is a long conversation by me with thomas from the devburn-devel mailing list on the issue and basically we gave up on getting this drive / firmware combo to work. One thing we did not try as i ended up getting another drive and selling this one is downgrading the firmware to A101.

I dont use it that often so I`ll have to put up with booting windows to burn...bit of a bummer but if as you say its never going to get a fix, it`ll have to do..I`d like to kill windows partition altogether as well..

---

### Post by psusi on 2010-03-03
> **surfed said:**
> Same for me, its a drive issue, not much you can do except get a different drive. There is a long conversation by me with thomas from the devburn-devel mailing list on the issue and basically we gave up on getting this drive / firmware combo to work. One thing we did not try as i ended up getting another drive and selling this one is downgrading the firmware to A101.

I was going to suggest trying to force the burn in TAO mode instead of SAO as it appears to be using.  Did you try that?

---

### Post by DoritosBR on 2010-03-03
It's a bug
[https://bugs.launchpad.net/ubuntu/+source/cdrkit/+bug/435237](https://bugs.launchpad.net/ubuntu/+source/cdrkit/+bug/435237)

Does anyone knows any workaround, or some burning gui that does not use wodim?

---

### Post by duffydack on 2010-03-04
> **DoritosBR said:**
> It's a bug
[https://bugs.launchpad.net/ubuntu/+source/cdrkit/+bug/435237](https://bugs.launchpad.net/ubuntu/+source/cdrkit/+bug/435237)

Does anyone knows any workaround, or some burning gui that does not use wodim?

It errors at the same point even using imgburn in WINE, and Ive also tried Nero Linux.
So i`m not sure its just limited to wodim...

---

### Post by duffydack on 2010-03-20
any new developments on this issue?  I still cant burn anything in ubuntu.  Anyone found an earlier firmware?

---

### Post by duffydack on 2010-03-27
Well Ive tried lucid before but I dont know whats changed as I have just burned a dvd using brasero.  Blanks ok, burns isos, burns files, but fails to eject it after finalise, which isnt a problem..

---

### Post by duffydack on 2010-04-09
Well its 'sods law' as Ive had to get a replacement laptop (same specs, free of charge for problems I had) and it has come with a different drive, the  HL-DT-ST' 'DVD+-RW GA31N  not the GA11N which worked fine.. this new one doesnt even recognise blank dvd/dvdrw (in win7 it does of course). I`m gutted.

[ 1193.608953] sr 4:0:0:0: [sr0] Unhandled sense code
[ 1193.608959] sr 4:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1193.608966] sr 4:0:0:0: [sr0] Sense Key : Medium Error [current] 
[ 1193.608974] sr 4:0:0:0: [sr0] Add. Sense: Unrecovered read error
[ 1193.608981] sr 4:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[ 1193.609003] __ratelimit: 109 callbacks suppressed
[ 1203.833738] sr 4:0:0:0: [sr0] Unhandled sense code
[ 1203.833744] sr 4:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1203.833751] sr 4:0:0:0: [sr0] Sense Key : Medium Error [current] 
[ 1203.833759] sr 4:0:0:0: [sr0] Add. Sense: Id CRC or ECC error
[ 1203.833766] sr 4:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00

Thats just what I get from inserting a blank disc..it doesnt even show on desktop

---

### Post by duffydack on 2010-04-17
Ok another update. It now WORKS!  Lets hope it doesnt get broken in an update.
<3 ubuntu

---

