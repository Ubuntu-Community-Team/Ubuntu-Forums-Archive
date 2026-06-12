---
title: "How to restore files recovered from photorec ?"
date: 2012-08-11
forum: General Help
---

### Post by mohanp06 on 2012-08-11
Hi,

[U]**History:**

[/U]Long back when I first installed Ubuntu 10.04 on my system, during installation, I checked by mistake something saying :

encrypt home folder.

Afterwards, I forgot my key to decrypt this, and then I did some messy stuff which finally concluded in deleting all of my home folder data.

Then I found that some tool (photorec or linux rescue?) can restore my deleted files, so I used this tool and restored my files.


**_Problem:_**

Now I have so many Photorec restored directories, such as:

recup_dir_1
recup_dir_2

and so on...

These directory contain all types of files (.txt, jpg etc) but mostly contain files with extension .ecryptfs e.g.

f67609584.eCryptfs

I need to restore/decrypt this data. Is there any way to do this so that I restore my home folder as it was? 
Help is much needed !...  :sad:

---

### Post by hal8000 on 2012-08-11
Have a look here at post 6# and see if that solution works for you:

[http://www.kubuntuforums.net/showthread.php?58140-Recover-accidentially-deleted-data](http://www.kubuntuforums.net/showthread.php?58140-Recover-accidentially-deleted-data)

---

### Post by mohanp06 on 2012-08-11
At 3rd point, i am getting something like---


ubuntu@ubuntu:~$ sudo apt-get update && sudo apt-get install extundelete
Ign cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)/ lucid/main Translation-en_US
Ign cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)/ lucid/restricted Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg                      
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release.gpg
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release.gpg
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release
.
.
.
.
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/universe Sources

E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
ubuntu@ubuntu:~$

should i continue ahead?

---

### Post by mohanp06 on 2012-08-12
well, I searched for above error and got this command to rectify that:

**sudo fuser -cuk /var/lib/dpkg/lock; sudo rm -f /var/lib/dpkg/lock**

after I ran this command, screen suddenly went **black**, then I restarted using ctrl+alt+del which worked, but now whenever I boot into ubuntu, all that I am getting is a black screen of death! I am not even able to log in :(

Please help me out...

(I think I am able to boot from live cd, probably thats the only option with me!)

---

