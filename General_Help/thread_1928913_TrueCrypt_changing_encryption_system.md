---
title: "TrueCrypt: changing encryption system?"
date: 2012-02-21
forum: General Help
---

### Post by Welly Wu on 2012-02-21
I use Ubuntu 11.10 64 bit and I use TruCrypt. I have a Seagate FreeAgent Desk 1.5 terabyte USB 2 external hard disk drive that is protected using TrueCrypt (AES-XTS mode 256 bits SHA-512 hash algorithm) and I want to change the encryption system to Serpent. I would like to decrypt all of my data and re-encrypt it using Serpent-XTS mode 256 bits Whirlpool hash algorithm. Is this even possible without re-formatting the hard drive and losing all of my data? How can it be done in Ubuntu 64 bit?

---

### Post by Paddy Landau on 2012-02-21
To the best of my knowledge, TrueCrypt does not support on-the-fly re-encryption like that.

You will have to back up your data; reformat your drive using TrueCrypt; and restore your data.

Or, better (if you can afford it), get a new external hard drive, format it with TrueCrypt, transfer your data; and then repeat on the old external hard drive. That way you have a full backup in case your external hard drive dies (as they all do, eventually).

---

