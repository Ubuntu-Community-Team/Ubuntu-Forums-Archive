---
title: "add user permission to use sudo in command line"
date: 2010-10-20
forum: General Help
---

### Post by gufide on 2010-10-20
Hi, I have a problem about user permission, I just destroy my user... :mad:[COLOR=#000000] So, I create a new one. But I can't have the permission to use "sudo" or to install program... So, I cannot do a lot of thing in my computer. The logical solution is to boot in failsafe mode and access to the root terminal, but, I don't know how to change the permission to allow me to use sudo. No one can help me?

Thank you
[/COLOR]

---

### Post by &#24746;&#39764;&#12398;&#31070; on 2010-10-20
I don't think I understood what you said. What do you mean you destroyed your user? And I don't quite get what you're trying to do. Can you please be more specific? I also have to say that you can access the root terminal in a regular session.

---

### Post by gufide on 2010-10-20
Yes, I make a partition that the mount point is /home and that erase my ancient /home, and my user too. To solve it, I just delete it make it a new one. I want to remake my ancient with the graphic way, but I need root password.

---

### Post by sisco311 on 2010-10-20
Boot into *recovery mode* and add your user to the **admin** group:
[http://psychocats.net/ubuntu/fixsudo](http://psychocats.net/ubuntu/fixsudo)

---

### Post by &#24746;&#39764;&#12398;&#31070; on 2010-10-20
Did you give a different password to the new user?  As about the root terminal:

1) Go to System > Preferences > Main Menu
2) On your left choose System Tools
3) Select Root Terminal
4) Go to Application > System Tools > Root Terminal

It should be there.

---

### Post by gufide on 2010-10-20
> **sisco311 said:**
> Boot into *recovery mode* and add your user to the **admin** group:
[http://psychocats.net/ubuntu/fixsudo](http://psychocats.net/ubuntu/fixsudo)

thank you very much

---

