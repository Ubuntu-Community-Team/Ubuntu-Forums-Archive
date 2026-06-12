---
title: "Brasero Burn Errors"
date: 2009-07-25
forum: General Help
---

### Post by interestinfellow on 2009-07-25
I can't successfully burn anything with brasero in Ubuntu 9.04 quickly.  

If I tell it to "burn direct" "burnproof" and "eject when finished" I get an errorat about 30%... every frickin time.  

I have to tell it not to burn direct (uncheck "burn directly to disk") and simulate writing in order to do a successful burn; but that ends up taking about an hour for one disk.  

I'm trying to burn a data CD (mp3's for my mp3 compatible car stereo) with data from my home partition (on the master drive) and some stuff from my z drive (long term storage).

the error log generated looks like this
> Checking session consistency (brasero_burn_check_session_consistency burn.c:1905)
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_set_output_size_for_current_track
BraseroBurnURI stopping
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_session_output_size
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
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_current_track
BraseroLocalTrack called brasero_job_get_input_type
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
BraseroChecksumFiles called brasero_job_get_input_type
BraseroChecksumFiles called brasero_job_get_current_track
BraseroChecksumFiles called brasero_job_set_current_action
BraseroChecksumFiles called brasero_job_get_flags
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_get_input_type
BraseroChecksumFiles called brasero_job_get_current_track
BraseroChecksumFiles Adding graft for checksum file /.checksum.md5 file:///tmp/brasero_tmp_ER3IXU.md5
BraseroChecksumFiles called brasero_job_add_track
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles Finished track successfully
BraseroChecksumFiles stopping
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_flags
BraseroChecksumImage Dummy operation, skipping
BraseroWodim called brasero_job_get_action
BraseroWodim creating input
BraseroWodim getting varg
BraseroWodim called brasero_job_get_action
BraseroWodim got varg:
BraseroWodim deactivating
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
	-graft-points
	-path-list
	/tmp/brasero_tmp_NKRLXU
	-exclude-list
	/tmp/brasero_tmp_0RULXU
	-V
	Data disc (25 Jul 09)
	-A
	Brasero-2.26.1
	-sysid
	LINUX
	-quiet
	-print-size
BraseroGenisoimage Launching command
BraseroGenisoimage called brasero_job_get_fd_out
BraseroGenisoimage stdout: 229859
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage called brasero_job_set_output_size_for_current_track
BraseroGenisoimage stdout: HUP
BraseroGenisoimage stderr: HUP
BraseroGenisoimage process finished with status 0
BraseroGenisoimage called brasero_job_get_fd_out
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage Finished track successfully
BraseroGenisoimage got killed
BraseroGenisoimage stopping
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_flags
BraseroChecksumImage Dummy operation, skipping
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
	-dummy
	speed=48
	driveropts=burnfree
	-dao
	fs=20m
	tsize=229859s
	-data
	-nopad
	-
BraseroWodim Launching command
BraseroWodim called brasero_job_get_fd_out
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage linked to BraseroWodim
BraseroGenisoimage getting varg
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage called brasero_job_get_current_track
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
	-graft-points
	-path-list
	/tmp/brasero_tmp_IUGFXU
	-exclude-list
	/tmp/brasero_tmp_TNGFXU
	-V
	Data disc (25 Jul 09)
	-A
	Brasero-2.26.1
	-sysid
	LINUX
BraseroGenisoimage Launching command
BraseroGenisoimage called brasero_job_get_fd_out
BraseroGenisoimage stderr: Using CROSS000.MP3;1 for  /Crossfade - Crossfade - 06 - The Deep End.mp3 (Crossfade - Crossfade - 02 - Cold.mp3)
BraseroGenisoimage stderr: Using BONE_000.MP3;1 for  /Bone Thugs N Harmony - East 1999 Eternal - 08 - Crossroads (Original).mp3 (Bone Thugs N Harmony - East 1999 Eternal - 08 - Crossroads.mp3)
BraseroGenisoimage stderr: Using CROSS001.MP3;1 for  /Crossfade - Crossfade - 02 - Cold.mp3 (Crossfade - Crossfade - 01 - Starless.mp3)
BraseroGenisoimage stderr: Using SEVEN000.MP3;1 for  /Seven Mary Three - American Standard - 10 - Punch In Punch Out - Seven Mar.mp3 (Seven Mary Three - American Standard - 02 - Cumbersome - Seven Mary Three.mp3)
BraseroGenisoimage stderr: Using EVERC000.MP3;1 for  Everclear/Sparkle And Fade/Everclear - Sparkle And Fade - 04 - Santa Monica.mp3 (Everclear - Sparkle And Fade - 14 - My Sexual Life.mp3)
BraseroGenisoimage stderr: Using EVERC001.MP3;1 for  Everclear/Sparkle And Fade/Everclear - Sparkle And Fade - 14 - My Sexual Life.mp3 (Everclear - Sparkle And Fade - 12 - Pale Green Stars.mp3)
BraseroGenisoimage stderr: Using EVERC002.MP3;1 for  Everclear/Sparkle And Fade/Everclear - Sparkle And Fade - 12 - Pale Green Stars.mp3 (Everclear - Sparkle And Fade - 06 - Strawberry.mp3)
BraseroGenisoimage stderr: Using EVERC003.MP3;1 for  Everclear/Sparkle And Fade/Everclear - Sparkle And Fade - 06 - Strawberry.mp3 (Everclear - Sparkle And Fade - 13 - Chemical Smile.mp3)
BraseroGenisoimage stderr: Using EVERC004.MP3;1 for  Everclear/Sparkle And Fade/Everclear - Sparkle And Fade - 13 - Chemical Smile.mp3 (Everclear - Sparkle And Fade - 05 - Summerland.mp3)
BraseroGenisoimage stderr: Using EVERC005.MP3;1 for  Everclear/Sparkle And Fade/Everclear - Sparkle And Fade - 05 - Summerland.mp3 (Everclear - Sparkle And Fade - 02 - Heroin Girl.mp3)
BraseroGenisoimage stderr: Using EVERC006.MP3;1 for  Everclear/Sparkle And Fade/Everclear - Sparkle And Fade - 02 - Heroin Girl.mp3 (Everclear - Sparkle And Fade - 11 - Queen Of The Air.mp3)
BraseroGenisoimage stderr: Using EVERC007.MP3;1 for  Everclear/Sparkle And Fade/Everclear - Sparkle And Fade - 11 - Queen Of The Air.mp3 (Everclear - Sparkle And Fade - 09 - Her Brand New Skin.mp3)
BraseroGenisoimage stderr: Using EVERC008.MP3;1 for  Everclear/Sparkle And Fade/Everclear - Sparkle And Fade - 09 - Her Brand New Skin.mp3 (Everclear - Sparkle And Fade - 10 - Nehalem.mp3)
BraseroGenisoimage stderr: Using EVERC009.MP3;1 for  Everclear/Sparkle And Fade/Everclear - Sparkle And Fade - 10 - Nehalem.mp3 (Everclear - Sparkle And Fade - 03 - You Make Me Feel Like A Whore.mp3)
BraseroGenisoimage stderr: Using EVERC00A.MP3;1 for  Everclear/Sparkle And Fade/Everclear - Sparkle And Fade - 03 - You Make Me Feel Like A Whore.mp3 (Everclear - Sparkle And Fade - 07 - Heartspark Dollarsign.mp3)
BraseroGenisoimage stderr: Using EVERC00B.MP3;1 for  Everclear/Sparkle And Fade/Everclear - Sparkle And Fade - 07 - Heartspark Dollarsign.mp3 (Everclear - Sparkle And Fade - 01 - Electra Made Me Blind.mp3)
BraseroGenisoimage stderr: Using EVERC00C.MP3;1 for  Everclear/Sparkle And Fade/Everclear - Sparkle And Fade - 01 - Electra Made Me Blind.mp3 (Everclear - Sparkle And Fade - 08 - The Twistinside.mp3)
BraseroGenisoimage stderr: Using EVE_6000.MP3;1 for  Eve 6/Horrorscope/Eve 6 - Horrorscope - 11 - Bang.mp3 (Eve 6 - Horrorscope - 10 - Nightmare.mp3)
BraseroGenisoimage stderr: Using EVE_6001.MP3;1 for  Eve 6/Horrorscope/Eve 6 - Horrorscope - 10 - Nightmare.mp3 (Eve 6 - Horrorscope - 08 - Nocturnal.mp3)
BraseroGenisoimage stderr: Using EVE_6002.MP3;1 for  Eve 6/Horrorscope/Eve 6 - Horrorscope - 08 - Nocturnal.mp3 (Eve 6 - Horrorscope - 06 - Amphetamines.mp3)
BraseroGenisoimage stderr: Using EVE_6003.MP3;1 for  Eve 6/Horrorscope/Eve 6 - Horrorscope - 06 - Amphetamines.mp3 (Eve 6 - Horrorscope - 05 - Here's To The Night.mp3)
BraseroGenisoimage stderr: Using EVE_6004.MP3;1 for  Eve 6/Horrorscope/Eve 6 - Horrorscope - 05 - Here's To The Night.mp3 (Eve 6 - Horrorscope - 07 - Enemy.mp3)
BraseroGenisoimage stderr: Using EVE_6005.MP3;1 for  Eve 6/Horrorscope/Eve 6 - Horrorscope - 07 - Enemy.mp3 (Eve 6 - Horrorscope - 01 - Rescue.mp3)
BraseroGenisoimage stderr: Using EVE_6006.MP3;1 for  Eve 6/Horrorscope/Eve 6 - Horrorscope - 01 - Rescue.mp3 (Eve 6 - Horrorscope - 03 - On The Roof Again.mp3)
BraseroGenisoimage stderr: Using EVE_6007.MP3;1 for  Eve 6/Horrorscope/Eve 6 - Horrorscope - 03 - On The Roof Again.mp3 (Eve 6 - Horrorscope - 04 - Sunset Strip Bitch.mp3)
BraseroGenisoimage stderr: Using EVE_6008.MP3;1 for  Eve 6/Horrorscope/Eve 6 - Horrorscope - 04 - Sunset Strip Bitch.mp3 (Eve 6 - Horrorscope - 02 - Promise.mp3)
BraseroGenisoimage stderr: Using EVE_6009.MP3;1 for  Eve 6/Horrorscope/Eve 6 - Horrorscope - 02 - Promise.mp3 (Eve 6 - Horrorscope - 12 - Girl Eyes.mp3)
BraseroGenisoimage stderr: Using EVE_600A.MP3;1 for  Eve 6/Horrorscope/Eve 6 - Horrorscope - 12 - Girl Eyes.mp3 (Eve 6 - Horrorscope - 09 - Jet Pack.mp3)
BraseroGenisoimage stderr: Using EVE6_000.MP3;1 for  Eve 6/Eve 6/Eve6 - Eve6 - 09 - Saturday Night.mp3 (Eve6 - Eve6 - 01 - How Much Longer.mp3)
BraseroGenisoimage stderr: Using EVE6_001.MP3;1 for  Eve 6/Eve 6/Eve6 - Eve6 - 01 - How Much Longer.mp3 (Eve6 - Eve6 - 02 - Inside Out.mp3)
BraseroGenisoimage stderr: Using EVE6_002.MP3;1 for  Eve 6/Eve 6/Eve6 - Eve6 - 02 - Inside Out.mp3 (Eve6 - Eve6 - 07 - Superhero Girl.mp3)
BraseroGenisoimage stderr: Using EVE6_003.MP3;1 for  Eve 6/Eve 6/Eve6 - Eve6 - 07 - Superhero Girl.mp3 (Eve6 - Eve6 - 04 - Showerhead.mp3)
BraseroGenisoimage stderr: Using EVE6_004.MP3;1 for  Eve 6/Eve 6/Eve6 - Eve6 - 04 - Showerhead.mp3 (Eve6 - Eve6 - 05 - Open Road Song.mp3)
BraseroGenisoimage stderr: Using EVE6_005.MP3;1 for  Eve 6/Eve 6/Eve6 - Eve6 - 05 - Open Road Song.mp3 (Eve6 - Eve6 - 06 - Jesus Nitelite.mp3)
BraseroGenisoimage stderr: Using EVE6_006.MP3;1 for  Eve 6/Eve 6/Eve6 - Eve6 - 06 - Jesus Nitelite.mp3 (Eve6 - Eve6 - 10 - There's A Face.mp3)
BraseroGenisoimage stderr: Using EVE6_007.MP3;1 for  Eve 6/Eve 6/Eve6 - Eve6 - 10 - There's A Face.mp3 (Eve6 - Eve6 - 03 - Leech.mp3)
BraseroGenisoimage stderr: Using EVE6_008.MP3;1 for  Eve 6/Eve 6/Eve6 - Eve6 - 03 - Leech.mp3 (Eve6 - Eve6 - 11 - Small Town Trap.mp3)
BraseroGenisoimage stderr: Using EVE6_009.MP3;1 for  Eve 6/Eve 6/Eve6 - Eve6 - 11 - Small Town Trap.mp3 (Eve6 - Eve6 - 08 - Tongue Tied.mp3)
BraseroGenisoimage stderr: Using FLYLE000 for  Flyleaf/Flyleaf (EP) (Flyleaf (Acoustic))
BraseroGenisoimage stderr: Using FLYLE000.MP3;1 for  Flyleaf/Flyleaf (Acoustic)/Flyleaf - Red Sam (Acoustic).mp3 (Flyleaf - All Around Me (Acoustic).mp3)
BraseroGenisoimage stderr: Using FLYLE001.MP3;1 for  Flyleaf/Flyleaf (Acoustic)/Flyleaf - All Around Me (Acoustic).mp3 (Flyleaf - Fully Alive (Acoustic).mp3)
BraseroGenisoimage stderr: Using FLYLE002.MP3;1 for  Flyleaf/Flyleaf (Acoustic)/Flyleaf - Fully Alive (Acoustic).mp3 (Flyleaf - Cassie (Acoustic).mp3)
BraseroGenisoimage stderr: Using FLYLE003.MP3;1 for  Flyleaf/Flyleaf (Acoustic)/Flyleaf - Cassie (Acoustic).mp3 (Flyleaf - I'm So Sick (Acoustic).mp3)
BraseroGenisoimage stderr: Using FLYLE000.MP3;1 for  Flyleaf/Flyleaf/Flyleaf - Perfect.mp3 (Flyleaf - Red Sam.mp3)
BraseroGenisoimage stderr: Using FLYLE001.MP3;1 for  Flyleaf/Flyleaf/Flyleaf - Red Sam.mp3 (Flyleaf - Fully Alive.mp3)
BraseroGenisoimage stderr: Using FLYLE002.MP3;1 for  Flyleaf/Flyleaf/Flyleaf - Fully Alive.mp3 (Flyleaf - There For You.mp3)
BraseroGenisoimage stderr: Using FLYLE003.MP3;1 for  Flyleaf/Flyleaf/Flyleaf - There For You.mp3 (Flyleaf - Sorrow.mp3)
BraseroGenisoimage stderr: Using FLYLE004.MP3;1 for  Flyleaf/Flyleaf/Flyleaf - Sorrow.mp3 (Flyleaf - I'm So Sick.mp3)
BraseroGenisoimage stderr: Using FLYLE005.MP3;1 for  Flyleaf/Flyleaf/Flyleaf - I'm So Sick.mp3 (Flyleaf - Breathe Today.mp3)
BraseroGenisoimage stderr: Using FLYLE006.MP3;1 for  Flyleaf/Flyleaf/Flyleaf - Breathe Today.mp3 (Flyleaf - All Around Me.mp3)
BraseroGenisoimage stderr: Using FLYLE007.MP3;1 for  Flyleaf/Flyleaf/Flyleaf - All Around Me.mp3 (Flyleaf - Cassie.mp3)
BraseroGenisoimage stderr: Using FLYLE008.MP3;1 for  Flyleaf/Flyleaf/Flyleaf - Cassie.mp3 (Flyleaf - I'm Sorry.mp3)
BraseroGenisoimage stderr: Using FLYLE009.MP3;1 for  Flyleaf/Flyleaf/Flyleaf - I'm Sorry.mp3 (Flyleaf - So I Thought.mp3)
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
BraseroWodim stdout: Identification : 'RW/DVD GCC-4481B'
BraseroWodim stdout: Revision       : '1.00'
BraseroWodim stdout: Device seems to be: Generic mmc2 DVD-ROM.
BraseroWodim stdout: Current: 0x0009 (CD-R)
BraseroWodim stdout: Profile: 0x000A (CD-RW) 
BraseroWodim stdout: Profile: 0x0009 (CD-R) (current)
BraseroWodim stdout: Profile: 0x0008 (CD-ROM) 
BraseroWodim stdout: Profile: 0x0002 (Removable disk) (current)
BraseroWodim stdout: Profile: 0x0010 (DVD-ROM) 
BraseroWodim stdout: Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
BraseroWodim stdout: Driver flags   : MMC-2 SWABAUDIO BURNFREE 
BraseroWodim stdout: Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
BraseroWodim stdout: Drive buf size : 1793792 = 1751 KB
BraseroWodim stdout: FIFO size      : 20971520 = 20480 KB
BraseroWodim stderr: Speed set to 8450 KB/s
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Track 01: data   448 MB        
BraseroWodim stdout: Total size:      515 MB (51:04.78) = 229859 sectors
BraseroWodim stdout: Lout start:      515 MB (51:06/59) = 229859 sectors
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
BraseroWodim stdout: Blocks total: 359846 Blocks current: 359846 Blocks remaining: 129987
BraseroWodim stdout: Starting to write CD/DVD at speed  48.0 in dummy SAO mode for single session.
BraseroGenisoimage stderr:   2.18% done, estimate finish Sat Jul 25 10:23:02 2009
BraseroWodim stdout: Last chance to quit, starting dummy write in    4 seconds.
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
BraseroWodim stdout: Sending CUE sheet...
BraseroWodim called brasero_job_get_input_type
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Writing pregap for track 1 at -150
BraseroWodim stdout: Starting new track at sector: 0
BraseroWodim stdout: 
BraseroGenisoimage stderr:   4.35% done, estimate finish Sat Jul 25 10:24:11 2009
BraseroWodim stdout: Track 01:    0 of  448 MB written.
BraseroWodim stdout: Track 01:    1 of  448 MB written (fifo  99%) [buf  92%]   1.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    2 of  448 MB written (fifo 100%) [buf 100%]   0.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    3 of  448 MB written (fifo 100%) [buf 100%]  23.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    4 of  448 MB written (fifo 100%) [buf 100%]  22.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    5 of  448 MB written (fifo 100%) [buf 100%]  23.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    6 of  448 MB written (fifo 100%) [buf 100%]  22.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    7 of  448 MB written (fifo 100%) [buf 100%]  23.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    8 of  448 MB written (fifo 100%) [buf 100%]  22.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:   6.53% done, estimate finish Sat Jul 25 10:27:53 2009
BraseroWodim stdout: Track 01:    9 of  448 MB written (fifo 100%) [buf 100%]  23.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   10 of  448 MB written (fifo 100%) [buf 100%]  22.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   11 of  448 MB written (fifo  99%) [buf 100%]  23.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   12 of  448 MB written (fifo 100%) [buf 100%]  22.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   13 of  448 MB written (fifo  99%) [buf 100%]  23.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   14 of  448 MB written (fifo 100%) [buf 100%]  22.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   15 of  448 MB written (fifo 100%) [buf 100%]  23.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   16 of  448 MB written (fifo 100%) [buf 100%]  22.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   17 of  448 MB written (fifo  99%) [buf 100%]  23.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   18 of  448 MB written (fifo  99%) [buf  97%]  22.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:   8.71% done, estimate finish Sat Jul 25 10:27:04 2009
BraseroWodim stdout: Track 01:   19 of  448 MB written (fifo  99%) [buf 100%]  24.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   20 of  448 MB written (fifo  99%) [buf  98%]  23.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   21 of  448 MB written (fifo 100%) [buf  99%]  23.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   22 of  448 MB written (fifo 100%) [buf 100%]  23.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   23 of  448 MB written (fifo 100%) [buf  99%]  23.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   24 of  448 MB written (fifo 100%) [buf 100%]  23.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   25 of  448 MB written (fifo 100%) [buf 100%]  24.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   26 of  448 MB written (fifo 100%) [buf 100%]  23.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   27 of  448 MB written (fifo 100%) [buf 100%]  24.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   28 of  448 MB written (fifo  99%) [buf 100%]  23.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  10.88% done, estimate finish Sat Jul 25 10:26:34 2009
BraseroWodim stdout: Track 01:   29 of  448 MB written (fifo 100%) [buf 100%]  24.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   30 of  448 MB written (fifo 100%) [buf 100%]  23.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   31 of  448 MB written (fifo 100%) [buf  99%]  24.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   32 of  448 MB written (fifo 100%) [buf 100%]  23.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   33 of  448 MB written (fifo 100%) [buf 100%]  24.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   34 of  448 MB written (fifo 100%) [buf 100%]  25.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   35 of  448 MB written (fifo 100%) [buf 100%]  24.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   36 of  448 MB written (fifo  99%) [buf 100%]  25.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   37 of  448 MB written (fifo 100%) [buf 100%]  24.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   38 of  448 MB written (fifo 100%) [buf 100%]  25.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  13.06% done, estimate finish Sat Jul 25 10:26:06 2009
BraseroWodim stdout: Track 01:   39 of  448 MB written (fifo 100%) [buf 100%]  24.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   40 of  448 MB written (fifo  99%) [buf 100%]  25.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   41 of  448 MB written (fifo 100%) [buf 100%]  24.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   42 of  448 MB written (fifo 100%) [buf 100%]  25.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   43 of  448 MB written (fifo 100%) [buf 100%]  24.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   44 of  448 MB written (fifo 100%) [buf  99%]  25.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   45 of  448 MB written (fifo 100%) [buf 100%]  24.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   46 of  448 MB written (fifo 100%) [buf 100%]  25.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   47 of  448 MB written (fifo 100%) [buf 100%]  24.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   48 of  448 MB written (fifo 100%) [buf 100%]  25.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  15.23% done, estimate finish Sat Jul 25 10:25:53 2009
BraseroWodim stdout: Track 01:   49 of  448 MB written (fifo 100%) [buf 100%]  24.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   50 of  448 MB written (fifo 100%) [buf 100%]  25.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   51 of  448 MB written (fifo 100%) [buf  99%]  24.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   52 of  448 MB written (fifo 100%) [buf 100%]  26.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   53 of  448 MB written (fifo 100%) [buf  99%]  24.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   54 of  448 MB written (fifo 100%) [buf 100%]  26.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   55 of  448 MB written (fifo 100%) [buf 100%]  25.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   56 of  448 MB written (fifo 100%) [buf 100%]  25.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   57 of  448 MB written (fifo 100%) [buf 100%]  25.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  17.41% done, estimate finish Sat Jul 25 10:25:43 2009
BraseroWodim stdout: Track 01:   58 of  448 MB written (fifo 100%) [buf 100%]  25.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   59 of  448 MB written (fifo 100%) [buf  98%]  24.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   60 of  448 MB written (fifo  99%) [buf  98%]  26.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   61 of  448 MB written (fifo 100%) [buf 100%]  25.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   62 of  448 MB written (fifo  99%) [buf 100%]  26.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   63 of  448 MB written (fifo 100%) [buf 100%]  25.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   64 of  448 MB written (fifo  99%) [buf  99%]  26.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   65 of  448 MB written (fifo 100%) [buf  99%]  27.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   66 of  448 MB written (fifo 100%) [buf  96%]  25.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   67 of  448 MB written (fifo 100%) [buf  99%]  27.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  19.58% done, estimate finish Sat Jul 25 10:25:31 2009
BraseroWodim stdout: Track 01:   68 of  448 MB written (fifo 100%) [buf 100%]  26.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   69 of  448 MB written (fifo  99%) [buf 100%]  27.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   70 of  448 MB written (fifo  98%) [buf 100%]  26.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   71 of  448 MB written (fifo  98%) [buf 100%]  27.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   72 of  448 MB written (fifo  99%) [buf 100%]  26.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   73 of  448 MB written (fifo 100%) [buf  99%]  27.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   74 of  448 MB written (fifo 100%) [buf 100%]  26.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   75 of  448 MB written (fifo  99%) [buf  97%]  27.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   76 of  448 MB written (fifo 100%) [buf 100%]  26.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   77 of  448 MB written (fifo 100%) [buf  96%]  26.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  21.76% done, estimate finish Sat Jul 25 10:25:25 2009
BraseroWodim stdout: Track 01:   78 of  448 MB written (fifo  99%) [buf  82%]  21.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   79 of  448 MB written (fifo  99%) [buf  99%]  37.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   80 of  448 MB written (fifo  99%) [buf 100%]  26.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   81 of  448 MB written (fifo 100%) [buf 100%]  27.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   82 of  448 MB written (fifo 100%) [buf 100%]  26.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   83 of  448 MB written (fifo  99%) [buf 100%]  27.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   84 of  448 MB written (fifo 100%) [buf 100%]  26.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   85 of  448 MB written (fifo 100%) [buf  99%]  27.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   86 of  448 MB written (fifo 100%) [buf 100%]  26.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   87 of  448 MB written (fifo  99%) [buf 100%]  27.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  23.93% done, estimate finish Sat Jul 25 10:25:20 2009
BraseroWodim stdout: Track 01:   88 of  448 MB written (fifo 100%) [buf  99%]  26.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   89 of  448 MB written (fifo  99%) [buf 100%]  27.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   90 of  448 MB written (fifo 100%) [buf 100%]  26.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   91 of  448 MB written (fifo  99%) [buf  99%]  27.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   92 of  448 MB written (fifo 100%) [buf  99%]  26.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   93 of  448 MB written (fifo 100%) [buf  99%]  28.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   94 of  448 MB written (fifo 100%) [buf 100%]  27.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   95 of  448 MB written (fifo 100%) [buf 100%]  27.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   96 of  448 MB written (fifo 100%) [buf  99%]  28.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  26.11% done, estimate finish Sat Jul 25 10:25:13 2009
BraseroWodim stdout: Track 01:   97 of  448 MB written (fifo  99%) [buf 100%]  27.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   98 of  448 MB written (fifo 100%) [buf 100%]  28.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   99 of  448 MB written (fifo  99%) [buf 100%]  28.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  100 of  448 MB written (fifo 100%) [buf 100%]  28.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  101 of  448 MB written (fifo  99%) [buf 100%]  28.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  102 of  448 MB written (fifo 100%) [buf 100%]  28.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  103 of  448 MB written (fifo  99%) [buf 100%]  28.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  104 of  448 MB written (fifo 100%) [buf 100%]  29.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  105 of  448 MB written (fifo 100%) [buf  99%]  28.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  106 of  448 MB written (fifo 100%) [buf 100%]  29.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  28.28% done, estimate finish Sat Jul 25 10:25:06 2009
BraseroWodim stdout: Track 01:  107 of  448 MB written (fifo 100%) [buf 100%]  28.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  108 of  448 MB written (fifo  99%) [buf 100%]  29.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  109 of  448 MB written (fifo 100%) [buf 100%]  28.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  110 of  448 MB written (fifo  99%) [buf 100%]  29.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  111 of  448 MB written (fifo  99%) [buf 100%]  28.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  112 of  448 MB written (fifo  98%) [buf 100%]  29.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  113 of  448 MB written (fifo  99%) [buf  99%]  28.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  114 of  448 MB written (fifo  99%) [buf 100%]  29.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  115 of  448 MB written (fifo 100%) [buf  99%]  28.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  116 of  448 MB written (fifo  99%) [buf 100%]  29.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  30.46% done, estimate finish Sat Jul 25 10:25:04 2009
BraseroWodim stdout: Track 01:  117 of  448 MB written (fifo  99%) [buf 100%]  28.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  118 of  448 MB written (fifo 100%) [buf 100%]  29.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  119 of  448 MB written (fifo 100%) [buf  99%]  28.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  120 of  448 MB written (fifo 100%) [buf 100%]  29.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  121 of  448 MB written (fifo 100%) [buf  98%]  28.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  122 of  448 MB written (fifo  99%) [buf 100%]  29.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  123 of  448 MB written (fifo 100%) [buf  99%]  28.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  124 of  448 MB written (fifo  99%) [buf 100%]  29.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  125 of  448 MB written (fifo 100%) [buf  98%]  28.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  126 of  448 MB written (fifo 100%) [buf 100%]  29.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  32.63% done, estimate finish Sat Jul 25 10:24:59 2009
BraseroWodim stdout: Track 01:  127 of  448 MB written (fifo  99%) [buf 100%]  30.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  128 of  448 MB written (fifo 100%) [buf  99%]  29.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  129 of  448 MB written (fifo 100%) [buf 100%]  30.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  130 of  448 MB written (fifo  99%) [buf 100%]  29.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  131 of  448 MB written (fifo 100%) [buf  99%]  30.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  132 of  448 MB written (fifo  99%) [buf  99%]  29.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  133 of  448 MB written (fifo 100%) [buf  99%]  30.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  134 of  448 MB written (fifo  99%) [buf  99%]  29.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  135 of  448 MB written (fifo 100%) [buf  99%]  30.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  34.81% done, estimate finish Sat Jul 25 10:24:55 2009
BraseroWodim stdout: Track 01:  136 of  448 MB written (fifo 100%) [buf 100%]  29.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  137 of  448 MB written (fifo  99%) [buf 100%]  30.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  138 of  448 MB written (fifo 100%) [buf 100%]  29.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  139 of  448 MB written (fifo 100%) [buf 100%]  30.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  140 of  448 MB written (fifo  99%) [buf 100%]  29.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  141 of  448 MB written (fifo  99%) [buf 100%]  30.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  142 of  448 MB written (fifo 100%) [buf  98%]  29.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  143 of  448 MB written (fifo  99%) [buf 100%]  31.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  144 of  448 MB written (fifo 100%) [buf 100%]  29.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  145 of  448 MB written (fifo 100%) [buf 100%]  30.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  36.98% done, estimate finish Sat Jul 25 10:24:53 2009
BraseroWodim stdout: Track 01:  146 of  448 MB written (fifo 100%) [buf 100%]  29.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  147 of  448 MB written (fifo 100%) [buf 100%]  30.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  148 of  448 MB written (fifo 100%) [buf 100%]  30.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  149 of  448 MB written (fifo 100%) [buf 100%]  30.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  150 of  448 MB written (fifo  99%) [buf 100%]  30.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  151 of  448 MB written (fifo 100%) [buf 100%]  31.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  152 of  448 MB written (fifo 100%) [buf  99%]  30.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  153 of  448 MB written (fifo 100%) [buf 100%]  31.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  154 of  448 MB written (fifo  99%) [buf 100%]  30.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  155 of  448 MB written (fifo  99%) [buf  99%]  31.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  39.16% done, estimate finish Sat Jul 25 10:24:50 2009
BraseroWodim stdout: Track 01:  156 of  448 MB written (fifo  98%) [buf 100%]  30.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  157 of  448 MB written (fifo 100%) [buf 100%]  31.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  158 of  448 MB written (fifo 100%) [buf  99%]  32.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  159 of  448 MB written (fifo 100%) [buf 100%]  31.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  160 of  448 MB written (fifo  99%) [buf  99%]  32.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  161 of  448 MB written (fifo 100%) [buf  99%]  30.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  162 of  448 MB written (fifo 100%) [buf 100%]  32.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  163 of  448 MB written (fifo  99%) [buf 100%]  31.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  164 of  448 MB written (fifo 100%) [buf  99%]  32.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  165 of  448 MB written (fifo  99%) [buf 100%]  31.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  41.33% done, estimate finish Sat Jul 25 10:24:47 2009
BraseroWodim stdout: Track 01:  166 of  448 MB written (fifo 100%) [buf  98%]  31.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  167 of  448 MB written (fifo 100%) [buf 100%]  31.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  168 of  448 MB written (fifo 100%) [buf 100%]  32.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  169 of  448 MB written (fifo 100%) [buf  99%]  31.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  170 of  448 MB written (fifo  99%) [buf 100%]  32.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  171 of  448 MB written (fifo  99%) [buf 100%]  31.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  172 of  448 MB written (fifo 100%) [buf  99%]  32.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  173 of  448 MB written (fifo  99%) [buf  98%]  30.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  174 of  448 MB written (fifo  99%) [buf 100%]  33.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  175 of  448 MB written (fifo 100%) [buf  99%]  31.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  43.51% done, estimate finish Sat Jul 25 10:24:44 2009
BraseroWodim stdout: Track 01:  176 of  448 MB written (fifo  98%) [buf  99%]  32.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  177 of  448 MB written (fifo 100%) [buf  99%]  31.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  178 of  448 MB written (fifo 100%) [buf  99%]  32.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  179 of  448 MB written (fifo  99%) [buf 100%]  31.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  180 of  448 MB written (fifo 100%) [buf 100%]  32.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  181 of  448 MB written (fifo  99%) [buf  99%]  31.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  182 of  448 MB written (fifo  99%) [buf 100%]  32.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  183 of  448 MB written (fifo 100%) [buf  99%]  31.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  184 of  448 MB written (fifo  99%) [buf  99%]  32.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  45.68% done, estimate finish Sat Jul 25 10:24:41 2009
BraseroWodim stdout: Track 01:  185 of  448 MB written (fifo  99%) [buf 100%]  31.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  186 of  448 MB written (fifo  99%) [buf  99%]  32.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  187 of  448 MB written (fifo 100%) [buf  99%]  31.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  188 of  448 MB written (fifo  99%) [buf 100%]  32.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  189 of  448 MB written (fifo 100%) [buf  99%]  33.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  190 of  448 MB written (fifo  99%) [buf  98%]  32.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  191 of  448 MB written (fifo  99%) [buf 100%]  34.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  192 of  448 MB written (fifo 100%) [buf  99%]  32.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  193 of  448 MB written (fifo 100%) [buf  99%]  33.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  194 of  448 MB written (fifo 100%) [buf  99%]  32.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  47.86% done, estimate finish Sat Jul 25 10:24:41 2009
BraseroWodim stdout: Track 01:  195 of  448 MB written (fifo 100%) [buf  99%]  33.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  196 of  448 MB written (fifo  99%) [buf 100%]  32.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  197 of  448 MB written (fifo  99%) [buf 100%]  33.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  198 of  448 MB written (fifo 100%) [buf  99%]  32.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  199 of  448 MB written (fifo 100%) [buf  98%]  33.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  200 of  448 MB written (fifo  99%) [buf  99%]  33.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  201 of  448 MB written (fifo 100%) [buf 100%]  33.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  202 of  448 MB written (fifo  99%) [buf 100%]  32.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  203 of  448 MB written (fifo  99%) [buf  99%]  33.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  204 of  448 MB written (fifo 100%) [buf  99%]  33.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  50.03% done, estimate finish Sat Jul 25 10:24:38 2009
BraseroWodim stdout: Track 01:  205 of  448 MB written (fifo 100%) [buf  99%]  33.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  206 of  448 MB written (fifo  99%) [buf  99%]  32.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  207 of  448 MB written (fifo 100%) [buf  99%]  33.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  208 of  448 MB written (fifo  99%) [buf 100%]  33.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  209 of  448 MB written (fifo 100%) [buf  99%]  33.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  210 of  448 MB written (fifo  99%) [buf  99%]  32.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  211 of  448 MB written (fifo 100%) [buf  99%]  33.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  212 of  448 MB written (fifo 100%) [buf  99%]  32.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  213 of  448 MB written (fifo  99%) [buf  98%]  33.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  214 of  448 MB written (fifo 100%) [buf  99%]  33.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  52.21% done, estimate finish Sat Jul 25 10:24:36 2009
BraseroWodim stdout: Track 01:  215 of  448 MB written (fifo  99%) [buf  99%]  33.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  216 of  448 MB written (fifo  99%) [buf 100%]  32.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  217 of  448 MB written (fifo  99%) [buf 100%]  34.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  218 of  448 MB written (fifo 100%) [buf  99%]  32.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  219 of  448 MB written (fifo 100%) [buf  99%]  34.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  220 of  448 MB written (fifo 100%) [buf  99%]  35.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  221 of  448 MB written (fifo 100%) [buf  99%]  33.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  222 of  448 MB written (fifo  99%) [buf 100%]  35.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  223 of  448 MB written (fifo 100%) [buf  99%]  33.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  54.38% done, estimate finish Sat Jul 25 10:24:34 2009
BraseroWodim stdout: Track 01:  224 of  448 MB written (fifo 100%) [buf  99%]  35.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  225 of  448 MB written (fifo 100%) [buf  99%]  34.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  226 of  448 MB written (fifo 100%) [buf  99%]  35.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  227 of  448 MB written (fifo 100%) [buf 100%]  34.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  228 of  448 MB written (fifo  99%) [buf  99%]  34.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  229 of  448 MB written (fifo 100%) [buf  99%]  34.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  230 of  448 MB written (fifo 100%) [buf  99%]  35.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  231 of  448 MB written (fifo 100%) [buf  99%]  34.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  232 of  448 MB written (fifo 100%) [buf  98%]  34.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  233 of  448 MB written (fifo 100%) [buf  99%]  34.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  56.56% done, estimate finish Sat Jul 25 10:24:33 2009
BraseroWodim stdout: Track 01:  234 of  448 MB written (fifo 100%) [buf  99%]  35.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  235 of  448 MB written (fifo  99%) [buf  99%]  34.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  236 of  448 MB written (fifo 100%) [buf  98%]  34.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  237 of  448 MB written (fifo  99%) [buf  99%]  34.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  238 of  448 MB written (fifo 100%) [buf  99%]  35.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  239 of  448 MB written (fifo 100%) [buf  99%]  34.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  240 of  448 MB written (fifo 100%) [buf  99%]  34.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  241 of  448 MB written (fifo 100%) [buf  99%]  34.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  242 of  448 MB written (fifo  99%) [buf  99%]  35.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  243 of  448 MB written (fifo  99%) [buf  99%]  34.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  58.73% done, estimate finish Sat Jul 25 10:24:31 2009
BraseroWodim stdout: Track 01:  244 of  448 MB written (fifo 100%) [buf  98%]  34.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  245 of  448 MB written (fifo 100%) [buf  96%]  34.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  246 of  448 MB written (fifo 100%) [buf  99%]  35.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  247 of  448 MB written (fifo 100%) [buf  97%]  33.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  248 of  448 MB written (fifo 100%) [buf  99%]  36.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  249 of  448 MB written (fifo 100%) [buf  99%]  34.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  250 of  448 MB written (fifo 100%) [buf  99%]  35.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  251 of  448 MB written (fifo 100%) [buf  99%]  36.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  252 of  448 MB written (fifo 100%) [buf  93%]  34.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  253 of  448 MB written (fifo  99%) [buf 100%]  37.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  60.91% done, estimate finish Sat Jul 25 10:24:29 2009
BraseroWodim stdout: Track 01:  254 of  448 MB written (fifo 100%) [buf  99%]  35.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  255 of  448 MB written (fifo  99%) [buf  99%]  36.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  256 of  448 MB written (fifo 100%) [buf  99%]  35.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  257 of  448 MB written (fifo  99%) [buf  99%]  36.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  258 of  448 MB written (fifo 100%) [buf  99%]  35.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  259 of  448 MB written (fifo 100%) [buf  99%]  36.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  260 of  448 MB written (fifo 100%) [buf  99%]  35.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  261 of  448 MB written (fifo 100%) [buf  99%]  36.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  262 of  448 MB written (fifo 100%) [buf  99%]  35.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  63.08% done, estimate finish Sat Jul 25 10:24:28 2009
BraseroWodim stdout: Track 01:  263 of  448 MB written (fifo 100%) [buf  99%]  36.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  264 of  448 MB written (fifo  99%) [buf  99%]  35.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  265 of  448 MB written (fifo  99%) [buf  99%]  36.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  266 of  448 MB written (fifo  99%) [buf  99%]  35.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  267 of  448 MB written (fifo  99%) [buf  99%]  36.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  268 of  448 MB written (fifo 100%) [buf  99%]  35.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  269 of  448 MB written (fifo 100%) [buf  99%]  36.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  270 of  448 MB written (fifo 100%) [buf  97%]  35.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  271 of  448 MB written (fifo  99%) [buf 100%]  36.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  272 of  448 MB written (fifo 100%) [buf  99%]  35.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  65.26% done, estimate finish Sat Jul 25 10:24:25 2009
BraseroWodim stdout: Track 01:  273 of  448 MB written (fifo 100%) [buf  99%]  36.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  274 of  448 MB written (fifo 100%) [buf  99%]  35.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  275 of  448 MB written (fifo  99%) [buf  99%]  36.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  276 of  448 MB written (fifo  99%) [buf  99%]  35.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  277 of  448 MB written (fifo  99%) [buf  99%]  36.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  278 of  448 MB written (fifo  99%) [buf  99%]  35.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  279 of  448 MB written (fifo 100%) [buf  99%]  36.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  280 of  448 MB written (fifo  99%) [buf  99%]  35.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  281 of  448 MB written (fifo 100%) [buf  99%]  36.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  282 of  448 MB written (fifo 100%) [buf  99%]  37.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  67.44% done, estimate finish Sat Jul 25 10:24:24 2009
BraseroWodim stdout: Track 01:  283 of  448 MB written (fifo  99%) [buf  98%]  36.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  284 of  448 MB written (fifo 100%) [buf  99%]  38.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  285 of  448 MB written (fifo  99%) [buf  99%]  36.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  286 of  448 MB written (fifo 100%) [buf  98%]  37.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  287 of  448 MB written (fifo  99%) [buf  99%]  37.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  288 of  448 MB written (fifo 100%) [buf  99%]  37.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  289 of  448 MB written (fifo  99%) [buf  99%]  36.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  290 of  448 MB written (fifo 100%) [buf  99%]  37.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  291 of  448 MB written (fifo  99%) [buf  99%]  36.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  292 of  448 MB written (fifo  99%) [buf  99%]  37.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  69.61% done, estimate finish Sat Jul 25 10:24:23 2009
BraseroWodim stdout: Track 01:  293 of  448 MB written (fifo 100%) [buf  98%]  36.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  294 of  448 MB written (fifo  99%) [buf  99%]  38.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  295 of  448 MB written (fifo 100%) [buf  99%]  36.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  296 of  448 MB written (fifo 100%) [buf  99%]  37.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  297 of  448 MB written (fifo 100%) [buf  99%]  36.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  298 of  448 MB written (fifo 100%) [buf  99%]  37.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  299 of  448 MB written (fifo  99%) [buf  99%]  36.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  300 of  448 MB written (fifo 100%) [buf  98%]  37.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  301 of  448 MB written (fifo 100%) [buf  99%]  37.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  71.78% done, estimate finish Sat Jul 25 10:24:22 2009
BraseroWodim stdout: Track 01:  302 of  448 MB written (fifo  99%) [buf  99%]  37.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  303 of  448 MB written (fifo 100%) [buf  99%]  36.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  304 of  448 MB written (fifo  99%) [buf  99%]  37.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  305 of  448 MB written (fifo  99%) [buf 100%]  36.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  306 of  448 MB written (fifo 100%) [buf  99%]  37.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  307 of  448 MB written (fifo 100%) [buf  99%]  36.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  308 of  448 MB written (fifo 100%) [buf  99%]  37.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  309 of  448 MB written (fifo 100%) [buf  99%]  36.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  310 of  448 MB written (fifo  99%) [buf 100%]  38.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  311 of  448 MB written (fifo 100%) [buf  99%]  36.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  73.96% done, estimate finish Sat Jul 25 10:24:21 2009
BraseroWodim stdout: Track 01:  312 of  448 MB written (fifo 100%) [buf  99%]  37.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  313 of  448 MB written (fifo  99%) [buf  99%]  39.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  314 of  448 MB written (fifo  99%) [buf  99%]  37.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  315 of  448 MB written (fifo  99%) [buf  99%]  39.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  316 of  448 MB written (fifo  99%) [buf  99%]  37.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  317 of  448 MB written (fifo 100%) [buf  99%]  39.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  318 of  448 MB written (fifo 100%) [buf  99%]  37.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  319 of  448 MB written (fifo 100%) [buf  99%]  39.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  320 of  448 MB written (fifo 100%) [buf  99%]  37.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  321 of  448 MB written (fifo 100%) [buf  99%]  39.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  76.14% done, estimate finish Sat Jul 25 10:24:20 2009
BraseroWodim stdout: Track 01:  322 of  448 MB written (fifo  99%) [buf  99%]  37.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  323 of  448 MB written (fifo  99%) [buf  99%]  39.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  324 of  448 MB written (fifo  99%) [buf 100%]  37.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  325 of  448 MB written (fifo 100%) [buf  99%]  39.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  326 of  448 MB written (fifo  99%) [buf  99%]  37.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  327 of  448 MB written (fifo 100%) [buf  99%]  38.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  328 of  448 MB written (fifo 100%) [buf  99%]  38.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  329 of  448 MB written (fifo 100%) [buf  99%]  39.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  330 of  448 MB written (fifo  99%) [buf 100%]  37.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  331 of  448 MB written (fifo 100%) [buf  99%]  38.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  78.31% done, estimate finish Sat Jul 25 10:24:18 2009
BraseroWodim stdout: Track 01:  332 of  448 MB written (fifo 100%) [buf  99%]  38.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  333 of  448 MB written (fifo 100%) [buf  99%]  39.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  334 of  448 MB written (fifo  99%) [buf  98%]  37.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  335 of  448 MB written (fifo 100%) [buf  99%]  39.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  336 of  448 MB written (fifo  99%) [buf 100%]  37.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  337 of  448 MB written (fifo  99%) [buf  99%]  39.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  338 of  448 MB written (fifo  99%) [buf  99%]  37.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  339 of  448 MB written (fifo  99%) [buf  99%]  39.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  340 of  448 MB written (fifo  99%) [buf  99%]  37.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  341 of  448 MB written (fifo 100%) [buf  99%]  39.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  80.48% done, estimate finish Sat Jul 25 10:24:17 2009
BraseroWodim stdout: Track 01:  342 of  448 MB written (fifo  99%) [buf  99%]  37.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  343 of  448 MB written (fifo  99%) [buf  99%]  39.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  344 of  448 MB written (fifo  99%) [buf  97%]  39.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  345 of  448 MB written (fifo  99%) [buf  97%]  38.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  346 of  448 MB written (fifo 100%) [buf  99%]  41.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  347 of  448 MB written (fifo 100%) [buf  99%]  39.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  348 of  448 MB written (fifo 100%) [buf  99%]  40.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  349 of  448 MB written (fifo 100%) [buf  98%]  38.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  350 of  448 MB written (fifo  99%) [buf  99%]  40.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  82.66% done, estimate finish Sat Jul 25 10:24:16 2009
BraseroWodim stdout: Track 01:  351 of  448 MB written (fifo 100%) [buf  99%]  39.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  352 of  448 MB written (fifo  99%) [buf  99%]  40.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  353 of  448 MB written (fifo 100%) [buf  98%]  38.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  354 of  448 MB written (fifo 100%) [buf  99%]  40.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  355 of  448 MB written (fifo 100%) [buf  99%]  39.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  356 of  448 MB written (fifo  99%) [buf  99%]  40.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  357 of  448 MB written (fifo 100%) [buf  99%]  39.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  358 of  448 MB written (fifo  99%) [buf  99%]  40.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  359 of  448 MB written (fifo 100%) [buf  99%]  38.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  360 of  448 MB written (fifo  99%) [buf  99%]  40.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  84.84% done, estimate finish Sat Jul 25 10:24:16 2009
BraseroWodim stdout: Track 01:  361 of  448 MB written (fifo  99%) [buf  99%]  39.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  362 of  448 MB written (fifo  99%) [buf  99%]  40.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  363 of  448 MB written (fifo  99%) [buf  99%]  39.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  364 of  448 MB written (fifo  99%) [buf  99%]  40.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  365 of  448 MB written (fifo  99%) [buf  99%]  39.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  366 of  448 MB written (fifo  99%) [buf  99%]  40.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  367 of  448 MB written (fifo 100%) [buf  99%]  39.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  368 of  448 MB written (fifo 100%) [buf  99%]  40.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  369 of  448 MB written (fifo  99%) [buf  99%]  39.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  370 of  448 MB written (fifo  99%) [buf 100%]  40.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  87.01% done, estimate finish Sat Jul 25 10:24:14 2009
BraseroWodim stdout: Track 01:  371 of  448 MB written (fifo 100%) [buf  99%]  39.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  372 of  448 MB written (fifo 100%) [buf  99%]  40.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  373 of  448 MB written (fifo  99%) [buf  98%]  38.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  374 of  448 MB written (fifo 100%) [buf  98%]  40.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  375 of  448 MB written (fifo 100%) [buf  99%]  42.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  376 of  448 MB written (fifo 100%) [buf  99%]  40.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  377 of  448 MB written (fifo 100%) [buf  99%]  41.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  378 of  448 MB written (fifo 100%) [buf  99%]  40.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  379 of  448 MB written (fifo 100%) [buf  96%]  41.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  380 of  448 MB written (fifo 100%) [buf  99%]  40.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  89.19% done, estimate finish Sat Jul 25 10:24:13 2009
BraseroWodim stdout: Track 01:  381 of  448 MB written (fifo 100%) [buf  99%]  42.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  382 of  448 MB written (fifo  99%) [buf  99%]  40.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  383 of  448 MB written (fifo 100%) [buf  99%]  41.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  384 of  448 MB written (fifo  99%) [buf  99%]  40.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  385 of  448 MB written (fifo 100%) [buf  99%]  41.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  386 of  448 MB written (fifo 100%) [buf  99%]  40.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  387 of  448 MB written (fifo 100%) [buf  99%]  41.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  388 of  448 MB written (fifo  99%) [buf  99%]  40.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  389 of  448 MB written (fifo  99%) [buf  99%]  41.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  91.37% done, estimate finish Sat Jul 25 10:24:13 2009
BraseroWodim stdout: Track 01:  390 of  448 MB written (fifo  99%) [buf  99%]  39.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  391 of  448 MB written (fifo  99%) [buf  99%]  41.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  392 of  448 MB written (fifo  99%) [buf  99%]  40.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  393 of  448 MB written (fifo 100%) [buf  98%]  40.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  394 of  448 MB written (fifo  99%) [buf  99%]  40.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  395 of  448 MB written (fifo 100%) [buf  99%]  41.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  396 of  448 MB written (fifo  99%) [buf  99%]  40.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  397 of  448 MB written (fifo 100%) [buf  99%]  41.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  398 of  448 MB written (fifo  99%) [buf  99%]  40.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  399 of  448 MB written (fifo  99%) [buf  99%]  41.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  93.54% done, estimate finish Sat Jul 25 10:24:11 2009
BraseroWodim stdout: Track 01:  400 of  448 MB written (fifo 100%) [buf  99%]  40.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  401 of  448 MB written (fifo 100%) [buf  99%]  41.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  402 of  448 MB written (fifo 100%) [buf  99%]  40.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  403 of  448 MB written (fifo  99%) [buf  99%]  41.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  404 of  448 MB written (fifo  99%) [buf  99%]  40.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  405 of  448 MB written (fifo 100%) [buf  99%]  41.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  406 of  448 MB written (fifo  99%) [buf  98%]  42.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  407 of  448 MB written (fifo 100%) [buf  99%]  42.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  408 of  448 MB written (fifo  99%) [buf  99%]  42.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  409 of  448 MB written (fifo 100%) [buf  99%]  41.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  95.72% done, estimate finish Sat Jul 25 10:24:10 2009
BraseroWodim stdout: Track 01:  410 of  448 MB written (fifo  99%) [buf  99%]  42.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  411 of  448 MB written (fifo 100%) [buf  99%]  41.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  412 of  448 MB written (fifo  99%) [buf  99%]  42.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  413 of  448 MB written (fifo 100%) [buf  99%]  41.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  414 of  448 MB written (fifo  99%) [buf  99%]  42.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  415 of  448 MB written (fifo  99%) [buf  99%]  41.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  416 of  448 MB written (fifo 100%) [buf  99%]  42.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  417 of  448 MB written (fifo 100%) [buf  96%]  40.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  418 of  448 MB written (fifo 100%) [buf  99%]  43.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  419 of  448 MB written (fifo 100%) [buf  98%]  40.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  97.89% done, estimate finish Sat Jul 25 10:24:10 2009
BraseroWodim stdout: Track 01:  420 of  448 MB written (fifo  99%) [buf  98%]  43.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  421 of  448 MB written (fifo  99%) [buf  99%]  41.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  422 of  448 MB written (fifo 100%) [buf  99%]  42.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  423 of  448 MB written (fifo  99%) [buf  99%]  41.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  424 of  448 MB written (fifo  99%) [buf  99%]  42.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  425 of  448 MB written (fifo  99%) [buf  99%]  41.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  426 of  448 MB written (fifo 100%) [buf  99%]  42.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  427 of  448 MB written (fifo 100%) [buf  99%]  41.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  428 of  448 MB written (fifo  99%) [buf  99%]  42.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr: Total translation table size: 0
BraseroGenisoimage stderr: Total rockridge attributes bytes: 12989
BraseroGenisoimage stderr: Total directory bytes: 22528
BraseroGenisoimage stderr: Path table size(bytes): 150
BraseroGenisoimage stderr: Max brk space used 21000
BraseroGenisoimage stderr: 229859 extents written (448 MB)
BraseroWodim stdout: Track 01:  429 of  448 MB written (fifo  99%) [buf  99%]  41.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr: HUP
BraseroWodim stdout: Track 01:  430 of  448 MB written (fifo  98%) [buf  99%]  42.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  431 of  448 MB written (fifo 100%) [buf 100%]  41.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  432 of  448 MB written (fifo 100%) [buf  99%]  42.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage process finished with status 0
BraseroGenisoimage called brasero_job_get_fd_out
BraseroGenisoimage Finished track successfully
BraseroGenisoimage got killed
BraseroGenisoimage disconnecting BraseroGenisoimage from BraseroWodim
BraseroGenisoimage deactivating
BraseroWodim stdout: Track 01:  433 of  448 MB written (fifo 100%) [buf  99%]  41.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  434 of  448 MB written (fifo 100%) [buf 100%]  42.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  435 of  448 MB written (fifo 100%) [buf  99%]  41.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  436 of  448 MB written (fifo 100%) [buf  99%]  42.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  437 of  448 MB written (fifo 100%) [buf 100%]  43.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  438 of  448 MB written (fifo 100%) [buf  99%]  42.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  439 of  448 MB written (fifo 100%) [buf  99%]  43.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  440 of  448 MB written (fifo 100%) [buf 100%]  42.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  441 of  448 MB written (fifo 100%) [buf  99%]  43.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  442 of  448 MB written (fifo 100%) [buf  99%]  42.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  443 of  448 MB written (fifo 100%) [buf 100%]  43.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  444 of  448 MB written (fifo 100%) [buf  99%]  42.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  445 of  448 MB written (fifo 100%) [buf 100%]  43.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  446 of  448 MB written (fifo 100%) [buf 100%]  42.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  447 of  448 MB written (fifo 100%) [buf  99%]  43.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  448 of  448 MB written (fifo 100%) [buf  99%]  42.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01: Total bytes read/written: 470751232/470751232 (229859 sectors).
BraseroWodim stdout: Writing  time:  110.433s
BraseroWodim stdout: Average write speed  27.8x.
BraseroWodim stdout: Min drive buffer fill was 82%
BraseroWodim stdout: Fixating...
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: WARNING: Some drives don't like fixation in dummy mode.
BraseroWodim stdout: Fixating time:    2.378s
BraseroWodim stderr: wodim: fifo had 7415 puts and 7415 gets.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: fifo was 0 times empty and 4236 times full, min fill was 95%.
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: BURN-Free was never needed.
BraseroWodim stderr: HUP
BraseroWodim stdout: HUP
BraseroWodim process finished with status 0
BraseroWodim called brasero_job_get_fd_out
BraseroWodim called brasero_job_get_action
BraseroWodim Finished successfully session
BraseroWodim stopping
BraseroWodim got killed
BraseroWodim closing connection for BraseroWodim
Dummy session successfully finished (brasero_burn_record_session burn.c:2090)
Checking session consistency (brasero_burn_check_session_consistency burn.c:1905)
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_set_output_size_for_current_track
BraseroBurnURI stopping
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_session_output_size
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
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_current_track
BraseroLocalTrack called brasero_job_get_input_type
BraseroLocalTrack no remote URIs
BraseroLocalTrack stopping
BraseroChecksumFiles called brasero_job_get_output_type
BraseroChecksumFiles called brasero_job_get_current_track
BraseroChecksumFiles called brasero_job_get_output_type
BraseroChecksumFiles called brasero_job_get_current_track
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
	-graft-points
	-path-list
	/tmp/brasero_tmp_LXJLXU
	-exclude-list
	/tmp/brasero_tmp_YZ4LXU
	-V
	Data disc (25 Jul 09)
	-A
	Brasero-2.26.1
	-sysid
	LINUX
	-quiet
	-print-size
BraseroGenisoimage Launching command
BraseroGenisoimage called brasero_job_get_fd_out
BraseroGenisoimage stdout: 229859
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage called brasero_job_set_output_size_for_current_track
BraseroGenisoimage stdout: HUP
BraseroGenisoimage stderr: HUP
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
	speed=48
	driveropts=burnfree
	-dao
	fs=20m
	tsize=229859s
	-data
	-nopad
	-
BraseroWodim Launching command
BraseroWodim called brasero_job_get_fd_out
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage linked to BraseroWodim
BraseroChecksumImage creating input
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_input_type
BraseroChecksumImage called brasero_job_set_current_action
BraseroChecksumImage called brasero_job_get_fd_in
BraseroChecksumImage Starting checksum generation live (size = 0)
BraseroChecksumImage called brasero_job_set_nonblocking
BraseroChecksumImage called brasero_job_get_fd_in
BraseroChecksumImage called brasero_job_get_fd_out
BraseroChecksumImage called brasero_job_get_fd_in
BraseroChecksumImage called brasero_job_get_fd_out
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage linked to BraseroChecksumImage
BraseroGenisoimage getting varg
BraseroGenisoimage called brasero_job_get_action
BraseroGenisoimage called brasero_job_get_current_track
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
	-graft-points
	-path-list
	/tmp/brasero_tmp_87WRXU
	-exclude-list
	/tmp/brasero_tmp_B1WRXU
	-V
	Data disc (25 Jul 09)
	-A
	Brasero-2.26.1
	-sysid
	LINUX
BraseroGenisoimage Launching command
BraseroGenisoimage called brasero_job_get_fd_out
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
BraseroGenisoimage stderr: Using CROSS000.MP3;1 for  /Crossfade - Crossfade - 06 - The Deep End.mp3 (Crossfade - Crossfade - 02 - Cold.mp3)
BraseroGenisoimage stderr: Using BONE_000.MP3;1 for  /Bone Thugs N Harmony - East 1999 Eternal - 08 - Crossroads (Original).mp3 (Bone Thugs N Harmony - East 1999 Eternal - 08 - Crossroads.mp3)
BraseroGenisoimage stderr: Using CROSS001.MP3;1 for  /Crossfade - Crossfade - 02 - Cold.mp3 (Crossfade - Crossfade - 01 - Starless.mp3)
BraseroGenisoimage stderr: Using SEVEN000.MP3;1 for  /Seven Mary Three - American Standard - 10 - Punch In Punch Out - Seven Mar.mp3 (Seven Mary Three - American Standard - 02 - Cumbersome - Seven Mary Three.mp3)
BraseroGenisoimage stderr: Using EVERC000.MP3;1 for  Everclear/Sparkle And Fade/Everclear - Sparkle And Fade - 04 - Santa Monica.mp3 (Everclear - Sparkle And Fade - 14 - My Sexual Life.mp3)
BraseroGenisoimage stderr: Using EVERC001.MP3;1 for  Everclear/Sparkle And Fade/Everclear - Sparkle And Fade - 14 - My Sexual Life.mp3 (Everclear - Sparkle And Fade - 12 - Pale Green Stars.mp3)
BraseroGenisoimage stderr: Using EVERC002.MP3;1 for  Everclear/Sparkle And Fade/Everclear - Sparkle And Fade - 12 - Pale Green Stars.mp3 (Everclear - Sparkle And Fade - 06 - Strawberry.mp3)
BraseroGenisoimage stderr: Using EVERC003.MP3;1 for  Everclear/Sparkle And Fade/Everclear - Sparkle And Fade - 06 - Strawberry.mp3 (Everclear - Sparkle And Fade - 13 - Chemical Smile.mp3)
BraseroGenisoimage stderr: Using EVERC004.MP3;1 for  Everclear/Sparkle And Fade/Everclear - Sparkle And Fade - 13 - Chemical Smile.mp3 (Everclear - Sparkle And Fade - 05 - Summerland.mp3)
BraseroGenisoimage stderr: Using EVERC005.MP3;1 for  Everclear/Sparkle And Fade/Everclear - Sparkle And Fade - 05 - Summerland.mp3 (Everclear - Sparkle And Fade - 02 - Heroin Girl.mp3)
BraseroGenisoimage stderr: Using EVERC006.MP3;1 for  Everclear/Sparkle And Fade/Everclear - Sparkle And Fade - 02 - Heroin Girl.mp3 (Everclear - Sparkle And Fade - 11 - Queen Of The Air.mp3)
BraseroGenisoimage stderr: Using EVERC007.MP3;1 for  Everclear/Sparkle And Fade/Everclear - Sparkle And Fade - 11 - Queen Of The Air.mp3 (Everclear - Sparkle And Fade - 09 - Her Brand New Skin.mp3)
BraseroGenisoimage stderr: Using EVERC008.MP3;1 for  Everclear/Sparkle And Fade/Everclear - Sparkle And Fade - 09 - Her Brand New Skin.mp3 (Everclear - Sparkle And Fade - 10 - Nehalem.mp3)
BraseroGenisoimage stderr: Using EVERC009.MP3;1 for  Everclear/Sparkle And Fade/Everclear - Sparkle And Fade - 10 - Nehalem.mp3 (Everclear - Sparkle And Fade - 03 - You Make Me Feel Like A Whore.mp3)
BraseroGenisoimage stderr: Using EVERC00A.MP3;1 for  Everclear/Sparkle And Fade/Everclear - Sparkle And Fade - 03 - You Make Me Feel Like A Whore.mp3 (Everclear - Sparkle And Fade - 07 - Heartspark Dollarsign.mp3)
BraseroGenisoimage stderr: Using EVERC00B.MP3;1 for  Everclear/Sparkle And Fade/Everclear - Sparkle And Fade - 07 - Heartspark Dollarsign.mp3 (Everclear - Sparkle And Fade - 01 - Electra Made Me Blind.mp3)
BraseroGenisoimage stderr: Using EVERC00C.MP3;1 for  Everclear/Sparkle And Fade/Everclear - Sparkle And Fade - 01 - Electra Made Me Blind.mp3 (Everclear - Sparkle And Fade - 08 - The Twistinside.mp3)
BraseroGenisoimage stderr: Using EVE_6000.MP3;1 for  Eve 6/Horrorscope/Eve 6 - Horrorscope - 11 - Bang.mp3 (Eve 6 - Horrorscope - 10 - Nightmare.mp3)
BraseroGenisoimage stderr: Using EVE_6001.MP3;1 for  Eve 6/Horrorscope/Eve 6 - Horrorscope - 10 - Nightmare.mp3 (Eve 6 - Horrorscope - 08 - Nocturnal.mp3)
BraseroGenisoimage stderr: Using EVE_6002.MP3;1 for  Eve 6/Horrorscope/Eve 6 - Horrorscope - 08 - Nocturnal.mp3 (Eve 6 - Horrorscope - 06 - Amphetamines.mp3)
BraseroGenisoimage stderr: Using EVE_6003.MP3;1 for  Eve 6/Horrorscope/Eve 6 - Horrorscope - 06 - Amphetamines.mp3 (Eve 6 - Horrorscope - 05 - Here's To The Night.mp3)
BraseroGenisoimage stderr: Using EVE_6004.MP3;1 for  Eve 6/Horrorscope/Eve 6 - Horrorscope - 05 - Here's To The Night.mp3 (Eve 6 - Horrorscope - 07 - Enemy.mp3)
BraseroGenisoimage stderr: Using EVE_6005.MP3;1 for  Eve 6/Horrorscope/Eve 6 - Horrorscope - 07 - Enemy.mp3 (Eve 6 - Horrorscope - 01 - Rescue.mp3)
BraseroGenisoimage stderr: Using EVE_6006.MP3;1 for  Eve 6/Horrorscope/Eve 6 - Horrorscope - 01 - Rescue.mp3 (Eve 6 - Horrorscope - 03 - On The Roof Again.mp3)
BraseroGenisoimage stderr: Using EVE_6007.MP3;1 for  Eve 6/Horrorscope/Eve 6 - Horrorscope - 03 - On The Roof Again.mp3 (Eve 6 - Horrorscope - 04 - Sunset Strip Bitch.mp3)
BraseroGenisoimage stderr: Using EVE_6008.MP3;1 for  Eve 6/Horrorscope/Eve 6 - Horrorscope - 04 - Sunset Strip Bitch.mp3 (Eve 6 - Horrorscope - 02 - Promise.mp3)
BraseroGenisoimage stderr: Using EVE_6009.MP3;1 for  Eve 6/Horrorscope/Eve 6 - Horrorscope - 02 - Promise.mp3 (Eve 6 - Horrorscope - 12 - Girl Eyes.mp3)
BraseroGenisoimage stderr: Using EVE_600A.MP3;1 for  Eve 6/Horrorscope/Eve 6 - Horrorscope - 12 - Girl Eyes.mp3 (Eve 6 - Horrorscope - 09 - Jet Pack.mp3)
BraseroGenisoimage stderr: Using EVE6_000.MP3;1 for  Eve 6/Eve 6/Eve6 - Eve6 - 09 - Saturday Night.mp3 (Eve6 - Eve6 - 01 - How Much Longer.mp3)
BraseroGenisoimage stderr: Using EVE6_001.MP3;1 for  Eve 6/Eve 6/Eve6 - Eve6 - 01 - How Much Longer.mp3 (Eve6 - Eve6 - 02 - Inside Out.mp3)
BraseroGenisoimage stderr: Using EVE6_002.MP3;1 for  Eve 6/Eve 6/Eve6 - Eve6 - 02 - Inside Out.mp3 (Eve6 - Eve6 - 07 - Superhero Girl.mp3)
BraseroGenisoimage stderr: Using EVE6_003.MP3;1 for  Eve 6/Eve 6/Eve6 - Eve6 - 07 - Superhero Girl.mp3 (Eve6 - Eve6 - 04 - Showerhead.mp3)
BraseroGenisoimage stderr: Using EVE6_004.MP3;1 for  Eve 6/Eve 6/Eve6 - Eve6 - 04 - Showerhead.mp3 (Eve6 - Eve6 - 05 - Open Road Song.mp3)
BraseroGenisoimage stderr: Using EVE6_005.MP3;1 for  Eve 6/Eve 6/Eve6 - Eve6 - 05 - Open Road Song.mp3 (Eve6 - Eve6 - 06 - Jesus Nitelite.mp3)
BraseroGenisoimage stderr: Using EVE6_006.MP3;1 for  Eve 6/Eve 6/Eve6 - Eve6 - 06 - Jesus Nitelite.mp3 (Eve6 - Eve6 - 10 - There's A Face.mp3)
BraseroGenisoimage stderr: Using EVE6_007.MP3;1 for  Eve 6/Eve 6/Eve6 - Eve6 - 10 - There's A Face.mp3 (Eve6 - Eve6 - 03 - Leech.mp3)
BraseroGenisoimage stderr: Using EVE6_008.MP3;1 for  Eve 6/Eve 6/Eve6 - Eve6 - 03 - Leech.mp3 (Eve6 - Eve6 - 11 - Small Town Trap.mp3)
BraseroGenisoimage stderr: Using EVE6_009.MP3;1 for  Eve 6/Eve 6/Eve6 - Eve6 - 11 - Small Town Trap.mp3 (Eve6 - Eve6 - 08 - Tongue Tied.mp3)
BraseroGenisoimage stderr: Using FLYLE000 for  Flyleaf/Flyleaf (EP) (Flyleaf (Acoustic))
BraseroGenisoimage stderr: Using FLYLE000.MP3;1 for  Flyleaf/Flyleaf (Acoustic)/Flyleaf - Red Sam (Acoustic).mp3 (Flyleaf - All Around Me (Acoustic).mp3)
BraseroGenisoimage stderr: Using FLYLE001.MP3;1 for  Flyleaf/Flyleaf (Acoustic)/Flyleaf - All Around Me (Acoustic).mp3 (Flyleaf - Fully Alive (Acoustic).mp3)
BraseroGenisoimage stderr: Using FLYLE002.MP3;1 for  Flyleaf/Flyleaf (Acoustic)/Flyleaf - Fully Alive (Acoustic).mp3 (Flyleaf - Cassie (Acoustic).mp3)
BraseroGenisoimage stderr: Using FLYLE003.MP3;1 for  Flyleaf/Flyleaf (Acoustic)/Flyleaf - Cassie (Acoustic).mp3 (Flyleaf - I'm So Sick (Acoustic).mp3)
BraseroGenisoimage stderr: Using FLYLE000.MP3;1 for  Flyleaf/Flyleaf/Flyleaf - Perfect.mp3 (Flyleaf - Red Sam.mp3)
BraseroGenisoimage stderr: Using FLYLE001.MP3;1 for  Flyleaf/Flyleaf/Flyleaf - Red Sam.mp3 (Flyleaf - Fully Alive.mp3)
BraseroGenisoimage stderr: Using FLYLE002.MP3;1 for  Flyleaf/Flyleaf/Flyleaf - Fully Alive.mp3 (Flyleaf - There For You.mp3)
BraseroGenisoimage stderr: Using FLYLE003.MP3;1 for  Flyleaf/Flyleaf/Flyleaf - There For You.mp3 (Flyleaf - Sorrow.mp3)
BraseroGenisoimage stderr: Using FLYLE004.MP3;1 for  Flyleaf/Flyleaf/Flyleaf - Sorrow.mp3 (Flyleaf - I'm So Sick.mp3)
BraseroGenisoimage stderr: Using FLYLE005.MP3;1 for  Flyleaf/Flyleaf/Flyleaf - I'm So Sick.mp3 (Flyleaf - Breathe Today.mp3)
BraseroGenisoimage stderr: Using FLYLE006.MP3;1 for  Flyleaf/Flyleaf/Flyleaf - Breathe Today.mp3 (Flyleaf - All Around Me.mp3)
BraseroGenisoimage stderr: Using FLYLE007.MP3;1 for  Flyleaf/Flyleaf/Flyleaf - All Around Me.mp3 (Flyleaf - Cassie.mp3)
BraseroGenisoimage stderr: Using FLYLE008.MP3;1 for  Flyleaf/Flyleaf/Flyleaf - Cassie.mp3 (Flyleaf - I'm Sorry.mp3)
BraseroGenisoimage stderr: Using FLYLE009.MP3;1 for  Flyleaf/Flyleaf/Flyleaf - I'm Sorry.mp3 (Flyleaf - So I Thought.mp3)
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
BraseroWodim stdout: Identification : 'RW/DVD GCC-4481B'
BraseroWodim stdout: Revision       : '1.00'
BraseroWodim stdout: Device seems to be: Generic mmc2 DVD-ROM.
BraseroWodim stdout: Current: 0x0009 (CD-R)
BraseroWodim stdout: Profile: 0x000A (CD-RW) 
BraseroWodim stdout: Profile: 0x0009 (CD-R) (current)
BraseroWodim stdout: Profile: 0x0008 (CD-ROM) 
BraseroWodim stdout: Profile: 0x0002 (Removable disk) (current)
BraseroWodim stdout: Profile: 0x0010 (DVD-ROM) 
BraseroWodim stdout: Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
BraseroWodim stdout: Driver flags   : MMC-2 SWABAUDIO BURNFREE 
BraseroWodim stdout: Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
BraseroWodim stdout: Drive buf size : 1793792 = 1751 KB
BraseroWodim stdout: FIFO size      : 20971520 = 20480 KB
BraseroWodim stderr: Speed set to 8450 KB/s
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Track 01: data   448 MB        
BraseroWodim stdout: Total size:      515 MB (51:04.78) = 229859 sectors
BraseroWodim stdout: Lout start:      515 MB (51:06/59) = 229859 sectors
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
BraseroWodim stdout: Blocks total: 359846 Blocks current: 359846 Blocks remaining: 129987
BraseroWodim stdout: Starting to write CD/DVD at speed  48.0 in real SAO mode for single session.
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
BraseroGenisoimage stderr:   2.18% done, estimate finish Sat Jul 25 10:30:35 2009
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
BraseroWodim stdout: Writing pregap for track 1 at -150
BraseroWodim stdout: Starting new track at sector: 0
BraseroWodim stdout: 
BraseroGenisoimage stderr:   4.35% done, estimate finish Sat Jul 25 10:30:13 2009
BraseroWodim stdout: Track 01:    0 of  448 MB written.
BraseroWodim stdout: Track 01:    1 of  448 MB written (fifo  99%) [buf  92%]   2.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    2 of  448 MB written (fifo 100%) [buf 100%]   0.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    3 of  448 MB written (fifo  99%) [buf 100%]  22.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    4 of  448 MB written (fifo  99%) [buf 100%]  21.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    5 of  448 MB written (fifo  99%) [buf 100%]  22.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    6 of  448 MB written (fifo  99%) [buf 100%]  21.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    7 of  448 MB written (fifo  98%) [buf 100%]  22.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    8 of  448 MB written (fifo  99%) [buf 100%]  21.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    9 of  448 MB written (fifo  98%) [buf 100%]  22.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:   6.53% done, estimate finish Sat Jul 25 10:31:53 2009
BraseroWodim stdout: Track 01:   10 of  448 MB written (fifo  98%) [buf 100%]  22.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   11 of  448 MB written (fifo  98%) [buf 100%]  22.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   12 of  448 MB written (fifo  98%) [buf 100%]  22.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   13 of  448 MB written (fifo  97%) [buf 100%]  22.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   14 of  448 MB written (fifo  97%) [buf 100%]  22.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   15 of  448 MB written (fifo  97%) [buf 100%]  22.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   16 of  448 MB written (fifo  97%) [buf  99%]  22.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   17 of  448 MB written (fifo  96%) [buf  99%]  23.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   18 of  448 MB written (fifo  96%) [buf 100%]  22.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   19 of  448 MB written (fifo  96%) [buf 100%]  23.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:   8.71% done, estimate finish Sat Jul 25 10:30:36 2009
BraseroWodim stdout: Track 01:   20 of  448 MB written (fifo  95%) [buf 100%]  22.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   21 of  448 MB written (fifo  94%) [buf 100%]  23.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   22 of  448 MB written (fifo  94%) [buf 100%]  22.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   23 of  448 MB written (fifo  94%) [buf 100%]  23.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   24 of  448 MB written (fifo  94%) [buf 100%]  22.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   25 of  448 MB written (fifo  93%) [buf 100%]  23.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   26 of  448 MB written (fifo  92%) [buf 100%]  22.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   27 of  448 MB written (fifo  92%) [buf 100%]  23.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   28 of  448 MB written (fifo  92%) [buf  99%]  22.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   29 of  448 MB written (fifo  91%) [buf 100%]  23.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   30 of  448 MB written (fifo  91%) [buf 100%]  22.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  10.88% done, estimate finish Sat Jul 25 10:29:50 2009
BraseroWodim stdout: Track 01:   31 of  448 MB written (fifo  90%) [buf 100%]  23.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   32 of  448 MB written (fifo  90%) [buf 100%]  22.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   33 of  448 MB written (fifo  89%) [buf 100%]  23.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   34 of  448 MB written (fifo  89%) [buf  99%]  24.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   35 of  448 MB written (fifo  88%) [buf 100%]  23.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   36 of  448 MB written (fifo  87%) [buf 100%]  24.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   37 of  448 MB written (fifo  87%) [buf  99%]  23.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   38 of  448 MB written (fifo  86%) [buf  99%]  24.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   39 of  448 MB written (fifo  86%) [buf 100%]  23.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   40 of  448 MB written (fifo  85%) [buf  99%]  24.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   41 of  448 MB written (fifo  84%) [buf  97%]  24.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  13.06% done, estimate finish Sat Jul 25 10:29:20 2009
BraseroWodim stdout: Track 01:   42 of  448 MB written (fifo  84%) [buf 100%]  24.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   43 of  448 MB written (fifo  83%) [buf 100%]  23.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   44 of  448 MB written (fifo  82%) [buf 100%]  24.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   45 of  448 MB written (fifo  81%) [buf 100%]  24.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   46 of  448 MB written (fifo  81%) [buf 100%]  24.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   47 of  448 MB written (fifo  80%) [buf 100%]  24.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   48 of  448 MB written (fifo  79%) [buf 100%]  24.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   49 of  448 MB written (fifo  78%) [buf 100%]  24.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   50 of  448 MB written (fifo  78%) [buf 100%]  24.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   51 of  448 MB written (fifo  77%) [buf 100%]  24.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   52 of  448 MB written (fifo  76%) [buf 100%]  25.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  15.23% done, estimate finish Sat Jul 25 10:29:04 2009
BraseroWodim stdout: Track 01:   53 of  448 MB written (fifo  76%) [buf  98%]  23.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   54 of  448 MB written (fifo  75%) [buf 100%]  25.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   55 of  448 MB written (fifo  74%) [buf  99%]  24.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   56 of  448 MB written (fifo  73%) [buf 100%]  25.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   57 of  448 MB written (fifo  72%) [buf 100%]  24.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   58 of  448 MB written (fifo  72%) [buf 100%]  25.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   59 of  448 MB written (fifo  71%) [buf 100%]  24.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   60 of  448 MB written (fifo  70%) [buf 100%]  25.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   61 of  448 MB written (fifo  69%) [buf 100%]  24.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   62 of  448 MB written (fifo  68%) [buf 100%]  25.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   63 of  448 MB written (fifo  67%) [buf 100%]  24.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   64 of  448 MB written (fifo  66%) [buf 100%]  25.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  17.41% done, estimate finish Sat Jul 25 10:28:47 2009
BraseroWodim stdout: Track 01:   65 of  448 MB written (fifo  66%) [buf  99%]  26.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   66 of  448 MB written (fifo  64%) [buf 100%]  25.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   67 of  448 MB written (fifo  63%) [buf 100%]  26.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   68 of  448 MB written (fifo  62%) [buf 100%]  25.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   69 of  448 MB written (fifo  62%) [buf  99%]  26.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   70 of  448 MB written (fifo  60%) [buf 100%]  25.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   71 of  448 MB written (fifo  60%) [buf  99%]  26.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   72 of  448 MB written (fifo  58%) [buf 100%]  25.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   73 of  448 MB written (fifo  57%) [buf 100%]  26.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   74 of  448 MB written (fifo  57%) [buf 100%]  25.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   75 of  448 MB written (fifo  55%) [buf 100%]  26.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   76 of  448 MB written (fifo  55%) [buf 100%]  25.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  19.58% done, estimate finish Sat Jul 25 10:28:34 2009
BraseroWodim stdout: Track 01:   77 of  448 MB written (fifo  53%) [buf 100%]  26.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   78 of  448 MB written (fifo  52%) [buf 100%]  25.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   79 of  448 MB written (fifo  50%) [buf 100%]  26.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   80 of  448 MB written (fifo  49%) [buf 100%]  25.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   81 of  448 MB written (fifo  48%) [buf 100%]  26.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   82 of  448 MB written (fifo  47%) [buf 100%]  25.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   83 of  448 MB written (fifo  46%) [buf 100%]  26.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   84 of  448 MB written (fifo  44%) [buf 100%]  26.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   85 of  448 MB written (fifo  43%) [buf 100%]  26.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   86 of  448 MB written (fifo  41%) [buf  97%]  26.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   87 of  448 MB written (fifo  40%) [buf  99%]  26.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   88 of  448 MB written (fifo  39%) [buf  99%]  26.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   89 of  448 MB written (fifo  37%) [buf 100%]  26.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  21.76% done, estimate finish Sat Jul 25 10:28:28 2009
BraseroWodim stdout: Track 01:   90 of  448 MB written (fifo  36%) [buf 100%]  26.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   91 of  448 MB written (fifo  35%) [buf  99%]  27.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   92 of  448 MB written (fifo  34%) [buf  99%]  26.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   93 of  448 MB written (fifo  33%) [buf 100%]  27.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   94 of  448 MB written (fifo  31%) [buf 100%]  26.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   95 of  448 MB written (fifo  31%) [buf  99%]  27.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   96 of  448 MB written (fifo  29%) [buf  99%]  27.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   97 of  448 MB written (fifo  28%) [buf 100%]  27.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   98 of  448 MB written (fifo  27%) [buf 100%]  28.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   99 of  448 MB written (fifo  26%) [buf  98%]  26.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  100 of  448 MB written (fifo  25%) [buf  99%]  28.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  101 of  448 MB written (fifo  24%) [buf  99%]  27.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  102 of  448 MB written (fifo  22%) [buf 100%]  28.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  23.93% done, estimate finish Sat Jul 25 10:28:18 2009
BraseroWodim stdout: Track 01:  103 of  448 MB written (fifo  21%) [buf 100%]  27.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  104 of  448 MB written (fifo  20%) [buf  99%]  28.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  105 of  448 MB written (fifo  19%) [buf 100%]  27.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  106 of  448 MB written (fifo  17%) [buf  98%]  27.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  107 of  448 MB written (fifo  16%) [buf 100%]  27.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  108 of  448 MB written (fifo  15%) [buf 100%]  28.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  109 of  448 MB written (fifo  14%) [buf  99%]  27.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  110 of  448 MB written (fifo  12%) [buf  99%]  28.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  111 of  448 MB written (fifo  11%) [buf 100%]  27.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  112 of  448 MB written (fifo  10%) [buf  99%]  28.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  113 of  448 MB written (fifo   8%) [buf 100%]  27.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  114 of  448 MB written (fifo   7%) [buf 100%]  28.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  115 of  448 MB written (fifo   6%) [buf  99%]  27.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  26.11% done, estimate finish Sat Jul 25 10:28:11 2009
BraseroWodim stdout: Track 01:  116 of  448 MB written (fifo   4%) [buf 100%]  28.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  117 of  448 MB written (fifo   3%) [buf 100%]  27.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  118 of  448 MB written (fifo   2%) [buf 100%]  28.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  119 of  448 MB written (fifo   0%) [buf 100%]  27.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  120 of  448 MB written (fifo   1%) [buf  69%]  19.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  121 of  448 MB written (fifo   0%) [buf  56%]  23.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  122 of  448 MB written (fifo   1%) [buf  21%]  18.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroGenisoimage stderr:  28.28% done, estimate finish Sat Jul 25 10:28:08 2009
BraseroGenisoimage stderr:  30.46% done, estimate finish Sat Jul 25 10:28:02 2009
BraseroWodim stderr: Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: CDB:  2A 00 00 00 F7 A3 00 00 1F 00
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
BraseroWodim stderr: cmd finished after 101.401s timeout 200s
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: A write error occured.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: Please properly read the error message above.
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Track 01:  123 of  448 MB written (fifo   0%) [buf  21%]  24.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: write track data: error after 129832960 bytes
BraseroWodim stdout: Writing  time:  156.553s
BraseroWodim stdout: Average write speed  20.2x.
BraseroWodim stdout: Min drive buffer fill was 21%
BraseroWodim stdout: Fixating...
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Fixating time:    2.399s
BraseroWodim stderr: wodim: fifo had 2364 puts and 2046 gets.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: fifo was 16 times empty and 32 times full, min fill was 0%.
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: BURN-Free was 1 times used.
BraseroWodim stderr: HUP
BraseroWodim stdout: HUP
BraseroWodim process finished with status 254
BraseroWodim called brasero_job_error
BraseroWodim finished with an error
BraseroWodim asked to stop because of an error
	error		= 0
	message	= "no message"
BraseroGenisoimage stopping
BraseroGenisoimage got killed
BraseroGenisoimage disconnecting BraseroGenisoimage from BraseroChecksumImage
BraseroChecksumImage stopping
BraseroChecksumImage disconnecting BraseroChecksumImage from BraseroWodim
BraseroChecksumImage closing connection for BraseroChecksumImage
BraseroWodim stopping
BraseroWodim got killed
BraseroWodim closing connection for BraseroWodim
Session error : unknown (brasero_burn_record burn.c:2602)


Please Help!

---

### Post by ptn107 on 2009-07-25
I see towards the end it says there is a 'medium error', and then presents a more formal 'write error'.  Check the type of blank disks you're using in this case.  Maybe they're crap?  Have you used these particular brands of medium before successfully?

Try running it again from the command line with the command:
```
brasero --brasero-media-debug --debug &> brasero-debug.txt
```
to reproduce the bug, and submit that 'brasero-debug.txt' file with a bug report on launchpad[1].

[1][https://launchpad.net/ubuntu/+source/brasero]("https://launchpad.net/ubuntu/+source/brasero")

---

### Post by interestinfellow on 2009-07-25
No, I haven't used them before, they are Phillips CDR 700mb 52x.  Even with the cheap discs on this same computer with that other o$, I didn't have problems.  I'll run that script and see what I get.

On another note, I am running a pri and slave on the same ide channel.  A 60gb (boot, formatted and partitioned by ubuntu) and my 120gb (files, a dynamic ntfs drive formatted by windows).  I didn't know if that had anything to do with it or not.

Thanks!

---

### Post by interestinfellow on 2009-11-03
It turned out to be a bad drive....

---

### Post by inkyfingers on 2009-11-22
Looks like you were using Hitachi-LG GCC-4481B which I was thinking of buying.
There were firmware upgrades for this drive, but they needed an installation workaround in Windows - if they are installed in windows the drive may work in Linux?

---

