---
title: "CD / DVD Burning Failures"
date: 2009-12-28
forum: General Help
---

### Post by Mahngiel on 2009-12-28
Trying to burn a damned CD iso so i can dual boot ubuntu and kubuntu. But the software k3b and brasero are failing miserably, and i can't figure it out.  Here are their respective error logs:

K3b:
```

 p, li { white-space: pre-wrap; }  [FONT=DejaVu Sans Mono]Devices[/FONT]
 [FONT=DejaVu Sans Mono]-----------------------[/FONT]
 [FONT=DejaVu Sans Mono]HL-DT-ST DVD-RW GWA-4080N 0C09 (/dev/sr0, CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD+R, DVD+RW) [DVD-ROM, DVD-R Sequential, DVD-RW Restricted Overwrite, DVD-RW Sequential, DVD+RW, DVD+R, CD-ROM, CD-R, CD-RW] [TAO, Restricted Overwrite] [%7][/FONT]
 
 [FONT=DejaVu Sans Mono]System[/FONT]
 [FONT=DejaVu Sans Mono]-----------------------[/FONT]
 [FONT=DejaVu Sans Mono]K3b Version: 1.68.0[/FONT]
 [FONT=DejaVu Sans Mono]KDE Version: 4.3.2 (KDE 4.3.2)[/FONT]
 [FONT=DejaVu Sans Mono]QT Version:  4.5.2[/FONT]
 [FONT=DejaVu Sans Mono]Kernel:      2.6.31-16-generic[/FONT]
 
 [FONT=DejaVu Sans Mono]Used versions[/FONT]
 [FONT=DejaVu Sans Mono]-----------------------[/FONT]
 [FONT=DejaVu Sans Mono]cdrecord: 1.1.9[/FONT]
 
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
 [FONT=DejaVu Sans Mono]Vendor_info    : 'HL-DT-ST'[/FONT]
 [FONT=DejaVu Sans Mono]Identification : 'DVD-RW GWA-4080N'[/FONT]
 [FONT=DejaVu Sans Mono]Revision       : '0C09'[/FONT]
 [FONT=DejaVu Sans Mono]Device seems to be: Generic mmc2 DVD-R/DVD-RW.[/FONT]
 [FONT=DejaVu Sans Mono]Current: 0x0009 (CD-R)[/FONT]
 [FONT=DejaVu Sans Mono]Profile: 0x0011 (DVD-R sequential recording) [/FONT]
 [FONT=DejaVu Sans Mono]Profile: 0x0014 (DVD-RW sequential recording) [/FONT]
 [FONT=DejaVu Sans Mono]Profile: 0x0013 (DVD-RW restricted overwrite) [/FONT]
 [FONT=DejaVu Sans Mono]Profile: 0x001A (DVD+RW) [/FONT]
 [FONT=DejaVu Sans Mono]Profile: 0x001B (DVD+R) [/FONT]
 [FONT=DejaVu Sans Mono]Profile: 0x0010 (DVD-ROM) [/FONT]
 [FONT=DejaVu Sans Mono]Profile: 0x0009 (CD-R) (current)[/FONT]
 [FONT=DejaVu Sans Mono]Profile: 0x000A (CD-RW) [/FONT]
 [FONT=DejaVu Sans Mono]Profile: 0x0008 (CD-ROM) [/FONT]
 [FONT=DejaVu Sans Mono]Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).[/FONT]
 [FONT=DejaVu Sans Mono]Driver flags   : MMC-3 SWABAUDIO BURNFREE [/FONT]
 [FONT=DejaVu Sans Mono]Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R[/FONT]
 [FONT=DejaVu Sans Mono]Drive buf size : 1053696 = 1029 KB[/FONT]
 [FONT=DejaVu Sans Mono]Drive DMA Speed: 8613 kB/s 48x CD 6x DVD[/FONT]
 [FONT=DejaVu Sans Mono]FIFO size      : 12582912 = 12288 KB[/FONT]
 [FONT=DejaVu Sans Mono]Speed set to 4234 KB/s[/FONT]
 [FONT=DejaVu Sans Mono]Track 01: data   682 MB        [/FONT]
 [FONT=DejaVu Sans Mono]Total size:      784 MB (77:40.42) = 349532 sectors[/FONT]
 [FONT=DejaVu Sans Mono]Lout start:      784 MB (77:42/32) = 349532 sectors[/FONT]
 [FONT=DejaVu Sans Mono]Current Secsize: 2048[/FONT]
 [FONT=DejaVu Sans Mono]ATIP info from disk:[/FONT]
 [FONT=DejaVu Sans Mono]  Indicated writing power: 5[/FONT]
 [FONT=DejaVu Sans Mono]  Is not unrestricted[/FONT]
 [FONT=DejaVu Sans Mono]  Is not erasable[/FONT]
 [FONT=DejaVu Sans Mono]  Disk sub type: Medium Type A, high Beta category (A+) (3)[/FONT]
 [FONT=DejaVu Sans Mono]  ATIP start of lead in:  -11634 (97:26/66)[/FONT]
 [FONT=DejaVu Sans Mono]  ATIP start of lead out: 359846 (79:59/71)[/FONT]
 [FONT=DejaVu Sans Mono]Disk type:    Short strategy type (Phthalocyanine or similar)[/FONT]
 [FONT=DejaVu Sans Mono]Manuf. index: 3[/FONT]
 [FONT=DejaVu Sans Mono]Manufacturer: CMC Magnetics Corporation[/FONT]
 [FONT=DejaVu Sans Mono]Blocks total: 359846 Blocks current: 359846 Blocks remaining: 10314[/FONT]
 [FONT=DejaVu Sans Mono]Starting to write CD/DVD at speed  24.0 in real TAO mode for single session.[/FONT]
 [FONT=DejaVu Sans Mono]Last chance to quit, starting real write in    2 seconds.[/FONT]
 [FONT=DejaVu Sans Mono]   1 seconds.[/FONT]
 [FONT=DejaVu Sans Mono]   0 seconds. Operation starts.[/FONT]
 [FONT=DejaVu Sans Mono]Waiting for reader process to fill input buffer ... input buffer ready.[/FONT]
 [FONT=DejaVu Sans Mono]Performing OPC...[/FONT]
 [FONT=DejaVu Sans Mono]Starting new track at sector: 0[/FONT]
 [FONT=DejaVu Sans Mono]Track 01:    0 of  682 MB written.[/FONT]
 [FONT=DejaVu Sans Mono]Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error[/FONT]
 [FONT=DejaVu Sans Mono]CDB:  2A 00 00 00 00 00 00 00 1F 00[/FONT]
 [FONT=DejaVu Sans Mono]status: 0x2 (CHECK CONDITION)[/FONT]
 [FONT=DejaVu Sans Mono]Sense Bytes: 70 00 25 00 00 00 00 10 2A 00 00 80 64 00 00 00[/FONT]
 [FONT=DejaVu Sans Mono]Sense Key: 0x5 Illegal Request, Segment 0[/FONT]
 [FONT=DejaVu Sans Mono]Sense Code: 0x64 Qual 0x00 (illegal mode for this track) Fru 0x0[/FONT]
 [FONT=DejaVu Sans Mono]Sense flags: Blk 0 (not valid) illegal block length [/FONT]
 [FONT=DejaVu Sans Mono]cmd finished after 3.648s timeout 40s[/FONT]
 [FONT=DejaVu Sans Mono]/usr/bin/wodim: A write error occured.[/FONT]
 [FONT=DejaVu Sans Mono]/usr/bin/wodim: Please properly read the error message above.[/FONT]
 [FONT=DejaVu Sans Mono]write track data: error after 0 bytes[/FONT]
 [FONT=DejaVu Sans Mono]Writing  time:   12.318s[/FONT]
 [FONT=DejaVu Sans Mono]Average write speed 380.4x.[/FONT]
 [FONT=DejaVu Sans Mono]Fixating...[/FONT]
 [FONT=DejaVu Sans Mono]Fixating time:    0.006s[/FONT]
 [FONT=DejaVu Sans Mono]/usr/bin/wodim: fifo had 192 puts and 1 gets.[/FONT]
 [FONT=DejaVu Sans Mono]/usr/bin/wodim: fifo was 0 times empty and 0 times full, min fill was 100%.[/FONT]
 
 [FONT=DejaVu Sans Mono]cdrecord command:[/FONT]
 [FONT=DejaVu Sans Mono]-----------------------[/FONT]
 [FONT=DejaVu Sans Mono]/usr/bin/wodim -v gracetime=2 dev=/dev/sr0 speed=24 -tao driveropts=burnfree -data -tsize=349530s -[/FONT]
 


```Brasero:
```

Checking session consistency (brasero_burn_check_session_consistency brasero-burn.c:1848)
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_set_output_size_for_current_track
BraseroBurnURI stopping
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_session_output_size
BraseroBurnURI output set (IMAGE) image = /tmp/brasero_tmp_75RG5U.bin toc = none
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
BraseroLocalTrack output set (IMAGE) image = /tmp/brasero_tmp_MYMG5U.bin toc = none
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
    speed=24
    driveropts=burnfree
    -dao
    fs=16m
    -data
    -nopad
    /media/Storage/Torrents/kubuntu-9.10-desktop-i386.iso
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
BraseroWodim stdout: Identification : 'DVD-RW GWA-4080N'
BraseroWodim stdout: Revision       : '0C09'
BraseroWodim stdout: Device seems to be: Generic mmc2 DVD-R/DVD-RW.
BraseroWodim stdout: Current: 0x0009 (CD-R)
BraseroWodim stdout: Profile: 0x0011 (DVD-R sequential recording) 
BraseroWodim stdout: Profile: 0x0014 (DVD-RW sequential recording) 
BraseroWodim stdout: Profile: 0x0013 (DVD-RW restricted overwrite) 
BraseroWodim stdout: Profile: 0x001A (DVD+RW) 
BraseroWodim stdout: Profile: 0x001B (DVD+R) 
BraseroWodim stdout: Profile: 0x0010 (DVD-ROM) 
BraseroWodim stdout: Profile: 0x0009 (CD-R) (current)
BraseroWodim stdout: Profile: 0x000A (CD-RW) 
BraseroWodim stdout: Profile: 0x0008 (CD-ROM) 
BraseroWodim stdout: Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
BraseroWodim stdout: Driver flags   : MMC-3 SWABAUDIO BURNFREE 
BraseroWodim stdout: Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
BraseroWodim stdout: Drive buf size : 1053696 = 1029 KB
BraseroWodim stdout: Drive DMA Speed: 8466 kB/s 48x CD 6x DVD
BraseroWodim stdout: FIFO size      : 16777216 = 16384 KB
BraseroWodim stderr: Speed set to 4234 KB/s
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Track 01: data   682 MB        
BraseroWodim stdout: Total size:      784 MB (77:40.40) = 349530 sectors
BraseroWodim stdout: Lout start:      784 MB (77:42/30) = 349530 sectors
BraseroWodim stdout: Current Secsize: 2048
BraseroWodim stdout: ATIP info from disk:
BraseroWodim stdout:   Indicated writing power: 5
BraseroWodim stdout:   Is not unrestricted
BraseroWodim stdout:   Is not erasable
BraseroWodim stdout:   Disk sub type: Medium Type A, high Beta category (A+) (3)
BraseroWodim stdout:   ATIP start of lead in:  -11634 (97:26/66)
BraseroWodim stdout:   ATIP start of lead out: 359846 (79:59/71)
BraseroWodim stdout: Disk type:    Short strategy type (Phthalocyanine or similar)
BraseroWodim stdout: Manuf. index: 3
BraseroWodim stdout: Manufacturer: CMC Magnetics Corporation
BraseroWodim stdout: Blocks total: 359846 Blocks current: 359846 Blocks remaining: 10316
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
BraseroWodim stderr: wodim: CUE sheet not accepted. Retrying with minimum pregapsize = 1.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Errno: 5 (Input/output error), send_cue_sheet scsi sendcmd: no error
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: CDB:  5D 00 00 00 00 00 00 00 20 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Writing  time:    0.087s
BraseroWodim stderr: status: 0x2 (CHECK CONDITION)
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Bytes: 70 00 05 00 00 00 00 10 5D 34 02 80 26 00 00 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Key: 0x5 Illegal Request, Segment 0
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Code: 0x26 Qual 0x00 (invalid field in parameter list) Fru 0x0
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense flags: Blk 0 (not valid) 
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: cmd finished after 0.004s timeout 200s
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: CUE sheet still not accepted. Please try to write in RAW (-raw96r) mode.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: Cannot send CUE sheet.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: Could not write Lead-in.
BraseroWodim called brasero_job_get_flags
BraseroWodim called brasero_job_error
BraseroWodim finished with an error
BraseroWodim asked to stop because of an error
    error        = 15
    message    = "An error occured while writing to disc"
BraseroWodim stopping
BraseroWodim got killed
Session error : An error occured while writing to disc (brasero_burn_record brasero-burn.c:2808)


```Any help understanding this would be greatly appreciated.

---

### Post by Mahngiel on 2009-12-28
bumpity-bump??

---

### Post by nerdtron on 2009-12-28
Try using other CD-R. I also have problems burning the iso file. Or try what worked for me: [www.pendrivelinux.com](www.pendrivelinux.com) helped me to make a bootable flash drive with Karmic on it...

---

### Post by Sef on 2009-12-29
Please wait for 24 hours before bumping you thread.  Thank you.

---

