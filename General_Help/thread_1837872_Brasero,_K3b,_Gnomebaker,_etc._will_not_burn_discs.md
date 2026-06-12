---
title: "Brasero, K3b, Gnomebaker, etc. will not burn discs"
date: 2011-09-02
forum: General Help
---

### Post by omegacfx on 2011-09-02
Hi,
I've tried burning a disc in Ubuntu 11 using Brasero, K3B, Nerolinux and Gnomebaker and I am not having any luck. It used to work a while back and it works fine in Windows, but I can't seem to get it to work in linux now. I have tried using other distros as well and I'm getting the same issues. 

Here is the log from Brasero

```
Checking session consistency (brasero_burn_check_session_consistency brasero-burn.c:1744)
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_set_output_size_for_current_track
BraseroBurnURI stopping
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_session_output_size
BraseroBurnURI output set (IMAGE) image = /tmp/brasero_tmp_WRNA1V.bin toc = none
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
BraseroLocalTrack output set (IMAGE) image = /tmp/brasero_tmp_KAPA1V.bin toc = none
BraseroLocalTrack called brasero_job_get_session_output_size
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
BraseroChecksumImage called brasero_job_get_flags
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_session_output_size
BraseroChecksumImage output set (IMAGE) image = /tmp/brasero_tmp_IRQA1V.bin toc = none
BraseroChecksumImage called brasero_job_get_session_output_size
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_input_type
BraseroChecksumImage called brasero_job_set_current_action
BraseroChecksumImage called brasero_job_get_fd_in
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage Starting checksuming file /home/omegacfx/Desktop/win7.iso (size = 3738042368)
BraseroChecksumImage called brasero_job_get_fd_out
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage Setting new checksum (type = 2) 93b589ce3f7439b8ee6df252fd4a0f51 ((null) before)
BraseroChecksumImage Finished track successfully
BraseroChecksumImage stopping
BraseroLibburn called brasero_job_get_action
BraseroLibburn called brasero_job_get_action
BraseroLibburn unsupported operation
BraseroLibburn deactivating
BraseroLibburn called brasero_job_get_action
BraseroLibburn called brasero_job_get_action
BraseroLibburn called brasero_job_get_device
BraseroLibburn Drive (/dev/sr0) init result = 1
BraseroLibburn called brasero_job_get_flags
BraseroLibburn called brasero_job_get_media
BraseroLibburn called brasero_job_get_fd_in
BraseroLibburn called brasero_job_get_tracks
BraseroLibburn Setting multi 0
BraseroLibburn Setting burnproof 0
BraseroLibburn Setting dummy 0
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn burn_drive_convert_fs_adr( /dev/sr0 )
BraseroLibburn Writing
BraseroLibburn called brasero_job_set_dangerous
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn burn_drive_is_enumerable_adr( /dev/sr0 ) is true
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn Async START UNIT succeeded after 0.1 seconds
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn mmc_set_streaming: end_lba=2295103 ,  r=4584 ,  w=11080
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn Allocating buffer via mmap()
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn dvd/bd Profile= 1Bh , obs= 32768 , obs_pad= 1
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn DVD+R pre-track 01 : get_nwa(0), ret= 1 , d->nwa= 0
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn DVD pre-track 01 : demand=3738042368, cap=4700372992

BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI error condition on command 2Ah WRITE(10): [3 0C 00] Write error
BraseroLibburn Something went wrong
BraseroLibburn called brasero_job_error
BraseroLibburn finished with an error
BraseroLibburn asked to stop because of an error
    error        = 15
    message    = "An error occurred while writing to disc"
BraseroLibburn stopping
Session error : An error occurred while writing to disc (brasero_burn_record brasero-burn.c:2862)
```

Thanks for the help!! :)

---

### Post by TeoBigusGeekus on 2011-09-02
What are you trying to burn: cd/dvd?
Also, is it a data session, an image burning, etc.?

---

### Post by omegacfx on 2011-09-02
I'm trying to burn an image to a DVD.

I used the cdrecord command as well and here is the output:

```
wodim: No write mode specified.
wodim: Assuming -tao mode.
wodim: Future versions of wodim may have different drive dependent defaults.
TOC Type: 1 = CD-ROM
scsidev: '/dev/scd0'
devname: '/dev/scd0'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.10
SCSI buffer size: 64512
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'HL-DT-ST'
Identification : 'DVDRAM_GSA-T50N '
Revision       : 'RF07'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x001B (DVD+R)
Profile: 0x0012 (DVD-RAM) 
Profile: 0x0011 (DVD-R sequential recording) 
Profile: 0x0015 (DVD-R/DL sequential recording) 
Profile: 0x0014 (DVD-RW sequential recording) 
Profile: 0x0013 (DVD-RW restricted overwrite) 
Profile: 0x001A (DVD+RW) 
Profile: 0x001B (DVD+R) (current)
Profile: 0x002B (DVD+R/DL) 
Profile: 0x0010 (DVD-ROM) 
Profile: 0x0009 (CD-R) 
Profile: 0x000A (CD-RW) 
Profile: 0x0008 (CD-ROM) 
Profile: 0x0002 (Removable disk) 
Using generic SCSI-3/mmc DVD-R(W) driver (mmc_mdvd).
Driver flags   : SWABAUDIO BURNFREE 
Supported modes: PACKET SAO
Drive buf size : 1114112 = 1088 KB
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
Drive DMA Speed: 15658 kB/s 88x CD 11x DVD
FIFO size      : 12582912 = 12288 KB
Track 01: data  3564 MB        
Total size:     4094 MB (405:36.21) = 1825216 sectors
Lout start:     4094 MB (405:38/16) = 1825216 sectors
Current Secsize: 2048
HINT: use dvd+rw-mediainfo from dvd+rw-tools for information extraction.
Blocks total: 1825216 Blocks current: 1825216 Blocks remaining: 0
Speed set to 11080 KB/s
Starting to write CD/DVD at speed   8.0 in real unknown mode for single session.
Last chance to quit, starting real write in    0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Errno: 5 (Input/output error), reserve track scsi sendcmd: no error
CDB:  53 00 00 00 00 00 1B D9 C0 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 53 35 1E 0E 72 05 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x72 Qual 0x05 (no more track reservations allowed) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.003s timeout 40s
wodim: Cannot open new session.
Writing  time:    0.058s
wodim: fifo had 192 puts and 0 gets.
wodim: fifo was 0 times empty and 0 times full, min fill was 100%.

```

---

### Post by TeoBigusGeekus on 2011-09-02
Try this
```
growisofs -dvd-compat -Z /dev/dvd=/path/imagename.iso
```
Replace path and imagename appropriately.
Also, replace /dev/dvd with whatever applies to your system: /dev/cd, /dev/sr0, etc.

---

### Post by omegacfx on 2011-09-02
No luck

> /dev/sr0: "Current Write Speed" is 8.2x1352KBps.
:-[ WRITE@LBA=220h failed with SK=3h/WRITE ERROR]: Input/output error
:-( write failed: Input/output error
/dev/sr0: flushing cache
:-[ FLUSH CACHE failed with SK=3h/WRITE ERROR]: Input/output error
:-[ SYNCHRONOUS FLUSH CACHE failed with SK=3h/ASC=A0h/ACQ=80h]: Input/output error


---

### Post by TeoBigusGeekus on 2011-09-02
If you try it with /dev/dvd instead of /dev/sr0?

---

### Post by omegacfx on 2011-09-02
Still didn't work. I'm beginning to think my drive is now defective or something. It can still read and play dvd's alright, but it has been a couple months since I tested it in Windows. It was definitely working then though.

---

### Post by TeoBigusGeekus on 2011-09-02
> **omegacfx said:**
> Still didn't work. I'm beginning to think my drive is now defective or something. It can still read and play dvd's alright, but it has been a couple months since I tested it in Windows. It was definitely working then though.

That's what's left for me to say as well, sorry.

PS: All linux (gui) burning software sucks. I'd advise you to learn how to do it from command line.

---

### Post by coldraven on 2011-09-02
I once had a box of brand new Memorex CDRs and they all failed to burn. Each one had little scratches near the centre. They must have been made on a Friday!

---

### Post by Iceycabbie on 2011-09-04
> **omegacfx said:**
> Still didn't work. I'm beginning to think my drive is now defective or something. It can still read and play dvd's alright, but it has been a couple months since I tested it in Windows. It was definitely working then though.

I thought the same but mine burns RW OK & works fine in windows (Dual Boot) - seems a bug crept in a few updates ago 

[http://cdrecord.berlios.de/private/linux-dist.html](http://cdrecord.berlios.de/private/linux-dist.html)

[http://jeff.ecchi.ca/blog/2010/05/31/burnt-by-disc-burning/](http://jeff.ecchi.ca/blog/2010/05/31/burnt-by-disc-burning/)

I have posted a bug & await a response

---

### Post by cottfcfan on 2011-09-04
Try NeroLinux.
The only thing to work for me.
[http://www.nero.com/enu/linux4.html](http://www.nero.com/enu/linux4.html)

edit....
Sorry didn't read your 1st post properly.
Seems you've tried that already.

---

### Post by Iceycabbie on 2011-09-07
[QUOTE=cottfcfan;11216670]Try NeroLinux.
The only thing to work for me.
[http://www.nero.com/enu/linux4.html](http://www.nero.com/enu/linux4.html)

No joy with nero _ also tried at 2x

Nero Log

Linux (Ubuntu 10.04 'lucid') 2.6.32-33-generic (i686)
Nero API version: 9.7.0.132
Using interface version: 9.0.1.4
Installed in: /usr/lib/nero/
Application: Nero AG\Nero Linux
Internal Version: 9, 7, 0, 132

Recorder:             <_NEC DVD+-RW ND-3530A>   Version: 103C - HA 1 TA 0 - 0.0.0.0
 Adapter driver:      <ata_piix>                HA 1
 Drive buffer  :      2048kB
 Bus Type      :      via Inquiry data
Excluded drive IDs: 
WriteBufferSize: 83886080 (0) Byte
BUFE           : 0
Physical memory     : 1246MB (1276520kB)
Free physical memory: 145MB (149376kB)
Memory in use       : 88 %
Uncached PFiles: 0x0
Global Bus Type: default (0)
Check supported media : Disabled (0) 

7.9.2011
NeroAPI
14:40:37    #1 Text 0 File Burncd.cpp, Line 3647
    Turn on Disc-At-Once, using DVD media
    
14:40:37    #2 Text 0 File DlgWaitCD.cpp, Line 313
    Last possible write address on media:  2298495
    Last address to be written:            2183930
    
14:40:37    #3 Text 0 File DlgWaitCD.cpp, Line 325
    Write in overburning mode: NO
    
14:40:37    #4 Text 0 File DlgWaitCD.cpp, Line 2856
    Recorder: _NEC DVD+-RW ND-3530A, Media type: DVD-R
     Disc Manufacturer ID: <MBI 01> <RG40>
     Disc Application Code: 64, Disc Physical Code: 193
    
14:40:37    #5 Text 0 File DlgWaitCD.cpp, Line 500
    >>> Protocol of DlgWaitCD activities: <<<
    =========================================
    
14:40:37    #6 Text 0 File ThreadedTransferInterface.cpp, Line 734
    Setup items (after recorder preparation)
     0: TRM_DATA_MODE1 (2 - CD-ROM Mode 1, Joliet)
        2 indices, index0 (150) not provided
        original disc pos #0 + 2183931 (2183931) = #2183931/485:19.6
        not relocatable, disc pos for caching/writing not required/not required
        -> TRM_DATA_MODE1, 2048, config 0, wanted index0 0 blocks, length 2183931 blocks [_NEC DVD+-RW ND-3530A (H:1 T:0)]
    --------------------------------------------------------------
    
14:40:38    #7 Text 0 File ThreadedTransferInterface.cpp, Line 936
    Prepare [_NEC DVD+-RW ND-3530A (H:1 T:0)] for write in CUE-sheet-DAO
    DAO infos:
    ==========
     MCN: ""
     TOCType: 0x00; Session Closed, disc fixated
     Tracks 1 to 1:                                  Idx 0         Idx 1      Next Trk
       1: TRM_DATA_MODE1, 2048/0x00, FilePos             0             0    4472690688, ISRC ""
    DAO layout:
    ===========
     ___Start_|____Track_|_Idx_|_CtrlAdr_|_____Size_|______NWA_|_RecDep__________
            0 |  lead-in |   0 |    0x41 |        0 |        0 | 0x00
            0 |        1 |   0 |    0x41 |        0 |        0 | 0x00
            0 |        1 |   1 |    0x41 |  2183931 |  2183931 | 0x00
      2183931 | lead-out |   1 |    0x41 |        0 |        0 | 0x00
    
14:40:38    #8 Text 0 File Burncd.cpp, Line 4354
    Caching options: cache CDRom or Network-No, small files-Yes (<32KB)
    
14:40:38    #9 Phase 24 File ExtendedProgress.cpp, Line 537
    Caching of files started
    
14:40:38    #10 Text 0 File Burncd.cpp, Line 4476
    Cache writing successful.
    
14:40:38    #11 Phase 25 File ExtendedProgress.cpp, Line 537
    Caching of files completed
    
14:40:38    #12 Phase 36 File ExtendedProgress.cpp, Line 537
    Burn process started at 8x (11080 KB/s)
    
14:40:39    #13 Text 0 File ThreadedTransferInterface.cpp, Line 2690
    Verifying disc position of item 0 (not relocatable, no disc pos, no patch infos, orig at #0): write at #0
    
14:40:39    #14 Text 0 File DVDR.cpp, Line 3287
    Recording mode: Sequential Recording Mode
    
14:40:39    #15 Text 0 File DVDR.cpp, Line 3441
    Start write address at LBA 0
    DVD high compatibility mode: Yes
    
14:40:39    #16 Text 0 File Cdrdrv.cpp, Line 10169
    ---- Disc Structure: Physical Format Information (00h) ----
    Media Type: 0, Layer: 0, Address: 0 (0 h), AGID: 0; Length: 2050
     Book Type: DVD-R (2), Part Version: 2.0x (5), Extended Part Version: 2.1 (33)
     Disc Size: 120 mm,      Maximum Transfer Rate: <not specified> (F h)
     Number of Layers: 1,    Track Path: Parallel Track Path (PTP),  Layer Type: recordable
     Linear Density:         0,267 um/bit,  Track Density:  0,74 um/track
     Starting Physical Sector Number of Data Area: 30000 h (DVD-ROM, DVD-R/-RW, DVD+R/+RW)
     Outer Limit of Data Recordable Area:          26127F h
     Data in Burst Cutting Area (BCA) does not exist
      Revision number of maximum recording speed: 6.0
      Revision number of minimum recording speed: -
      Revision number table of recording speed: 1.0 2.0 3.0 4.0 5.0 - - 
      Class: 0,  Extended part version: 33
      Start PSN of the Extra Border Zone: 2FE10 h
      Start PSN of Physical format information blocks in Extra Border Zone: 2FFA0 h
     Media Specific [16..783]:
        00 60 00 10 20 30 40 50 - 00 00 00 21 00 00 00 00    .`...0@P...!....
        00 02 FE 10 00 02 FF A0 - 00 00 00 00 00 00 00 00    ................
        00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
        00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
        00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
        00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
        00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
        00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
        00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
        00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
        00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
        00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
        00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
        00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
        00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
        00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
        00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
        00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
        00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
        00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
        00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
        00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
        00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
        00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
        00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
        00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
        00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
        00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
        00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
        00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
        00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
        1D 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
        01 40 C1 FD 9E D8 52 00 - 02 85 0D 10 88 9A 80 00    .@....R.........
        03 4D 42 49 20 30 31 00 - 04 52 47 34 30 00 00 00    .MBI.01..RG40...
        05 88 80 00 00 00 02 00 - 06 09 0D 13 87 78 80 00    .............x..
        07 88 80 00 00 00 00 00 - 08 05 15 0D 10 0B 0A 00    ................
        09 98 08 0F 0B 78 88 00 - 0A 80 00 00 00 00 10 00    .....x..........
        0B 07 19 15 A7 88 75 00 - 0C 99 BC AA A2 20 22 00    ......u.......".
        0D 00 00 D0 00 00 00 00 - 0E 09 25 33 2F 29 1E 00    ..........%3/)..
        0F 50 21 2D 1F 9A B6 00 - 10 88 84 00 04 00 04 00    .P!-............
        11 00 00 00 00 00 00 00 - 12 09 2F 37 2F 29 1E 00    ........../7/)..
        13 50 1F 2D 1F 9A B6 00 - 14 88 C4 00 04 00 04 00    .P.-............
        15 00 00 00 00 00 00 00 - 16 0B 3F 33 2F 29 1E 00    ..........?3/)..
        17 50 21 2D 1F 9A B6 00 - 18 88 84 00 04 00 04 00    .P!-............
        19 00 00 00 00 00 00 00 - 1A 0B 51 37 2F 29 1E 00    ..........Q7/)..
        1B 50 1F 2D 1F 9A B6 00 - 1C 88 C4 00 04 00 04 00    .P.-............
        1D 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
        00 00 00 00 00 00 00 00 - 00 00 00 00 00 00 00 00    ................
    
14:40:39    #17 SCSI -1046 File SCSIInterface.cpp, Line 367
    SCSI Exec, HA 1, TA 0, LUN 0
    Status:     0x04 (0x01, SCSI_ERR)
    HA-Status   0x00 (0x00, OK)
    TA-Status   0x05 (0x0B, SCSI_TASTATUS_FAILED)
    Sense Key:  0x05 (KEY_ILLEGAL_REQUEST)
    Sense Code: 0x30
    Sense Qual: 0x05
    CDB Data:   0x53 0x00 0x00 0x00 0x00 0x00 0x21 0x53 0x00 0x00 0x00 0x00 
    Sense Data: 0x70 0x00 0x05 0x00 0x00 0x00 0x00 0x0A 
                0x00 0x00 0x00 0x00 0x30 0x05 
    
14:40:39    #18 Text 0 File DVDR.cpp, Line 3579
    Reserved Track size: 2183936 (215300h, 4265MB) -> return code -1046
    
14:40:39    #19 CDR -1046 File ThreadedTransferInterface.cpp, Line 1688
    Illegal disc
    _NEC DVD+-RW ND-3530A (H:1 T:0)
    
14:40:39    #20 TRANSFER -27 File ThreadedTransferInterface.cpp, Line 1688
    Could not perform start of Disc-at-once
    
14:40:39    #21 Text 0 File DVDPlusDualLayer.cpp, Line 1455
    SetDriveCaps: Set LAST LBA of layer 1 to 0
    
14:40:39    #22 Text 0 File ThreadedTransfer.cpp, Line 273
    Pipe memory size 83836800
    
14:40:39    #23 Phase 38 File ExtendedProgress.cpp, Line 537
    Burn process failed at 8x (11080 KB/s)

---

