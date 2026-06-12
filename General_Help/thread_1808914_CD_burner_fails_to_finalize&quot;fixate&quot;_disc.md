---
title: "CD burner fails to finalize/&quot;fixate&quot; disc"
date: 2011-07-20
forum: General Help
---

### Post by jswhite on 2011-07-20
Trying to burn a copy of Natty so I can do a reinstall on my wife's computer. The burning process seems to go just fine using both Gnomebaker and Brasero. But, when it gets to the finalization stage, I get an error and it just fails. Afterwards, I'm left with a disc that doesn't appear on my list of media when I insert it. Manually doing "sudo mount /dev/cdrom /mnt/cdrom/" will actually mount the disc, and I can see that all the files from the .iso are on the disc...but it's not showing up and I can't finalize it.

Relevant output from brasero-session.log:

```

BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn Async SYNCHRONIZE CACHE succeeded after 5.1 seconds
BraseroLibburn Closing
BraseroLibburn called brasero_job_set_dangerous
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn Closing session
BraseroLibburn Asynchronous SCSI error on CLOSE TRACK SESSION: [5 72 03] Session fixation error, incomplete track in session
BraseroLibburn Writing
BraseroLibburn Async CLOSE TRACK SESSION failed after 1.4 seconds
BraseroLibburn Writing
BraseroLibburn Writing
BraseroLibburn SCSI error condition on command 43h READ TOC/PMA/ATIP: [5 24 00] Invalid field in cdb
BraseroLibburn Something went wrong
BraseroLibburn called brasero_job_error
BraseroLibburn finished with an error
BraseroLibburn asked to stop because of an error
	error		= 15
	message	= "An error occurred while writing to disc"
BraseroLibburn stopping
Session error : An error occurred while writing to disc (brasero_burn_record brasero-burn.c:2862)

```

I'm hoping someone can tell me this is a quickie software fix and my burner isn't fried somehow. I've burned lots of CDs before and never had a problem.

---

### Post by amias on 2011-10-10
i had this problem , it seems the cd discs are not being fixated properly . i just did the fixation manually with following command.

cdrecord -fix -dev=/dev/dvdrw

fwiw, i'm using a dell vostro 1710 with the following drive.

Vendor_info    : 'TEAC    '
Identification : 'DVD+-RW DVW28SLC'
Revision       : 'A.06'

---

### Post by johnaaronrose on 2012-03-23
I'm trying to burn a CD from the iso for Ubuntu 10.04.4. 

I've tried cdrecord -fix -dev=/dev/dvdrw, cdrecord -fix -dev=/dev/cdrw & cdrecord -fix -dev=/dev/cdrom. They all give 'Error trying to open /dev/cdrom exclusively (Device or resource busy)... retrying in 1 second.' (or similar) repeatedly. Any ideas?

PS I looked on Launchpad bugs & there's a 2010 bug about brasero & wodim: if I understand it correctly, the problem is with wodim.

---

