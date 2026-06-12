---
title: "Saving files to CD problem, help"
date: 2011-01-15
forum: General Help
---

### Post by Camilia on 2011-01-15
I know the basics of saving files on CD/DVD. I dragged file to a CD-RW, which has 1 song on it. Got message the destination is read-only. That doesn't make sense for CD-RW is a rewritable disk. Tried with an empty DVD-R and got this:
BraseroBurnURI Added file /media/FlashDisc/Forms.ods at /Forms.ods

BraseroBurnURI called brasero_job_add_track

BraseroBurnURI called brasero_job_get_action

BraseroBurnURI Finished track successfully

BraseroBurnURI stopping

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

BraseroChecksumFiles Adding graft for checksum file /.checksum.md5 file:///tmp/brasero_tmp_HEEHPV.md5

BraseroChecksumFiles called brasero_job_add_track

BraseroChecksumFiles called brasero_job_get_action

BraseroChecksumFiles Finished track successfully

BraseroChecksumFiles stopping

BraseroGrowisofs called brasero_job_get_action

BraseroGrowisofs getting varg

BraseroGrowisofs called brasero_job_get_action

BraseroGrowisofs called brasero_job_get_current_track

BraseroGrowisofs called brasero_job_get_flags

BraseroGrowisofs called brasero_job_get_speed

BraseroGrowisofs called brasero_job_get_device

BraseroGrowisofs called brasero_job_get_action

BraseroGrowisofs called brasero_job_get_session_output_size

BraseroGrowisofs called brasero_job_get_current_track

BraseroGrowisofs called brasero_job_get_fd_in

BraseroGrowisofs Using genisoimage

BraseroGrowisofs called brasero_job_get_current_track

BraseroGrowisofs called brasero_job_get_tmp_dir

BraseroGrowisofs called brasero_job_get_action

BraseroGrowisofs called brasero_job_set_current_action

BraseroGrowisofs got varg:

	growisofs

	-use-the-force-luke=notray

	-use-the-force-luke=4gms

	-dvd-compat

	-speed=4

	-use-the-force-luke=tty

	-Z

	/dev/sr0

	-dry-run

	-r

	-J

	-input-charset

	utf8

	-graft-points

	-path-list

	/tmp/brasero_tmp_51QTPV

	-exclude-list

	/tmp/brasero_tmp_40QTPV

	-print-size

BraseroGrowisofs Launching command

BraseroGrowisofs called brasero_job_get_fd_out

BraseroGrowisofs stdout: Executing 'genisoimage -r -J -input-charset utf8 -graft-points -path-list /tmp/brasero_tmp_51QTPV -exclude-list /tmp/brasero_tmp_40QTPV -print-size | builtin_dd of=/dev/sr0 obs=32k seek=0'

BraseroGrowisofs called brasero_job_set_dangerous

BraseroGrowisofs stderr: Total extents scheduled to be written = 288

BraseroGrowisofs called brasero_job_get_action

BraseroGrowisofs called brasero_job_set_output_size_for_current_track

BraseroGrowisofs Finished successfully session

BraseroGrowisofs stopping

BraseroGrowisofs got killed

BraseroGrowisofs called brasero_job_get_action

BraseroGrowisofs getting varg

BraseroGrowisofs called brasero_job_get_action

BraseroGrowisofs called brasero_job_get_flags

BraseroGrowisofs called brasero_job_get_speed

BraseroGrowisofs called brasero_job_get_device

BraseroGrowisofs called brasero_job_get_action

BraseroGrowisofs called brasero_job_get_session_output_size

BraseroGrowisofs called brasero_job_get_current_track

BraseroGrowisofs called brasero_job_get_fd_in

BraseroGrowisofs Using genisoimage

BraseroGrowisofs called brasero_job_get_current_track

BraseroGrowisofs called brasero_job_get_tmp_dir

BraseroGrowisofs called brasero_job_get_action

BraseroGrowisofs called brasero_job_get_data_label

BraseroGrowisofs called brasero_job_set_current_action

BraseroGrowisofs got varg:

	growisofs

	-use-the-force-luke=notray

	-use-the-force-luke=4gms

	-dvd-compat

	-speed=4

	-use-the-force-luke=tracksize:288

	-use-the-force-luke=tty

	-Z

	/dev/sr0

	-r

	-J

	-input-charset

	utf8

	-graft-points

	-path-list

	/tmp/brasero_tmp_NLBSPV

	-exclude-list

	/tmp/brasero_tmp_MIBSPV

	-A

	Brasero-2.28.2

	-sysid

	LINUX

	-v

BraseroGrowisofs Launching command

BraseroGrowisofs called brasero_job_get_fd_out

BraseroGrowisofs stderr: genisoimage 1.1.9 (Linux)

BraseroGrowisofs stdout: Executing 'genisoimage -r -J -input-charset utf8 -graft-points -path-list /tmp/brasero_tmp_NLBSPV -exclude-list /tmp/brasero_tmp_MIBSPV -A Brasero-2.28.2 -sysid LINUX -v | builtin_dd of=/dev/sr0 obs=32k seek=0'

BraseroGrowisofs called brasero_job_set_dangerous

BraseroGrowisofs stderr: Writing:   Initial Padblock                        Start Block 0

BraseroGrowisofs stderr: Done with: Initial Padblock                        Block(s)    16

BraseroGrowisofs stderr: Writing:   Primary Volume Descriptor               Start Block 16

BraseroGrowisofs stderr: Done with: Primary Volume Descriptor               Block(s)    1

BraseroGrowisofs stderr: Writing:   Joliet Volume Descriptor                Start Block 17

BraseroGrowisofs stderr: Done with: Joliet Volume Descriptor                Block(s)    1

BraseroGrowisofs stderr: Writing:   End Volume Descriptor                   Start Block 18

BraseroGrowisofs stderr: Done with: End Volume Descriptor                   Block(s)    1

BraseroGrowisofs stderr: Writing:   Version block                           Start Block 19

BraseroGrowisofs stderr: Done with: Version block                           Block(s)    1

BraseroGrowisofs stderr: Writing:   Path table                              Start Block 20

BraseroGrowisofs stderr: Done with: Path table                              Block(s)    4

BraseroGrowisofs stderr: Writing:   Joliet path table                       Start Block 24

BraseroGrowisofs stderr: Done with: Joliet path table                       Block(s)    4

BraseroGrowisofs stderr: Writing:   Directory tree                          Start Block 28

BraseroGrowisofs stderr: Done with: Directory tree                          Block(s)    1

BraseroGrowisofs stderr: Writing:   Joliet directory tree                   Start Block 29

BraseroGrowisofs stderr: Done with: Joliet directory tree                   Block(s)    1

BraseroGrowisofs stderr: Writing:   Directory tree cleanup                  Start Block 30

BraseroGrowisofs stderr: Done with: Directory tree cleanup                  Block(s)    0

BraseroGrowisofs stderr: Writing:   Extension record                        Start Block 30

BraseroGrowisofs stderr: Done with: Extension record                        Block(s)    1

BraseroGrowisofs stderr: Writing:   The File(s)                             Start Block 31

BraseroGrowisofs stderr: Total translation table size: 0

BraseroGrowisofs stderr: Total rockridge attributes bytes: 918

BraseroGrowisofs stderr: Total directory bytes: 0

BraseroGrowisofs stderr: Path table size(bytes): 10

BraseroGrowisofs stderr: Done with: The File(s)                             Block(s)    107

BraseroGrowisofs stderr: Writing:   Ending Padblock                         Start Block 138

BraseroGrowisofs stderr: Done with: Ending Padblock                         Block(s)    150

BraseroGrowisofs stderr: Max brk space used 0

BraseroGrowisofs stderr: 288 extents written (0 MB)

BraseroGrowisofs stderr: :-[ PERFORM OPC failed with SK=2h/CANNOT WRITE MEDIUM - INCOMPATIBLE FORMAT]: Wrong medium type

BraseroGrowisofs stderr: /dev/sr0: "Current Write Speed" is 4.1x1352KBps.

BraseroGrowisofs stderr: :-[ WRITE@LBA=0h failed with SK=2h/CANNOT WRITE MEDIUM - INCOMPATIBLE FORMAT]: Wrong medium type

BraseroGrowisofs stderr: :-( media is not formatted or unsupported.

BraseroGrowisofs stdout: HUP

BraseroGrowisofs stderr: :-( write failed: Wrong medium type

BraseroGrowisofs stderr: HUP

BraseroGrowisofs process finished with status 124

BraseroGrowisofs called brasero_job_error

BraseroGrowisofs finished with an error

BraseroGrowisofs asked to stop because of an error

	error		= 0

	message	= "no message"


BraseroGrowisofs stopping

BraseroGrowisofs got killed

Session error : unknown (brasero_burn_record brasero-burn.c:2811)

---

