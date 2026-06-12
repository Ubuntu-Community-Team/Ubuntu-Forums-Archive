---
title: "&quot;could not update ICEauthority&quot;"
date: 2010-10-28
forum: General Help
---

### Post by azerty.123.450 on 2010-10-28
Hello, I have Lucid Lynx with Gnome. At the start of the system, the  following message appears on my screem  :"could not update ICEauthority"

File's rights are the following :

-rwxr-xr-x 1 alpha alpha 54736 2010-10-27 16:17 .ICEauthority

I tried to remove this file, but there was no change.

Anyone can help me ?

---

### Post by ajgreeny on 2010-10-28
The permissions should be:-
-rw------- 1 username username 33768 2010-10-28 10:18 .ICEauthority
so you need to change that with chmod.  I assume your username is *alpha *and the file ownership is OK, so use ```
chmod 700 /home/alpha/.ICEauthority
``` and see if that helps.

---

### Post by azerty.123.450 on 2010-10-28
Thanks for your reply.

It doesn't work and the height of my file is still 33768.

---

### Post by philinux on 2010-10-28
> **azerty.123.450 said:**
> Hello, I have Lucid Lynx with Gnome. At the start of the system, the  following message appears on my screem  :"could not update ICEauthority"

File's rights are the following :

-rwxr-xr-x 1 alpha alpha 54736 2010-10-27 16:17 .ICEauthority

I tried to remove this file, but there was no change.

Anyone can help me ?

```
sudo chown username:username ~/.ICEauthority
```
From:-
[https://help.ubuntu.com/community/Troubleshooting#Desktop%20Environments](https://help.ubuntu.com/community/Troubleshooting#Desktop%20Environments)

---

### Post by azerty.123.450 on 2010-10-31
I think I'm already the owner of the file.

---

### Post by azerty.123.450 on 2010-11-02
My problem has been solved with this command
```

sudo chmod 0644 ~/.ICEauthority
```

---

