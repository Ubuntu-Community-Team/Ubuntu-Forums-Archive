---
title: "update manager issues"
date: 2010-04-18
forum: General Help
---

### Post by Ready2DropWin on 2010-04-18
Hello,

I have tried to use

sudo apt-get update
sudo apt-get upgrade

and I restarted and tried to do update manager and I still get this

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg)   Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 -  No address associated with hostname)
Failed to fetch cdrom://Ubuntu 10.04 _Lucid Lynx_ - Beta amd64  (20100406.1)/dists/lucid/main/binary-amd64/Packages.gz  Please use  apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot  be used to add new CD-ROMs
Failed to fetch cdrom://Ubuntu 10.04 _Lucid Lynx_ - Beta amd64  (20100406.1)/dists/lucid/restricted/binary-amd64/Packages.gz  Please use  apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot  be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones  used instead.

As you can see I am using 10.04 x64 and this issue happened after I  updated last night. I am not sure what else to do. Thanks in advance for  any help.

---

### Post by Ready2DropWin on 2010-04-18
Is there anyone else out there having this problem with this version, or having an issue with update manager?

---

### Post by joeaura7 on 2010-04-18
I have the same problem with same exact version as you. I am not for sure why it is complaining out the hostname. Perhaps they changed their ip address on us. If that is the case I wonder what the new ip addresses are. :confused:

I am crossing my fingers in hoping an update will fix the problem. :wink:

The two cdrom errors can be fixed simply by unchecking them in the software sources

---

### Post by Ready2DropWin on 2010-04-19
[COLOR=black][FONT=Verdana]Yeah I hope an update will fix it.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]As far as cdrom errors, I didn't add those sources, so I was afraid to remove them. Wasn't sure if it would update at all, if I did remove them.[/FONT][/COLOR]

---

### Post by plucky on 2010-04-19
> **Ready2DropWin said:**
> [COLOR=black][FONT=Verdana]Yeah I hope an update will fix it.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]As far as cdrom errors, I didn't add those sources, so I was afraid to remove them. Wasn't sure if it would update at all, if I did remove them.[/FONT][/COLOR]

**System > Administration > Software Sources** and un-tick the boxes for the CD-roms as these are added when you install.You shouldn't need them after the install.

Also in the same GUI,try selecting the Main Server and see if that corrects the problems.Sometimes the mirrors get out of sync.

Good Luck

---

### Post by Redsunz on 2010-04-19
Same problem with me I'm using Karmic 9.10.
I noticed this on Sunday Apr. 18th 2010.
I tried changing update servers and am still encountering the problem.
:confused:

---

### Post by Ready2DropWin on 2010-04-19
I have removed the check mark for cdrom, and I didn't see the error, this time. Then I did sudo apt-get update, and sudo apt-get upgrade. After it is done I am going to run the update manager and see if all is back to normal. Thanks for the help, plucky.

---

### Post by Ready2DropWin on 2010-04-19
Everything seems to be working fine, thanks for all the help.

---

