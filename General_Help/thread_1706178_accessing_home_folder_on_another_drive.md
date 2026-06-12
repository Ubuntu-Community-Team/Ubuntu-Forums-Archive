---
title: "accessing home folder on another drive"
date: 2011-03-13
forum: General Help
---

### Post by brijraj22 on 2011-03-13
i somehow managed to corrupt ubuntu 10.10 installed on my laptop and subsequently, i loaded a fresh version of ubuntu 10.10 on another partition.
i want to access the data in the home folder of the other (previous) partition, but sudo nautilus gives me root privileges only in the current "filesystem" and not on the home folder of the other partition.

although i've been using ubuntu for some time now, but i am largely ignorant about most of the terminal commands. can someone please help.

---

### Post by llamabr on 2011-03-13
Try posting the output of 

```
df -h
```
to begin.

---

### Post by brijraj22 on 2011-03-13
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda7             9.1G  5.6G  3.1G  65% /
none                  491M  276K  491M   1% /dev
none                  497M  3.1M  494M   1% /dev/shm
none                  497M  388K  496M   1% /var/run
none                  497M     0  497M   0% /var/lock
/dev/sda5              23G   12G  9.9G  53% /media/188aa762-9cc3-4b08-9e44-923229cbbfce
/dev/sda1             109G   77G   32G  71% /media/4815180C799D13EA
/dev/sdb1             932G  869G   63G  94% /media/BRIJ


i'm interested in the home folder on /dev/sda5 while the current installation is on dev/sda7

---

### Post by coffeecat on 2011-03-13
Don't worry about using a root nautilus. Have a look in the Places menu. You should be able to see the previous Ubuntu's partition there, identified either by partition label or, if it didn't have one, by size. Simply click on it and a nautilus window will open showing the filesystem of the old Ubuntu. Open the home folder, then your account folder. You probably won't run into ownership or permissions problems because the UID of your account on your old system is likely to be the same as your new one.

If the old partition doesn't show in Places or won't mount, then something is wrong with the filesystem and we'll need to investigate further.

---

### Post by llamabr on 2011-03-13
If you know you want sda5, what happens when you:

```
cd /media/188aa762-9cc3-4b08-9e44-923229cbbfce
```
?  You should just be able to look around and get what you want from your corrupted disk.

---

### Post by brijraj22 on 2011-03-13
it doesn't work. i see two icons namely "access-your-private-data.desktop" and "readme.txt" and nothing else. when i try to run these files, i get this error:
"This link cannot be used, because its target "/usr/share/ecryptfs-utils/ecryptfs-mount-private.txt" doesn't exist."

---

### Post by vanadium on 2011-03-13
You apparently had the wisdom to encrypt your home directory in your previous install. See here: [https://help.ubuntu.com/community/EncryptedPrivateDirectory](https://help.ubuntu.com/community/EncryptedPrivateDirectory) on background on how this works. You will need this data to gain access to the partition. At one point, you will need to supply the password. If you do not have that anymore, then it will be pretty much impossible to access the data.

---

### Post by llamabr on 2011-03-13
> **brijraj22 said:**
> it doesn't work. i see two icons namely "access-your-private-data.desktop" and "readme.txt" and nothing else. when i try to run these files, i get this error:
"This link cannot be used, because its target "/usr/share/ecryptfs-utils/ecryptfs-mount-private.txt" doesn't exist."

Ah, you didn't mention that your disk was encrypted.  You'll need to supply the encryptfs-mount-private.txt, and you'll need your password.

[https://help.ubuntu.com/community/EncryptedFilesystemHowto](https://help.ubuntu.com/community/EncryptedFilesystemHowto)

---

### Post by brijraj22 on 2011-03-13
i dont have the passphrase, i realized its not the same as the login password.
anyway,thanks for the help,much appreciated :)

---

