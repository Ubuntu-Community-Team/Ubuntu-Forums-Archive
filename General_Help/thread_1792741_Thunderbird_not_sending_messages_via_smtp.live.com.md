---
title: "Thunderbird not sending messages via smtp.live.com"
date: 2011-06-28
forum: General Help
---

### Post by DAB4970 on 2011-06-28
I have two accnts in Thunderbird 3.1.10 in Lucid 64bit - gmail and itt-tech.edu (smtp.live.com).  I removed apparmor because of the bug not allowing the file system to be mounted.  I can send via gmail, not smtp.live.com.  Smtp settings are correct.  Any security package setting that might be hindering this mail send action?  I have UFW installed.  Can anyone help, please?

---

### Post by An Sanct on 2011-06-28
A quick google search got this:

> Verify "25" is entered under *Port:*. 
[LIST]
[*]If you run into problems sending mail, try "587" instead.
[/LIST]
[The source]("http://email.about.com/od/mozillathunderbirdtips/qt/et_free_hotmail.htm") ...

---

### Post by DAB4970 on 2011-10-25
I fixed the issue.  It was the authentication method.:P
Thanks anyway.

---

