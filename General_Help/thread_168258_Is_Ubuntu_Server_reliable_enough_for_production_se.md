---
title: "Is Ubuntu Server reliable enough for production servers?"
date: 2006-04-30
forum: General Help
---

### Post by Linux7 on 2006-04-30
Hi, I am new to Ubuntu and the server version.  Have been using CentOS-4.3 for my production servers but have one Supermicro MB that I can't get lm_sensors data for because it has the lm87 sensors chip which isn't currently supported in the current CentOS kernel.  It is supported in the Ubuntu kernel however.

Was wondering how stable and reliable Ununtu server has been for anyone that has tried it?  Is it ready for production servers this early?  Is it tested throughly enough like CentOS to be reliable?  How reliable compared to CentOS-4?

I really like the ease of the Ubuntu setup and APF / lm-sensors / webmin are working fine it appears.  Just have to install Plesk 8.

Forum was great for finding clear setup help with lm-sensors and APF firewall.

Thanks...

---

### Post by 2501 on 2006-04-30
hi....

read this article. i don't know if it can help but so far it looks pretty solid.

[http://fr.sys-con.com/read/151639.htm](http://fr.sys-con.com/read/151639.htm)

-2501

---

### Post by Linux7 on 2006-04-30
Thanks 2501 I read the article....

Well everything was going great until I tried to install Plesk 8.

Have tried 3 clean os installs and then Plesk autoinstaller...after letting psa autoinstaller do it's thing it freezes on the last line below.  Also tried the rpm version but problems also, I could not find all of these required packages and their dependencies.  I enabled all the repositories in sources.list Any suggestions?

Req packages for Plesk RPM
*************************
Install the packages of indicated versions or higher from the Ubuntu 5.10 i386 disc:

update-deb-Ubuntu-5.10-i386/
libtomcat4-java_4.1.31-3_all.deb
tomcat4_4.1.31-3_all.deb
tomcat4-admin_4.1.31-3_all.deb
libapache2-mod-jk_1.2.15-1_i386.deb
tomcat4-webapps_4.1.31-3_all.deb
*************************



Results of Plesk Autoinstaller Run
*************************
Please select the components you wish to install:

 1. [*] Base packages of Plesk
 2. [*] Plesk Updater
 3. [ ] Frontpage 2002 support
 4. [ ] Apache ASP support
 5. [ ] Mailman mailing list manager support
 6. [ ] PosgreSQL server support
 7. [ ] Tomcat Java Servlets support
 8. [ ] SpamAssassin support
 9. [ ] SPAM blocker for QMail daemon
10. [ ] Apache mod_python module
11. [ ] Application vault packages
12. [ ] Additional Horde (webmail) components for Plesk
13. [ ] Additional Plesk manuals
14. [ ] Backup utilities
15. [ ] Dr. Web antivirus
16. [ ] Plesk Professional Web Site Editor
17. [ ] Plesk API [former Plesk Agent]
18. [ ] SSHTerm - SSH Terminal java applet
19. [ ] Plesk migration manager
20. [ ] Plesk Firewall module
21. [ ] Plesk Counter-Strike game server module
22. [ ] Plesk VPN module
23. [ ] Plesk Battlefield 1942 game server module
24. [ ] Plesk Battlefield2 game server module
25. [ ] Plesk Fileserver module and SMB file server package
26. [ ] Watchdog (System monitoring module)
27. [ ] SiteBuilder and Sitebuilder module for Plesk
28. [ ] ColdFusion support for Plesk
29. [ ] Acronis TrueImage module

N) Next page; P) Go back;  Q) Cancel installing;
A) Select all; D) Deselect all;
To toggle component enter its number;
Type a number or a character of desired action [N]:
resolve packages with apt-get
Ign [http://autoinstall.plesk.com](http://autoinstall.plesk.com) PSA_8.0.0/ Release.gpg
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release.gpg [189B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release.gpg [189B]
Ign [http://autoinstall.plesk.com](http://autoinstall.plesk.com) PSA_8.0.0/ Release
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports Release.gpg [189B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release
Ign [http://autoinstall.plesk.com](http://autoinstall.plesk.com) PSA_8.0.0/ Packages
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release
Get:5 [http://autoinstall.plesk.com](http://autoinstall.plesk.com) PSA_8.0.0/ Packages [13.6kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
Fetched 13.6kB in 1s (11.7kB/s)
Reading package lists...
Preparing system for Plesk installation
===============================================================================

There are 68 standard packages, that are necessary for Plesk and which
were not found in your system.

There are 0 standard packages, that are installed, but will be upgraded
for product installation.



N) Install Plesk and all required packages; P) Go back;
Q) Cancel installing; L) Show list of packages;
Select action [N]:
Start Deb-based installation with apt
Ign [http://autoinstall.plesk.com](http://autoinstall.plesk.com) PSA_8.0.0/ Release.gpg
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release.gpg [189B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release.gpg [189B]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports Release.gpg [189B]
Ign [http://autoinstall.plesk.com](http://autoinstall.plesk.com) PSA_8.0.0/ Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release
Ign [http://autoinstall.plesk.com](http://autoinstall.plesk.com) PSA_8.0.0/ Packages
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports Release
Get:5 [http://autoinstall.plesk.com](http://autoinstall.plesk.com) PSA_8.0.0/ Packages [13.6kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
Fetched 13.6kB in 1s (12.7kB/s)
Reading package lists...
Reading package lists...
Building dependency tree...
Suggested packages:
  apache2-doc lynx www-browser bind9-doc php-pear uw-mailutils libcurl3-gssapi
  ca-certificates libldap2-dev dbishell libfreetype6-dev libgd-tools krb5-doc
  krb5-user libcompress-zlib-perl libio-socket-ssl-perl zip
Recommended packages:
  libmysqlclient14-dev libmailtools-perl libhtml-format-perl xml-core
The following NEW packages will be installed:
  apache2 apache2-common apache2-mpm-prefork apache2-utils bind9 gawk
  libapache2-mod-perl2 libapache2-mod-php4 libapr0 libboost-filesystem1.33.0
  libc-client2002edebian libcurl3 libdbd-mysql-perl libdbi-perl
  libdevel-symdump-perl libexpat1 libfreetype6 libgd2-noxpm libhtml-parser-perl
  libhtml-tagset-perl libhtml-tree-perl libidn11 libjpeg62 libkrb53
  liblockfile1 libmysqlclient12 libmysqlclient14 libnet-daemon-perl
  libpam-plesk libpcre3 libperl5.8 libplrpc-perl libpng12-0 liburi-perl
  libwww-perl libxml2 libxslt1.1 libzzip-0-12 mailx mlock mysql-client-4.1
  mysql-common-4.1 mysql-server-4.1 openssl php4-cli php4-common php4-domxml
  php4-imap php4-mysql psa psa-api psa-autoinstaller psa-courier-imap
  psa-courier-imap-add psa-horde psa-imp psa-locale-base-en-us
  psa-php4-configurator psa-proftpd psa-proftpd-inetd psa-pylibplesk psa-qmail
  python2.4-libxml2 sharutils ssl-cert unzip webalizer xinetd
0 upgraded, 68 newly installed, 0 to remove and 29 not upgraded.
Need to get 98.6MB/104MB of archives.
After unpacking 288MB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  psa-pylibplesk psa-qmail psa-locale-base-en-us psa-proftpd psa-proftpd-inetd
  psa-courier-imap psa-courier-imap-add psa-api psa-autoinstaller
  psa-php4-configurator psa libpam-plesk psa-horde psa-imp
Authentication warning overridden.
Get:1 [http://autoinstall.plesk.com](http://autoinstall.plesk.com) PSA_8.0.0/ psa-pylibplesk 8.0.0-ubuntu5.10.build80060331.13 [22.5kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main libgd2-noxpm 2.0.33-1.1ubuntu1 [191kB]
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main mysql-common-4.1 4.1.12-1ubuntu3.2 [36.2kB]
Get:4 [http://autoinstall.plesk.com](http://autoinstall.plesk.com) PSA_8.0.0/ psa-qmail 1.03-ubuntu5.10.build80060331.13 [2160kB]
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main libmysqlclient14 4.1.12-1ubuntu3.2 [1474kB]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe webalizer 2.01.10-26 [306kB]

downloads for a few minutes on the last line then stops and nothing else happens....
*********************

---

### Post by Linux7 on 2006-05-02
Well it appears you have to have the Ubuntu CD in the drive while using the Plesk Auto-Installer of all things....some authentication warning or something.  I just happened to hit "enter" at that part when it froze again then a request came up to enter the CD.

So very confusing as it should ask for the CD at the point it needs it and not just freeze then you have to stumble upon hitting "enter".

After that and also earlier enabling the universe/multi repositories only and not any of the other ones in the "sources.list" Plesk seemed to install just fine.

Lm-sensors is working great also and it's nice that Ubuntu recognizes both lm87 sensors chips as I believe Centos-4.3 only recognizes one of the chips which was very annoying as you can't monitor all the sensors stats at once.

---

### Post by Jason_25 on 2006-05-02
Your sources.list is wrong if you had to use the ubuntu cd.  Search the wiki for apt sources or post back here if you need an example copy.

---

### Post by Linux7 on 2006-05-02
Couldn't find anything on wiki....do you have a correct list you can post then. Plesk adds the Plesk repo so it's in there unless there is another one that should be added.

I've tried a few more installs and I get dependency errors with the default sources.list then when allowing varous combinations of repos in sources.list the process always wants to access the Ubuntu CD to verify authentication of 3 or 4 plesk (psa-xxx) files.


******************************************************
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

---

### Post by zipperback on 2006-12-20
I have Ubuntu Server deployed in a live environment and it's very solid.:mrgreen:

---

### Post by koenn on 2006-12-20
> Was wondering how stable and reliable Ununtu server has been for anyone that has tried it? Is it ready for production servers this early? Is it tested throughly enough like CentOS to be reliable? How reliable compared to CentOS-4?
It all depends on how you define "stable" and "reliable" - and also on your production environment (how long can you afford to have that server offline while you are troubleshooting something that did not go as smooth as expected ?"
Personally, I'd probably look at a Debian Stable Release for a production server. Debian makes a point of creating a rock solid system before they release it, and don't modify it afterwards (except for security related issues). Remember the infamous 6.06 LTS Xorg update that ruined Xorg. OK, that was for desktop systems, and your server wouldn't run Xorg anyway, but it was in the 'stable' LTS release. Imagene that in a server update for a critical application ...
Downside of Debian's stability strategy is that it does not include more recent software releases -but the weight of that downside depends on what you're going to use that server for (and trade off against how much downtime you can afford). 

If I were to run a Ubuntu server, I'd probably try to stick with the main repository and stay away from the others (universe, ...) and especially the 3th party repo's. That notice 
of ```
software from this repository may not have been tested as extensively as that contained in the main release, ... 
``` is not something you like to see on a productions erver. And it's not only those packages as such : also the way they'll behave in combination with the other packeges you install on your server is unpredictable. 
My interpretation is that you should consider any configuration that includes packages from other repos than main (and restricted ?) as "untested", and unsupported by Ubuntu (meaning that you're on your own if something breaks).   

-----------------------
As for the problems you mentioned:
the authentication failure probably refers to the plex repository - you'd neet to acquire and install a key from the plex server so that the packages downloaded can be authenticated as being genuine and not tampered with. I've seen guidelines elsewhere in this forum, maybe you can search;  

dependency problems are usually related to incorrect sources.list : a package you want to install requires additional packages that can not be found in the repositories that you've listed. I'll have a look at your sources.list in a minute.

---

### Post by koenn on 2006-12-20
Your sources.list is all about breezy. Is that for a reason ? 
It is possible that the plesk packages you try to install depend on ubuntu packages of higher versions than the ones breezy offers. 
Check (or post) the exact  dependency errors  you mentioned

---

### Post by celliott on 2007-01-15
Ubuntu 6.06LTS will run Plesk 8.1.0. I have it running on my machine at home. Now, i only have the free 1 domain version running because i dont feel like spening alot of cash on it but im not sure if that would make a difference. Before i was able to install, i needed to go to by source.list file and uncoment all the repositories..i was then able to install plesk using the Ubuntu version from their site.

---

### Post by Linux7 on 2007-02-14
Thanks for the replies.  Just an update to my initial post.  I've learned a lot since then about Ubuntu and I just can't say how much I like it for a production server.  It's been the most trouble-free, stable and reliable OS I've ever used and the apt-get package manager is awesome.

Just took me some time to get use to the changes between CentOS and Ubuntu.  After that initial period moving to Ubuntu has solved a lot of problems for me and I just like how the Ubuntu developers thinks especially with security.  Seting up a server is much easier than ever before and I rarely have dependency problems anymore which drove me crazy with other rpm based OS's.

I can't recommend Ubuntu enough...

I did get Plesk 8.1.0 running just fine though Plesk itself always continues to be about 90% of my problems no matter what the OS is.

---

### Post by el3ktro on 2007-02-14
All I can say about the reliability of Ubuntu as a server is this:

Main file server (Samba PDC), 4x Xeon processors, >100 users connected all day:
uptime: 205 days

Second fileserver for different network, 2x Pentium, >30 users connected all day:
uptime: 373 days

Relatively new backup server, 2x Pentium, runs Amanda to backup above fileservers:
uptime 88 days

They're running, and running, and running, and running and we didn't have ANY issues so far. Of course this also depends on the hardware ...

---

