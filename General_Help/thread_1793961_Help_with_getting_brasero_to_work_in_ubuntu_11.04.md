---
title: "Help with getting brasero to work in ubuntu 11.04"
date: 2011-06-30
forum: General Help
---

### Post by Ghostnik11 on 2011-06-30
Hi for the pass day i have been trying to get brasero to work to burn avi files to a dvd or to make a data dvd.  Yet for some reason when I try to create this through brasero i get this error: "SCSI error on write(0,16): [3 0C 00] Write error." 

I tried gnomebaker and xburn and both had same problem could not burn files to dvd.  here is a log of brasero session log:> Checking session consistency (brasero_burn_check_session_consistency brasero-burn.c:1744)
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
BraseroChecksumFiles Adding graft for checksum file /.checksum.md5 file:///tmp/brasero_tmp_8VANXV.md5
BraseroChecksumFiles called brasero_job_add_track
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles Finished track successfully
BraseroChecksumFiles stopping
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_flags
BraseroLibburn called brasero_job_get_action
BraseroLibburn creating input
BraseroLibburn called brasero_job_get_action
BraseroLibburn unsupported operation
BraseroLibburn deactivating
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage creating input
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_fd_in
BraseroChecksumImage deactivating
BraseroLibisofs called brasero_job_get_action
BraseroLibisofs called brasero_job_get_action
BraseroLibisofs called brasero_job_set_current_action
BraseroLibisofs creating volume
BraseroLibisofs called brasero_job_get_data_label
BraseroLibisofs called brasero_job_get_flags
BraseroLibisofs called brasero_job_get_current_track
BraseroLibisofs Adding graft disc path = /.checksum.md5, URI = file:///tmp/brasero_tmp_8VANXV.md5
BraseroLibisofs Found parent
BraseroLibisofs Adding graft disc path = /P90X.DISC.04.Yoga.X.avi, URI = file:///media/Elements/Movies/P90X/Videos/P90X.DISC.04.Yoga.X.avi
BraseroLibisofs Found parent
BraseroLibisofs Adding graft disc path = /P90X.DISC.06.Kenpo.X.avi, URI = file:///media/Elements/Movies/P90X/Videos/P90X.DISC.06.Kenpo.X.avi
BraseroLibisofs Found parent
BraseroLibisofs Adding graft disc path = /P90X.DISC.01.Chest.Back.avi, URI = file:///media/Elements/Movies/P90X/Videos/P90X.DISC.01.Chest.Back.avi
BraseroLibisofs Found parent
BraseroLibisofs Adding graft disc path = /P90X.DISC.02.Plyometrics.avi, URI = file:///media/Elements/Movies/P90X/Videos/P90X.DISC.02.Plyometrics.avi
BraseroLibisofs Found parent
BraseroLibisofs Adding graft disc path = /P90X.DISC.05.Legs.And.Back.avi, URI = file:///media/Elements/Movies/P90X/Videos/P90X.DISC.05.Legs.And.Back.avi
BraseroLibisofs Found parent
BraseroLibisofs Adding graft disc path = /P90X.DISC.03.Shoulders.Arms.avi, URI = file:///media/Elements/Movies/P90X/Videos/P90X.DISC.03.Shoulders.Arms.avi
BraseroLibisofs Found parent
BraseroLibisofs Adding graft disc path = /P90X.DISC.00.How.To.Bring.It.avi, URI = file:///media/Elements/Movies/P90X/Videos/P90X.DISC.00.How.To.Bring.It.avi
BraseroLibisofs Found parent
BraseroLibisofs called brasero_job_set_output_size_for_current_track
BraseroLibisofs called brasero_job_get_action
BraseroLibisofs Finished track successfully
BraseroLibisofs stopping
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_flags
BraseroLibburn called brasero_job_get_action
BraseroLibburn creating input
BraseroLibburn called brasero_job_get_action
BraseroLibburn called brasero_job_get_device
BraseroLibburn Drive (/dev/sr0) init result = 1
BraseroLibburn called brasero_job_get_flags
BraseroLibburn called brasero_job_get_media
BraseroLibburn called brasero_job_get_fd_in
BraseroLibburn called brasero_job_get_fd_in
BraseroLibburn called brasero_job_get_input_type
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn Setting multi 0
BraseroLibburn Setting burnproof 1
BraseroLibburn Setting dummy 0
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage linked to BraseroLibburn
BraseroChecksumImage creating input
BraseroChecksumImage called brasero_job_get_action
BraseroLibisofs called brasero_job_get_action
BraseroLibisofs linked to BraseroChecksumImage
BraseroLibisofs called brasero_job_get_action
BraseroLibisofs Entering thread
BraseroLibisofs called brasero_job_get_fd_out
BraseroLibisofs called brasero_job_set_nonblocking
BraseroLibisofs called brasero_job_get_fd_in
BraseroLibisofs called brasero_job_get_fd_out
BraseroLibisofs called brasero_job_set_current_action
BraseroLibisofs called brasero_job_get_fd_out
BraseroLibisofs Writing to pipe
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_input_type
BraseroChecksumImage called brasero_job_set_current_action
BraseroChecksumImage called brasero_job_get_fd_in
BraseroChecksumImage Starting checksum generation live (size = 0)
BraseroChecksumImage called brasero_job_set_nonblocking
BraseroChecksumImage called brasero_job_get_fd_in
BraseroChecksumImage called brasero_job_get_fd_out
BraseroChecksumImage called brasero_job_get_fd_in
BraseroChecksumImage called brasero_job_get_fd_out
BraseroLibburn burn_drive_convert_fs_adr( /dev/sr0 )
BraseroLibburn Writing
BraseroLibburn called brasero_job_set_dangerous
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn burn_drive_is_enumerable_adr( /dev/sr0 ) is true
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn Async START UNIT succeeded after 0.1 seconds
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn mmc_set_streaming: end_lba=2298495 ,  r=4584 ,  w=11080
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn Allocating buffer via mmap()
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn dvd/bd Profile= 11h , obs= 32768 , obs_pad= 1
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn DVD pre-track 01 : get_nwa(0), ret= 1 , d->nwa= 0
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn DVD pre-track 01 : demand=4581881856, cap=4706074624

BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI error condition on command 2Ah WRITE(10): [3 0C 00] Write error
BraseroLibburn Closing
BraseroLibburn called brasero_job_set_dangerous
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn Libburn reported an error SCSI error on write(0,16): [3 0C 00] Write error
BraseroLibburn called brasero_job_error
BraseroLibburn finished with an error
BraseroLibburn asked to stop because of an error
	error		= 1
	message	= "SCSI error on write(0,16): [3 0C 00] Write error"
BraseroLibisofs stopping
BraseroLibisofs Getting out thread
BraseroLibisofs disconnecting BraseroLibisofs from BraseroChecksumImage
BraseroChecksumImage stopping
BraseroChecksumImage disconnecting BraseroChecksumImage from BraseroLibburn
BraseroChecksumImage closing connection for BraseroChecksumImage
BraseroLibburn stopping
BraseroLibburn closing connection for BraseroLibburn
Session error : SCSI error on write(0,16): [3 0C 00] Write error (brasero_burn_record brasero-burn.c:2862)

Was told in brasero-mailing list that I should use cdrkit/cdrtools instead of libburn and that I could priorities this or change which one is used first between libburn and cdrkit/cdrtools through gconf-editor.  The problem is when i load gconf-editor there is no brasero in apps folder or shcemas/apps folder.  Here is print screen pics of my dilemma in gconf-editor: [IMG]http://imagebin.org/160733[/IMG] and [IMG]http://imagebin.org/160735[/IMG]

Any help would be appreciated as this problem of brasero not working has been plaguing me.  Thanks in advance.

---

### Post by Ghostnik11 on 2011-06-30
bump

---

### Post by wildmanne39 on 2011-07-01
> **Ghostnik11 said:**
> bump
Hi, have you installed the restricted packages already so you can burn cds and dvds? If not go here and follow the directions carefully and go down the whole page, and do what it says for the version of ubuntu you are using.
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by toufiqueimam on 2011-07-01
I got same problem. Then I installed k3b. K3b is working fine. Even better than brasero.

---

### Post by sandman887 on 2011-07-01
Originally, Brasero worked great for me, then after a reinstall, it didn't work as good. I had faulty burning sessions, and other stuff. After getting fed up with it, I decided to go back to K3B (which I had originally used anyway), and it's worked great for me ever since. I know that's not a resolution, but back then, I didn't know enough about Linux to be able to solve many problems, and I didn't want to waste any more time on it.

I know this isn't really an answer to your problem, but I just thought I would share this with you.

---

