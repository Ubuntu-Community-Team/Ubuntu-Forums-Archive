---
title: "How to block users from looking into folders of others?"
date: 2011-08-23
forum: General Help
---

### Post by ragiete on 2011-08-23
I created an account for my brother but it's a very limited account, just so he can browse and listen to music and stuff like that.

However, what I do find funny is the fact that accounts are secured with a password but limited accounts can browse to /home and see the files of everyone, even admins, without Ubuntu asking for a password.

I obviously do not want this to happen.

Anyway, is there any way  I can block him from being able to browse to my homefolder, other than encrypting it?
I'm not a huge fan of encryption.

---

### Post by Toz on 2011-08-23
Open a terminal window, and type in the following command to secure the directories:
```
sudo chmod 770 /home/<user>
```
where <user> is the username of every account you want to secure.

---

### Post by ragiete on 2011-08-23
> **Toz said:**
> Open a terminal window, and type in the following command to secure the directories:
```
sudo chmod 770 /home/<user>
```where <user> is the username of every account you want to secure.

That's exactly what I needed, thanks! :D

However, when I install Oneiric Ocelot when it comes out,
will I still be able to access my own folder?

---

### Post by Toz on 2011-08-23
> **ragiete said:**
> However, when I install Oneiric Ocelot when it comes out, will I still be able to access my own folder?

I don't see why not.

Have a look at [https://help.ubuntu.com/community/FilePermissions]("https://help.ubuntu.com/community/FilePermissions") for a detailed explanation of file and directory permissions.

---

