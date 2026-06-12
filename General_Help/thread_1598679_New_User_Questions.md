---
title: "New User Questions"
date: 2010-10-16
forum: General Help
---

### Post by Preston Durbin on 2010-10-16
I have been having issues with Windows 7 so I partitioned and install Ubuntu 10.04.1 LTS (I believe it is called that) I am having issues getting it to save my stuff. I create my User Accounts and when I shut down everything is deleted and I have to re setup everything. Could someone please teach me how to operate this?

---

### Post by TBABill on 2010-10-16
Can you provide a bit more information? What specifically are you configuring that needs to be setup again when you restart? Saving configuration settings should be pretty easy to resolve with some more info.

---

### Post by Quackers on 2010-10-16
Welcome to Ubuntu Forums :-)
Is it a wubi install? Are you booting Ubuntu via a usb stick?

---

### Post by Preston Durbin on 2010-10-17
well i just looked over everything... and i guess i havent partitioned my drive yet... so I need a walkthrough on how to partition my drive and keep my windows 7 and all of its settings intact. I have a bunch of stuff I dont want to lose... but at the same time i no longer have my external hard drive as a backup :(

---

### Post by GeoMX on 2010-10-17
If you are running Ubuntu from a Live CD, you won't be able to keep your changes/files since they'll be deleted when shutting down, unless you save them to disk or any persistent media.

If you are planning to install Ubuntu and keep your current Windows installation, MAKE A BACKUP before attempting any change to your hard drive partitions, I have helped many friends to install Ubuntu (or another distro) to their systems and have never had problems, but it is better to be safe... :).

After backing up your system, you can start your system from a LiveCD and resize your Windows partition to make some space for Ubuntu, then follow the installer instructions.

---

### Post by Preston Durbin on 2010-10-17
Okay so where can I get my hands on a LiveCD? Price?

---

### Post by krishnandu.sarkar on 2010-10-17
> **Preston Durbin said:**
> Okay so where can I get my hands on a LiveCD? Price?

Price : Absolutely Free

[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

Download the ISO and burn the image to a CD and get started.

---

### Post by Preston Durbin on 2010-10-17
Should i use windows to get the file or could i use Ubuntu?

---

### Post by krishnandu.sarkar on 2010-10-17
Use anything...doesn't matter. The Ubuntu 10.04 LTS CD that you have with you right now is also a Live CD. And the link I provided is of updated version of Ubuntu - Ubuntu 10.10.

I don't think you have Ubuntu installed right now, so you can't use Ubuntu, so download it from Windows. And burn it with Nero or other CD/DVD burning program that you have.

---

### Post by Preston Durbin on 2010-10-17
I dont have a Ubuntu CD. I downloaded the install straight to my hard drive and ran from there. I can open Ubuntu from my boot menu but i think it is just the trial until I fully install

---

### Post by Preston Durbin on 2010-10-17
do I need to un pack (unzip) before i write it to the disk?

---

### Post by krishnandu.sarkar on 2010-10-17
You mean you downloaded the ISO and mounted it with some Virtual CD/DVD Manager and ran it from there..?? If that's the case you installed Ubuntu with Wubi. Means you already have Ubuntu installed.

---

### Post by krishnandu.sarkar on 2010-10-17
> **krishnandu.sarkar said:**
> You mean you downloaded the ISO and mounted it with some Virtual CD/DVD Manager and ran it from there..?? If that's the case you installed Ubuntu with Wubi. Means you already have Ubuntu installed.

No, I think ISO icon is showing as .zip icons. Don't unzip it, they are not zipped archives. Just burn that image.

BTW if you've installed with Wubi, then that's just not the trial, as you're saying you can select Ubuntu from Boot Menu, means it's already installed.

---

### Post by Preston Durbin on 2010-10-17
Well i can choose to run from my boot menu but when i do it still has the icon saying install on the desktop

---

### Post by krishnandu.sarkar on 2010-10-17
Leave it, Download the ISO, burn the image and install freshly booting from the Live CD.

---

### Post by Preston Durbin on 2010-10-17
ok i didnt want to run the desktop install because i didnt want to delete my windows

---

### Post by krishnandu.sarkar on 2010-10-17
I don't know what you did, installing with Wubi doesn't delete windows. Can you please describe what you did from first..??

---

### Post by Preston Durbin on 2010-10-17
I downloaded Ubuntu 10.04 from the Back Track 4 site. I ran the install i downloaded and it put the Ubuntu 10.04 on my pc as a trial that i cant alter settings for, and it put the actual install inside the trial that was installed.. so it is there but not really

I opened the real Installer to see how it works but it wouldnt partition so i canceled it and have left it alone since

---

### Post by Preston Durbin on 2010-10-17
here is a nice side note... my C:/ drive used to be called eMachines and now it is called Install Ubuntu

---

### Post by krishnandu.sarkar on 2010-10-17
It's getting much clear now...can you please confirm the link..?? Did you downloaded from [http://www.backtrack-linux.org/downloads/](http://www.backtrack-linux.org/downloads/) ??

---

### Post by Preston Durbin on 2010-10-17
Yeah thats the site. but for some reason it wont open anymore says it cant connect. my disk is done writing. so what steps do i take from here?

---

### Post by krishnandu.sarkar on 2010-10-17
I hardly guess did you really downloaded and installed Ubuntu?? Ubuntu is not there.

Anyway...boot the PC using that CD. Put the CD in tray, restart your PC, go to BIOS and select CD/DVD Drive as 1st Boot Device, then save your preferences and exit.

Ubuntu will automatically boot and then you can install Ubuntu from there.

---

### Post by Preston Durbin on 2010-10-17
ok... will i still be able to choose to boot Ubuntu or Windows when I start my PC?

---

### Post by krishnandu.sarkar on 2010-10-17
Yes after installing Ubuntu you'll can choose between Windows or Ubuntu or any other OS(if installed).

---

### Post by Preston Durbin on 2010-10-17
alright sweet im booting now then

---

### Post by Preston Durbin on 2010-10-17
ok so i got to the partitioning part and it kep saying Error: No Root File System Found.

---

### Post by krishnandu.sarkar on 2010-10-17
Ya you need to allocate space for installation. I mean you need to make some space for installing Ubuntu(Like where would you like to install Ubuntu)

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

Follow these.

[http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/](http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/)

Take a look at this if you need to partition manually.

---

### Post by matt_symes on 2010-10-17
Hi,

Am i missing something. Backtrack 4 is not Ubuntu??

 > "BackTrack is a Linux-based penetration testing arsenal that aids  security professionals in the ability to perform assessments in a purely  native environment dedicated to hacking."

Kind regards

---

### Post by krishnandu.sarkar on 2010-10-17
No..!! Back Track 4 is some other Linux Distro.

OP never used / installed Ubuntu.

---

### Post by Preston Durbin on 2010-10-17
So ithe installer wont let me partition and Im not sure how to run gParted Live, aid?

---

### Post by Preston Durbin on 2010-10-17
I used the Wubi install and an error keeps happening. This is posted in the log for it:

10-17 10:56 DEBUG  TaskList: New task get_metalink
10-17 10:56 ERROR  TaskList: Cannot download the metalink and therefore the ISO
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 493, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 331, in download_iso
Exception: Cannot download the metalink and therefore the ISO
10-17 10:56 DEBUG  TaskList: # Cancelling tasklist
10-17 10:56 DEBUG  TaskList: # Finished tasklist

---

### Post by Preston Durbin on 2010-10-17
Which installer should I use? I have been using Unetbootin

---

### Post by cgroza on 2010-10-17
Its so confusing. Are you running from the CD? When you installed Ubuntu did you clicked anything like. wubi.exe? If no you are running from the LiveCD  because Ubuntu can't be installed on its own partition because you said that you partitions are not modified.

---

### Post by Preston Durbin on 2010-10-17
I used Unetbootin to install it

---

### Post by Preston Durbin on 2010-10-18
I've taken a new approach and decided to partition my drive manually. I now have a 30GB (Z:/) drive that is set aside for my Ubuntu... I just need to know how to install it to that drive

---

### Post by Preston Durbin on 2010-10-18
ok i finally did it... thx for the help

---

