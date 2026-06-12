---
title: "Cant Update My System In (Debian)"
date: 2012-05-06
forum: General Help
---

### Post by StrangeTrip on 2012-05-06
Sorry if this is in an wrong sub forum,but i need urgent help for this.

I install debian 6.04 and i cant update my system! This happend more than once ( i re installed it like 5 times) 


so i checked the  software sources and it seems that i cant  check from where i need to download updates i cant check anything. :confused:
[IMG]http://s17.postimage.org/mha3pfy8t/Screenshot_Software_Sources.png[/IMG]


i already was on the debian forum but there i cant find any help 
i also tried this in terminal

[SIZE="1"]```
root@Gandhi:/home/nature# sudo apt-get update
Ign cdrom://[Debian GNU/Linux 6.0.4 _Squeeze_ - Official i386 DVD Binary-1 20120128-12:53] squeeze Release.gpg
Ign cdrom://[Debian GNU/Linux 6.0.4 _Squeeze_ - Official i386 DVD Binary-1 20120128-12:53]/ squeeze/contrib Translation-en
Ign cdrom://[Debian GNU/Linux 6.0.4 _Squeeze_ - Official i386 DVD Binary-1 20120128-12:53]/ squeeze/contrib Translation-en_AU
Ign cdrom://[Debian GNU/Linux 6.0.4 _Squeeze_ - Official i386 DVD Binary-1 20120128-12:53]/ squeeze/main Translation-en
Ign cdrom://[Debian GNU/Linux 6.0.4 _Squeeze_ - Official i386 DVD Binary-1 20120128-12:53]/ squeeze/main Translation-en_AU
Ign cdrom://[Debian GNU/Linux 6.0.4 _Squeeze_ - Official i386 DVD Binary-1 20120128-12:53] squeeze Release
Ign cdrom://[Debian GNU/Linux 6.0.4 _Squeeze_ - Official i386 DVD Binary-1 20120128-12:53] squeeze/contrib i386 Packages/DiffIndex
Ign cdrom://[Debian GNU/Linux 6.0.4 _Squeeze_ - Official i386 DVD Binary-1 20120128-12:53] squeeze/main i386 Packages/DiffIndex
Hit http://ftp.debian.org squeeze-updates Release.gpg
Ign http://ftp.debian.org/debian/ squeeze-updates/contrib Translation-en
Ign http://ftp.debian.org/debian/ squeeze-updates/contrib Translation-en_AU
Ign http://ftp.debian.org/debian/ squeeze-updates/main Translation-en
Ign http://ftp.debian.org/debian/ squeeze-updates/main Translation-en_AU
Hit http://ftp.debian.org squeeze-updates Release
Hit http://http.us.debian.org squeeze Release.gpg
Hit http://ftp.debian.org squeeze-updates/main i386 Packages/DiffIndex
Ign http://http.us.debian.org/debian/ squeeze/contrib Translation-en
Ign http://http.us.debian.org/debian/ squeeze/contrib Translation-en_AU
Hit http://ftp.debian.org squeeze-updates/contrib i386 Packages
Hit http://ftp.debian.org squeeze-updates/main i386 Packages
Ign http://http.us.debian.org/debian/ squeeze/main Translation-en
Ign http://http.us.debian.org/debian/ squeeze/main Translation-en_AU
Ign http://http.us.debian.org/debian/ squeeze/non-free Translation-en
Ign http://http.us.debian.org/debian/ squeeze/non-free Translation-en_AU
Hit http://http.us.debian.org squeeze Release
Hit http://http.us.debian.org squeeze/contrib i386 Packages
Hit http://http.us.debian.org squeeze/non-free i386 Packages
Hit http://http.us.debian.org squeeze/main i386 Packages
Reading package lists... Done
root@Gandhi:/home/nature# sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@Gandhi:/home/nature# 

```[/SIZE]

---

