---
title: "Can't burn a data disk."
date: 2011-01-14
forum: General Help
---

### Post by Saeger on 2011-01-14
I can't burn a data disk through Ubuntu.  I tried using the built-in disk creator, It had some kind of error saying the disk cannot be mounted.  So I used Brasero instead and I got essentially the same error.  When I tried to open both CD's the files appeared to be present but were all corrupt.  Braso works fine for burning music CD's but I can't get it to work for data.  here is the error log from Brasero:

BraseroReadom stderr: Time total: 131.474sec
BraseroReadom stderr: Read 666760.00 kB at 5071.4 kB/sec.
BraseroReadom stderr: HUP
BraseroReadom process finished with status 0
BraseroReadom Finished track successfully
BraseroReadom called brasero_job_get_done_tracks
BraseroReadom called brasero_job_get_fd_out
BraseroReadom disconnecting BraseroReadom from BraseroChecksumImage
BraseroReadom deactivating
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage Setting new checksum (type = 2) 43221235cd19844c58f58223fecac32d (3b9f3fac2b3a9a9597f7c069cee8c13e before)
BraseroChecksumImage called brasero_job_error
BraseroChecksumImage finished with an error
BraseroChecksumImage asked to stop because of an error
    error        = 27
    message    = "Some files may be corrupted on the disc"
BraseroChecksumImage stopping
BraseroChecksumImage closing connection for BraseroChecksumImage
Session error : Some files may be corrupted on the disc (brasero_burn_record brasero-burn.c:2862)

---

### Post by Jahid65 on 2011-01-14
Use K3b or Nero-Linux(There is a deb package on their site). Brasero is not so very good.

---

### Post by Jahid65 on 2011-01-14
removed

---

### Post by Jahid65 on 2011-01-14
removed

---

