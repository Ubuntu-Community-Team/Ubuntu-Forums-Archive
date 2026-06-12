---
title: "Tryng to create a CD from a .ISO"
date: 2010-08-26
forum: General Help
---

### Post by Zirts on 2010-08-26
So I want to write a OS on a DVD-RW
I open Brasero choose the option wich takes the .ISO and makes it a bootable CD.

But when it's on the phase: starting writing, it gives me a error,

```

Checking session consistency (brasero_burn_check_session_consistency brasero-burn.c:1741)
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_set_output_size_for_current_track
BraseroBurnURI stopping
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_session_output_size
BraseroBurnURI output set (IMAGE) image = /tmp/brasero_tmp_Q2L3HV.bin toc = none
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
BraseroLocalTrack output set (IMAGE) image = /tmp/brasero_tmp_MNK3HV.bin toc = none
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
BraseroChecksumImage There is a checksum already 0
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs getting varg
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_current_track
BraseroGrowisofs got varg:
BraseroGrowisofs deactivating
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
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs got varg:
	growisofs
	-use-the-force-luke=notray
	-use-the-force-luke=4gms
	-speed=4
	-use-the-force-luke=tracksize:329477
	-use-the-force-luke=tty
	-Z
	/dev/sr0=/home/kaspar/Töölaud/os.iso
BraseroGrowisofs Launching command
BraseroGrowisofs called brasero_job_get_fd_out
BraseroGrowisofs called brasero_job_get_fd_in
BraseroGrowisofs called brasero_job_get_fd_out
BraseroGrowisofs stdout: Executing 'builtin_dd if=/home/kaspar/Töölaud/os.iso of=/dev/sr0 obs=32k seek=0'
BraseroGrowisofs called brasero_job_set_dangerous
BraseroGrowisofs stderr: /dev/sr0: pre-formatting blank DVD+RW...
BraseroGrowisofs stderr: /dev/sr0: "Current Write Speed" is 4.1x1352KBps.
BraseroGrowisofs stderr: :-[ WRITE@LBA=0h failed with SK=5h/CANNOT FORMAT MEDIUM - INCOMPATIBLE MEDIUM]: Wrong medium type
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
Session error : unknown (brasero_burn_record brasero-burn.c:2842)

```

---

### Post by Quackers on 2010-08-26
It appears to be saying that the dvd+rw disc type is not supported. Presumably by the drive. Would that be right?

---

### Post by HPD2 on 2010-08-26
```
BraseroGrowisofs stderr: :-( write failed: Wrong medium type
```Try a different type of CD or DVD. Like maybe a CD-R or DVD-R.

---

### Post by doktarZues on 2010-08-26
I had a terrible time using Brasero, I was getting various errors at different times (hard to duplicate).  I loaded gnomebaker and not only do I like the interface much better but I haven't had any errors or a single coaster.

---

### Post by Ginsu543 on 2010-08-26
Yup, you can always try other programs (that's the wonder of Linux!). But FWIW, I use Brasero all the time and I've never had an error (no coasters, LOL).

---

