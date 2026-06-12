---
title: "ubuntu 12.04 no space even deleting files"
date: 2012-05-10
forum: General Help
---

### Post by gabak on 2012-05-10
hi
i have been deleting many files everywhere and even that always i got ZERO space available
i made one partition of 50gb for OS and the rest of 1tb for data.
no games no weird software just emails and other small software like pidgin

i have followed this link and i have deleted log , tmps , trash , and nothing. i had run fsck and all is ok.
i m clueless now

[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)

gab@gab-System-Product-Name:~$ df -la
Filesystem       1K-blocks      Used Available Use% Mounted on
/dev/sda1         52641768  52641768         0 100% /
proc                     0         0         0    - /proc
sysfs                    0         0         0    - /sys
none                     0         0         0    - /sys/fs/fuse/connections
none                     0         0         0    - /sys/kernel/debug
none                     0         0         0    - /sys/kernel/security
udev               1982456         4   1982452   1% /dev
devpts                   0         0         0    - /dev/pts
tmpfs               809688       928    808760   1% /run
none                  5120         8      5112   1% /run/lock
none               2024212        76   2024136   1% /run/shm
overflow              1024       120       904  12% /tmp


thank you guys in advances.

---

### Post by papibe on 2012-05-10
Hi gabak.

Try removing some unused downloaded packages:
```
sudo apt-get autoclean

sudo apt-get autoremove

sudo apt-get clean
```

You can also remove old kernels following [this]("http://www.omgubuntu.co.uk/2011/07/kernel-entries-gone/") tutorial.

Hope it helps.
Regards.

---

### Post by jerome1232 on 2012-05-10
Looks like you have a crap ton of stuff in your home. You could use a command like below to list all files in your ~/ above say 300 MB's

```
find ~/ -size +500M
```

---

### Post by gabak on 2012-05-10
i have done that but it does nt work.
gab@gab-System-Product-Name:~$ sudo apt-get autoremove
[sudo] password for gab: 
sudo: unable to write to /var/lib/sudo/gab/7: No space left on device
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
gab@gab-System-Product-Name:~$ sudo apt-get clean
[sudo] password for gab: 
sudo: unable to write to /var/lib/sudo/gab/7: No space left on device
gab@gab-System-Product-Name:~$ sudo apt-get autoclean
[sudo] password for gab: 
sudo: unable to write to /var/lib/sudo/gab/7: No space left on device
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
gab@gab-System-Product-Name:~$ sudo dpkg --configure -a
[sudo] password for gab: 
sudo: unable to write to /var/lib/sudo/gab/7: No space left on device
dpkg: error: failed to write status database record about 'tcpd' to '/var/lib/dpkg/status': No space left on device

> **papibe said:**
> Hi gabak.

Try removing some unused downloaded packages:
```
sudo apt-get autoclean

sudo apt-get autoremove

sudo apt-get clean
```

You can also remove old kernels following [this]("http://www.omgubuntu.co.uk/2011/07/kernel-entries-gone/") tutorial.

Hope it helps.
Regards.

---

### Post by CatKiller on 2012-05-10
You haven't said that you've deleted root's Trash, and running Baobab as a normal user as you've done in the screenshot won't show root's files.

For future reference, holding down shift while you delete things in Nautilus will bypass the Trash.

---

### Post by gabak on 2012-05-10
i have deleted tons of Virtual machines that were big like 5gb each and it still nothing it looks like a bug to me

gab@gab-System-Product-Name:~$ find ~/ -size +500M
/home/gab/VirtualBox VMs/xp1.vdi
/home/gab/VirtualBox VMs/2k3 with serial/2k3 with serial.vhd
/home/gab/VirtualBox VMs/zentyal/zentyal.vdi
/home/gab/VirtualBox VMs/win xp clonar/win xp clonar.vdi
/home/gab/VirtualBox VMs/xp/xp1.vdi
/home/gab/VirtualBox VMs/XP ENGLISH.vdi
/home/gab/VirtualBox VMs/2003 r2.vmdk
/home/gab/Videos/IMAG0055.MP4
/home/gab/cosas utiles win server y clases/Microsoft.Windows.XP.SP3.Professional.March.2011/XPmarch2011.iso
/home/gab/cosas utiles win server y clases/SW_CD_Windows_Svr_Std_2003_R2_32-BIT_X64_English_ISO_32bit_1_MLF_X13-73742.ISO
/home/gab/cosas utiles win server y clases/cursos/cursos.rar
/home/gab/.thunderbird/zmb1fhh1.default/Mail/pop3.live.com/Inbox
/home/gab/.thunderbird/zmb1fhh1.default/ImapMail/imap.googlemail.com/INBOX
/home/gab/.thunderbird/zmb1fhh1.default/ImapMail/imap.googlemail.com/[Gmail].sbd/Enviados
/home/gab/angie/katana-v2.0.rar
/home/gab/Dropbox/fer antena/fer antena.rar
gab@gab-System-Product-Name:~$ find ~/ -size +500M
/home/gab/VirtualBox VMs/xp1.vdi
/home/gab/VirtualBox VMs/2k3 with serial/2k3 with serial.vhd
/home/gab/VirtualBox VMs/zentyal/zentyal.vdi
/home/gab/VirtualBox VMs/win xp clonar/win xp clonar.vdi
/home/gab/VirtualBox VMs/xp/xp1.vdi
/home/gab/VirtualBox VMs/XP ENGLISH.vdi
/home/gab/VirtualBox VMs/2003 r2.vmdk
/home/gab/Videos/IMAG0055.MP4
/home/gab/cosas utiles win server y clases/Microsoft.Windows.XP.SP3.Professional.March.2011/XPmarch2011.iso
/home/gab/cosas utiles win server y clases/SW_CD_Windows_Svr_Std_2003_R2_32-BIT_X64_English_ISO_32bit_1_MLF_X13-73742.ISO
/home/gab/cosas utiles win server y clases/cursos/cursos.rar
/home/gab/.thunderbird/zmb1fhh1.default/Mail/pop3.live.com/Inbox
/home/gab/.thunderbird/zmb1fhh1.default/ImapMail/imap.googlemail.com/INBOX
/home/gab/.thunderbird/zmb1fhh1.default/ImapMail/imap.googlemail.com/[Gmail].sbd/Enviados
/home/gab/angie/katana-v2.0.rar
/home/gab/Dropbox/fer antena/fer antena.rar



> **jerome1232 said:**
> Looks like you have a crap ton of stuff in your home. You could use a command like below to list all files in your ~/ above say 300 MB's

```
find ~/ -size +500M
```

---

### Post by gabak on 2012-05-10
here other screenshot

gab@gab-System-Product-Name:~$ sudo find ~/ -size +500M
[sudo] password for gab: 
sudo: unable to write to /var/lib/sudo/gab/7: No space left on device
/home/gab/VirtualBox VMs/xp1.vdi
/home/gab/VirtualBox VMs/2k3 with serial/2k3 with serial.vhd
/home/gab/VirtualBox VMs/zentyal/zentyal.vdi
/home/gab/VirtualBox VMs/win xp clonar/win xp clonar.vdi
/home/gab/VirtualBox VMs/xp/xp1.vdi
/home/gab/VirtualBox VMs/XP ENGLISH.vdi
/home/gab/VirtualBox VMs/2003 r2.vmdk
/home/gab/Videos/IMAG0055.MP4
/home/gab/cosas utiles win server y clases/Microsoft.Windows.XP.SP3.Professional.March.2011/XPmarch2011.iso
/home/gab/cosas utiles win server y clases/SW_CD_Windows_Svr_Std_2003_R2_32-BIT_X64_English_ISO_32bit_1_MLF_X13-73742.ISO
/home/gab/cosas utiles win server y clases/cursos/cursos.rar
find: `/home/gab/.gvfs': Permission denied
/home/gab/.thunderbird/zmb1fhh1.default/Mail/pop3.live.com/Inbox
/home/gab/.thunderbird/zmb1fhh1.default/ImapMail/imap.googlemail.com/INBOX
/home/gab/.thunderbird/zmb1fhh1.default/ImapMail/imap.googlemail.com/[Gmail].sbd/Enviados
/home/gab/angie/katana-v2.0.rar
gab@gab-System-Product-Name:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        51G   51G     0 100% /
udev            1.9G  4.0K  1.9G   1% /dev
tmpfs           791M  928K  790M   1% /run
none            5.0M  8.0K  5.0M   1% /run/lock
none            2.0G   76K  2.0G   1% /run/shm
overflow        1.0M  128K  896K  13% /tmp



> **CatKiller said:**
> You haven't said that you've deleted root's Trash, and running Baobab as a normal user as you've done in the screenshot won't show root's files.

For future reference, holding down shift while you delete things in Nautilus will bypass the Trash.

---

### Post by gabak on 2012-05-10
it is so weird now after restart the pc i got a little bit more of space!
how come? why it cant update the free space right away?

gab@gab-System-Product-Name:~$ df
Filesystem     1K-blocks      Used Available Use% Mounted on
/dev/sda1       52641768   6127036  43877472  13% /
udev             1982456         4   1982452   1% /dev
tmpfs             809688       920    808768   1% /run
none                5120         8      5112   1% /run/lock
none             2024212        76   2024136   1% /run/shm
/dev/sda2      915703648 212612284 657260148  25% /home
gab@gab-System-Product-Name:~$ sudo apt-get clean
[sudo] password for gab: 
gab@gab-System-Product-Name:~$ sudo apt-get autoclean
E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the download directory
gab@gab-System-Product-Name:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 38 not upgraded.

---

### Post by lisati on 2012-05-10
> **gabak said:**
> it is so weird now after restart the pc i got a little bit more of space!
how come? 
The /tmp folder, roughly equivalent to the %temp% directory in Windows, usually gets cleaned out when you reboot.

---

### Post by gabak on 2012-05-10
lisati thank you for your answer.
i have been at tmp too and i have deleted all and still running out of space.

last resource will remove all my data and format and install everything again but i wont know what was wrong with it.

> **lisati said:**
> The /tmp folder, roughly equivalent to the %temp% directory in Windows, usually gets cleaned out when you reboot.

---

### Post by Amida on 2012-09-04
> **gabak said:**
> lisati thank you for your answer.
i have been at tmp too and i have deleted all and still running out of space.

last resource will remove all my data and format and install everything again but i wont know what was wrong with it.

Hi sorry to bump an old thread but this may help other with the same issue.

It is a bug indeed, caused by the Guest account. After [disabling]("http://ashu-geek.blogspot.com/2012/05/guest-account-on-ubuntu-precise-how-to.html") it my free space in /home became 6GB from 0 (it is 9 GB in total). I was freaking out where my space went :)

---

### Post by fishman35 on 2013-01-25
I have this same problem. I have a 120GB SSD with Ubuntu 12.04 on it and I use it as a Clonezilla server. I had been deleting images that I no longer use, thinking they were going away for good, but pretty soon the drive filled up and I get the "system is running in low resolution" error at boot.
 
I have tried everything from the terminal outside of the OS, from altering lightdm.conf to running sudo apt-get clean. Nothing works. I took the drive out of that system and put it into one of my working servers. I can see the files I need to delete using the find ~/ -size +1000M, but when I run rm on them, they do not delete. Most have a . in front of them, so I know that means hidden. But they will not go away.
 
I do not even have enough space to install Autoclean or Bleachbit on that drive. 
 
Please help!! I rerally do not want to reinstall because it took forever to get Clonezilla working on this server for the sites I have to visit. 
 
Thanks to any Linux gurus who can solve this weird one.

---

