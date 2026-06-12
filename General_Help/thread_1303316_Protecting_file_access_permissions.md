---
title: "Protecting file access permissions"
date: 2009-10-28
forum: General Help
---

### Post by dolarsrg on 2009-10-28
Hi everyone!

I'm having some problems with my webpage security. There is a blog section where the users are the owners of each blog folder. 

Some users are changin the access permissions of that folders and I was wondering if is there someway at Linux to prevent that permissions from being changed. I want to be root the only user able to use CHMOD and CHOWN at that folders.

Thank you very much in advance ;)

---

### Post by rockstarrem on 2009-10-28
Can you set it up so you own the folders? Your user, I mean. If they own the folders I believe they can chmod and chown.

---

### Post by dolarsrg on 2009-10-28
Hi rockstarrem, thanks a lot for the answer. I can't, since I need them to log in trought FTP to upload their files. When they use their FTP client to log in they are connected directly to their blog folder and cand do "whatever" they want into them, but some times they change the main folder premissions:

If the user's name is User222 he is loged into:
/var/www/webpage/blogs/User222/

./User222's owner is User222 so he can upload whatever he wants. But It's very dangerous to allow User222 to change that folder permissions :(

---

