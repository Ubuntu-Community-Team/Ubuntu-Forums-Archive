---
title: "keyring problems"
date: 2010-12-14
forum: General Help
---

### Post by inthepit on 2010-12-14
thought i fixed my keyring problems, now i am back to square 1...  seems that the gnome keyring on my system does not want to keep any passwords.  worked fine after i did the remove process to fix the issue like all other posts say to do, but now it is right  back where i started.  having to delete the default.keyring every other day is getting tiresome.  is there a way to disable or remove the keyring all together?  and if so will the individual programs save the passwords... or is it safe to remove and reinstall the keyring?  are there any logs or something i could post to get some help on this issue.  

thanks

alex

---

### Post by dcstar on 2010-12-15
> **inthepit said:**
> thought i fixed my keyring problems, now i am back to square 1...  seems that the gnome keyring on my system does not want to keep any passwords.  worked fine after i did the remove process to fix the issue like all other posts say to do, but now it is right  back where i started.  having to delete the default.keyring every other day is getting tiresome.  is there a way to disable or remove the keyring all together?  and if so will the individual programs save the passwords... or is it safe to remove and reinstall the keyring?  are there any logs or something i could post to get some help on this issue.  


[LIST=1]
[*]Did you do a standard Ubuntu install?
[*]How do you have your /home partition set up?
[/LIST]

---

### Post by mcduck on 2010-12-15
> **inthepit said:**
> thought i fixed my keyring problems, now i am back to square 1...  seems that the gnome keyring on my system does not want to keep any passwords.  worked fine after i did the remove process to fix the issue like all other posts say to do, but now it is right  back where i started.  having to delete the default.keyring every other day is getting tiresome.  is there a way to disable or remove the keyring all together?  and if so will the individual programs save the passwords... or is it safe to remove and reinstall the keyring?  are there any logs or something i could post to get some help on this issue.  

thanks

alex

Would you care to explain a bit more what your actual problem is, and what you have deleted to solve it?

Under any normal conditions you shouldn't ever have to delete the keyring to fix problems. The only thing I can think of that might require that approach s the keyring files becoming owned by root, as a result from wrong use of "sudo" (like running GUI apps with "sudo" instead of "gksudo", or using "sudo -s" in a terminal instead of "sudo -i".)

---

