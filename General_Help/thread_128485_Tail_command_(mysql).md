---
title: "Tail command (mysql)"
date: 2006-02-11
forum: General Help
---

### Post by rensu on 2006-02-11
Im trying to to this:
# In one window do this
tail -f /var/log/mysql/mysql.log
# then in another
tail -f /var/log/maillog.info

But after writing the second thing on another window I get this error:
tail: cannot open `/var/log/maillog.info' for reading: No such file or directory
tail: no files remaining

What should I do?:S Should I just create the maillog.info file?:-k

---

### Post by engla on 2006-02-11
Well; if it doesn't exist it's pretty pointless to 'tail' it; however, if you expect it to be filling with messages and want to set up tail to grab those before the first message is output (the file is created with the first message, I assume), you can create the file to monitor it.

To create an empty file, you use 'touch filename', that's a command to set the changed-date of any file to the current date and time, with the side effect that nonexistant files are created.
So, go ahead and
'sudo touch /var/log/maillog.info'
If you know/anticipate that it's going to be created anyway.

---

