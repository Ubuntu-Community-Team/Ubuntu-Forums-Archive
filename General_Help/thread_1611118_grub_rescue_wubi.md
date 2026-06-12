---
title: "grub rescue wubi"
date: 2010-11-01
forum: General Help
---

### Post by jane2345 on 2010-11-01
I have a laptop dual-booted with vista/ubuntu using Wubi and upgraded this today from 9.10 to 10.10
but now I just get grub rescue when I try to boot up.I have searched forum for solutions but none have worked.
Tried [COLOR=Navy][FONT=Courier New]sudo apt-get install lilo[/FONT][/COLOR] using live cd but said lilo couldn't be found

From sudo fdisk -l

            Start End Blocks

/dev/sda    1          1274       102333731  unknown
 "                         2 5519       34093056   Fat16
 "                         3          9730       33822720   HPFS/NTFS

I ditched Windows altogether on my desktop for Ubuntu and have never had any regrets
and I am tempted to do the same with my laptop but would like to access my vista to retrieve some files/photos etc

Any help appreciated

---

### Post by oldfred on 2010-11-01
Welcome to the forums.

You have to enable universe. Software Sources, With Maverick they moved it to update manager settings.

Restore basic windows style boot loader - universe enabled from Ubuntu or liveCD
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR

drs305 has some info on wubi:
Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)

---

### Post by jane2345 on 2010-11-01
Thank you but just get "couldn't find package lilo
and second command for mbr says" command not found!! "

---

### Post by jane2345 on 2010-11-01
Sorry but can you enable Universe from a live CD

---

### Post by jane2345 on 2010-11-01
enabled universe but didn't make any difference

---

### Post by drs305 on 2010-11-01
> **jane2345 said:**
> enabled universe but didn't make any difference

jane2345,

Welcome to the Ubuntu forums.

After you enabled it, did you press the "Reload" button? You must update the repositories before you will find new packages.

---

### Post by jane2345 on 2010-11-01
yes pressed "reload" button and updated repositories still the same!!

---

### Post by jane2345 on 2010-11-01
ubuntu@ubuntu:~$ sudo apt-get install lido
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package lido
ubuntu@ubuntu:~$ sudo lilo-M/dev/sda mbr
sudo: lilo-M/dev/sda: command not found
ubuntu@ubuntu:~$ sudo lilo-M/dev/sda mbr
sudo: lilo-M/dev/sda: command not found
ubuntu@ubuntu:~$ sudo lilo -M/dev/sda mbr
sudo: lilo: command not found
ubuntu@ubuntu:~$ sudo apt-get install lido
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package lido
ubuntu@ubuntu:~$ sudo lilo -M/dev/sda mbr
sudo: lilo: command not found
ubuntu@ubuntu:~$ sudo apt-get install lido
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package lido
ubuntu@ubuntu:~$ sudo bash [path/to/the/download_folder]/boot_info_script*.sh
bash: [path/to/the/download_folder]/boot_info_script*.sh: No such file or directory
ubuntu@ubuntu:~$ sudo apt-get update
Ign cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic/main Translation-en_US
Ign cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5) karmic/restricted Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_US     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic-updates/universe Sources
Reading package lists... Done
ubuntu@ubuntu:~$ sudo apt-get install lido
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package lido
ubuntu@ubuntu:~$ sudo apt-get install lido
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package lido
ubuntu@ubuntu:~$

---

### Post by drs305 on 2010-11-01
The program is *lilo*, not *lido*.

Also make sure you have the correct spaces in the command:
```
sudo lilo -M /dev/sda mbr
```

---

### Post by jane2345 on 2010-11-01
It worked!!
Thank you so much
Spelling and spaces!!! Must remember

Now an avid fan of Ubuntu Forums as well as 
Ubuntu!!

Did I see a solved forum somewhere
I can post to!

Such a buzz hehe!!

Thanks again

---

### Post by drs305 on 2010-11-01
> **jane2345 said:**
> It worked!!
Thank you so much

Did I see a solved forum somewhere
I can post to!

Thanks again

:-)

You can mark the thread 'SOLVED' via the 'Thread Tools' link near the top right of the first post.

Happy Ubuntu-ing !  (When you return to Ubuntu.)

---

