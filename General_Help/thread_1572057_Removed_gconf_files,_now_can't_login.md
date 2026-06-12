---
title: "Removed gconf files, now can't login"
date: 2010-09-10
forum: General Help
---

### Post by Priswell on 2010-09-10
OK, I should have paid more attention.

I was getting an ""Error loading addressbook" msg and so I did a search and found this thread:

[http://ubuntuforums.org/showthread.php?t=688911](http://ubuntuforums.org/showthread.php?t=688911)

and followed these instructions:

----
- close Evolution
- delete /home/username/.gconf/apps/evolution/addressbook (it will be recreated)
- delete /home/username/.evolution/addressbook (it will be recreated)
- reboot your computer (this is crucial, otherwise the faulty gconf files will be restored)
- launch Evolution and enjoy your working address book
----

When I rebooted, I was unable to log into my system. It loads up to the login page, gives me the option to choose my login name, but I can't type my password in. The password line remains blank and if I click OK, it gives me an Invalid Authorization message.

What do I do now?

The computer is a system76 Wildebeest running Ubuntu 10.04 64bit.

---

