---
title: "Encrypted Drive Question"
date: 2011-10-03
forum: General Help
---

### Post by Torqumada286 on 2011-10-03
I had a power supply failure that kept the system from booting up.  I decided to do some hardware upgrading and then reinstall everything.  I upgraded the home directory from a 300gb drive to a 1tb drive.  Once I got Win 7 and 10.10 installed, I started looking at the old drive and it said nothing was in the folders.  Then I discovered that my data had been encrypted. (I thought I was opting out of encryption when the popup happened.  Might want to make that just a tad bit more user friendly)  I found the encrypted files, but couldn't access them.  After some looking around, I found some [help](https://help.ubuntu.com/community/EncryptedPrivateDirectory) on how to access those files.  My concern is that once I access those older files, and move them to my new home, will they be re-encrypted to the new encryption for the new hard drive?  If I move them to a non-encrypted drive, will they remain encrypted? (I hadn't backed up my music files in a while.)

Torqumada

---

### Post by Torqumada286 on 2011-10-04
24 or so hours and no responses?  Have I stumped the experts?  Do I get a prize for that?

Torqumada

---

### Post by Torqumada286 on 2011-10-05
48 hours and still no replies?

Torqumada

---

### Post by mikejonesey on 2011-10-05
lol split ur paragraphs up... noone wants to read all that... lol

no ur files wont be re-encrypted... 

your using the ecryptfs... ecrypted file are stored /home/.ecryptfs/user/.Private/ 

once this dir is mounted to /home/user/ all files accessible through here will be unencrypted and remain so even if coppied anywhere...

ps... yes they will be reincrypted (if you opted in for encription on the new one)...

---

### Post by 3Miro on 2011-10-05
The "encrypt home option" is not enabled by default on the installer. If you got the popup, this means that you enabled encryption and the popup will give you a key to access your files in case on a system failure like the one that you had.

Assuming you get to your files, then you can take them and move them anywhere that you like. If you put them on an encrypted drive, they will get encrypted, if you put them on a regular drive, they will not get encrypted. Think of encryption as a property of the driver rather than the file itself.

---

