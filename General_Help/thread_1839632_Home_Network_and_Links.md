---
title: "Home Network and Links"
date: 2011-09-06
forum: General Help
---

### Post by slotdoctor on 2011-09-06
Hello guys, I need a little help.

I am trying to set up a home network, where: 

I have my desktop running Ubuntu 10.10; A laptop with Windows XP; Another  desktop with Win7; And finally an older laptop with Ubuntu. 

Also I have a wireless router connected to DSL and a Netgear ReadyNAS Duo with 2 HD 1Tb each (I think they are RIAD1).

Obviously I would like to move all my files (documents, music and pictures to the NAS. Also, I would like to have every computer in the house be able to access the files. On my desktop only, I would like to have links, as to when I click on documents or pictures under Places, it goes to the right folder in the NAS.

I have try for the last month to get this accomplished with some limited success. I build an Ubuntu server. But, that did not work well (is a Samba thing). So I got the Netgear NAS device. 

I am asking could it be done. Have any one done it successfully. Do you know of any step by step tutorials I can follow? I think I know what I want, I yes do not know how to getter done, or if it is possible. Could anyone help?

Thank you, much appreciated.

---

### Post by Grenage on 2011-09-06
I've seen the ReadyNAS units before; nice build quality.  If I recall correctly, there were various ways of configuring shares through the device's web interface; FTP/Samba(might be listed as windows share) were definitely listed.

Assuming you have created the shares on the device, you can simply open Nautilus and either browse *Network*, or type in the address - for example:

smb://192.168.1.99/mysharename

Once accessed, you can create a bookmark by using the bookmark menu.  In Gnome classic you would simply click *Tools/Connect to Server*, but God knows where that option is in Unity; perhaps someone else will know.

---

### Post by rolnics on 2011-09-06
How about using NFS for your linux boxes, you'll get better transfer rates. [Here is a link for an NFS setup]("http://ubuntuforums.org/showthread.php?t=249889&highlight=nfs+setup")

Also [this howto for Samba]("http://ubuntuforums.org/showthread.php?t=202605&highlight=upgrade+samba") might help, as this is what I followed to get my shares working.

---

### Post by slotdoctor on 2011-09-06
Hey Grenage and Rolnics, Thanks for replying. 

Rolnics I checked the links, but I am still confused. I set samba on my desktop or the Netgear box? 

Thank you.

---

