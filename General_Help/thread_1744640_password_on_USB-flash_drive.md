---
title: "password on USB-flash drive"
date: 2011-04-30
forum: General Help
---

### Post by Jonker on 2011-04-30
Hello,

I would like to know, if there is a possibility of password protecting an USB Flash drive. I would imagine, that it prompts you for a password, every time you want to view the folders/files (only the first time after boot, and just every time, the computer gets started). Is this possible?

Thx
Jonker

---

### Post by Joe of loath on 2011-04-30
Yes, but only on Linux.

Open the disk utility, unmount and delete and partitions on the disk, then create a new one (Anything you like, ext4 is best IMHO), and select 'encrypt underlying device'. Well done, your USB stick is now encrypted :p

---

### Post by Jonker on 2011-05-01
[FONT=&quot]Is there not a possibility, which would work on Mac, Win and Linux?

Would TrueCrypt with auto run function work?[/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot]Thanks[/FONT]
  [FONT=&quot] [/FONT]
  [FONT=&quot]PS: Your suggestion did not work (child process could not be started, because there is no such file or dir)[/FONT]

---

### Post by Joe of loath on 2011-05-01
Truecrypt would work, but each machine would have to have truecrypt installed. You could always put the truecrypt binaries on an unencrypted fat32 partition, though.

I'm not sure why it didn't work, sounds like you might not have the required stuff installed.

---

### Post by Jonker on 2011-05-01
so, a portable version on a hidden partition in a auto start folder would work? is there a portable truecrypt?

---

### Post by Joe of loath on 2011-05-01
Yup, for windows you can just google it and bring ups some results, and the mac version is portable by definition.

For Linux it's a little more complicated, but essentially you copy over the binaries and the libraries into their own directory, with /bin, /lib etc.

---

### Post by Jonker on 2011-05-01
so to serve all OS'es I would need to install 3 different versions?

How is that with to auto start folders, also 3 diffrent ones?

thx

---

### Post by Joe of loath on 2011-05-01
You don't need autostart anything, just have the fat32 partition the first one on the stick, and all OSes will detect it, and the user can run the specified files.

---

