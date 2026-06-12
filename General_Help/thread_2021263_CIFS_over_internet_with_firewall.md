---
title: "CIFS over internet with firewall?"
date: 2012-07-08
forum: General Help
---

### Post by yuanzhoulu on 2012-07-08
I need to share huge amounts of large files (figure 50-100 GB at a time, this is for HD video editing collaboration) across a college campus, and from one college campus to another. Server will be Linux. Clients could be Linux, Mac, or Windows. Both ends have gigabit drops and fantastic bandwidth to the outside. Data is not particularly sensitive so I'm not worried about eavesdropping, but I want to avoid my server being trashed by bots and whatnot that exploit known vulnerabilities.

Encryption via SSHFS or FTP-SSL makes it deadly slow (9-12 MB/s with arcfour, vs. 50-70 MB/s with SMB or plain old FTP).

Question is this:

Is it safe to use CIFS/SMB over the internet, but restricted to only certain subnets, assuming I trust all users on the destination subnet? Suppose say I trust everyone on A.B.*.* to not be hackers (but not necessarily all should have access, so I still need password protection). If I configure Samba to only let connection from A.B.*.*, would I be generally safe from security exploitation from the outside otherwise? (Let's forget about man-in-the-middle attacks for now, this is all wired ethernet within a few km and man-in-the-middle is an unlikely scenario.)

I only wish to use SMB over FTP since it's just snappier to work directly off of. Mounting an SMB share one can directly load files and work on it; using any kind of FTP mounting scheme has serious file system lags if you're doing video editing. SSHFS is slow, and NFSv4 is just impractically difficult to teach people to use, since it wants Kerberos and can't accept a simple password-based authentication scheme.

I really wish there were a better cross-platform file sharing solution that allowed for gigabit bandwidths AND security AND mountability on all 3 OSes :-/

Thanks!

---

