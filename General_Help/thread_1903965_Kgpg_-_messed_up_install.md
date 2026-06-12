---
title: "Kgpg - messed up install"
date: 2012-01-03
forum: General Help
---

### Post by Sharpie1 on 2012-01-03
Having problems running and using kgpg after not using it for ages, a couple of years, a couple of kernel upgrades etc and I dont want to overwrite my keyrings etc...
Kgpg wont start from the menu, I have to invoke it from the terminal... if I start without sudo (ie kgpg -k) it cant access my keyring.
If I start as root, it spits out complaints about various folders and files in the var/temp folder being 
Error: "/var/tmp/kdecache-rory" is owned by uid 1000 instead of uid 0 - but I can get access to my keyring, and encrypt/decrypt.
Ive tried to figure this out, its to do with permissions, and not running kde apps as root, should I export my keys, de-install, clean up and re-install, and could someone help me to do that properly so that the permissions are correctly set ? Or do I need to install kdesudo ?

Ubuntu 11.10
Kgpg 2.6.2
KDE 4.7.3

tia
Sharpie1

---

### Post by Enigma-Ocean on 2012-01-27
I found out how to fix this.  I was having the same issue and was able to locate the desktop file to make the minor change needed to start the program from the icon.

Go to:
**/usr/share/applications/kde4**

Then edit the file:
**kgpg.desktop**

The beginning looks like this:
[B][Desktop Entry]
Type=Application
Exec=kgpg %U
Icon=kgpg
X-DocPath=kgpg/index.html[/B]

Edit the line:
**Exec=kgpg %U**

To Look like this:
**Exec=kgpg %U -k**

Then all is working.  At least it did for me.  I can launch it from the launcher panel without having to go command line and get the errors and it not work right either.

This all worked after removing and installing it again and also installing gnupg-agent.

Hope it works for you.
/Marc

---

