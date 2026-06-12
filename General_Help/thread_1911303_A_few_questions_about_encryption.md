---
title: "A few questions about encryption"
date: 2012-01-18
forum: General Help
---

### Post by Basher101 on 2012-01-18
Hello fellow Ubuntu forums users!

first of, i have no experience with encryption whatsoever...and searching the forums i do not really find answers to all. So:

1. I have some sensitive data on my windows partition (my **_shared_** NTFS storage partition for both windows and ubuntu). I got most data there, will encrypting it have a big impact on performance? The shared partition is ~ 1 TB big.

2. Will encrypting my C: partition with windows 7 on it keep it from booting? Will it slow down?

3. What about a full disk encryption? it would give the highest security, but i have no sensitive data on Ubuntu at all.


thanks alot for your time and advice in advance.


regards

---

### Post by Paqman on 2012-01-18
> **Basher101 said:**
> 
1. I have some sensitive data on my windows partition (my **_shared_** NTFS storage partition for both windows and ubuntu). I got most data there, will encrypting it have a big impact on performance? The shared partition is ~ 1 TB big.


Remember that you'd need to use an encryption package that is cross-platform. Truecrypt springs to mind. I've never done it, but I don't see why a container created with Truecrypt in Linux shouldn't open with Truecrypt on Windows, or vice versa.

> 2. Will encrypting my C: partition with windows 7 on it keep it from booting? Will it slow down?

That depends. If you encrypt it using Linux, there's no way in a million years it will boot. If you use Windows 7's own encryption, it' ll be fine.

Any performance hit would be negligible.

> 3. What about a full disk encryption? it would give the highest security, but i have no sensitive data on Ubuntu at all.

I'm of the opinion that full disk encryption is overkill for most people, and merely introduces one more thing that can go wrong. It's very secure, and there are cases where it would be desirable, but I've never felt the need.

---

### Post by Basher101 on 2012-01-18
```
Long believed unbreakable, TrueCrypt is a free open-source full-disk encryption software for Windows 7/Vista/XP, Mac OS X and Linux, that creates virtual hard disks with real-time encryption.

 Passware Kit Forensic allows for memory acquisition of a seized computer over the FireWire port, even if the computer is locked. When a target computer is seized and turned on with the encryption disk accessible, the software scans its memory image and extracts the encryption keys, so law enforcement personnel can access the stored data. 

 Passware Kit Forensic 9.7 is a complete encrypted evidence discovery solution that reports all password-protected items on a computer and gains access to these items using the advanced decryption and password recovery algorithms. The software, which can also run in portable mode from a USB drive, is capable of finding encrypted data and recovering file and website passwords without making any changes to the target computer.

 It supports over 180 different file types and features recovery of passwords for PGP archives and virtual disks. The software supports Windows 7, Vista, 2003, XP, and 2008 Server, and now works with Guidance EnCase E01 disk image files -- the de-facto standard for computer forensics.
``` 

i read a thread where the securest encryption is to create one big encrypted volume, where you create inside of it more smaller, also encrypted volumes. Can this setup be accessed with the program listed above?

---

### Post by Paqman on 2012-01-18
That software sounds like it just gains access to memory (which is apparently possible over Firewire) and yanks out the keys to the encrypted volume. So the machine would have to be powered up for it to work. If it was shut down or had just been booted up without the encrypted volume having been opened it wouldn't work.

Standard advice is that if someone has physical access to your machine, they can access anything on it. Having said that it takes quite a bit of technological nous to crack encryption, it's not something your average opportunistic thief is going to be able to do if you have your laptop nicked.

In short, don't sweat it, the normal consumer encryption tools like Truecrypt or the encryption tools in modern OSes are perfectly good enough to protect your data from the kinds of bad guys you're likely to encounter.

---

### Post by Basher101 on 2012-01-18
i do not want to encrypt a laptop hard drive, but my Desktop PC drive a lá self built (see sig). Physical access would only occur when i am at school, and when i am my PC is always shut down (i even turn the PSU switch). Also my MSI motherboard has no Firewire port... 

But i guess you are right..

thanks alot for the advice.


So then may i ask, how do i go about encrypting my windows partition and the shared one? I just install truecrypt, encrypt them, then reboot into Ubuntu, install truecrypt there and just use it? 


thanks again


regards

---

### Post by Paqman on 2012-01-18
> **Basher101 said:**
> 
So then may i ask, how do i go about encrypting my windows partition and the shared one? I just install truecrypt, encrypt them, then reboot into Ubuntu, install truecrypt there and just use it? 


If you want to encrypt Windows you should use Windows' own encryption system. I don't know anything about that, or whether it's possible to enable it post-install or not.

Regarding Truecrypt: do a test. Install Truecrypt on both systems, create a little encrypted volume on one system, and see if you can open it on the other.

Ask yourself though: do you really *need* to encrypt this data? Even if you do, consider whether keeping an unencrypted backup is feasible. Encryption is a good tool for keeping other people away from your data, but if something goes wrong it can deny you access to it as well. If it's important enough to encrypt that's a risk you should consider.

---

### Post by Basher101 on 2012-01-18
thanks alot for the advice, i will try it with the small volume (or maybe even in a virtualbox just to be sure).

---

