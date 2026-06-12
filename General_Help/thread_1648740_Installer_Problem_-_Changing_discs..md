---
title: "Installer Problem - Changing discs."
date: 2010-12-19
forum: General Help
---

### Post by diskopanda on 2010-12-19
Hello ubuntu people! I installed ubuntu a couple of days ago and im starting to get a hang of it atm :)

For the moment being im trying to install World of Warcraft, when i tried to install with the CD's it wouldn't allow me to change from DISC 1 to DISC 2, in other words when it says...

"Please insert the CD labeled "World of Warcraft Disc 2" it wont work with changing CD's (the proper way)

I tried to do it with downloading the 4 discs in ISO format and mount it with Gmount
didnt work either...

So now I've got no idea how to make it work, I've tried to install several other games with several discs and it wont work for some reason...

I'm running on the latest ubuntu version (some hardy thing) and I've got the latest updates.
(p.s. im trying to install the vanilla version, not the cataclysm version :popcorn:)

---

### Post by Vigh on 2010-12-19
Try Furious ISO Mount Tool

just search for iso in software centre and install

dont bother re-ripping the isos, just make sure the isos are mounting to the same virtual drive, so mount, install, unmount, mount disc 2, continue install etc.

i had WoW running on linux awhile back, ran perfectly if not better than on windows

i did however use crossover and installed directly from cds

good luck

had similar problems trying to install some synth software in wine, ended up experimenting with the ISO mount programs, i think furious was the one that worked, keep trying the iso mount programs, i don't like Gmount that much for some reason it doesnt always work for me

---

### Post by diskopanda on 2010-12-19
First of all, thanks for the reply :)

So I installed Furious ISO and canceled the installer, then I tried to reinstall with the Furious ISO tool and got past the first CD, but when I came to the second disc popup it just did the same thing again.

"Please insert the CD labeled "World of Warcraft Disc 2."

On my desktop I can see that I HAVE the second disc mounted.

Something's wrong...

---

### Post by Vigh on 2010-12-19
any chance of a manual install? maybe you could try copying the critical files directly into the install folder, like the mpq's etc. should be in home folder/.wine/c/programfiles or something like that

have to show hidden files to be able to see the .wine folder

provided the files are in the correct directory structure thats all the installer program is basically doing anyway, so you may be able to just copy paste the contents of disc2/disc3 etc. into the WoW folder that has been created from the first install disc

---

### Post by diskopanda on 2010-12-19
The only files that are in the discs are "Installer.exe (i double click it in disc 2 but it wont change anything)", "Installer Tome.mpq" "Autorun.inf" and "Installer.ico"

I extracted them and double clicked like a moron, doesen't work.

I have to some way register that the disc (2,3,4) is actually in the system, it just wont register it to the installer...

---

### Post by diskopanda on 2010-12-19
bump!

---

### Post by diskopanda on 2010-12-19
lock this thread please.

---

