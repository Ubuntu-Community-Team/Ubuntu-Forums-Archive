---
title: "Problem with printing via cups"
date: 2006-06-18
forum: General Help
---

### Post by dallingham on 2006-06-18
I am trying to connect to a network drive on another machine. Both machines are running 6.06. The printer is a LaserJet 4L, and works properly on the host machine. If I enable "Detect Lan Printers" in the printer settings, the printer shows up.

Any attempt to print to the printer fails. The job never prints, and the printer indicates Ready, with 1 job.

The cupsd/error_log is filling up with the following messages:
E [18/Jun/2006:19:20:16 -0600] cupsdAuthorize: Local authentication certificate not found!
E [18/Jun/2006:19:20:16 -0600] cupsdAuthorize: Local authentication certificate not found!
E [18/Jun/2006:19:20:16 -0600] cupsdAuthorize: Local authentication certificate not found!
E [18/Jun/2006:19:20:18 -0600] cupsdAuthorize: Local authentication certificate not found!
E [18/Jun/2006:19:20:21 -0600] cupsdAuthorize: Local authentication certificate not found!
E [18/Jun/2006:19:20:21 -0600] cupsdAuthorize: Local authentication certificate not found!
E [18/Jun/2006:19:20:21 -0600] cupsdAuthorize: Local authentication certificate not found!
E [18/Jun/2006:19:20:21 -0600] cupsdAuthorize: Local authentication certificate not found!

Any suggestions?

---

