---
title: "Can't upgrade from 11.04 to 11.10"
date: 2011-10-13
forum: General Help
---

### Post by nykilde on 2011-10-13
I can't upgrade from 11.04 to 11.10

Why? Shouldn't it just work?

---

### Post by Simon_WM on 2011-10-13
HI Mike, 

had the same issue, just downloaded the 11.10 torrent and loaded it to a disk, and formatted 11.04, but you might want to use the upgrade option

---

### Post by effenberg0x0 on 2011-10-13
Have you guys looked at the possibly of directly upgrading via network, instead of using ISOs for now? It's documented here:
[https://help.ubuntu.com/community/OneiricUpgrades](https://help.ubuntu.com/community/OneiricUpgrades)

Regards,
Effenberg

---

### Post by K4NEB on 2011-10-13
i tried updating and i kept getting an error and wouldnt work

then it just popped up randomly a while later so i started the upgrade

then half way through it stopped saying it couldnt find the installation files :/

---

### Post by the.chemist.ds on 2011-10-13
I'm currently having issues upgrading. When I click on Upgrade I get the message "Could not download the release notes".

It's just a guess, but I'm thinking that the Ubunbtu servers are being hit really hard as everyone tries to upgrade. I'd suggest trying upgrading again in a few hours (possibly even a few days)

Dave

---

### Post by Pest1lence on 2011-10-14
same problem here,

"W:GPG error: [http://archive.canonical.com](http://archive.canonical.com) oneiric Release: The 
following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu 
Archive Automatic Signing Key <ftpmaster@ubuntu.com>, W:Failed to 
fetch cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 
(20111012)/dists/oneiric/Release Unable to find expected entry 
'restricted/binary-i386/Packages' in Release file (Wrong sources.list 
entry or malformed file) 
, W:Failed to fetch cdrom://Ubuntu 11.10 _Oneiric Ocelot_ - Release 
amd64 (20111012)/dists/oneiric/main/binary-i386/Packages Please use 
apt-cdrom to make this CD-ROM recognized by APT. apt-get update 
cannot be used to add new CD-ROMs 
, E:Some index files failed to download. They have been ignored, or 
old ones used instead. "


***
thats what im getting everytime :confused:

---

### Post by krtica on 2011-10-14
Try to uncheck:

[ ] **cdrom:[Ubuntu 11.10_Oneric Ocelot...**

in Software Sources.

---

### Post by Pest1lence on 2011-10-14
thanks krtica, that did the job! :guitar:

---

