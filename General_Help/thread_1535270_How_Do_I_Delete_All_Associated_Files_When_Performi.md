---
title: "How Do I Delete All Associated Files When Performing A Purge"
date: 2010-07-20
forum: General Help
---

### Post by hayhursm on 2010-07-20
[SIZE=3]I went to remove FreeNX from my Ubuntu Lucid machine so I opened the terminal and typed: "sudo aptitude purge freenx"  The command worked but when I used the command "locate nx" I got a list of FreeNX associated files (as well as nxserver files).  Is it possible to completely remove a program from my system?  I thought "sudo aptitude purge" would do it but apparently not.  My only concern is that in the future if I decide to install something related to this program it will interfere and cause problems.[/SIZE]

---

### Post by stlsaint on 2010-07-20
Those may be files that are being used with other packages.

---

### Post by hayhursm on 2010-07-22
> **stlsaint said:**
> Those may be files that are being used with other packages.
 
[FONT=Times New Roman][SIZE=3]Thank you for the reply.  I don’t think those FreeNX files were associated with other files because they explicitly stated “freenx” in the filename.  I believe some crucial FreeNX files were not removed from my system because when I installed NX Free Edition for Linux from NoMachine it would not work.  However, when I did the exact same installation on my laptop (which never had FreeNX installed) it worked flawlessly.  Is there a command to make sure all associated files are removed?[/SIZE][/FONT]

---

### Post by Excedio on 2010-07-22
Try this:
```
 
sudo apt-get autoremove

```
It removes libraries that are not in use/tied to anything. Also, open Nautilus and go to your home folder (usually the default). Press Ctrl + H to unhide all folders. Look for any folders called FreeNX. These are typically configuration files, for if you decided to re-install again later and use the same user settings. These can be deleted.

---

### Post by hayhursm on 2010-07-24
> **Excedio said:**
> Try this:
```
 
sudo apt-get autoremove

```It removes libraries that are not in use/tied to anything. Also, open Nautilus and go to your home folder (usually the default). Press Ctrl + H to unhide all folders. Look for any folders called FreeNX. These are typically configuration files, for if you decided to re-install again later and use the same user settings. These can be deleted.


Just curious, how is "apt-get autoremove" different from "aptitude purge"?

---

### Post by hayhursm on 2010-07-27
> **hayhursm said:**
> just curious, how is "apt-get autoremove" different from "aptitude purge"?
 
 
bump

---

