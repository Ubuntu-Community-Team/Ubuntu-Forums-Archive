---
title: "Is WINE Needed?"
date: 2010-07-12
forum: General Help
---

### Post by Vapourstreak on 2010-07-12
Just a quick question.  Is WINE able to run Windows programs from other partitons? 

You see, I've installed Ubuntu onto a 4gb USB Drive, and I need as much space as I can.  I'm just wondering, if I plug it and boot it from another person's Windows computer, will I be able to run the programs located on their Windows hard drive?

One more thing, I'm using Ext4 on the USB right now to run Ubuntu, but I heard it shortens the lifespan.  So what do I do?  I've tried formatting it to Ext2 before install, but it didn't work for me.

---

### Post by Woody1987 on 2010-07-12
It can run programs off other partitions, although not always successfully. It depends how the partition is formatted. If it is NTFS as i suspect it should work most of the time. As for Ext4, i have no problems using Ext4 on USB, but if you are worried, try Ext3, not 2 as it is known to have stability problems.

---

### Post by Vapourstreak on 2010-07-12
Kay well, I tried running hl2.exe from a NTFS partition to run CS:S (Digital Zone Torrented.) And it had the wait cursor for a bit, then went back to the normal cursor.  Nothing ever launched, though.

So it's not too bad, the shortened lifespan?  It will be constantly reading and writing for however long the computer is on.  How long have you been running Ubuntu off the USB?

---

### Post by gradinaruvasile on 2010-07-12
Wine has its own configuration settings in the ~/.wine folder. It has a registry and all there (program files folder and such).

IT IS NOT USING ANYTHING FROM THE WINDOWS SETTINGS if you have Windows on another partition. So dont just expect that it will magically load the installed Windows registry and use it. It doesnt do that.
Why? Because IT IS NOT WINDOWS. It IS a compatibility layer that translates (some) Windows functions to Linux functions. So it has its own configurations and registry.

You have to install the programs under Wine in order to create its own registry key sets.

When you launch a windows program that is not installed in this environment it is normal not to run unless it doesnt need anything specific from the registry (small programs mainly and cracked programs/games).
Also you have to set up your drives from winecfg (autodetect works great). Otherwise the other partitions will be unavailable to Wine and thus you will not be able to launch anything from them.
In case of a program that doesnt run on double-click, open a terminal in that folder and try to launch that program with:

wine progname

The names are case sensitive, unlike Windows. Surely some error/missing dll will pop up and you can google it (i solved mny problems like this).

---

### Post by Vapourstreak on 2010-07-12
Yeah, I know all about the registry..

The DigitalZone version of CS:S doesn't need steam or registry entries, that's why I could freely  transfer the program folder from computer to computer without breaking the game.

---

