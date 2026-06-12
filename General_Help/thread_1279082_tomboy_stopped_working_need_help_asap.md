---
title: "tomboy stopped working need help asap"
date: 2009-09-30
forum: General Help
---

### Post by onesojourner on 2009-09-30
I started using tomboy at the begining of the semester and it has been great. Now when I try to open tomboy nothing happens. If I try to run it from terminal I get this error

Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.

---

### Post by directhex on 2009-09-30
Which release are you running?

---

### Post by MickS on 2009-09-30
Don't know if this will help but I get similar results trying to launch Tomboy but I have found if I open Thunderbird or Firefox first then Tomboy launches no problem, no idea why this should be.


Mick

---

### Post by krackersk on 2009-12-27
My installation of Tomboy stopped working, I un-installed Tomboy and removed it's config folders and re-installed and it worked.

Uninstall:
sudo apt-get remove tomboy

To remove all of tomboys folders you first have to find them:
find ~ -name tomboy

it should show you these folders in your home directory:
.local/share/tomboy
.config/tomboy
.cache/tomboy
.gconf/apps/tomboy

Your notes are stored in .local/share/tomboy, copy these to another location to make a backup and then delete these folders using 'rm -r'

Once these folders are deleted re-install Tomboy:

sudo apt-get install tomboy

---

