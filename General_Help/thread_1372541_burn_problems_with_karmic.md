---
title: "burn problems with karmic"
date: 2010-01-04
forum: General Help
---

### Post by Drakkenkill on 2010-01-04
well i tried burning puppy linux through brasero k3b and gnomebaker and this is what i got with brasero as a unknown error

Checking session consistency (brasero_burn_check_session_consistency brasero-burn.c:1799)
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_set_output_size_for_current_track
BraseroBurnURI stopping
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_session_output_size
BraseroBurnURI output set (IMAGE) image = /tmp/brasero_tmp_RZRF6U.bin toc = none
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
BraseroLocalTrack output set (IMAGE) image = /tmp/brasero_tmp_LAQF6U.bin toc = none
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
    speed=40
    driveropts=burnfree
    fs=16m
    -data
    -nopad
    /home/drakkenkill/Downloads/pup-431 (2).iso
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
BraseroWodim stderr: Errno: 5 (Input/output error), read buffer scsi sendcmd: no error
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: TOC Type: 1 = CD-ROM
BraseroWodim stderr: CDB:  3C 00 00 00 00 00 00 FC 00 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Driveropts: 'burnfree'
BraseroWodim stderr: status: 0x2 (CHECK CONDITION)
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Device type    : Removable CD-ROM
BraseroWodim stderr: Sense Bytes: 72 0B 00 00 00 00 00 0E 09 0C 00 00 00 02 00 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Version        : 5
BraseroWodim stderr: Sense Key: 0x0 No Additional Sense, Segment 11
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Response Format: 2
BraseroWodim stderr: Sense Code: 0x00 Qual 0x02 (end-of-partition/medium detected) Fru 0x0
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Capabilities   : 
BraseroWodim stderr: Sense flags: Blk 0 (not valid) 
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Vendor_info    : 'CyberDrv'
BraseroWodim stderr: cmd finished after 91.254s timeout 40s
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Identification : 'CW078D CD-R/RW  '
BraseroWodim stdout: Revision       : '150E'
BraseroWodim stdout: Device seems to be: Generic mmc CD-RW.
BraseroWodim stdout: Current: 0x0009 (CD-R)
BraseroWodim stdout: Profile: 0x000A (CD-RW) 
BraseroWodim stdout: Profile: 0x0009 (CD-R) (current)
BraseroWodim stdout: Profile: 0x0008 (CD-ROM) 
BraseroWodim stdout: Profile: 0x0002 (Removable disk) 
BraseroWodim stdout: Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
BraseroWodim stdout: Driver flags   : MMC-2 SWABAUDIO BURNFREE 
BraseroWodim stdout: Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
BraseroWodim stdout: Drive buf size : 1806336 = 1764 KB
BraseroWodim stdout: FIFO size      : 16777216 = 16384 KB
BraseroWodim stderr: wodim: Cannot load media.
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Track 01: data   104 MB        
BraseroWodim stderr: HUP
BraseroWodim stdout: Total size:      120 MB (11:56.45) = 53734 sectors
BraseroWodim stdout: Lout start:      120 MB (11:58/34) = 53734 sectors
BraseroWodim stdout: HUP
BraseroWodim process finished with status 255
BraseroWodim called brasero_job_error
BraseroWodim finished with an error
BraseroWodim asked to stop because of an error
    error        = 0
    message    = "no message"
BraseroWodim stopping
BraseroWodim got killed
Session error : unknown (brasero_burn_record brasero-burn.c:2769)






any ideas?

---

### Post by quicknick_26 on 2010-01-04
This might be a dumb question. Rather than using GnomeBaker, have you already tried right-clicking on the "pup-431 (2).iso" icon in the file browser and selecting "Write to Disc..."? That usually works well for me.

---

### Post by Drakkenkill on 2010-01-05
yes that's what i did prior to posting this thread i've tried every way i could think of and it still doesn't work

---

### Post by jamesisin on 2010-01-05
What error do you get when you right-click and choose Burn to Disc?

---

