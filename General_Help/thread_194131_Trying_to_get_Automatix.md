---
title: "Trying to get Automatix"
date: 2006-06-11
forum: General Help
---

### Post by Drifter on 2006-06-11
I have tried to get automatix with arnieboys thread but I can't seem to get it,  This is what happens;

david@david-desktop:~$ sudo gedit /etc/apt/sources.list
Password:
david@david-desktop:~$ gpg --keyserver subkeys.pgp.net --recv-keys 521A9C7C
gpg: requesting key 521A9C7C from hkp server subkeys.pgp.net
gpg: key 521A9C7C: "Justin Hayes (Automatix Repository Master) <wildtangent@w1ldt4ng3nt.net>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
david@david-desktop:~$ gpg --export --armor 521A9C7C | sudo apt-key add -
OK
david@david-desktop:~$ sudo apt-get update
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg [189B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg [189B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Fetched 3B in 1s (2B/s)
Reading package lists... Done
david@david-desktop:~$ sudo apt-get install automatix
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package automatix
david@david-desktop:~$ sudo apt-get install automatix
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package automatix
david@david-desktop:~$

What am I doing wrong

---

### Post by voitrix on 2006-06-11
Hi, just download it on the desktop from this site [http://www.beerorkid.com/arnieboy/automatix_6.1-8_i386.deb](http://www.beerorkid.com/arnieboy/automatix_6.1-8_i386.deb) and after that open a terminal window and type the commands
     
     cd Desktop

     sudo dpkg -i automatix_6.1-8_i386.deb

that's all :)

---

### Post by Drifter on 2006-06-11
I got it after a couple of tries with Arnieboys how to:  I had the file in the source list wrong. Thanks anyway.

---

