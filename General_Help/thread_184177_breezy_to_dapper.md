---
title: "breezy to dapper"
date: 2006-05-29
forum: General Help
---

### Post by zigoto on 2006-05-29
Hi, i have ubuntu breezy badger 5.10, and ubuntu dapper drake 6.06 final version is comming on 1st June and i want to ask if is possible to upgrade  to my 5.10 to the new 6.06, because i dont want to format and install every thing... and if is possible i loose the information???
And if is possible i ask for someone put a how to upgrade to 6.06

Regards!

---

### Post by kingmonkey on 2006-05-29
it will be possible to upgrade from 5.10 to 6.06

It will be as easy as update notifyer saying there is an upgrade available and clicking on upgrade.

---

### Post by AirRaven on 2006-05-29
Just a small note- the Breezy->Dapper upgrade is huge. 

You'll need to do something like leave your computer on overnight to complete it. For me it had about 1.5 GB of packages to download.

---

### Post by cacharreo on 2006-05-29
A new version of the Update Manager application has entered breezy-updates which can upgrade your entire system in a few simple steps.
To perform the upgrade:
   1.      Update your system to ensure that you have the latest version of Update Manager and associated packages. The necessary versions are available from the breezy-updates repository, which is enabled by default.
   2.      Run the following command (either via ALT-F2 or a terminal):
[B]gksudo "update-manager -d"
[/B]
    
The "-d" switch instructs Update Manager to consider pre-release versions, including this Beta release. Without this switch, only official, final releases will be considered.
]If you have a working network connection, it should then inform you about a new release and offer to upgrade your system.
For more information : [http://www.ubuntu.com/testing/dapperrc](http://www.ubuntu.com/testing/dapperrc)

---

### Post by Ramses de Norre on 2006-05-29
[QUOTE=AirRaven]Just a small note- the Breezy->Dapper upgrade is huge. 

You'll need to do something like leave your computer on overnight to complete it. For me it had about 1.5 GB of packages to download.[/QUOTE]
The upgrade took something between two and three hours for me on an athlon 64 3700+ 2.20GHz and 1Gig RAM with broadband connection. Should give you an idea =)

---

### Post by AirRaven on 2006-05-29
[QUOTE=Ramses de Norre]The upgrade took something between two and three hours for me on an athlon 64 3700+ 2.20GHz and 1Gig RAM with broadband connection. Should give you an idea =)[/QUOTE]
Identical specs, and 6 hours for me. 576k/s broadband is *not* meant for upgrading entire OSs.

---

### Post by drpaul on 2006-05-29
Is it likely to take 1.5 GB of free disk to upgrade?

thanks,

Paul

---

### Post by zigoto on 2006-05-29
Hi, i have installed things like postgresql, php5, and if i upgrade to dapper i don't loose the configuration of postgres and samba? And the files of my home directory, will no be deleted?

---

### Post by Ramses de Norre on 2006-05-29
[QUOTE=drpaul]Is it likely to take 1.5 GB of free disk to upgrade?[/QUOTE]
The upgrade replaces old packages, so there wont be very much more disk space used as before the upgrade.

---

### Post by Cavalierski on 2006-05-29
[QUOTE=zigoto]Hi, i have installed things like postgresql, php5, and if i upgrade to dapper i don't loose the configuration of postgres and samba? And the files of my home directory, will no be deleted?[/QUOTE]

 I upgraded my box at home & at work. Both they are ok to keep the previous conf file. I don't have php5, postgresql installed but some of the middleware applications upgraded with the previous conf. Dist upgrade definitly upgrade the version ,however if it's not major upgrade ,which the conf parameters are changed drastically, you can keep the previous conf file.

 If update manager overwrites some conf, it will ask you with the diff info whether it's ok to overwrite the conf or not. Some of them I keep previous conf answering "no", the others overwrote with "yes". Afterall every middleware works pretty well so far :) 

--
Not quite exactly related topic but might help...
[http://www.ubuntuforums.org/showthread.php?t=182439](http://www.ubuntuforums.org/showthread.php?t=182439)

---

