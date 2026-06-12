---
title: "Maverick, encrypting home directory after installation"
date: 2010-11-10
forum: General Help
---

### Post by arkaitzj on 2010-11-10
Hi, 
I did a fresh Maverick install with custom partition layout and didn't select "encrypt home parition" as my home partition was being saved from previous installation.

Now, is there a guide I could follow to encrypt my home partition the same way Maverick would do? I just want to avoid screwing my system in the next upgrade if encrypting methods differ.

Thanks

---

### Post by dearingj on 2010-11-22
I'm looking for a way to do this too. I'll post here if I find anything.

---

### Post by gmargo on 2010-11-22
I have not tried this myself, but this article: [https://help.ubuntu.com/community/EncryptedHome](https://help.ubuntu.com/community/EncryptedHome) points at this forum thread: [http://ubuntuforums.org/showthread.php?t=1449168](http://ubuntuforums.org/showthread.php?t=1449168) which runs through a procedure.

Basically, you'll need to install the **ecryptfs-utils** package and then let **adduser** do all the work setting up the encryption.

---

