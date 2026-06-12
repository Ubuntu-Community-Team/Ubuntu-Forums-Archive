---
title: "freshclam won't run"
date: 2009-08-21
forum: General Help
---

### Post by mohnkern on 2009-08-21
I'm having problems with clamav .94 on an ubuntu 8.04 box.  I've installed clamav (and all the parts).  

When I run freshclam, I get the following error:

root@zambezi:/etc/init.d# freshclam
ClamAV update process started at Fri Aug 21 10:17:04 2009
WARNING: Your ClamAV installation is OUTDATED!
WARNING: Local version: 0.94.2 Recommended version: 0.95.2
DON'T PANIC! Read [http://www.clamav.net/support/faq](http://www.clamav.net/support/faq)
ERROR: getfile: Can't create new file /var/clamav/clamav-5491fb1d993386319cf566dfd54cf27d in /var/clamav
Hint: The database directory must be writable for UID 441 or GID 204
WARNING: Can't download main.cvd from db.us.clamav.net
root@zambezi:/etc/init.d#


there is a user clamav in /etc/passwd,  it's uid is 441.  There's a directory /var/clamav owned by uid 441.

I'm at a loss as to figure out why freshclam won't write to the directory.

---

### Post by XCan on 2009-08-21
I'm not familiar with the whole uid ownership thingy, but I'm quite certain that by default you need to run freshclam as root, i.e., sudo.

---

