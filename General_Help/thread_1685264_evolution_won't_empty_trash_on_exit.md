---
title: "evolution won't empty trash on exit"
date: 2011-02-10
forum: General Help
---

### Post by rdh61 on 2011-02-10
Evolution 2.28.3 on Ubuntu 10.04 won't empty trash on exit even though this is specified in preferences. Neither will it expunge with right click on trash -> empty trash.

I have tried the solution at: [http://ubuntuforums.org/showthread.php?t=966187](http://ubuntuforums.org/showthread.php?t=966187)

i.e.

Close Evolution and open your file browser. 
Go to /home/put-your-ubuntu-login-name-here/.evolution/mail/local
There are 2 files (Junk.cmeta and Trash.cmeta). 
I deleted the Trash.cmeta file and opened Evolution again.
When you reopen Evolution, it creates a new Trash.cmeta file.

But still the same problem persists.

Any help appreciated.

---

### Post by rdh61 on 2011-02-11
OK, the trash.cmeta file was in .evolution/mail/local/.#evolution.sbd.

Deleted trash.cmeta, now it works.

---

### Post by rdh61 on 2011-02-14
Back to square one. This "fix" only lasted a couple of days, then back to situation where trash cannot be deleted.

---

### Post by claracc on 2011-02-14
First of all close evolution.

Then, you go to Places, you personal folder, select on see hidden files. Then go to .evolution, mail, local. There, you delete folders.db.

Then run evolution and try to empty trash folder again

---

### Post by rdh61 on 2011-02-17
Thanks!

---

