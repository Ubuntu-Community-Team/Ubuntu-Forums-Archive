---
title: "K3B/Brasero Burning Issues"
date: 2011-05-20
forum: General Help
---

### Post by Tumpster on 2011-05-20
Trying to burn a DVD full of media and I keep getting errors on both above programs. Here is the error oupout I get from Brasero:
```
Checking session consistency (brasero_burn_check_session_consistency brasero-burn.c:1744)
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_set_output_size_for_current_track
BraseroBurnURI stopping
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_session_output_size
BraseroBurnURI output set (IMAGE) image = /tmp/brasero_tmp_YHKKVV.bin toc = none
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
BraseroLocalTrack output set (IMAGE) image = /tmp/brasero_tmp_BFKKVV.bin toc = none
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
BraseroChecksumImage output set (IMAGE) image = /tmp/brasero_tmp_C7JKVV.bin toc = none
BraseroChecksumImage called brasero_job_get_session_output_size
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_input_type
BraseroChecksumImage called brasero_job_set_current_action
BraseroChecksumImage called brasero_job_get_fd_in
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage Starting checksuming file /home/craig/Desktop/brasero.iso (size = 4082948096)
BraseroChecksumImage called brasero_job_get_fd_out
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage Setting new checksum (type = 2) f81d595944d40733d53679fe1be98424 ((null) before)
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
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn burn_drive_is_enumerable_adr( /dev/sr0 ) is true
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn Async START UNIT succeeded after 0.1 seconds
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn mmc_set_streaming: end_lba=2295103 ,  r=9168 ,  w=22160
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn Allocating buffer via mmap()
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn dvd/bd Profile= 1Bh , obs= 32768 , obs_pad= 1
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn DVD+R pre-track 01 : get_nwa(0), ret= 1 , d->nwa= 0
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn DVD pre-track 01 : demand=4082948096, cap=4700372992

BraseroLibburn called brasero_job_set_current_action

BraseroLibburn SCSI error condition on command 2Ah WRITE(10): [3 0C 00] Write error
BraseroLibburn Something went wrong
BraseroLibburn called brasero_job_error
BraseroLibburn finished with an error
BraseroLibburn asked to stop because of an error
	error		= 15
	message	= "An error occurred while writing to disc"
BraseroLibburn stopping
Session error : An error occurred while writing to disc (brasero_burn_record brasero-burn.c:2862)
```

Anyone know what I can do to fix this and get things up and running again? Would like to be burning to DVD's again. Running 11.04 and also had the same problem with 10.04. Thanks everyone!

---

### Post by linuxinstalledfromhdd on 2011-05-20
Try Xfburn

sudo apt-get install xfburn

---

### Post by Tumpster on 2011-05-20
> **linuxinstalledfromhdd said:**
> Try Xfburn

sudo apt-get install xfburn

Did so,

"Failure: Cannot reserve track of 4082958336 bytes"

Any ideas?

---

### Post by linuxinstalledfromhdd on 2011-05-20
Take your live disc and boot from it or your live USB stick of Linux.

Try to burn something with it. 

Check hardware first, then assume it's software.

---

### Post by linuxinstalledfromhdd on 2011-05-20
Download Ubuntu.

Create a startup usb.. Something that has 2GB.

System >> Admin >> Startup Creator

Boot from that USB stick.

Try to burn something with it.

---

### Post by Tumpster on 2011-05-20
> **linuxinstalledfromhdd said:**
> Download Ubuntu.

Create a startup usb.. Something that has 2GB.

System >> Admin >> Startup Creator

Boot from that USB stick.

Try to burn something with it.

Did that still have same issues, yet I always have no trouble burning a CD. What could this be?

---

### Post by linuxinstalledfromhdd on 2011-05-20
My feeling is this could be hardware.  Maybe the Ubuntu iso you are burning is smaller than the other iso file that is failing on you? And the writer is failing after a certain size write.

---

### Post by 4Orbs on 2011-05-20
Possibly your /tmp directory doesn't have enough empty space remaining. You can test this by going into k3b configuration and pointing the temporary folder somewhere there is more than 5gb of unused space.

---

### Post by Tumpster on 2011-05-22
> **4Orbs said:**
> Possibly your /tmp directory doesn't have enough empty space remaining. You can test this by going into k3b configuration and pointing the temporary folder somewhere there is more than 5gb of unused space.

Did as you said, but no luck. Does play DVD's fine, burns CD's fine, but just not DVD's for some reason.

---

### Post by linuxinstalledfromhdd on 2011-05-22
Interesting. What make and model DVD writer is it? Internal, External? Laptop, desktop. etc.  And how old is it?

---

### Post by Tumpster on 2011-05-22
> **linuxinstalledfromhdd said:**
> Interesting. What make and model DVD writer is it? Internal, External? Laptop, desktop. etc.  And how old is it?

[http://www.newegg.com/Product/Product.aspx?Item=N82E16827136177](http://www.newegg.com/Product/Product.aspx?Item=N82E16827136177)

---

