---
title: "Home directory suddenly encrypted"
date: 2012-04-30
forum: General Help
---

### Post by ump001 on 2012-04-30
hi,

i recently found my hard disk was full on my Ubuntu server and when i logged in i found the following file under my Home directory, there are a good few entries of a similar name:

HP:~$ ls
ECRYPTFS_FNEK_ENCRYPTED.FWaj.4-ixSIXNkQxPD16Fkufr4wUwiyly8kp1HfZAblcVqufWjU27rddnk--
ECRYPTFS_FNEK_ENCRYPTED.FWaj.4-ixSIXNkQxPD16Fkufr4wUwiyly8kp2p82xnbQhQKjIY3I01X2nk--
ECRYPTFS_FNEK_ENCRYPTED.FWaj.4-ixSIXNkQxPD16Fkufr4wUwiyly8kp3YhoFhInhZbDmv.TNZ-eak--
ECRYPTFS_FNEK_ENCRYPTED.FWaj.4-ixSIXNkQxPD16Fkufr4wUwiyly8kp6SzPm5YP-f6UJe9spy1Nrk--
ECRYPTFS_FNEK_ENCRYPTED.FWaj.4-ixSIXNkQxPD16Fkufr4wUwiyly8kp7.0lV6KugbrZCfMbpxUsME--
ECRYPTFS_FNEK_ENCRYPTED.FWaj.4-ixSIXNkQxPD16Fkufr4wUwiyly8kp8uMpjcvHhR2mXDvu1Gx2m---
ECRYPTFS_FNEK_ENCRYPTED.FWaj.4-ixSIXNkQxPD16Fkufr4wUwiyly8kp8VhpsR3FimiNPVt2XYMLZ---
ECRYPTFS_FNEK_ENCRYPTED.FWaj.4-ixSIXNkQxPD16Fkufr4wUwiyly8kp9u-ec2dqnZuNFW1OchAW9k--
ECRYPTFS_FNEK_ENCRYPTED.FWaj.4-ixSIXNkQxPD16Fkufr4wUwiyly8kpaBkvGVoasGyOMLtCwdLHxE--
ECRYPTFS_FNEK_ENCRYPTED.FWaj.4-ixSIXNkQxPD16Fkufr4wUwiyly8kpaJ1qai9.Z2zMZB16boeXdk--
ECRYPTFS_FNEK_ENCRYPTED.FWaj.4-ixSIXNkQxPD16Fkufr4wUwiyly8kpbDIDJSjv6EsPMt2gBiwDAE--
ECRYPTFS_FNEK_ENCRYPTED.FWaj.4-ixSIXNkQxPD16Fkufr4wUwiyly8kpBxsZ2dVESHuu1oPMOU1WtE--
ECRYPTFS_FNEK_ENCRYPTED.FWaj.4-ixSIXNkQxPD16Fkufr4wUwiyly8kpCddf4Cnrw.VWQjSsJtkMTU--
ECRYPTFS_FNEK_ENCRYPTED.FWaj.4-ixSIXNkQxPD16Fkufr4wUwiyly8kpCIwzmoR2FvWcHAlH5vgyaU--
ECRYPTFS_FNEK_ENCRYPTED.FWaj.4-ixSIXNkQxPD16Fkufr4wUwiyly8kpD6IfnLtCRSCsixNzjwlpJk--
ECRYPTFS_FNEK_ENCRYPTED.FWaj.4-ixSIXNkQxPD16Fkufr4wUwiyly8kpe79V3JOrSG9GTgJXfOaO7---
ECRYPTFS_FNEK_ENCRYPTED.FWaj.4-ixSIXNkQxPD16Fkufr4wUwiyly8kpfHGfEawJe5udIbS-4iNmj---



i dont see my usual listing of files. After doing some searching i found my home directory could be encrypted which i dont remember doing.

Anyway roudn this issue? A little new to ubuntu command so a pointer to a guide would be great.

---

### Post by ump001 on 2012-05-01
bump

---

### Post by ump001 on 2012-05-01
bump!

---

### Post by ump001 on 2012-05-02
help!

---

### Post by milosz.galazka on 2012-05-02
Look at [this]("https://help.ubuntu.com/community/EncryptedPrivateDirectory#Recovering%20Your%20Data%20Manually") documentation. I hope it contain the answers of your all questions

---

### Post by ump001 on 2012-05-03
Brilliant thanks.
read a few of Dustin Kirkland's articles and it lead me to this one:

[http://blog.dustinkirkland.com/2011/04/introducing-ecryptfs-recover-private.html](http://blog.dustinkirkland.com/2011/04/introducing-ecryptfs-recover-private.html)

Quite a simple fix really, but will need to reinstall the OS. Data is safe however :)

---

