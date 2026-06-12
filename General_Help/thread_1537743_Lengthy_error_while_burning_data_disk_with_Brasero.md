---
title: "Lengthy error while burning data disk with Brasero"
date: 2010-07-24
forum: General Help
---

### Post by unckybob on 2010-07-24
I'm having trouble burning a data disk. When I burn it ejects the DVD, then saves a log. Here's the last few lines of its contents: 

BraseroGenisoimage stderr: /usr/bin/genisoimage: Warning: Directory loop (/home/robert/Desktop/Mount_Directory/var/at/spool dev: 700 ino: 13323).
BraseroGenisoimage stderr: /usr/bin/genisoimage: Warning: Directory loop (/home/robert/Desktop/Mount_Directory/var/spool/postfix dev: 700 ino: 13200).
BraseroGenisoimage stderr: /usr/bin/genisoimage: Warning: Directory loop (/home/robert/Desktop/Mount_Directory/var/spool/postfix/pid dev: 700 ino: 13210).
BraseroGenisoimage stderr: /usr/bin/genisoimage: Warning: Directory loop (/home/robert/Desktop/Mount_Directory/var/spool/samba dev: 700 ino: 13247).
BraseroGenisoimage stderr: /usr/bin/genisoimage: No such file or directory. Non-existent or inaccessible: /home/robert/Desktop/Mount_Directory/Read Before You Install.app/Contents/Resources/ko.lproj/&#49444;&#52824; &#51204;&#50640; &#51069;&#50612;&#48372;&#44592;.pdf
BraseroGenisoimage stderr: /usr/bin/genisoimage: Warning: Directory loop (/home/robert/Desktop/Mount_Directory/var/cron/tabs dev: 700 ino: 12670).
BraseroGenisoimage stderr: /usr/bin/genisoimage: Error: '/home/robert/Desktop/Mount_Directory/private/var/log/wtmp' and '/home/robert/Desktop/Mount_Directory/var/log/wtmp' have the same Rock Ridge name 'wtmp'.
BraseroGenisoimage stderr: Unable to sort directory var/log
BraseroGenisoimage called brasero_job_error
BraseroGenisoimage finished with an error
BraseroGenisoimage asked to stop because of an error
	error		= 16
	message	= "An image could not be created"
BraseroGenisoimage stopping
BraseroGenisoimage got killed
Session error : An image could not be created (brasero_burn_record brasero-burn.c:2839)

Quite a bit of stuff. You can download its full contents. 

I have no idea what this means and I really would like to make this disk. Please help.

---

### Post by unckybob on 2010-07-24
Bump

---

### Post by unckybob on 2010-07-24
I was creating a disk image of a mounted directory. I copied the contents of the mounted directory which produced errors because it was referencing links that were referenced according to the mounted directory. Instead I burned the mounted directory instead of the contents of the directory and everything worked fine.

---

