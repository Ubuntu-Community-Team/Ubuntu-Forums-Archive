---
title: "Brasero Won't Burn to a CD-R"
date: 2011-07-27
forum: General Help
---

### Post by Incarnadine on 2011-07-27
I am trying to burn a image file to a CD-R, but it fails to start the burn process. Below is the error log. Thanks for the help :popcorn:

Checking session consistency (brasero_burn_check_session_consistency brasero-burn.c:1744)
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_set_output_size_for_current_track
BraseroBurnURI stopping
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_session_output_size
BraseroBurnURI output set (IMAGE) image = /tmp/brasero_tmp_MSPPZV.bin toc = /tmp/brasero_tmp_MSPPZV.toc
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
BraseroLocalTrack output set (IMAGE) image = /tmp/brasero_tmp_PDSPZV.bin toc = /tmp/brasero_tmp_PDSPZV.toc
BraseroLocalTrack called brasero_job_get_session_output_size
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_current_track
BraseroLocalTrack no remote URIs
BraseroLocalTrack stopping
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao getting varg
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_current_track
BraseroCdrdao got varg:
BraseroCdrdao deactivating
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao getting varg
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_input_type
BraseroCdrdao called brasero_job_get_current_track
BraseroCdrdao called brasero_job_get_bus_target_lun
BraseroCdrdao called brasero_job_get_flags
BraseroCdrdao called brasero_job_get_flags
BraseroCdrdao called brasero_job_get_speed
BraseroCdrdao called brasero_job_set_use_average_rate
BraseroCdrdao called brasero_job_set_current_action
BraseroCdrdao got varg:
	cdrdao
	write
	--device
	/dev/sr0
	-n
	-v
	2
	--speed
	4
	/media/2260367060364AB5/Disc Images/Software/Rosetta Stone: English (American) Level 1.toc
BraseroCdrdao Launching command
BraseroCdrdao called brasero_job_get_fd_in
BraseroCdrdao called brasero_job_get_fd_out
BraseroCdrdao stderr: WARNING: Environment variable 'HOME' not defined- cannot read .cdrdao.
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_current_track
BraseroCdrdao stderr: Cdrdao version 1.2.3 - (C) Andreas Mueller <andreas@daneb.de>
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_current_track
BraseroCdrdao stderr: ERROR: Track 1: Cannot open data file "/media/2260367060364AB5/Disc Images/Rosetta Stone: English (American) Level 1.toc.bin": No such file or directory
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_current_track
BraseroCdrdao stderr: ERROR: The toc check function detected at least one warning.
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_current_track
BraseroCdrdao stderr: ERROR: If you record this toc the resulting CD might be unusable
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_current_track
BraseroCdrdao stderr: ERROR: or the recording process might abort with error.
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_current_track
BraseroCdrdao stderr: ERROR: Use option --force to ignore the warnings.
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_current_track
BraseroCdrdao stderr: ERROR: Toc file "/media/2260367060364AB5/Disc Images/Software/Rosetta Stone: English (American) Level 1.toc" is inconsistent.
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_current_track
BraseroCdrdao stderr: HUP
BraseroCdrdao process finished with status 1
BraseroCdrdao called brasero_job_error
BraseroCdrdao finished with an error
BraseroCdrdao asked to stop because of an error
	error		= 0
	message	= "no message"
BraseroCdrdao stopping
Session error : unknown (brasero_burn_record brasero-burn.c:2865)

---

### Post by haqking on 2011-07-27
> **Incarnadine said:**
> I am trying to burn a image file to a CD-R, but it fails to start the burn process. Below is the error log. Thanks for the help :popcorn:

Checking session consistency (brasero_burn_check_session_consistency brasero-burn.c:1744)
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_set_output_size_for_current_track
BraseroBurnURI stopping
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_session_output_size
BraseroBurnURI output set (IMAGE) image = /tmp/brasero_tmp_MSPPZV.bin toc = /tmp/brasero_tmp_MSPPZV.toc
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
BraseroLocalTrack output set (IMAGE) image = /tmp/brasero_tmp_PDSPZV.bin toc = /tmp/brasero_tmp_PDSPZV.toc
BraseroLocalTrack called brasero_job_get_session_output_size
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_current_track
BraseroLocalTrack no remote URIs
BraseroLocalTrack stopping
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao getting varg
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_current_track
BraseroCdrdao got varg:
BraseroCdrdao deactivating
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao getting varg
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_input_type
BraseroCdrdao called brasero_job_get_current_track
BraseroCdrdao called brasero_job_get_bus_target_lun
BraseroCdrdao called brasero_job_get_flags
BraseroCdrdao called brasero_job_get_flags
BraseroCdrdao called brasero_job_get_speed
BraseroCdrdao called brasero_job_set_use_average_rate
BraseroCdrdao called brasero_job_set_current_action
BraseroCdrdao got varg:
    cdrdao
    write
    --device
    /dev/sr0
    -n
    -v
    2
    --speed
    4
    /media/2260367060364AB5/Disc Images/Software/Rosetta Stone: English (American) Level 1.toc
BraseroCdrdao Launching command
BraseroCdrdao called brasero_job_get_fd_in
BraseroCdrdao called brasero_job_get_fd_out
BraseroCdrdao stderr: WARNING: Environment variable 'HOME' not defined- cannot read .cdrdao.
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_current_track
BraseroCdrdao stderr: Cdrdao version 1.2.3 - (C) Andreas Mueller <andreas@daneb.de>
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_current_track
BraseroCdrdao stderr: ERROR: Track 1: Cannot open data file "/media/2260367060364AB5/Disc Images/Rosetta Stone: English (American) Level 1.toc.bin": No such file or directory
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_current_track
BraseroCdrdao stderr: ERROR: The toc check function detected at least one warning.
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_current_track
BraseroCdrdao stderr: ERROR: If you record this toc the resulting CD might be unusable
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_current_track
BraseroCdrdao stderr: ERROR: or the recording process might abort with error.
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_current_track
BraseroCdrdao stderr: ERROR: Use option --force to ignore the warnings.
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_current_track
BraseroCdrdao stderr: ERROR: Toc file "/media/2260367060364AB5/Disc Images/Software/Rosetta Stone: English (American) Level 1.toc" is inconsistent.
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_current_track
BraseroCdrdao stderr: HUP
BraseroCdrdao process finished with status 1
BraseroCdrdao called brasero_job_error
BraseroCdrdao finished with an error
BraseroCdrdao asked to stop because of an error
    error        = 0
    message    = "no message"
BraseroCdrdao stopping
Session error : unknown (brasero_burn_record brasero-burn.c:2865)

braseros is known to be problematic, try k3b

---

### Post by Incarnadine on 2012-07-23
> **haqking said:**
> braseros is known to be problematic, try k3b

Crap :(

---

