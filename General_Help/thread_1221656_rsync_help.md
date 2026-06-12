---
title: "rsync help"
date: 2009-07-24
forum: General Help
---

### Post by krisrae675 on 2009-07-24
can anyone explain this command to me
-f :_.rsync-filter --delete-after

---

### Post by nikhilk on 2009-07-24
> **krisrae675 said:**
> can anyone explain this command to me
-f :_.rsync-filter --delete-after

From rsync man page:

--delete-after
              Request that the file-deletions on the receiving side be done after the transfer  has  completed.   This  is useful  if you are sending new per-directory merge files as a part of the transfer and you want their exclusions to take effect for the delete phase of the current transfer.  See --delete (which is implied) for more details on file-deletion.

The -f option is specifying a file to read filtering rules. I strongly suggest you to consult the "FILTER RULES" section in rsync man page for details.

---

### Post by krisrae675 on 2009-07-24
hi thanx for that can anyone help further

you mentioned taking a look at the rsync file filter rules.
I have listed these below to see if you can help any further on what changes if any we should make to these.
At present in the folder it is bringing in is selfile, download, obexfile.log, obexscan.log
At moment it is only bringing in the selfile and download and not the other 2 and its those 2 we need as well.
- /download/**/.lock*
- /download/**/.log*
+ /download
+ /download/**
+ /selfile
+ /selfile/**
+ .rsync-filter
: .rsync-filter
- *

any help would be most appreciated
again thx for your time
chris

---

### Post by XCan on 2009-07-24
Are you sure you need to specify any advanced filters? Which paths exactly are you trying to backup? This would help a lot if you could specify from where and to where you want to backup.

---

### Post by krisrae675 on 2009-07-24
Thx for your reply

The pathway is var/opt/ccobex

within this folder is
selfile
download
obexfile.log
obexscan.log
.rsyncfilter

At present the rsync command brings the selfile  and download only and does not replace the obexfile and obexscan
we want it to bring these in also and replace them on the client also but for some reason is not and just wondered if our filter was wrong

---

