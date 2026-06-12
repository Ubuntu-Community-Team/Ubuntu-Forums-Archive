---
title: "execute wow from command line"
date: 2011-09-08
forum: General Help
---

### Post by Arminius on 2011-09-08
I'm trying to run world of warcraft from the command line, but don't know the commands to get ```
/home/user/.wine/drive_c/Program Files/World of Warcraft/wow.exe
``` to run.
just keeps returning no such directory exisits, even though it does

---

### Post by haqking on 2011-09-08
> **Arminius said:**
> I'm trying to run world of warcraft from the command line, but don't know the commands to get ```
/home/user/.wine/drive_c/Program Files/World of Warcraft/wow.exe
``` to run.
just keeps returning no such directory exisits, even though it does


not a wow or wine user myself but you might want to read this WOW how to thread [http://ubuntuforums.org/showthread.php?t=579378&highlight=world+warcraft](http://ubuntuforums.org/showthread.php?t=579378&highlight=world+warcraft)

shouldnt it be something like this

[SIZE=2] wine "C:\Program Files\World of Warcraft\WoW.exe"[/SIZE]

---

### Post by ajgreeny on 2011-09-08
I have no idea what the executable for wow is but if there are spaces in it, use quotation marks around the full pathway, or use a backslash before the space to escape any spaces in the pathway or file name and also use wine as the program to run the executable, eg,[FONT=monospace]
wine "[/FONT]/home/user/.wine/drive_c/Program Files/World of Warcraft/wow.exe"
or[FONT=monospace]
wine [/FONT]/home/user/.wine/drive_c/Program Files/World\ of\ Warcraft/wow.exe

---

