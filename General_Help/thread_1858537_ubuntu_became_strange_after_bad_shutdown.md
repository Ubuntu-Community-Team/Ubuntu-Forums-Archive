---
title: "ubuntu became strange after bad shutdown"
date: 2011-10-12
forum: General Help
---

### Post by fadi hamadneh on 2011-10-12
i was using my ubuntu 10.04 lucid laptop normally on charger power, and the charger was unplugged by mistake from the outlet .. i logged in again normally and was surprised by many strange things :

1- Networking is Disabled (no network interfaces in the network manager) and it cannot be re-enabled.

2- all opening windows became unresponsive .. every application or window i open becomes unresponsive .

3- i tried to reinstall the networks interface but it tells me that it failed to resolve archive.ubuntu.com , then the hardware drivers window becomes unresponsive.

4- i tried to install the .deb file of network interfaces from a flash memory .. but the window freezes and no application runs. 

5- when i try to use the FORCE QUIT application it doesn't make a sense.

Pls Help me to solve this .. i want a fix to restore my system to an earlier date or a fix that recovers these issues .. my ubuntu became broken and unresponsive.

I will be thankful guys

---

### Post by fadi hamadneh on 2011-10-12
Pls help guys i need help :( :(

---

### Post by cryptotheslow on 2011-10-12
OK - firstly - a little patience please! It is considered rude to bump your post so frequently.

Do you have a LiveCD or a LiveUSB of Ubuntu? e.g. the CD or USB drive you used to install Ubuntu originally?

If you do - try booting from that and take the "Try Ubuntu" option. [COLOR=Red]_**DO NOT**_[COLOR=Black] take the "Install" option. Once it has booted to the desktop - see if networking is available then post back here.

This is just a simple and safe check to try and see if your hardware is OK.
[/COLOR][/COLOR]

---

### Post by fadi hamadneh on 2011-10-12
> **cryptotheslow said:**
> OK - firstly - a little patience please! It is considered rude to bump your post so frequently.

Do you have a LiveCD or a LiveUSB of Ubuntu? e.g. the CD or USB drive you used to install Ubuntu originally?

If you do - try booting from that and take the "Try Ubuntu" option. [COLOR=Red]_**DO NOT**_[COLOR=Black] take the "Install" option. Once it has booted to the desktop - see if networking is available then post back here.

This is just a simple and safe check to try and see if your hardware is OK.
[/COLOR][/COLOR]


ok i will try and reply .. and sorry for the bumping my post :)

---

### Post by fadi hamadneh on 2011-10-12
yes my hardware is okay i checked and everything appeared okay using live cd

---

### Post by cryptotheslow on 2011-10-12
That is good news! :D At least you know your hardware is OK.

From your expansive catalogue of problems, it is most likely some filesystem corruption caused by having a hard power outage whilst the filesystems were mounted.

So we can know what filesystems you have in use can you please boot back into the probalem installation (not LiveCD) and post up the output of this command entered into a Terminal:

```
sudo parted -l
```

That is a lowercase L as an option and the command simply lists partitions and their formats on disks connected to your PC. Do not enter any other option to the parted command than that one above!

---

### Post by wildmanne39 on 2011-10-12
Hi, often when you have a hard shut down you get file corruption and bad sectors on your hard drive.

You can run disk check with disk utility to see if you have any bad sectors from the livecd I believe.
Thank you

---

### Post by realstarman on 2011-10-13
Question: Have you tried booting in recovery mode and using a couple of options available there? (I.e. booting into file system check trying whether the root shell works.).

---

### Post by fadi hamadneh on 2011-10-14
> **realstarman said:**
> Question: Have you tried booting in recovery mode and using a couple of options available there? (I.e. booting into file system check trying whether the root shell works.).

how tell me ??? i am not professional .. give me some commands to do .. i want my network interface back :(

---

### Post by fadi hamadneh on 2011-10-14
> **wildmanne39 said:**
> Hi, often when you have a hard shut down you get file corruption and bad sectors on your hard drive.

You can run disk check with disk utility to see if you have any bad sectors from the livecd I believe.
Thank you
how to run it ??

---

### Post by fadi hamadneh on 2011-10-14
> **cryptotheslow said:**
> That is good news! :D At least you know your hardware is OK.

From your expansive catalogue of problems, it is most likely some filesystem corruption caused by having a hard power outage whilst the filesystems were mounted.

So we can know what filesystems you have in use can you please boot back into the probalem installation (not LiveCD) and post up the output of this command entered into a Terminal:

```
sudo parted -l
```That is a lowercase L as an option and the command simply lists partitions and their formats on disks connected to your PC. Do not enter any other option to the parted command than that one above!

[COLOR=Red]fadi-admin@fadi-admin-laptop:~$ sudo parted -l
[sudo] password for fadi-admin: 
Model: ATA WDC WD5000BEVT-7 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  106MB   105MB   primary   fat16           diag
 2      106MB   10.6GB  10.5GB  primary   ntfs            boot
 3      10.6GB  73.5GB  62.9GB  primary   ntfs
 4      73.5GB  500GB   427GB   extended                  lba
 5      73.5GB  303GB   229GB   logical   ntfs
 7      303GB   492GB   189GB   logical   ext4
 6      492GB   500GB   8053MB  logical   linux-swap(v1)
[/COLOR]

---

### Post by fadi hamadneh on 2011-10-14
GUYSSSS :D:D its solved :D

i booted with recovery mode .. and chose the FIX BROKEN PACKAGES option ... it took 1 hour to do that and restarted ,, and everything became okay :D :D .

thanks for your efforts :D

---

### Post by wildmanne39 on 2011-10-14
Hi, I am glad it is working.
Enjoy

---

