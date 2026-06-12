---
title: "Brasero Fails to finish the CD/DVD"
date: 2009-12-26
forum: General Help
---

### Post by signlesskid on 2009-12-26
Hi, This is Amir.
It is a while that I have problem with burning Disks by Brasero. I tried burning files, images on many disks but it seems to fails every time. Here is the log. Hope someone could help me.

Checking session consistency (brasero_burn_check_session_consistency brasero-burn.c:1848)
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_set_output_size_for_current_track
BraseroBurnURI stopping
BraseroBurnURI called brasero_job_get_action
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
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_current_track
BraseroLocalTrack no remote URIs
BraseroLocalTrack stopping
BraseroChecksumFiles called brasero_job_get_output_type
BraseroChecksumFiles called brasero_job_get_current_track
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_set_output_size_for_current_track
BraseroChecksumFiles stopping
BraseroChecksumFiles called brasero_job_get_output_type
BraseroChecksumFiles called brasero_job_get_current_track
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_get_session_output_size
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_get_current_track
BraseroChecksumFiles called brasero_job_get_current_track
BraseroChecksumFiles called brasero_job_set_current_action
BraseroChecksumFiles called brasero_job_get_flags
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_get_current_track
BraseroChecksumFiles Adding graft for checksum file /.checksum.md5 file:///tmp/brasero_tmp_LQ7D5U.md5
BraseroChecksumFiles called brasero_job_add_track
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles Finished track successfully
BraseroChecksumFiles stopping
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_flags
BraseroWodim called brasero_job_get_action
BraseroWodim creating input
BraseroWodim getting varg
BraseroWodim called brasero_job_get_action
BraseroWodim got varg:
BraseroWodim deactivating
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage creating input
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_fd_in
BraseroChecksumImage deactivating
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage getting varg
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage called brasero_job_get_current_track
BraseroGenisoimage called brasero_job_get_tmp_dir
BraseroGenisoimage called brasero_job_get_data_label
BraseroGenisoimage called brasero_job_get_flags
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage called brasero_job_set_current_action
BraseroGenisoimage got varg:
    /usr/bin/genisoimage
    -input-charset
    utf8
    -r
    -J
    -graft-points
    -path-list
    /tmp/brasero_tmp_5AJF5U
    -exclude-list
    /tmp/brasero_tmp_M8IF5U
    -V
    Data disc (26 Dec 09)
    -A
    Brasero-2.28.2
    -sysid
    LINUX
    -quiet
    -print-size
BraseroGenisoimage Launching command
BraseroGenisoimage called brasero_job_get_fd_out
BraseroGenisoimage stderr: HUP
BraseroGenisoimage stdout: 331242
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage called brasero_job_set_output_size_for_current_track
BraseroGenisoimage stdout: HUP
BraseroGenisoimage process finished with status 0
BraseroGenisoimage called brasero_job_get_fd_out
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage Finished track successfully
BraseroGenisoimage got killed
BraseroGenisoimage stopping
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_flags
BraseroWodim called brasero_job_get_action
BraseroWodim creating input
BraseroWodim getting varg
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_get_device
BraseroWodim called brasero_job_get_flags
BraseroWodim called brasero_job_get_speed
BraseroWodim called brasero_job_get_flags
BraseroWodim called brasero_job_get_input_type
BraseroWodim called brasero_job_get_fd_in
BraseroWodim called brasero_job_get_input_type
BraseroWodim called brasero_job_get_session_output_size
BraseroWodim called brasero_job_set_current_action
BraseroWodim got varg:
    wodim
    -v
    dev=/dev/sr0
    speed=24
    driveropts=burnfree
    fs=29m
    tsize=331242s
    -data
    -nopad
    -
BraseroWodim Launching command
BraseroWodim called brasero_job_get_fd_out
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage linked to BraseroWodim
BraseroChecksumImage creating input
BraseroChecksumImage called brasero_job_get_action
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage linked to BraseroChecksumImage
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_current_track
BraseroGenisoimage getting varg
BraseroChecksumImage called brasero_job_get_input_type
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_set_current_action
BraseroChecksumImage called brasero_job_get_fd_in
BraseroChecksumImage Starting checksum generation live (size = 0)
BraseroChecksumImage called brasero_job_set_nonblocking
BraseroChecksumImage called brasero_job_get_fd_in
BraseroChecksumImage called brasero_job_get_fd_out
BraseroChecksumImage called brasero_job_get_fd_in
BraseroChecksumImage called brasero_job_get_fd_out
BraseroGenisoimage called brasero_job_get_tmp_dir
BraseroGenisoimage called brasero_job_get_data_label
BraseroGenisoimage called brasero_job_get_flags
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage called brasero_job_get_fd_out
BraseroGenisoimage called brasero_job_set_current_action
BraseroGenisoimage got varg:
    /usr/bin/genisoimage
    -input-charset
    utf8
    -r
    -J
    -graft-points
    -path-list
    /tmp/brasero_tmp_FN4P5U
    -exclude-list
    /tmp/brasero_tmp_1K4P5U
    -V
    Data disc (26 Dec 09)
    -A
    Brasero-2.28.2
    -sysid
    LINUX
BraseroGenisoimage Launching command
BraseroGenisoimage called brasero_job_get_fd_out
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
BraseroWodim stdout: Vendor_info    : 'SONY    '
BraseroWodim stdout: Identification : 'DVD RW DRU-870S '
BraseroWodim stdout: Revision       : '1.60'
BraseroWodim stdout: Device seems to be: Generic mmc2 DVD-R/DVD-RW.
BraseroWodim stdout: Current: 0x0009 (CD-R)
BraseroWodim stdout: Profile: 0x002B (DVD+R/DL) 
BraseroWodim stdout: Profile: 0x001B (DVD+R) 
BraseroWodim stdout: Profile: 0x001A (DVD+RW) 
BraseroWodim stdout: Profile: 0x0016 (DVD-R/DL layer jump recording) 
BraseroWodim stdout: Profile: 0x0015 (DVD-R/DL sequential recording) 
BraseroWodim stdout: Profile: 0x0014 (DVD-RW sequential recording) 
BraseroWodim stdout: Profile: 0x0013 (DVD-RW restricted overwrite) 
BraseroWodim stdout: Profile: 0x0012 (DVD-RAM) 
BraseroWodim stdout: Profile: 0x0011 (DVD-R sequential recording) 
BraseroWodim stdout: Profile: 0x0010 (DVD-ROM) 
BraseroWodim stdout: Profile: 0x000A (CD-RW) 
BraseroWodim stdout: Profile: 0x0009 (CD-R) (current)
BraseroWodim stdout: Profile: 0x0008 (CD-ROM) (current)
BraseroWodim stdout: Profile: 0x0002 (Removable disk) 
BraseroWodim stdout: Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
BraseroWodim stdout: Driver flags   : MMC-3 SWABAUDIO BURNFREE 
BraseroWodim stdout: Supported modes: TAO PACKET SAO SAO/R96R RAW/R96R
BraseroWodim stdout: Drive buf size : 1273856 = 1244 KB
BraseroWodim stdout: FIFO size      : 30408704 = 29696 KB
BraseroWodim stderr: Speed set to 4234 KB/s
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Track 01: data   646 MB        
BraseroWodim stdout: Total size:      742 MB (73:36.58) = 331244 sectors
BraseroWodim stdout: Lout start:      743 MB (73:38/44) = 331244 sectors
BraseroWodim stdout: Current Secsize: 2048
BraseroWodim stdout: ATIP info from disk:
BraseroWodim stdout:   Indicated writing power: 5
BraseroWodim stdout:   Is not unrestricted
BraseroWodim stdout:   Is not erasable
BraseroWodim stdout:   Disk sub type: Medium Type B, low Beta category (B-) (4)
BraseroWodim stdout:   ATIP start of lead in:  -11607 (97:27/18)
BraseroWodim stdout:   ATIP start of lead out: 359849 (79:59/74)
BraseroWodim stdout: Disk type:    Short strategy type (Phthalocyanine or similar)
BraseroWodim stdout: Manuf. index: 18
BraseroWodim stdout: Manufacturer: Plasmon Data systems Ltd.
BraseroWodim stdout: Blocks total: 359849 Blocks current: 359849 Blocks remaining: 28605
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
BraseroGenisoimage stderr:   1.51% done, estimate finish Sat Dec 26 08:48:04 2009
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
BraseroGenisoimage stderr:   3.02% done, estimate finish Sat Dec 26 08:47:31 2009
BraseroWodim stdout: Waiting for reader process to fill input buffer ... input buffer ready.
BraseroWodim stdout: Performing OPC...
BraseroWodim stdout: Starting new track at sector: 0
BraseroWodim stdout: 
BraseroWodim stdout: Track 01:    0 of  646 MB written.
BraseroGenisoimage stderr:   4.53% done, estimate finish Sat Dec 26 08:49:10 2009
BraseroWodim stdout: Track 01:    1 of  646 MB written (fifo  96%) [buf  84%] 229.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    2 of  646 MB written (fifo 100%) [buf 100%]   2.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    3 of  646 MB written (fifo 100%) [buf 100%]  19.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    4 of  646 MB written (fifo  99%) [buf 100%]  18.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    5 of  646 MB written (fifo 100%) [buf 100%]  19.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    6 of  646 MB written (fifo 100%) [buf 100%]  18.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    7 of  646 MB written (fifo 100%) [buf 100%]  19.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    8 of  646 MB written (fifo 100%) [buf 100%]  18.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    9 of  646 MB written (fifo 100%) [buf 100%]  19.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:   6.04% done, estimate finish Sat Dec 26 08:50:00 2009
BraseroWodim stdout: Track 01:   10 of  646 MB written (fifo 100%) [buf 100%]  18.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   11 of  646 MB written (fifo 100%) [buf 100%]  19.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   12 of  646 MB written (fifo 100%) [buf 100%]  18.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   13 of  646 MB written (fifo 100%) [buf 100%]  19.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   14 of  646 MB written (fifo 100%) [buf 100%]  19.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   15 of  646 MB written (fifo 100%) [buf 100%]  19.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   16 of  646 MB written (fifo 100%) [buf 100%]  19.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   17 of  646 MB written (fifo 100%) [buf 100%]  19.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   18 of  646 MB written (fifo 100%) [buf 100%]  19.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   19 of  646 MB written (fifo 100%) [buf 100%]  19.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:   7.55% done, estimate finish Sat Dec 26 08:49:37 2009
BraseroWodim stdout: Track 01:   20 of  646 MB written (fifo 100%) [buf 100%]  19.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   21 of  646 MB written (fifo 100%) [buf 100%]  19.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   22 of  646 MB written (fifo 100%) [buf 100%]  19.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   23 of  646 MB written (fifo 100%) [buf 100%]  19.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   24 of  646 MB written (fifo 100%) [buf 100%]  19.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   25 of  646 MB written (fifo 100%) [buf 100%]  20.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   26 of  646 MB written (fifo 100%) [buf 100%]  19.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   27 of  646 MB written (fifo 100%) [buf 100%]  20.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   28 of  646 MB written (fifo 100%) [buf 100%]  19.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   29 of  646 MB written (fifo 100%) [buf 100%]  20.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:   9.06% done, estimate finish Sat Dec 26 08:49:32 2009
BraseroWodim stdout: Track 01:   30 of  646 MB written (fifo 100%) [buf 100%]  19.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   31 of  646 MB written (fifo 100%) [buf 100%]  20.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   32 of  646 MB written (fifo 100%) [buf 100%]  19.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   33 of  646 MB written (fifo 100%) [buf 100%]  20.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   34 of  646 MB written (fifo 100%) [buf 100%]  20.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   35 of  646 MB written (fifo 100%) [buf 100%]  20.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   36 of  646 MB written (fifo 100%) [buf 100%]  21.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   37 of  646 MB written (fifo 100%) [buf 100%]  20.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   38 of  646 MB written (fifo  99%) [buf 100%]  21.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   39 of  646 MB written (fifo  99%) [buf 100%]  20.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  10.57% done, estimate finish Sat Dec 26 08:49:20 2009
BraseroWodim stdout: Track 01:   40 of  646 MB written (fifo 100%) [buf 100%]  21.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   41 of  646 MB written (fifo 100%) [buf 100%]  20.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   42 of  646 MB written (fifo 100%) [buf 100%]  21.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   43 of  646 MB written (fifo 100%) [buf 100%]  20.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   44 of  646 MB written (fifo  99%) [buf 100%]  21.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   45 of  646 MB written (fifo  99%) [buf 100%]  20.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   46 of  646 MB written (fifo  99%) [buf 100%]  21.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   47 of  646 MB written (fifo  99%) [buf 100%]  20.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   48 of  646 MB written (fifo  99%) [buf 100%]  21.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   49 of  646 MB written (fifo 100%) [buf 100%]  20.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  12.08% done, estimate finish Sat Dec 26 08:49:10 2009
BraseroWodim stdout: Track 01:   50 of  646 MB written (fifo 100%) [buf 100%]  21.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   51 of  646 MB written (fifo 100%) [buf 100%]  20.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   52 of  646 MB written (fifo 100%) [buf 100%]  21.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   53 of  646 MB written (fifo 100%) [buf 100%]  20.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   54 of  646 MB written (fifo 100%) [buf 100%]  21.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   55 of  646 MB written (fifo 100%) [buf 100%]  21.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   56 of  646 MB written (fifo 100%) [buf 100%]  21.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   57 of  646 MB written (fifo 100%) [buf 100%]  21.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   58 of  646 MB written (fifo 100%) [buf 100%]  21.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  13.59% done, estimate finish Sat Dec 26 08:49:10 2009
BraseroWodim stdout: Track 01:   59 of  646 MB written (fifo 100%) [buf 100%]  21.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   60 of  646 MB written (fifo 100%) [buf 100%]  21.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   61 of  646 MB written (fifo 100%) [buf 100%]  21.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   62 of  646 MB written (fifo  99%) [buf 100%]  21.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   63 of  646 MB written (fifo 100%) [buf 100%]  21.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   64 of  646 MB written (fifo 100%) [buf 100%]  21.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   65 of  646 MB written (fifo 100%) [buf 100%]  22.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   66 of  646 MB written (fifo 100%) [buf 100%]  21.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   67 of  646 MB written (fifo 100%) [buf 100%]  22.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   68 of  646 MB written (fifo 100%) [buf 100%]  21.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  15.10% done, estimate finish Sat Dec 26 08:49:04 2009
BraseroWodim stdout: Track 01:   69 of  646 MB written (fifo  99%) [buf 100%]  22.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   70 of  646 MB written (fifo 100%) [buf 100%]  22.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   71 of  646 MB written (fifo 100%) [buf 100%]  22.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   72 of  646 MB written (fifo 100%) [buf 100%]   3.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   73 of  646 MB written (fifo  99%) [buf 100%]  22.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   74 of  646 MB written (fifo  99%) [buf 100%]  22.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   75 of  646 MB written (fifo  98%) [buf 100%]  22.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   76 of  646 MB written (fifo  97%) [buf 100%]  22.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   77 of  646 MB written (fifo  97%) [buf 100%]  22.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   78 of  646 MB written (fifo  96%) [buf 100%]  22.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   79 of  646 MB written (fifo  96%) [buf 100%]  23.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  16.61% done, estimate finish Sat Dec 26 08:49:10 2009
BraseroWodim stdout: Track 01:   80 of  646 MB written (fifo  97%) [buf 100%]  22.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   81 of  646 MB written (fifo  97%) [buf 100%]  23.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   82 of  646 MB written (fifo  97%) [buf 100%]  22.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   83 of  646 MB written (fifo  97%) [buf 100%]  23.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   84 of  646 MB written (fifo  97%) [buf 100%]  22.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   85 of  646 MB written (fifo  98%) [buf 100%]  23.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   86 of  646 MB written (fifo  98%) [buf 100%]  22.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   87 of  646 MB written (fifo  98%) [buf 100%]  23.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   88 of  646 MB written (fifo  98%) [buf 100%]  22.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  18.11% done, estimate finish Sat Dec 26 08:48:59 2009
BraseroWodim stdout: Track 01:   89 of  646 MB written (fifo  98%) [buf 100%]  23.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   90 of  646 MB written (fifo  98%) [buf 100%]  22.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   91 of  646 MB written (fifo  98%) [buf 100%]  23.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   92 of  646 MB written (fifo  99%) [buf 100%]  22.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   93 of  646 MB written (fifo  98%) [buf 100%]  23.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   94 of  646 MB written (fifo  98%) [buf 100%]  22.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   95 of  646 MB written (fifo  98%) [buf 100%]  23.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   96 of  646 MB written (fifo  98%) [buf 100%]  24.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   97 of  646 MB written (fifo  98%) [buf 100%]  23.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   98 of  646 MB written (fifo  98%) [buf 100%]  24.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  19.63% done, estimate finish Sat Dec 26 08:48:55 2009
BraseroWodim stdout: Track 01:   99 of  646 MB written (fifo  98%) [buf 100%]  23.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  100 of  646 MB written (fifo  98%) [buf 100%]  24.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  101 of  646 MB written (fifo  98%) [buf 100%]  23.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  102 of  646 MB written (fifo  98%) [buf 100%]  24.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  103 of  646 MB written (fifo  98%) [buf 100%]  23.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  104 of  646 MB written (fifo  98%) [buf 100%]  24.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  105 of  646 MB written (fifo  98%) [buf 100%]  23.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  106 of  646 MB written (fifo  98%) [buf 100%]  24.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  107 of  646 MB written (fifo  98%) [buf 100%]  23.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  108 of  646 MB written (fifo  98%) [buf 100%]  24.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  21.13% done, estimate finish Sat Dec 26 08:48:52 2009
BraseroWodim stdout: Track 01:  109 of  646 MB written (fifo  98%) [buf 100%]  23.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  110 of  646 MB written (fifo  98%) [buf 100%]  24.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  111 of  646 MB written (fifo 100%) [buf 100%]   4.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  112 of  646 MB written (fifo  99%) [buf 100%]  25.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  113 of  646 MB written (fifo  99%) [buf 100%]  24.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  114 of  646 MB written (fifo  99%) [buf 100%]  25.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  115 of  646 MB written (fifo  99%) [buf 100%]  24.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  116 of  646 MB written (fifo  98%) [buf 100%]  25.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  117 of  646 MB written (fifo  98%) [buf 100%]  24.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  22.64% done, estimate finish Sat Dec 26 08:48:53 2009
BraseroWodim stdout: Track 01:  118 of  646 MB written (fifo  98%) [buf 100%]  24.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  119 of  646 MB written (fifo  98%) [buf 100%]  24.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  120 of  646 MB written (fifo  98%) [buf 100%]  24.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  121 of  646 MB written (fifo  98%) [buf 100%]  24.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  122 of  646 MB written (fifo  98%) [buf 100%]  24.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  123 of  646 MB written (fifo  97%) [buf 100%]  24.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  124 of  646 MB written (fifo  97%) [buf 100%]  24.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  125 of  646 MB written (fifo  97%) [buf 100%]  24.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  126 of  646 MB written (fifo  97%) [buf 100%]  24.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  127 of  646 MB written (fifo  97%) [buf 100%]  25.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  128 of  646 MB written (fifo  97%) [buf 100%]  24.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  24.16% done, estimate finish Sat Dec 26 08:48:50 2009
BraseroWodim stdout: Track 01:  129 of  646 MB written (fifo  96%) [buf 100%]  25.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  130 of  646 MB written (fifo  96%) [buf 100%]  24.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  131 of  646 MB written (fifo  96%) [buf 100%]  25.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  132 of  646 MB written (fifo  95%) [buf 100%]  24.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  133 of  646 MB written (fifo  95%) [buf 100%]  25.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  134 of  646 MB written (fifo  95%) [buf 100%]  24.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  135 of  646 MB written (fifo  95%) [buf 100%]  25.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  136 of  646 MB written (fifo  95%) [buf 100%]  24.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  137 of  646 MB written (fifo  95%) [buf 100%]  25.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  138 of  646 MB written (fifo  94%) [buf 100%]  24.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  25.66% done, estimate finish Sat Dec 26 08:48:47 2009
BraseroWodim stdout: Track 01:  139 of  646 MB written (fifo  94%) [buf 100%]  25.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  140 of  646 MB written (fifo  94%) [buf 100%]  24.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  141 of  646 MB written (fifo  94%) [buf 100%]  25.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  142 of  646 MB written (fifo  94%) [buf 100%]  24.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  143 of  646 MB written (fifo  93%) [buf 100%]  25.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  144 of  646 MB written (fifo  93%) [buf 100%]  24.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  145 of  646 MB written (fifo  93%) [buf 100%]  25.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  146 of  646 MB written (fifo  93%) [buf 100%]  24.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  147 of  646 MB written (fifo  93%) [buf 100%]  24.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  148 of  646 MB written (fifo  93%) [buf 100%]  24.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  27.17% done, estimate finish Sat Dec 26 08:48:45 2009
BraseroWodim stdout: Track 01:  149 of  646 MB written (fifo  93%) [buf 100%]  24.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  150 of  646 MB written (fifo  92%) [buf 100%]  24.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  151 of  646 MB written (fifo  92%) [buf 100%]  24.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  152 of  646 MB written (fifo  92%) [buf 100%]  24.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  153 of  646 MB written (fifo  92%) [buf 100%]  24.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  154 of  646 MB written (fifo  92%) [buf 100%]  24.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  155 of  646 MB written (fifo  92%) [buf 100%]  24.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  156 of  646 MB written (fifo  92%) [buf 100%]  24.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  157 of  646 MB written (fifo  92%) [buf 100%]  24.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  158 of  646 MB written (fifo  92%) [buf 100%]  25.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  28.68% done, estimate finish Sat Dec 26 08:48:43 2009
BraseroWodim stdout: Track 01:  159 of  646 MB written (fifo  91%) [buf 100%]  24.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  160 of  646 MB written (fifo  91%) [buf 100%]  25.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  161 of  646 MB written (fifo  91%) [buf 100%]  24.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  162 of  646 MB written (fifo  91%) [buf 100%]  25.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  163 of  646 MB written (fifo  91%) [buf 100%]  24.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  164 of  646 MB written (fifo  90%) [buf 100%]  25.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  165 of  646 MB written (fifo  90%) [buf 100%]  24.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  166 of  646 MB written (fifo  90%) [buf 100%]  25.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  167 of  646 MB written (fifo  90%) [buf 100%]  24.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  168 of  646 MB written (fifo  90%) [buf 100%]  25.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  30.19% done, estimate finish Sat Dec 26 08:48:41 2009
BraseroWodim stdout: Track 01:  169 of  646 MB written (fifo  90%) [buf 100%]  24.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  170 of  646 MB written (fifo  90%) [buf 100%]  25.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  171 of  646 MB written (fifo  90%) [buf 100%]  24.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  172 of  646 MB written (fifo  89%) [buf 100%]  25.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  173 of  646 MB written (fifo  89%) [buf 100%]  24.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  174 of  646 MB written (fifo  89%) [buf 100%]  25.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  175 of  646 MB written (fifo  89%) [buf 100%]  24.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  176 of  646 MB written (fifo  89%) [buf 100%]  25.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  177 of  646 MB written (fifo  89%) [buf 100%]  24.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  178 of  646 MB written (fifo  89%) [buf 100%]  25.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  179 of  646 MB written (fifo  88%) [buf 100%]  24.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  31.70% done, estimate finish Sat Dec 26 08:48:39 2009
BraseroWodim stdout: Track 01:  180 of  646 MB written (fifo  88%) [buf 100%]  24.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  181 of  646 MB written (fifo  88%) [buf 100%]  24.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  182 of  646 MB written (fifo  97%) [buf 100%]   6.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  183 of  646 MB written (fifo  97%) [buf 100%]  24.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  184 of  646 MB written (fifo  96%) [buf 100%]  24.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  185 of  646 MB written (fifo  96%) [buf 100%]  24.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  186 of  646 MB written (fifo  96%) [buf 100%]  24.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  33.21% done, estimate finish Sat Dec 26 08:48:37 2009
BraseroWodim stdout: Track 01:  187 of  646 MB written (fifo  95%) [buf 100%]  24.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  188 of  646 MB written (fifo  95%) [buf 100%]  24.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  189 of  646 MB written (fifo  95%) [buf 100%]  25.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  190 of  646 MB written (fifo  95%) [buf 100%]  24.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  191 of  646 MB written (fifo  95%) [buf 100%]  25.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  192 of  646 MB written (fifo  94%) [buf 100%]  24.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  193 of  646 MB written (fifo  94%) [buf 100%]  25.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  194 of  646 MB written (fifo  94%) [buf 100%]  24.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  195 of  646 MB written (fifo  94%) [buf 100%]  25.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  196 of  646 MB written (fifo  94%) [buf 100%]  24.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  197 of  646 MB written (fifo  94%) [buf 100%]  25.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  34.72% done, estimate finish Sat Dec 26 08:48:36 2009
BraseroWodim stdout: Track 01:  198 of  646 MB written (fifo  94%) [buf 100%]  24.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  199 of  646 MB written (fifo  93%) [buf 100%]  25.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  200 of  646 MB written (fifo  93%) [buf 100%]  24.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  201 of  646 MB written (fifo  93%) [buf 100%]  25.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  202 of  646 MB written (fifo  93%) [buf 100%]  24.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  203 of  646 MB written (fifo  93%) [buf 100%]  25.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  204 of  646 MB written (fifo  93%) [buf 100%]  24.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  205 of  646 MB written (fifo  93%) [buf 100%]  25.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  206 of  646 MB written (fifo  92%) [buf 100%]  24.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  207 of  646 MB written (fifo  92%) [buf 100%]  25.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  36.23% done, estimate finish Sat Dec 26 08:48:35 2009
BraseroWodim stdout: Track 01:  208 of  646 MB written (fifo  92%) [buf 100%]  24.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  209 of  646 MB written (fifo  92%) [buf 100%]  24.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  210 of  646 MB written (fifo  92%) [buf 100%]  24.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  211 of  646 MB written (fifo  92%) [buf 100%]  24.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  212 of  646 MB written (fifo  92%) [buf 100%]  24.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  213 of  646 MB written (fifo  92%) [buf 100%]  24.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  214 of  646 MB written (fifo  92%) [buf 100%]  24.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  215 of  646 MB written (fifo  91%) [buf 100%]  24.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  216 of  646 MB written (fifo  91%) [buf 100%]  24.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  217 of  646 MB written (fifo  91%) [buf 100%]  24.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  37.74% done, estimate finish Sat Dec 26 08:48:31 2009
BraseroWodim stdout: Track 01:  218 of  646 MB written (fifo  91%) [buf 100%]  24.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  219 of  646 MB written (fifo  91%) [buf 100%]  24.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  220 of  646 MB written (fifo  91%) [buf 100%]  25.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  221 of  646 MB written (fifo  90%) [buf 100%]  24.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  222 of  646 MB written (fifo  90%) [buf 100%]  25.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  223 of  646 MB written (fifo  90%) [buf 100%]  24.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  224 of  646 MB written (fifo  90%) [buf 100%]  25.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  225 of  646 MB written (fifo  90%) [buf 100%]  24.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  226 of  646 MB written (fifo  89%) [buf 100%]  25.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  227 of  646 MB written (fifo  89%) [buf 100%]  24.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  39.25% done, estimate finish Sat Dec 26 08:48:30 2009
BraseroWodim stdout: Track 01:  228 of  646 MB written (fifo  89%) [buf 100%]  25.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  229 of  646 MB written (fifo  89%) [buf 100%]  24.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  230 of  646 MB written (fifo  89%) [buf 100%]  25.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  231 of  646 MB written (fifo  88%) [buf 100%]  24.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  232 of  646 MB written (fifo  88%) [buf 100%]  25.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  233 of  646 MB written (fifo  88%) [buf 100%]  24.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  234 of  646 MB written (fifo  88%) [buf 100%]  25.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  235 of  646 MB written (fifo  88%) [buf 100%]  24.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  236 of  646 MB written (fifo  88%) [buf 100%]  25.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  237 of  646 MB written (fifo  88%) [buf 100%]  24.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  40.76% done, estimate finish Sat Dec 26 08:48:29 2009
BraseroWodim stdout: Track 01:  238 of  646 MB written (fifo  88%) [buf 100%]  25.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  239 of  646 MB written (fifo  88%) [buf 100%]  24.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  240 of  646 MB written (fifo  87%) [buf 100%]  24.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  241 of  646 MB written (fifo  87%) [buf 100%]  24.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  242 of  646 MB written (fifo  87%) [buf 100%]  24.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  243 of  646 MB written (fifo  87%) [buf 100%]  24.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  244 of  646 MB written (fifo  87%) [buf 100%]  24.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  245 of  646 MB written (fifo  87%) [buf 100%]  24.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  246 of  646 MB written (fifo  87%) [buf 100%]  24.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  247 of  646 MB written (fifo  86%) [buf 100%]  24.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  248 of  646 MB written (fifo  86%) [buf 100%]  24.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  42.27% done, estimate finish Sat Dec 26 08:48:28 2009
BraseroWodim stdout: Track 01:  249 of  646 MB written (fifo  86%) [buf 100%]  24.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  250 of  646 MB written (fifo  86%) [buf 100%]  24.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  251 of  646 MB written (fifo  86%) [buf 100%]  25.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  252 of  646 MB written (fifo  94%) [buf 100%]   7.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  253 of  646 MB written (fifo  94%) [buf 100%]  25.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  254 of  646 MB written (fifo  94%) [buf 100%]  24.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  255 of  646 MB written (fifo  93%) [buf 100%]  25.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  43.77% done, estimate finish Sat Dec 26 08:48:27 2009
BraseroWodim stdout: Track 01:  256 of  646 MB written (fifo  93%) [buf 100%]  24.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  257 of  646 MB written (fifo  93%) [buf 100%]  25.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  258 of  646 MB written (fifo  93%) [buf 100%]  24.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  259 of  646 MB written (fifo  93%) [buf 100%]  25.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  260 of  646 MB written (fifo  93%) [buf 100%]  24.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  261 of  646 MB written (fifo  93%) [buf 100%]  25.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  262 of  646 MB written (fifo  92%) [buf 100%]  24.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  263 of  646 MB written (fifo  92%) [buf 100%]  25.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  264 of  646 MB written (fifo  92%) [buf 100%]  24.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  265 of  646 MB written (fifo  92%) [buf 100%]  25.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  266 of  646 MB written (fifo  92%) [buf 100%]  24.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  45.29% done, estimate finish Sat Dec 26 08:48:26 2009
BraseroWodim stdout: Track 01:  267 of  646 MB written (fifo  92%) [buf 100%]  25.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  268 of  646 MB written (fifo  92%) [buf 100%]  24.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  269 of  646 MB written (fifo  92%) [buf 100%]  25.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  270 of  646 MB written (fifo  92%) [buf 100%]  24.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  271 of  646 MB written (fifo  92%) [buf 100%]  24.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  272 of  646 MB written (fifo  92%) [buf 100%]  24.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  273 of  646 MB written (fifo  91%) [buf 100%]  24.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  274 of  646 MB written (fifo  91%) [buf 100%]  24.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  275 of  646 MB written (fifo  91%) [buf 100%]  24.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  276 of  646 MB written (fifo  91%) [buf 100%]  24.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  46.79% done, estimate finish Sat Dec 26 08:48:26 2009
BraseroWodim stdout: Track 01:  277 of  646 MB written (fifo  91%) [buf 100%]  24.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  278 of  646 MB written (fifo  91%) [buf 100%]  24.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  279 of  646 MB written (fifo  90%) [buf 100%]  24.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  280 of  646 MB written (fifo  90%) [buf 100%]  24.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  281 of  646 MB written (fifo  90%) [buf 100%]  24.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  282 of  646 MB written (fifo  90%) [buf 100%]  25.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  283 of  646 MB written (fifo  90%) [buf 100%]  24.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  284 of  646 MB written (fifo  90%) [buf 100%]  25.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  285 of  646 MB written (fifo  90%) [buf 100%]  24.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  286 of  646 MB written (fifo  90%) [buf 100%]  25.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  48.31% done, estimate finish Sat Dec 26 08:48:25 2009
BraseroWodim stdout: Track 01:  287 of  646 MB written (fifo  89%) [buf 100%]  24.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  288 of  646 MB written (fifo  89%) [buf 100%]  25.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  289 of  646 MB written (fifo  89%) [buf 100%]  24.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  290 of  646 MB written (fifo  89%) [buf 100%]  25.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  291 of  646 MB written (fifo  89%) [buf 100%]  24.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  292 of  646 MB written (fifo  88%) [buf 100%]  25.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  293 of  646 MB written (fifo  88%) [buf 100%]  24.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  294 of  646 MB written (fifo  88%) [buf 100%]  25.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  295 of  646 MB written (fifo  88%) [buf 100%]  24.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  296 of  646 MB written (fifo  88%) [buf 100%]  25.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  49.81% done, estimate finish Sat Dec 26 08:48:24 2009
BraseroWodim stdout: Track 01:  297 of  646 MB written (fifo  88%) [buf 100%]  24.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  298 of  646 MB written (fifo  88%) [buf 100%]  25.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  299 of  646 MB written (fifo  88%) [buf 100%]  24.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  300 of  646 MB written (fifo  88%) [buf 100%]  25.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  301 of  646 MB written (fifo  87%) [buf 100%]  24.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  302 of  646 MB written (fifo  87%) [buf 100%]  25.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  303 of  646 MB written (fifo  87%) [buf 100%]  24.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  304 of  646 MB written (fifo  87%) [buf 100%]  24.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  305 of  646 MB written (fifo  87%) [buf 100%]  24.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  306 of  646 MB written (fifo  87%) [buf 100%]  24.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  51.32% done, estimate finish Sat Dec 26 08:48:24 2009
BraseroWodim stdout: Track 01:  307 of  646 MB written (fifo  86%) [buf 100%]  24.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  308 of  646 MB written (fifo  86%) [buf 100%]  24.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  309 of  646 MB written (fifo  86%) [buf 100%]  24.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  310 of  646 MB written (fifo  86%) [buf 100%]  24.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  311 of  646 MB written (fifo  86%) [buf 100%]  24.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  312 of  646 MB written (fifo  86%) [buf 100%]  24.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  313 of  646 MB written (fifo  86%) [buf 100%]  25.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  314 of  646 MB written (fifo  85%) [buf 100%]  24.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  315 of  646 MB written (fifo  85%) [buf 100%]  25.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  316 of  646 MB written (fifo  85%) [buf 100%]  24.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  52.84% done, estimate finish Sat Dec 26 08:48:21 2009
BraseroWodim stdout: Track 01:  317 of  646 MB written (fifo  85%) [buf 100%]  25.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  318 of  646 MB written (fifo  85%) [buf 100%]  24.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  319 of  646 MB written (fifo  85%) [buf 100%]  25.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  320 of  646 MB written (fifo  85%) [buf 100%]  24.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  321 of  646 MB written (fifo  85%) [buf 100%]  25.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  322 of  646 MB written (fifo  84%) [buf 100%]  24.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  323 of  646 MB written (fifo  91%) [buf 100%]   7.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  324 of  646 MB written (fifo  91%) [buf 100%]  24.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  54.34% done, estimate finish Sat Dec 26 08:48:21 2009
BraseroWodim stdout: Track 01:  325 of  646 MB written (fifo  91%) [buf 100%]  25.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  326 of  646 MB written (fifo  91%) [buf 100%]  24.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  327 of  646 MB written (fifo  91%) [buf 100%]  25.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  328 of  646 MB written (fifo  91%) [buf 100%]  24.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  329 of  646 MB written (fifo  90%) [buf 100%]  25.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  330 of  646 MB written (fifo  90%) [buf 100%]  24.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  331 of  646 MB written (fifo  90%) [buf 100%]  25.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  332 of  646 MB written (fifo  90%) [buf 100%]  24.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  333 of  646 MB written (fifo  90%) [buf 100%]  24.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  334 of  646 MB written (fifo  90%) [buf 100%]  24.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  335 of  646 MB written (fifo  90%) [buf 100%]  24.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  55.85% done, estimate finish Sat Dec 26 08:48:20 2009
BraseroWodim stdout: Track 01:  336 of  646 MB written (fifo  90%) [buf 100%]  24.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  337 of  646 MB written (fifo  89%) [buf 100%]  24.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  338 of  646 MB written (fifo  89%) [buf 100%]  24.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  339 of  646 MB written (fifo  89%) [buf 100%]  24.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  340 of  646 MB written (fifo  89%) [buf 100%]  24.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  341 of  646 MB written (fifo  89%) [buf 100%]  24.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  342 of  646 MB written (fifo  89%) [buf 100%]  24.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  343 of  646 MB written (fifo  88%) [buf 100%]  24.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  344 of  646 MB written (fifo  88%) [buf 100%]  25.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  345 of  646 MB written (fifo  88%) [buf 100%]  24.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  57.36% done, estimate finish Sat Dec 26 08:48:20 2009
BraseroWodim stdout: Track 01:  346 of  646 MB written (fifo  88%) [buf 100%]  25.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  347 of  646 MB written (fifo  88%) [buf 100%]  24.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  348 of  646 MB written (fifo  88%) [buf 100%]  25.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  349 of  646 MB written (fifo  88%) [buf 100%]  24.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  350 of  646 MB written (fifo  88%) [buf 100%]  25.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  351 of  646 MB written (fifo  87%) [buf 100%]  24.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  352 of  646 MB written (fifo  87%) [buf 100%]  25.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  353 of  646 MB written (fifo  87%) [buf 100%]  24.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  354 of  646 MB written (fifo  87%) [buf 100%]  25.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  355 of  646 MB written (fifo  87%) [buf 100%]  24.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  58.87% done, estimate finish Sat Dec 26 08:48:20 2009
BraseroWodim stdout: Track 01:  356 of  646 MB written (fifo  87%) [buf 100%]  25.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  357 of  646 MB written (fifo  87%) [buf 100%]  24.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  358 of  646 MB written (fifo  87%) [buf 100%]  25.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  359 of  646 MB written (fifo  86%) [buf 100%]  24.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  360 of  646 MB written (fifo  86%) [buf 100%]  25.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  361 of  646 MB written (fifo  86%) [buf 100%]  24.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  362 of  646 MB written (fifo  86%) [buf 100%]  25.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  363 of  646 MB written (fifo  86%) [buf 100%]  24.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  364 of  646 MB written (fifo  85%) [buf 100%]  24.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  365 of  646 MB written (fifo  85%) [buf 100%]  24.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  60.38% done, estimate finish Sat Dec 26 08:48:19 2009
BraseroWodim stdout: Track 01:  366 of  646 MB written (fifo  85%) [buf 100%]  24.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  367 of  646 MB written (fifo  84%) [buf 100%]  23.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  368 of  646 MB written (fifo  83%) [buf 100%]  25.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  369 of  646 MB written (fifo  83%) [buf 100%]  24.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  370 of  646 MB written (fifo  82%) [buf 100%]  24.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  371 of  646 MB written (fifo  82%) [buf 100%]  24.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  372 of  646 MB written (fifo  82%) [buf 100%]  24.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  373 of  646 MB written (fifo  82%) [buf 100%]  24.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  374 of  646 MB written (fifo  81%) [buf 100%]  24.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  375 of  646 MB written (fifo  80%) [buf 100%]  25.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  376 of  646 MB written (fifo  80%) [buf 100%]  24.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  61.89% done, estimate finish Sat Dec 26 08:48:19 2009
BraseroWodim stdout: Track 01:  377 of  646 MB written (fifo  80%) [buf 100%]  25.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  378 of  646 MB written (fifo  80%) [buf 100%]  24.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  379 of  646 MB written (fifo  79%) [buf 100%]  25.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  380 of  646 MB written (fifo  79%) [buf 100%]  24.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  381 of  646 MB written (fifo  79%) [buf 100%]  25.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  382 of  646 MB written (fifo  79%) [buf 100%]  24.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  383 of  646 MB written (fifo  79%) [buf 100%]  25.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  384 of  646 MB written (fifo  79%) [buf 100%]  24.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  385 of  646 MB written (fifo  77%) [buf 100%]  25.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  386 of  646 MB written (fifo  76%) [buf 100%]  24.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  387 of  646 MB written (fifo  76%) [buf 100%]  25.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  63.40% done, estimate finish Sat Dec 26 08:48:18 2009
BraseroWodim stdout: Track 01:  388 of  646 MB written (fifo  76%) [buf 100%]  24.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  389 of  646 MB written (fifo  76%) [buf 100%]  25.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  390 of  646 MB written (fifo  75%) [buf 100%]  24.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  391 of  646 MB written (fifo  75%) [buf 100%]  25.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  392 of  646 MB written (fifo  74%) [buf 100%]  24.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  393 of  646 MB written (fifo  82%) [buf 100%]   7.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  394 of  646 MB written (fifo  82%) [buf 100%]  24.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  395 of  646 MB written (fifo  82%) [buf 100%]  24.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  64.91% done, estimate finish Sat Dec 26 08:48:18 2009
BraseroWodim stdout: Track 01:  396 of  646 MB written (fifo  82%) [buf 100%]  24.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  397 of  646 MB written (fifo  81%) [buf 100%]  24.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  398 of  646 MB written (fifo  81%) [buf 100%]  24.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  399 of  646 MB written (fifo  81%) [buf 100%]  24.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  400 of  646 MB written (fifo  80%) [buf 100%]  24.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  401 of  646 MB written (fifo  79%) [buf 100%]  24.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  402 of  646 MB written (fifo  79%) [buf 100%]  24.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  403 of  646 MB written (fifo  79%) [buf 100%]  24.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  404 of  646 MB written (fifo  79%) [buf 100%]  24.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  405 of  646 MB written (fifo  78%) [buf 100%]  24.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  406 of  646 MB written (fifo  78%) [buf 100%]  25.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  66.42% done, estimate finish Sat Dec 26 08:48:18 2009
BraseroWodim stdout: Track 01:  407 of  646 MB written (fifo  77%) [buf 100%]  24.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  408 of  646 MB written (fifo  77%) [buf 100%]  25.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  409 of  646 MB written (fifo  77%) [buf 100%]  24.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  410 of  646 MB written (fifo  77%) [buf 100%]  25.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  411 of  646 MB written (fifo  76%) [buf 100%]  24.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  412 of  646 MB written (fifo  76%) [buf 100%]  25.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  413 of  646 MB written (fifo  76%) [buf 100%]  24.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  414 of  646 MB written (fifo  76%) [buf 100%]  25.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  415 of  646 MB written (fifo  75%) [buf 100%]  24.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  416 of  646 MB written (fifo  75%) [buf 100%]  25.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  417 of  646 MB written (fifo  74%) [buf 100%]  24.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  67.93% done, estimate finish Sat Dec 26 08:48:19 2009
BraseroWodim stdout: Track 01:  418 of  646 MB written (fifo  73%) [buf 100%]  24.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  419 of  646 MB written (fifo  73%) [buf 100%]  25.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  420 of  646 MB written (fifo  72%) [buf 100%]  25.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  421 of  646 MB written (fifo  72%) [buf 100%]  24.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  422 of  646 MB written (fifo  72%) [buf 100%]  25.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  423 of  646 MB written (fifo  71%) [buf 100%]  24.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  424 of  646 MB written (fifo  71%) [buf 100%]  25.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  425 of  646 MB written (fifo  71%) [buf 100%]  24.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  426 of  646 MB written (fifo  71%) [buf 100%]  24.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  427 of  646 MB written (fifo  70%) [buf 100%]  24.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  428 of  646 MB written (fifo  70%) [buf 100%]  24.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  69.44% done, estimate finish Sat Dec 26 08:48:19 2009
BraseroWodim stdout: Track 01:  429 of  646 MB written (fifo  69%) [buf 100%]  24.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  430 of  646 MB written (fifo  69%) [buf 100%]  24.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  431 of  646 MB written (fifo  69%) [buf 100%]  24.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  432 of  646 MB written (fifo  68%) [buf 100%]  24.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  433 of  646 MB written (fifo  68%) [buf 100%]  24.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  434 of  646 MB written (fifo  68%) [buf 100%]  24.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  435 of  646 MB written (fifo  68%) [buf 100%]  24.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  436 of  646 MB written (fifo  68%) [buf 100%]  24.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  437 of  646 MB written (fifo  67%) [buf 100%]  25.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  438 of  646 MB written (fifo  67%) [buf 100%]  24.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  70.95% done, estimate finish Sat Dec 26 08:48:18 2009
BraseroWodim stdout: Track 01:  439 of  646 MB written (fifo  67%) [buf 100%]  25.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  440 of  646 MB written (fifo  67%) [buf 100%]  24.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  441 of  646 MB written (fifo  67%) [buf 100%]  25.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  442 of  646 MB written (fifo  66%) [buf 100%]  24.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  443 of  646 MB written (fifo  66%) [buf 100%]  25.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  444 of  646 MB written (fifo  65%) [buf 100%]  24.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  445 of  646 MB written (fifo  65%) [buf 100%]  25.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  446 of  646 MB written (fifo  65%) [buf 100%]  24.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  447 of  646 MB written (fifo  64%) [buf 100%]  25.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  448 of  646 MB written (fifo  63%) [buf 100%]  24.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  449 of  646 MB written (fifo  62%) [buf 100%]  25.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  450 of  646 MB written (fifo  62%) [buf 100%]  24.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  72.46% done, estimate finish Sat Dec 26 08:48:18 2009
BraseroWodim stdout: Track 01:  451 of  646 MB written (fifo  61%) [buf 100%]  25.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  452 of  646 MB written (fifo  61%) [buf 100%]  24.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  453 of  646 MB written (fifo  60%) [buf 100%]  24.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  454 of  646 MB written (fifo  59%) [buf 100%]  24.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  455 of  646 MB written (fifo  59%) [buf 100%]  24.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  456 of  646 MB written (fifo  58%) [buf 100%]  24.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  457 of  646 MB written (fifo  57%) [buf 100%]  24.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  458 of  646 MB written (fifo  56%) [buf 100%]  24.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  459 of  646 MB written (fifo  56%) [buf 100%]  24.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  460 of  646 MB written (fifo  55%) [buf 100%]  24.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  461 of  646 MB written (fifo  54%) [buf 100%]  24.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  462 of  646 MB written (fifo  54%) [buf 100%]  24.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  73.97% done, estimate finish Sat Dec 26 08:48:18 2009
BraseroWodim stdout: Track 01:  463 of  646 MB written (fifo  53%) [buf 100%]  24.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  464 of  646 MB written (fifo  58%) [buf 100%]   7.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  465 of  646 MB written (fifo  57%) [buf 100%]  24.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  466 of  646 MB written (fifo  57%) [buf 100%]  24.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  467 of  646 MB written (fifo  55%) [buf 100%]  24.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  468 of  646 MB written (fifo  54%) [buf 100%]  25.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  469 of  646 MB written (fifo  53%) [buf 100%]  24.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  470 of  646 MB written (fifo  52%) [buf 100%]  25.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  471 of  646 MB written (fifo  51%) [buf 100%]  24.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  472 of  646 MB written (fifo  50%) [buf 100%]  25.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  473 of  646 MB written (fifo  49%) [buf 100%]  24.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  474 of  646 MB written (fifo  48%) [buf 100%]  25.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  75.48% done, estimate finish Sat Dec 26 08:48:19 2009
BraseroWodim stdout: Track 01:  475 of  646 MB written (fifo  46%) [buf 100%]  24.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  476 of  646 MB written (fifo  45%) [buf 100%]  25.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  477 of  646 MB written (fifo  44%) [buf 100%]  24.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  478 of  646 MB written (fifo  43%) [buf 100%]  25.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  479 of  646 MB written (fifo  42%) [buf 100%]  24.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  480 of  646 MB written (fifo  40%) [buf 100%]  25.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  481 of  646 MB written (fifo  39%) [buf 100%]  24.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  482 of  646 MB written (fifo  38%) [buf 100%]  25.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  483 of  646 MB written (fifo  36%) [buf 100%]  24.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  484 of  646 MB written (fifo  35%) [buf 100%]  25.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  485 of  646 MB written (fifo  34%) [buf 100%]  24.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  486 of  646 MB written (fifo  32%) [buf 100%]  24.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  487 of  646 MB written (fifo  31%) [buf 100%]  24.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  488 of  646 MB written (fifo  29%) [buf 100%]  25.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  489 of  646 MB written (fifo  27%) [buf 100%]  24.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  76.98% done, estimate finish Sat Dec 26 08:48:21 2009
BraseroWodim stdout: Track 01:  490 of  646 MB written (fifo  27%) [buf 100%]  24.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  491 of  646 MB written (fifo  26%) [buf 100%]  24.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  492 of  646 MB written (fifo  26%) [buf 100%]  24.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  493 of  646 MB written (fifo  26%) [buf 100%]  24.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  494 of  646 MB written (fifo  26%) [buf 100%]  24.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  495 of  646 MB written (fifo  26%) [buf 100%]  24.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  496 of  646 MB written (fifo  26%) [buf 100%]  24.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  497 of  646 MB written (fifo  26%) [buf 100%]  24.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  498 of  646 MB written (fifo  26%) [buf 100%]  24.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  499 of  646 MB written (fifo  26%) [buf 100%]  25.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  78.50% done, estimate finish Sat Dec 26 08:48:20 2009
BraseroWodim stdout: Track 01:  500 of  646 MB written (fifo  26%) [buf 100%]  24.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  501 of  646 MB written (fifo  25%) [buf 100%]  25.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  502 of  646 MB written (fifo  25%) [buf 100%]  24.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  503 of  646 MB written (fifo  25%) [buf 100%]  25.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  504 of  646 MB written (fifo  25%) [buf 100%]  24.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  505 of  646 MB written (fifo  25%) [buf 100%]  25.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  506 of  646 MB written (fifo  25%) [buf 100%]  24.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  507 of  646 MB written (fifo  25%) [buf 100%]  25.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  508 of  646 MB written (fifo  24%) [buf 100%]  24.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  509 of  646 MB written (fifo  23%) [buf 100%]  25.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  510 of  646 MB written (fifo  22%) [buf 100%]  24.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  80.00% done, estimate finish Sat Dec 26 08:48:20 2009
BraseroWodim stdout: Track 01:  511 of  646 MB written (fifo  22%) [buf 100%]  25.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  512 of  646 MB written (fifo  21%) [buf 100%]  24.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  513 of  646 MB written (fifo  21%) [buf 100%]  25.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  514 of  646 MB written (fifo  21%) [buf 100%]  24.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  515 of  646 MB written (fifo  20%) [buf 100%]  24.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  516 of  646 MB written (fifo  19%) [buf 100%]  24.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  517 of  646 MB written (fifo  18%) [buf 100%]  25.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  518 of  646 MB written (fifo  18%) [buf 100%]  24.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  519 of  646 MB written (fifo  17%) [buf 100%]  24.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  520 of  646 MB written (fifo  15%) [buf 100%]  24.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  521 of  646 MB written (fifo  15%) [buf 100%]  24.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  522 of  646 MB written (fifo  14%) [buf 100%]  24.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  81.51% done, estimate finish Sat Dec 26 08:48:20 2009
BraseroWodim stdout: Track 01:  523 of  646 MB written (fifo  14%) [buf 100%]  24.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  524 of  646 MB written (fifo  14%) [buf 100%]  24.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  525 of  646 MB written (fifo  14%) [buf 100%]  24.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  526 of  646 MB written (fifo  14%) [buf 100%]  24.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  527 of  646 MB written (fifo  14%) [buf 100%]  24.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  528 of  646 MB written (fifo  14%) [buf 100%]  24.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  529 of  646 MB written (fifo  14%) [buf 100%]  24.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  530 of  646 MB written (fifo  13%) [buf 100%]  25.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  531 of  646 MB written (fifo  12%) [buf 100%]  24.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  532 of  646 MB written (fifo  12%) [buf 100%]  25.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  83.02% done, estimate finish Sat Dec 26 08:48:20 2009
BraseroWodim stdout: Track 01:  533 of  646 MB written (fifo  11%) [buf 100%]  24.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  534 of  646 MB written (fifo  19%) [buf 100%]   7.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  535 of  646 MB written (fifo  19%) [buf 100%]  24.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  536 of  646 MB written (fifo  19%) [buf 100%]  25.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  537 of  646 MB written (fifo  19%) [buf 100%]  24.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  538 of  646 MB written (fifo  19%) [buf 100%]  25.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  539 of  646 MB written (fifo  18%) [buf 100%]  24.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  540 of  646 MB written (fifo  18%) [buf 100%]  25.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  84.53% done, estimate finish Sat Dec 26 08:48:20 2009
BraseroWodim stdout: Track 01:  541 of  646 MB written (fifo  18%) [buf 100%]  24.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  542 of  646 MB written (fifo  18%) [buf 100%]  25.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  543 of  646 MB written (fifo  18%) [buf 100%]  24.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  544 of  646 MB written (fifo  18%) [buf 100%]  25.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  545 of  646 MB written (fifo  18%) [buf 100%]  24.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  546 of  646 MB written (fifo  17%) [buf 100%]  25.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  547 of  646 MB written (fifo  17%) [buf 100%]  24.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  548 of  646 MB written (fifo  17%) [buf 100%]  25.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  549 of  646 MB written (fifo  17%) [buf 100%]  24.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  550 of  646 MB written (fifo  17%) [buf 100%]  24.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  86.04% done, estimate finish Sat Dec 26 08:48:19 2009
BraseroWodim stdout: Track 01:  551 of  646 MB written (fifo  17%) [buf 100%]  24.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  552 of  646 MB written (fifo  17%) [buf 100%]  24.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  553 of  646 MB written (fifo  16%) [buf 100%]  24.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  554 of  646 MB written (fifo  16%) [buf 100%]  24.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  555 of  646 MB written (fifo  16%) [buf 100%]  24.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  556 of  646 MB written (fifo  16%) [buf 100%]  24.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  557 of  646 MB written (fifo  16%) [buf 100%]  24.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  558 of  646 MB written (fifo  16%) [buf 100%]  24.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  559 of  646 MB written (fifo  16%) [buf 100%]  24.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  560 of  646 MB written (fifo  15%) [buf 100%]  24.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  87.55% done, estimate finish Sat Dec 26 08:48:19 2009
BraseroWodim stdout: Track 01:  561 of  646 MB written (fifo  15%) [buf 100%]  25.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  562 of  646 MB written (fifo  15%) [buf 100%]  24.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  563 of  646 MB written (fifo  15%) [buf 100%]  25.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  564 of  646 MB written (fifo  14%) [buf 100%]  24.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  565 of  646 MB written (fifo  14%) [buf 100%]  25.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  566 of  646 MB written (fifo  13%) [buf 100%]  24.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  567 of  646 MB written (fifo  13%) [buf 100%]  25.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  568 of  646 MB written (fifo  12%) [buf 100%]  24.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  569 of  646 MB written (fifo  11%) [buf 100%]  25.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  570 of  646 MB written (fifo  11%) [buf 100%]  24.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  571 of  646 MB written (fifo  11%) [buf 100%]  25.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  572 of  646 MB written (fifo  11%) [buf 100%]  24.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  89.06% done, estimate finish Sat Dec 26 08:48:19 2009
BraseroWodim stdout: Track 01:  573 of  646 MB written (fifo  10%) [buf 100%]  25.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  574 of  646 MB written (fifo  10%) [buf 100%]  24.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  575 of  646 MB written (fifo  10%) [buf 100%]  25.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  576 of  646 MB written (fifo  10%) [buf 100%]  24.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  577 of  646 MB written (fifo   9%) [buf 100%]  25.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  578 of  646 MB written (fifo   8%) [buf 100%]  24.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  579 of  646 MB written (fifo   8%) [buf 100%]  25.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  580 of  646 MB written (fifo   8%) [buf 100%]  24.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  581 of  646 MB written (fifo   7%) [buf 100%]  25.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  582 of  646 MB written (fifo   6%) [buf 100%]  24.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  583 of  646 MB written (fifo   6%) [buf 100%]  24.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  90.57% done, estimate finish Sat Dec 26 08:48:19 2009
BraseroWodim stdout: Track 01:  584 of  646 MB written (fifo   5%) [buf 100%]  24.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  585 of  646 MB written (fifo   4%) [buf 100%]  24.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  586 of  646 MB written (fifo   3%) [buf 100%]  24.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  587 of  646 MB written (fifo   2%) [buf 100%]  24.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  588 of  646 MB written (fifo   1%) [buf 100%]  24.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  589 of  646 MB written (fifo   0%) [buf 100%]  24.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  590 of  646 MB written (fifo   0%) [buf  88%]  19.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  591 of  646 MB written (fifo   0%) [buf  49%]  16.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  592 of  646 MB written (fifo   0%) [buf  28%]  20.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  92.08% done, estimate finish Sat Dec 26 08:48:19 2009
BraseroGenisoimage stderr:  93.59% done, estimate finish Sat Dec 26 08:48:19 2009
BraseroWodim stderr: Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: CDB:  2A 00 00 04 A3 B0 00 00 1F 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: status: 0x2 (CHECK CONDITION)
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Bytes: F0 00 03 00 04 A1 1F 0A 00 00 00 00 0C 00 00 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Key: 0x3 Medium Error, Segment 0
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Code: 0x0C Qual 0x00 (write error) Fru 0x0
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense flags: Blk 303391 (valid) 
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: cmd finished after 3.806s timeout 40s
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: A write error occured.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: Please properly read the error message above.
BraseroWodim called brasero_job_get_flags
BraseroGenisoimage stderr:  95.10% done, estimate finish Sat Dec 26 08:48:19 2009
BraseroWodim stdout: Track 01:  593 of  646 MB written (fifo   0%) [buf  40%]  16.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stderr: Errno: 5 (Input/output error), close track/session scsi sendcmd: no error
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: write track data: error after 622690304 bytes
BraseroWodim stderr: CDB:  5B 00 02 00 00 00 00 00 00 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Writing  time:  196.715s
BraseroWodim stderr: status: 0x2 (CHECK CONDITION)
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Average write speed  22.9x.
BraseroWodim stderr: Sense Bytes: 70 00 05 00 00 00 00 0A 00 00 00 00 72 04 00 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Min drive buffer fill was 28%
BraseroWodim stderr: Sense Key: 0x5 Illegal Request, Segment 0
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Fixating...
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stderr: Sense Code: 0x72 Qual 0x04 (empty or partially written reserved track) Fru 0x0
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Fixating time:    0.002s
BraseroWodim stderr: Sense flags: Blk 0 (not valid) 
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: cmd finished after 0.001s timeout 480s
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: cmd finished after 0.001s timeout 480s
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: Cannot fixate disk.
BraseroWodim called brasero_job_get_flags
BraseroWodim called brasero_job_error
BraseroWodim finished with an error
BraseroWodim asked to stop because of an error
    error        = 15
    message    = "An error occured while writing to disc"
BraseroGenisoimage stopping
BraseroGenisoimage got killed
BraseroGenisoimage disconnecting BraseroGenisoimage from BraseroChecksumImage
BraseroChecksumImage stopping
BraseroChecksumImage disconnecting BraseroChecksumImage from BraseroWodim
BraseroChecksumImage closing connection for BraseroChecksumImage
BraseroWodim stopping
BraseroWodim got killed
BraseroWodim closing connection for BraseroWodim
Session error : An error occured while writing to disc (brasero_burn_record brasero-burn.c:2808)

---

### Post by labinnsw on 2009-12-26
If you don't have or want to use nero. I recommend K3b. It is one of the top 3 KDE applications in my opinion. (It would also have to feature in my Linux top 10)

---

### Post by switch10 on 2009-12-26
I get the same problem sometimes with Braseo.  If I burn at the slowest possible speed it works though.

> **labinnsw said:**
> If you don't have or want to use nero. I recommend K3b. It is one of the top 3 KDE applications in my opinion. (It would also have to feature in my Linux top 10)


how do you use Nero on Linux??  Does it work in wine??

---

### Post by labinnsw on 2009-12-26
Yes it works with the latest version of wine.

[Visit wineHQ for instructions to install the latest version.]("http://www.winehq.org/download/deb")

---

### Post by scorptig on 2009-12-31
Yes, I have same issue, I am using 2 Brand New LG Manufacturer Id: GH24LS50/BK, SATA. As well new motherboard Asus P5Q PRO Turbo, new CPU
Intel Core 2 Quad Q8300 2.5GHz 1333 MHz LGA775 L2 4MB, new Hard Drives SATA, 4  Gigs of Memory.
I had same errors not only in Ubuntu Kosmic Koala 9.10 64 bit, but also in Linux-Mint Helena 64 Bit, OpenSuse 11.2 64 Bit.
> BraseroWodim process finished with status 254
Now what's strange I have a second computer running with a Pioneer DVR-110D IDE with an AMD XP-2400, and I have no errors with Brasero or K3b.
So I saved my reports from error log generated, and at this point I really have no clue, I've had LG before, no issues, in this brand new computer, I have issues, and this is not my first Linux installation.
I've been a Linux user since February 2003.
Additional note, BIOS setting are AHCI SATA, all hardware recognized, two hard drives and two dvd drives, all SATA.
Being New Years Eve, I don't really expect any solutions, my next move will be to switch both my LG drives for two new Pioneer drives, some point next week, Yes DMA is enabled.
If anyone with a solution needs more data, please let me know.
Thank you in advance for your time in replying, and Best Wishes for 2010.

---

### Post by scorptig on 2009-12-31
Ok I say solved because in my situation it did solve my errors.
OK I went into my BIOS, I am using AmiBios, on the MAIN page entry of BIOS you should see Storage Configuration, I now have Sata Configuration set to Enhanced and I configured SATA as IDE, 3 choices offered IDE, AHCI and RAID.
Previously I had my SATA Configuration set to AHCI, creating Brasero & K3B errors.
My MAIN also shows 
Sata 1 HDD
Sata 2 DVDRAM
Sata 3 HDD
Sata 4 DVDRAM

So to all with Brasero or K3B Errors, check your BIOS configuration.

On that note, Best Wishes to All for 2010.

OK another note on BIOS settings, check to see if your AUTO for CDROM, if so, set to CDROM, Hard Drives AUTO setting fine DMA should be enabled.

---

### Post by scorptig on 2009-12-31
Worth noting, I tried a new fresh install of Ubuntu using my setting SATA
IDE, and my installation was taking too long, so I went back to AHCI SATA setting in BIOS, then I re-tried my installation, it was super fast.
So after I install, I'll retest my DVD burner Brasero, and see if settings do cause error. I'll post back on Forum, regarding BIOS settings SATA AHCI or ENHANCED IDE..

---

### Post by ST3ALTHPSYCH0 on 2009-12-31
I had an issue for a while with Brasero in Karmic where it misidentified the amount of free space on a blank disc. One of the more recent updates solved that though... I know it was some issue with Karmic, or Karmic's brasero, b/c I also have Jaunty installed on that machine and brasero in Jaunty gave no issues whatsoever.

---

### Post by signlesskid on 2010-01-01
Hi- Thanks for opinions.
Indeed, My Brasero was working good enough until I tried to burn DVD-RW disks ... cleaning/burning ... cleaning/burning and Brasero was not capable of cleaning a Disk as good as enought for another burning. Thus I used commands like dvd-rw-format and etc.
after that Brasero became crazy and I tried it's reinstallation but nothing got better.

considering the note about BIOS conf. I dont have any AHCI or similar option.
considering the option to use NERO, I installed it but it doesn't recognize my DISK and the image burning feature is only available. I check Wine Conf. to involve dev/cdrom in drives tab and still nothing shows up in Nero.
considering the option for K3B, I prefer not to use K-packages, I really don't know why! but it seems I have to.
considering burning with low speed in Brasero, I tried 16x, but I still get the dame error while writing on disk.

PS. my drive is a SATS Sony DVD-RW drive and my HDD is a SATA 500GB Maxtor.

Good Luck - waiting for solutions :)

---

