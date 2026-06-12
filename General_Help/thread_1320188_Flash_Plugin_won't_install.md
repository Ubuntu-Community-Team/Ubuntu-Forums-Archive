---
title: "Flash Plugin won't install"
date: 2009-11-09
forum: General Help
---

### Post by aznsmartj0ck on 2009-11-09
I've just totally uninstalled/reinstalled compiz, and now Firefox's Flash plugin refuses to install.  I've tried sudo aptitude comands, as well as sudo apt-get commands, nothing is working.  I've also tried every method Adobe has to manually/automatically install the Flash plugin.  Does anybody know how I can fix this problem?  

P.S. every time I open the .deb file to install, i get the error "Could not open install_flash_player_10_linux.deb". The package might be corrupt, or you are not allowed to open the file. Check the permissions of the file. 

Any help would be appreciated.  Thanks.

---

### Post by jbrown96 on 2009-11-09
Could you give the output from the apt-get commands?

---

### Post by Rayve on 2009-11-09
[copied from your other thread]

What packages do you have installed for flash? I was having trouble until I uninstalled gnash and all swfdec stuff, and only kept flashplugin-installer.

Also, are you using 9.04 or 9.10, 32 or 64 bit?  I believe there has been an update for the 64 bit in 9.10.

---

### Post by aznsmartj0ck on 2009-11-09
I am running Ubuntu 9.10 x86.  

This is the error message:
E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.

Any help?  Thanks.

---

### Post by aznsmartj0ck on 2009-11-09
Sorry, I forgot to mention that it can't uninstall either...

It was installed b4, stopped working, and won't reinstall.

---

### Post by michy99 on 2009-11-09
Make sure the partner repositories are enabled. The update to 9.10 disables them and you have to re-enable them yourself.

---

### Post by aznsmartj0ck on 2009-11-09
what are the partner repositories?

since the flash plugin is corrupt, synaptic package manager doesn't work, so I'll need the exact names of the repositories through sudo apt-get.  Thanks.

---

### Post by michy99 on 2009-11-09
System->Administration->Software Sources->Other Software

---

### Post by aznsmartj0ck on 2009-11-09
THANK YOU!
everything is fixed now.  :D

---

