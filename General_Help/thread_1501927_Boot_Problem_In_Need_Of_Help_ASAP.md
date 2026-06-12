---
title: "Boot Problem In Need Of Help ASAP"
date: 2010-06-04
forum: General Help
---

### Post by Spigon on 2010-06-04
I was writing a letter to an extremely dear friend of mine who I may not be able to stay in contact with anymore due to certain circumstances. The letter was easily 5-6 pages long and very heartfelt and emotional. Unfortunately the letter is lost to me because in the middle of writing it my screen started to pixelated in hues of red, green, or blue. Afterwards my screen froze forcing me to start a reboot. However it seems that upon my next login I am kick out back to login screen after the screen goes black. This worries me as I often saved the document so much of my work isn't lost however I have no means of recovering it as I cannot log in. An example of my problem can be seen in the attachment.

P.S. It seems that I can log in xsession, I think that what it is called, but I have no mastery with commands in the terminal.

P.S.S. Anyone who can offer a solution to my problem please put it in terms that a linux novice can understand and later utilize. Or if you can post a video with commentary to show me how to solve said problem. Thank you for any and all help that may be provided.

---

### Post by lavinog on 2010-06-04
It is likely to be a hardware failure.
Have you tried booting with a live cd to see if it isn't just a corrupt file system?
Also on the live cd there is a menu option to test the system memory.  Give that a try.

---

### Post by Spigon on 2010-06-04
If the file system is corrupt which I'll have to check later is there any means to retrieving my document. Because there no way I can rewrite the letter without it losing meaning. And the letter is really important to me because it meant for someone truly important and dear to me.

---

### Post by lavinog on 2010-06-04
It is very likely that the file is fine, and retrievable.
You should be able to access it with the live cd.

---

### Post by Spigon on 2010-06-04
ROFL RLY? HOLY SMACKER! sorry for tha caps that oh joyous of days if this truly works! BRB gonna go try to see if it is there.

---

### Post by Spigon on 2010-06-04
Ummm how would I access it from the live cd?

---

### Post by lavinog on 2010-06-04
It has been a while since I have used the xubuntu cd, but the ubuntu live cd should let you mount the hard drive by going to places.
xubuntu should let you mount the hard drive in a similar manner.

---

### Post by lavinog on 2010-06-04
if all else fails you can mount the drive from the terminal:
```

sudo mkdir /media/harddrive
sudo mount /dev/sda1 /media/harddrive

then go to /media/harddrive and it should be your drive (assuming you only had a single partition on the drive)

```

---

### Post by Spigon on 2010-06-04
I am dual booting xubuntu and windows 7.....

---

### Post by Spigon on 2010-06-04
any more advice?

---

### Post by lavinog on 2010-06-04
> **Spigon said:**
> I am dual booting xubuntu and windows 7.....

ok
try this:
```

sudo fdisk -l /dev/sda

```
you should get something like this:
```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          51      409626   83  Linux
/dev/sda2              52       65077   522321314+   5  Extended
/dev/sda4   *       65078       77825   102398310    7  HPFS/NTFS
/dev/sda5              52        4095    32483398+  83  Linux
/dev/sda6            4096       16924   103048911   83  Linux
/dev/sda7           16925       30444   108599368+  83  Linux
/dev/sda8           30445       30571     1020096   82  Linux swap / Solaris
/dev/sda9           30572       60360   239280111   83  Linux
/dev/sda10          60361       65077    37889271   83  Linux

```
Most likely with less entries.
Look for the /dev/sda# that is a linux filesystem (not NTFS)  replace the 1 in /dev/sda1 in the mount example with that number

You can unmount the mounted filesystem this way:
```

sudo umount /media/harddrive

```

---

### Post by Spigon on 2010-06-04
ok it worked I mounted it but I now don't know how to access my document or desktop; i forget where i save my documents at.

---

### Post by lavinog on 2010-06-04
> **Spigon said:**
> ok it worked I mounted it but I now don't know how to access my document or desktop; i forget where i save my documents at.

If you saved it on your desktop you should be able to find your desktop:
```

cd /media/harddrive/home/username/Desktop

```

use the ls command to list the files

If you change to the desktop folder then use:
```

thunar .

```
it should open the filemanager at your desktop.

---

### Post by Spigon on 2010-06-04
I cannot access my folder. I go to harddrive then my username then i get "The application launcher "Access-Your-Private-Data.desktop" has not been marked as trusted. If you do not know the source of this file, launching it may be unsafe." BTW only reason I got this far was because I had to use sudo nautilus because I cannot open my locked folder otherwise.

---

### Post by lavinog on 2010-06-05
> **Spigon said:**
> I cannot access my folder. I go to harddrive then my username then i get "The application launcher "Access-Your-Private-Data.desktop" has not been marked as trusted. If you do not know the source of this file, launching it may be unsafe." BTW only reason I got this far was because I had to use sudo nautilus because I cannot open my locked folder otherwise.

It looks like your home folder is encrypted.
I don't have much experience with encrypted folders, give me some time to look it up.

---

### Post by lavinog on 2010-06-05
What version of xubuntu was installed?

---

### Post by Spigon on 2010-06-05
9.10

---

### Post by lavinog on 2010-06-05
you might be able to follow this guide:
[https://help.ubuntu.com/community/EncryptedPrivateDirectory#Recovering Your Data Manually](https://help.ubuntu.com/community/EncryptedPrivateDirectory#Recovering Your Data Manually)

---

### Post by Spigon on 2010-06-05
Hey I am just wondering.... since I am able to log in into the orginal Xubuntu OS through the Xsession and I use sudo nautilus can't I retrieve my file that way instead of through the live cd? Only reason I can't do it know cause through xsession it seems that wifi doesn't auto detect so I need to plug the ethernet cord in directly tomorrow. That way i can apt-get install nautilus, sudo nautilus, plug in flash drive then copy it over? Will that work?

---

### Post by lavinog on 2010-06-05
I could.  It shouldn't hurt to try.

---

### Post by Spigon on 2010-06-05
kk thx gotta try tomorrow parents sleeping

---

### Post by Spigon on 2010-06-05
[LIST=1]
[*]If you use encrypted filenames (standard in  Ubuntu >= 9.04) you have to do the following first: 

[LIST]
[*] sudo ecryptfs-add-passphrase --fnek   
[*] Passphrase:  (Enter the *mount*  passphrase you recorded when you setup the mount--this passphrase is  different from your *login* passphrase.) 
[*]You should now get two lines looking  like this: 
[*] Inserted auth tok with sig [9986ad986f986af7] into the user session keyring   
[*] Inserted auth tok with sig [76a9f69af69a86fa] into the user session keyring   (write down the second value in the square brackets) 
[/LIST]
[*]Mount using  sudo: 
[LIST]
[*] sudo mount -t ecryptfs /home/username/.Private /home/username/Private   
[*]** Selection: 3  (use a passphrase key type)  **
[*] Passphrase:   (Enter the *mount* passphrase you recorded when you setup the  mount--this passphrase is different from your *login*  passphrase.) 
[*] Selection: aes  (use the aes cipher) 
[*] Selection: 16   (use a 16 byte key) 
[*] Enable plaintext passthrough: n  
[*] Enable filename encryption: y   (This and the following options only apply if you are using filename  encryption) 
[*] Filename Encryption Key (FNEK) Signature: **  (the value you wrote down from the second line above) **
[/LIST]
[/LIST]
Ok..... I get pretty are but two problems pop up, these problems are bolded. First part.... it never offers me a selection for me to type in 3. Secondly ummmm the signature doesn't match what I got from step 1 part 5.

---

### Post by lavinog on 2010-06-05
I am not sure what to do at this point.

---

### Post by Spigon on 2010-06-05
Ok I figure out what I did wrong.... so I accidently rebooted now then i do this: 
bash:** sudo mount -t ecryptfs /home/henery/.Private /home/henery/Private**: No such file or directory

so im following the guide and when i type the command in bold it can't find it anymore, which it did the first time. All i need is probably help with this and it will work.

---

### Post by Spigon on 2010-06-05
please come back and answer this last question =p

---

### Post by lavinog on 2010-06-05
you need to mount /media/harddisk first

The afterwards the command should be something like:
```
sudo mount -t ecryptfs /media/harddisk/home/henery/.Private /media/harddisk/home/henery/Private
```
(Assuming you are doing this from the live cd.)

---

