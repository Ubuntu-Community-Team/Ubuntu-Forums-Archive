---
title: "Undo drivers, Terminal commands, etc."
date: 2011-07-10
forum: General Help
---

### Post by RogerDavis on 2011-07-10
While trying to make a Winmodem work, I've installed drivers, done magic incantations in Terminal, etc., without keeping complete records of what I did.  

Is there a "clean" routine or something that will remove unused drivers, or do a system rollback, or some other way to clean up the mess?

---

### Post by wildmanne39 on 2011-07-10
> **RogerDavis said:**
> While trying to make a Winmodem work, I've installed drivers, done magic incantations in Terminal, etc., without keeping complete records of what I did.  

Is there a "clean" routine or something that will remove unused drivers, or do a system rollback, or some other way to clean up the mess?Hi, only if you know what you did then you can use this command.
```
sudo apt-get --purge remove packagename
```
You could install bleachbit and run it but you need to pay close attention and make sure it does not remove anything you need,sometimes those program will tell you that it is no longer needed when it is.

---

### Post by oldos2er on 2011-07-10
Did you create a backup before making any changes in your system?

Your terminal commands are kept in ~/.bash_history. Type **history** in a terminal to see it.

If you installed drivers using a package manager, you should be able to use the same method to uninstall or remove them.

---

