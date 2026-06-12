---
title: "How do I add my windows hard drive in the wine configuration."
date: 2009-08-13
forum: General Help
---

### Post by rhythmiccycle on 2009-08-13
i want to run dreamweaver, that is installed in my xp paptiton (i have a dual boot with xp and ubuntu 9)

i read this in an archive

> many windows programs require the use of different registry entries. When the program is installed, the appropriate registry entry is created or updated. Trying to run this program in wine will most likely not work, because the program's registry data is in your windows install, and wine is reading a registry file in your ~/.wine directory.

then the reply was given

> I've had luck running spore from a windows installation. Didn't have any registry problems what-so-ever. I just had to add my windows hard drive in the wine configuration.

Most games/applications should technically work from a windows partition/hard-drive if they work on wine anyway. The only problems you could come across is with registry but you can try exporting windows registry entries then importing them to the wine registry and changing the paths to point to the correct locations (depending on what you set the drive letter for the windows installation). However, this would be quite tedious. ;)

but how is this done?

i've been googleing and reading wineHQ but i can't find anything about adding windows partition registry to wine.

---

### Post by Ranax on 2009-08-13
Runing programs from your Windows partition/harddrive with Wine is a very bad idea! It can cause errors with Windows itself and with Wine!

Don't do it!

---

