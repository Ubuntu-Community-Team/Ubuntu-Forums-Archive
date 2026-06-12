---
title: "Blank error msg in Sbackup Restore"
date: 2010-10-09
forum: General Help
---

### Post by Curbuntu on 2010-10-09
With some wailing and gnashing of teeth, I've gotten Sbackup working on our three Ubuntu 10.04.1 laptops in the house.  All back up to a drive on an external server, in the location [servername]/var/hda/files/bu[BackupClientMachineName].

Well and good.  But a backup is only good if you can restore it, so I thought I'd test by deleting a useless file, then trying to restore it.  The restore process finds the desired file (in this case I'm using the .FUL file) like so:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=171746&stc=1&d=1286646530[/IMG]

When I click "Yes" to restore, three things happen:

1) What seems to be a temporary restore folder is created at the restore target, but it is never populated;
2) The restore operation freezes and eventually has to be killed; and, 
3) A completely blank dialog box (I assume this was meant to be an error message) appears like so:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=171747&stc=1&d=1286646530[/IMG]

Anybody have any idea what's wrong or what the error message is trying to communicate?  TIA...

---

