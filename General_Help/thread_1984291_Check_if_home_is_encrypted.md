---
title: "Check if home is encrypted?"
date: 2012-05-21
forum: General Help
---

### Post by mattfrog on 2012-05-21
I know it's a bit simple of me, but I've forgotten whether I clicked the "Encrypt my home folder" option when installing 12.04.. 

How could I check if I did or not please?

Thanks in advance :guitar:

---

### Post by ubuntu27 on 2012-05-21
I'm sure there is a terminal command to check it, but you could run a Live CD (or Desktop CD), and try to access your home folder. If it dosn't let you, then it is encrypted.

---

### Post by roelforg on 2012-05-21
> **ubuntu27 said:**
> I'm sure there is a terminal command to check it, but you could run a Live CD (or Desktop CD), and try to access your home folder. If it dosn't let you, then it is encrypted.

ecryptfs has to have ecryptfsd running (IIRC it's fuse based), so you could check if it's running.

---

### Post by loklaan on 2012-05-21
There is a pretty great question on [AskUbuntu](http://askubuntu.com/questions/53242/check-if-partition-is-encrypted) that has several solutions.

:)

---

### Post by mattfrog on 2012-05-21
Thanks everyone! 

Seems I forgot to click the checkbox :mad:

Can I retroactively enable it? If so, how please?

Thanks again :popcorn:

---

### Post by kanikilu on 2012-05-21
> **mattfrog said:**
> Can I retroactively enable it? If so, how please? [http://ubuntuforums.org/showthread.php?t=1648741](http://ubuntuforums.org/showthread.php?t=1648741)

Edit - it doesn't look like ecryptfs-utils (which has the migrate-home utility) is installed by default, so you'll need to install it first: ```
sudo apt-get install ecryptfs-utils
```

---

