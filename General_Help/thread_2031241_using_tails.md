---
title: "using tails"
date: 2012-07-21
forum: General Help
---

### Post by antobbo on 2012-07-21
Hi there, since I chose to use tails rather than tor, I thought it will make more sense to open another thread.
I have downloaded tails and now I am trying to install it on a usb.
I have mounted the iso image, downloaded and imported the key:

gpg: key BE2CD9C1: public key "Tails developers (signing key) <tails@boum.org>" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
gpg: no ultimately trusted keys found

One thing I can't do though is to verify the installer. 
I have downloaded the tails signature and placed in the same folder where the iso is (bear in mind that I have mounted the iso on a different location)
I then cd'd in the folder where the iso and the signature are and typed this command:
 gpg --verify tails-i386-0.12.iso.pgp tails-i386-0.12.iso 
The output I received isn't that good:

gpg: can't open `tails-i386-0.12.iso.pgp'
gpg: verify signatures failed: file open error

Can anybody help me with that please?
thanks

---

