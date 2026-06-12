---
title: "Partition Question Upgrading To 10.04"
date: 2010-05-03
forum: General Help
---

### Post by Aflack on 2010-05-03
should i do this if i have windows partitions?

[http://img405.imageshack.us/content_round.php?page=done&l=img405/5452/screenshotei.png](http://img405.imageshack.us/content_round.php?page=done&l=img405/5452/screenshotei.png)

---

### Post by GSF1200S on 2010-05-03
> **Aflack said:**
> should i do this if i have windows partitions?

[http://img405.imageshack.us/content_round.php?page=done&l=img405/5452/screenshotei.png](http://img405.imageshack.us/content_round.php?page=done&l=img405/5452/screenshotei.png)

Should be fine, but post the results of:
```
sudo fdisk -l
```
here so we can have a look.

---

### Post by Aflack on 2010-05-03
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       62151   499227876    7  HPFS/NTFS
/dev/sda2           62152       83436   170971762+   7  HPFS/NTFS
/dev/sda3           89711       91201    11976457+   7  HPFS/NTFS
/dev/sda4           83437       89710    50395905    5  Extended
/dev/sda5           83437       87318    31182133+  83  Linux
/dev/sda6           87319       87490     1381558+  82  Linux swap / Solaris

---

### Post by dino99 on 2010-05-03
/dev/sda is where windoz is installed and its bootloader too  !!!!

if you install grub on it, it will overwrite it and you'll not be able to boot windoz anymore

you have to know where ubuntu is installed and install grub on that mbr partition (ie if ubuntu is on /dev/sdc1, then put grub on /dev/sdc)

as it seems you have installed ubuntu on the same hdd as windoz and is installed on /dev/sda5, as you cant put grub on /dev/sda (because of windows), install grub on /dev/sda5.

note: its better to create a /home partition for your data instead of mixing them with the system files

[http://ubuntuforums.org/showthread.php?t=1467891&page=2](http://ubuntuforums.org/showthread.php?t=1467891&page=2) post 14

---

### Post by Aflack on 2010-05-03
> **dino99 said:**
> /dev/sda is where windoz is installed and its bootloader too  !!!!

if you install grub on it, it will overwrite it and you'll not be able to boot windoz anymore

you have to know where ubuntu is installed and install grub on that mbr partition (ie if ubuntu is on /dev/sdc1, then put grub on /dev/sdc)

tell me what to do lol.

right now the first thing i see is grub and i choose ubuntu or windows

then if i choose windows it takes me to windows 7 or vista and i choose. i want to keep this.

please answer its 4 am and i cant sleep with my computer on its too loud and i dont want to interrupt this

---

### Post by john newbuntu on 2010-05-03
Yes, please install grub to the MBR of /dev/sda just like how you have indicated in the screenshot.

---

### Post by dino99 on 2010-05-03
i've giving you an explication in post 4, if things have not changed since your screenshot there is no trouble at time, just follow post 4

---

### Post by Aflack on 2010-05-03
> **john newbuntu said:**
> Yes, please install grub to the MBR of /dev/sda just like how you have indicated in the screenshot.

are you completely sure this will allow me to still boot into windows 7 and windows vista?

edit: sorry to the poster above me i dont understand what your saying

---

### Post by dino99 on 2010-05-03
> **john newbuntu said:**
> Yes, please install grub to the MBR of /dev/sda just like how you have indicated in the screenshot.

/dev/sda1 * 1 62151 499227876 7 HPFS/NTFS

what are you trying to do ? look my post, you dont help that way , learn yourself

---

### Post by Aflack on 2010-05-03
> **dino99 said:**
> /dev/sda1 * 1 62151 499227876 7 HPFS/NTFS

what are you trying to do ? look my post

i said what i was trying to do and i see your post, but im extremely tired and i cant think too much right now and cant figure this out so well.

waiting for comfirmation on whether or not my screenshot is how i should do this to keep my triple boot..

---

### Post by dino99 on 2010-05-03
please answer its 4 am : goog time to go bed, you're right :)

two things to do:

-uncheck /dev/sda
- check /dev/sda5

and let's go

---

### Post by Aflack on 2010-05-03
> **dino99 said:**
> please answer its 4 am : goog time to go bed, you're right :)

two things to do:

-uncheck /dev/sda
- check /dev/sda5

and let's go
That's different from what the other guy confidently said  :(

---

### Post by dino99 on 2010-05-03
> **Aflack said:**
> That's different from what the other guy confidently said  :(

maybe its time to go bed, there are users giving wrong help too

---

### Post by john newbuntu on 2010-05-03
Dino,
I think you are right and I stand corrected.  He needs to choose /dev/sda5 for installing grub-pc.  I was thinking that this is the configuration part and that grub needs to be installed in the MBR.  Sorry for the confusion.
Aflack,  Sorry again.

---

### Post by Aflack on 2010-05-03
> **john newbuntu said:**
> Dino,
I think you are right and I stand corrected.  He needs to choose /dev/sda5 for installing grub-pc.  I was thinking that this is the configuration part and that grub needs to be installed in the MBR.  Sorry for the confusion.
Aflack,  Sorry again.

kk i will select sda 5.

---

