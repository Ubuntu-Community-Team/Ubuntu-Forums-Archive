---
title: "True Crypt and Ubuntu"
date: 2010-10-24
forum: General Help
---

### Post by kellyapproved on 2010-10-24
I know True Crypt offers full drive encryption for Windows OS but in looking through the screenshots, I can't seem to see if this is an option for Linux.

Just wondering if anyone has been able to encrypt their entire drive (including boot drive) with TrueCrypt?

---

### Post by oracle2b on 2010-10-25
Truecrypt doesn't offer full disk encryption on Linux but here is a [guide]("http://rationallyparanoid.com/articles/ubuntu-10-lts-security.html") to show you how to do full disk encryption with luks.

---

### Post by NertSkull on 2010-10-25
luks is the way to go.  its actually not too bad once you have it figured out, and it works great.

here is another tutorial that I use on all my systems when I was learning to dual boot an entire encrypted windows and ubuntu hard disk.  [link]("http://blog.nyxyn.com/2010/05/encrypted-ubuntu-104-on-dual-boot.html")

the tutorials may seem long, but work through them slowly and its not that bad, you just have to get a grasp of the partitioning scheme which is a bit more complicated than the way truecrypt does it

---

### Post by wieman01 on 2010-10-25
If you need full-drive-encryption, do a fresh install and chose that option in the installer. No need to go through LUKS which can be quite a pain. It works, but why not go with Ubuntu's default encryption method.

---

### Post by kellyapproved on 2010-10-25
> **wieman01 said:**
> If you need full-drive-encryption, do a fresh install and chose that option in the installer. No need to go through LUKS which can be quite a pain. It works, but why not go with Ubuntu's default encryption method.

I'd like to try this, do all versions of Ubuntu have full-drive encryption?

Also, how secure is the full drive encryption that come with Ubuntu?  Would it be on par with TrueCrypt/Bit Locker?

---

### Post by wieman01 on 2010-10-26
> **kellyapproved said:**
> I'd like to try this, do all versions of Ubuntu have full-drive encryption?

Also, how secure is the full drive encryption that come with Ubuntu?  Would it be on par with TrueCrypt/Bit Locker?
I believe it's on the Alternate CD.

It's secure, believe me. I think you can - for instance - choose av 256-Bit AES encryption which is really secure and recommended for governmental use, read this for more:

[https://help.ubuntu.com/community/EncryptedFilesystemHowto]("https://help.ubuntu.com/community/EncryptedFilesystemHowto")

So to answer your last questions, it is quite on par with TrueCrypt. 

I personally use TrueCrypt as I only encrypt my data partition which I keep separate from /home. I don't need more than this. All personal /home folders point to my data partition, hence my personal data are securely locked away.

---

