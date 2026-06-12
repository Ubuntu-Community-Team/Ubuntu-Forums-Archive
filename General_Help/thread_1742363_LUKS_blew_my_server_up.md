---
title: "LUKS blew my server up"
date: 2011-04-28
forum: General Help
---

### Post by Deathcon_1 on 2011-04-28
I've a large problem right now where, after a power outage, one of the disks won't come back online.  Brief overview of what I have: each drive is encrypted with LUKS, then each decrypted drive is added to a RAID6, which is then combined into a LVM.  Right now, I don't need to go into details of the setup, I may change it in the future, what I need now is to figure out why I'm seeing the message:
[INDENT]```
cryptsetup luksOpen /dev/sdi1 CRYPT_AWRB
Enter passphrase for /dev/sdi1: 
device-mapper: reload ioctl failed: Invalid argument
Failed to setup dm-crypt key mapping for device /dev/sdi1.
Check that kernel supports aes-cbc-essiv:sha256 cipher (check syslog for more info).
Failed to read from key storage.
```[/INDENT]

There are 11 total drives in the RAID, which was about 88% through a rebalance operation when the power cut out.  Each drive was encrypted using cbc-essiv:sha256 and I can open 10 of them no problems:

[INDENT]```
cryptsetup luksDump /dev/sdh1
LUKS header information for /dev/sdh1

Version:       	1
Cipher name:   	aes
Cipher mode:   	cbc-essiv:sha256
Hash spec:     	sha1

cryptsetup luksDump /dev/sdi1
^[[ALUKS header information for /dev/sdi1

Version:       	1
Cipher name:   	aes
Cipher mode:   	cbc-essiv:sha256
Hash spec:     	sha1

cryptsetup luksDump /dev/sdj1
LUKS header information for /dev/sdj1

Version:       	1
Cipher name:   	aes
Cipher mode:   	cbc-essiv:sha256
Hash spec:     	sha1
```[/INDENT]

What is this message, and how do I fix it?  Or should I force-start the RAID, fail the drive out, re-encrypt it, then re-add it, and wait for it to rebalance?  This is a critical server and I don't like it sitting in this inconsistent state...I may just remove encryption after this.

---

