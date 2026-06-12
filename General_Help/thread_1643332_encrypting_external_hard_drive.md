---
title: "encrypting external hard drive"
date: 2010-12-11
forum: General Help
---

### Post by emreakbas on 2010-12-11
I want to create a encrypted filesystem in my external hard drive. I don't know where to start. Could anyone suggest me a tutorial to start with?

---

### Post by Bitrate on 2010-12-11
[https://help.ubuntu.com/community/TrueCrypt](https://help.ubuntu.com/community/TrueCrypt)

---

### Post by emreakbas on 2010-12-12
TrueCrypt is not in the Ubuntu repositories. I downloaded it and attempted to setup but it asked me the root password, and I couldn't trust it. I don't know what changes it is going to make. 

So I looked for another option and decided on dm-crypt/LUKS. I set it up today and it works great! Here are the steps I followed: [setup dm-crypt/LUKS]("http://tipstrickshowtos.blogspot.com/2010/12/so-you-want-to-take-backups-into-your.html").

---

### Post by Megaptera on 2010-12-13
> **emreakbas said:**
> TrueCrypt is not in the Ubuntu repositories. I downloaded it and attempted to setup but it asked me the root password, and I couldn't trust it. I don't know what changes it is going to make. 

So I looked for another option and decided on dm-crypt/LUKS. I set it up today and it works great! Here are the steps I followed: [setup dm-crypt/LUKS]("http://tipstrickshowtos.blogspot.com/2010/12/so-you-want-to-take-backups-into-your.html").

TrueCrypt download from Truecrypt website is OK to use, but I admire your caution ... better safe than sorry!
Glad you got the setup you wanted.

---

