---
title: "can't backup kmail email b/c ':' is in file name"
date: 2006-02-25
forum: General Help
---

### Post by harty83 on 2006-02-25
Hello,

How can I back up my email when kmail places a ':' in the file name?  It will not back up saying "Invalid argument."

---

### Post by dcstar on 2006-02-25
[QUOTE=harty83]Hello,

How can I back up my email when kmail places a ':' in the file name?  It will not back up saying "Invalid argument."[/QUOTE]
Linux has no problem with ":" in file names, show us the exact error message.

---

### Post by harty83 on 2006-02-26
So I noticed.  

I ended up tarring the whole directory and then untarring it to restore.  Worked flawlessly.  

Thanks!

---

### Post by Pete051 on 2006-04-20
I've found that when I try to restore my kmail folder all my emails are there but when I click on then the header changes to No Subject and I've got a completly empty email, anyone else had this problem? :(

---

### Post by Pete051 on 2006-04-21
Solution found restore the write permission and it works fine :)

---

