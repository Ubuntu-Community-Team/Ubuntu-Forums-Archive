---
title: "I cannot download ANY software through &quot;add/remove&quot;, or manually...."
date: 2009-10-05
forum: General Help
---

### Post by earth.to.justin on 2009-10-05
I recently installed Ubuntu desktop "Jaunty Jacalope" on my laptop, and for the first two days had no problems setting it up and managing the software/programs/(whatever the 
right terminology is) via Applications -> Add/Remove. Now I cannot use the Add/Remove software feature. System -> Administration -> Software sources does not work either. ALSO, when trying to manually download programs like Adobe Flash, I can download the file onto my desktop but cannot unpack it. 

All of these different problems adding and downloading software give me the same error message:

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Is there a way that I can manually run this? Could someone tell me how? 
I really appreciate any help, I want to make Ubuntu work for me!







This may or may not be imprtant, but I also get this error when trying to update my downloadable software programs:

GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)/dists/jaunty/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)/dists/jaunty/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by itsbrad212 on 2009-10-05
this actually happened to me on an install of jaunty jackalope. the only thing i know of is to back up all of your files and re-install ubuntu. :)

---

### Post by wojox on 2009-10-05
Open up a terminal:
 
```
cat /etc/apt/sources.list
``` 

and copy and paste it up here.

---

### Post by lidex on 2009-10-06
To run manually, open up a terminal. In your menu it would be Accessories>Terminal. Copy and paste this command:
```
sudo dpkg --configure -a
```
Press the enter key. It will ask for your password. Enter that and press enter again.

---

