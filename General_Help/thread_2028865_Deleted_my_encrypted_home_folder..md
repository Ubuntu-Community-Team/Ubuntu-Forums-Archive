---
title: "Deleted my encrypted home folder."
date: 2012-07-19
forum: General Help
---

### Post by insertusernamehere on 2012-07-19
Don't ask me how I did this.  Noob mistake.
 
I have most of the partition still, I might be missing a couple things but all I want is the files in the encrypted home folder that was deleted.

Can I use scalpel, or a similar program to get this back?

Thank you for any help!

By the way I still have the directory /home/.ecryptfs

I'm not sure if this was created when I used ecryptfs to try and recover things...?

---

### Post by insertusernamehere on 2012-07-19
HOLY SMOKES, I got it!!!

This is all I did:

1) Get Ubuntu, or another OS, onto a flash drive and boot it

2) Open up a Terminal window and type:

```
sudo ecrypt-recover-private
```

3) Wait a bit and then it will say success or fail.

4) You'll need to remember the password(whatever you used to login with the DELETED user).  Type that it when prompted.

5) It will say success/fail and mount the folder in the /tmp/ folder/

6) Profit.

I tried this like five times and finally got all of my information in the end so don't give up if it fails the first time.  Also, do what you can to preserve the partition.  For example, don't install a new OS, download a bunch of things, and encrypt  the disk then expect to get much back.

---

