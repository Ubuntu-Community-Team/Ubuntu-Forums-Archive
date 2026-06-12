---
title: "Encrypted Hard Drive - Unable to unlock"
date: 2012-02-12
forum: General Help
---

### Post by sickrick43 on 2012-02-12
Hello all : )

I ran into a VERY big problem today. I have an external hard drive with months of work on it. ext 4. encrypted with passphrase. 

My computer froze overnight. I removed the power cord from the hard drive and may have caused an error in crypt-setup or something.

But when I put in the passphrase, it just says it's incorrect. i know it's correct. I have tried restarting and unlocking a few times. I'm not getting anywhere.

Is there a way to repair and salvage the data on this hard drive? It is EXTREMELY valuable to me and I'm pretty devastated right now. Counting on some Linux guru's to help me out.

Any help is GREATLY appreciated!

---

### Post by linuxwalker on 2012-02-12
Wish I could help. I'm not sure. I had a panic moment like that one time when I chose the "encrypt home folder" option in Ubuntu and forgot my password. I figured I don't need to, at least for now.

I'm thinking if you can boot from a repair disk/thumbdrive and somehow copy the data onto a backup. Maybe once you get it safe and copied (maybe multiple times for safety), and can get your encryption-decryption solution working, it can be decrypted.

I know commands like "dd" can be used for straight data copying like this, but still new to advanced tricks like that.

---

### Post by winh8r on 2012-02-12
There is this thread:

[http://ubuntuforums.org/showthread.php?t=1597246]("http://ubuntuforums.org/showthread.php?t=1597246")

although it is aimed at encrypted /home partitions so I am not 100% sure if it would work on your EXT HDD.

It will also depend on what you used to encrypt it.

Trouble is with encryption that it is designed to make it almost impossible to get to the data unless you are authorised to do so, so when something goes wrong like it has for you it puts you in the position of an "unauthorized" person. 

I am sure someone else will post here and tell you that if there was an easy way to get into an encrypted partition then there would be no point in encrypting it in the first place!!

Only other advice I can offer is to talk to the original poster on the thread in the link and see if they have any further insight that was not added to the post.

Good Luck

---

### Post by sickrick43 on 2012-02-12
thanks for the replies

yeah, it was stupid to even encrypt it. it was formatted and encrypted using Disk Utility on ubuntu 11.10. 

i think the error was caused from removing the usb cable from the hard drive while the computer was running. i did that before with another external HD and it would no longer be recognized under Disk Utility to mount. 

i am going to try from a live cd and continue looking for solutions. thanks again!

---

### Post by sickrick43 on 2012-02-12
here is the error code i get from Disk Utility when i click the button to remove the drive safely.

```
Error detaching: helper exited with exit code 1: Detaching device /dev/sdh
USB device: /sys/devices/pci0000:00/0000:00:13.2/usb2/2-3)
SYNCHRONIZE CACHE: FAILED: No such file or directory
(Continuing despite SYNCHRONIZE CACHE failure.)
STOP UNIT: FAILED: No such file or directory

```

---

