---
title: "lftp edit command permission denied"
date: 2009-12-15
forum: General Help
---

### Post by danielsbrewer on 2009-12-15
I am using the command line ftp client lftp and want to edit a text file on the ftp server.  No matter what I do I get a "permission denied" message.  For example:
lftp localhost:/ProgramFiles/Settings> edit EPG2MEI.ini
873 bytes transferred                         
bash: /home/daniel/.lftp/edit.tmp.5649: Permission denied

I have tried setting the permissions on .lftp to 777 and $EDITOR is set to vim, but still no joy.

Any ideas?

---

