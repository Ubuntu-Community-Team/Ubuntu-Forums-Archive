---
title: "World of Warcraft on Ubuntu 9.10"
date: 2009-11-15
forum: General Help
---

### Post by Zweibart on 2009-11-15
I used Ubuntu 8.04 for 3 months and upgraded to 9.10 today. I am very impressed about how everything runs smoother, but i can't figure out on how to make WoW run now. It worked under 8.04.

I have:

[LIST=1]
[*]Installed 9.10 and did run an update immediately afterwards
[*]Installed the newest NVIDIA-driver (190).
[*]Installed the newest version of Wine (1.2).
[*]Downloaded the MS Truetype-fonts.
[*]Checked that direct rendering was turned on (see below)
[/LIST]
I then browsed the Wine-directory and was absolutely sure that the previous failing installations of WoW were gone, and installed it again using original CDs. 

When starting the game from Wine -> Programs -> World of Warcraft, i see that the status bar at the bottom shows a new task saying "Starting World of Warcraft" and then.... nothing. No error messages or system freeze, just plain nothing.

The task disappears and no World of Warcraft. Any ideas? 
Thx for any help.

Zweibart

[COLOR=DimGray]Comments:
On point two i used the following description that explains how to update the drivers:
[http://www.ubuntugeek.com/install-nvidia-graphics-drivers-190-42-in-ubuntu-karmicjauntyintrepidhardy.html](http://www.ubuntugeek.com/install-nvidia-graphics-drivers-190-42-in-ubuntu-karmicjauntyintrepidhardy.html)

On point three i used the following thread that explains how to use Synaptic to update Wine. This also fixed sound problems in Spotify:
[http://http://ubuntuforums.org/showthread.php?t=1304988]("http://http//ubuntuforums.org/showthread.php?t=1304988")

In point four i used the following thread that explains how to correct a line in a file.
[https://bugs.launchpad.net/ubuntu/+source/msttcorefonts/+bug/464422](https://bugs.launchpad.net/ubuntu/+source/msttcorefonts/+bug/464422))

In point five i used commands from the following document:
[https://help.ubuntu.com/community/WorldofWarcraft#Original%20WoW]("https://help.ubuntu.com/community/WorldofWarcraft#Original%20WoW")[/COLOR]

---

### Post by Sin@Sin-Sacrifice on 2009-11-15
It looks like wow support has gotten crappy since wine 1.1.32. You might want to downgrade it back to 1.1.31 where it still has a "platinum" rating in the wine appdb [http://appdb.winehq.org/objectManager.php?sClass=version&iId=17421](http://appdb.winehq.org/objectManager.php?sClass=version&iId=17421)

I don't even see any testing on versions higher than 1.1.32. Although... the rating is "gold" in that version. Hope this helps.

---

### Post by Zmrlzna on 2009-11-16
Hi there,

I'm also getting some problems trying to run WoW on Wine (version 1.0.1), I get this error:

[I]This application has encountered a critical error:
ERROR #132 (0x85100084) Fatal Exception
Program:  Y:\Windows\World of Warcraft\Wow.exe
Exception:  0xC0000005 (ACCES_VIOLATION) at 0...
The instruction at "0x616D2450" referenced memory at "0...
The memory could not be "read".[/I]

Some idea? Thanks.

---

### Post by ArcaVex on 2009-11-16
I would get an older version of WINE.  Also install PlayOnLinux, this may help for an easier install

---

### Post by Zweibart on 2009-11-17
_Status:_ Partially solved
I have found a solution, but i'm not quite satisfied yet. The game runs with a lot of tricks, so i'll be trying easier ways tomorrow.

I've even compiled my own version of Wine, but being a total Linux noob, the compilation lacked support for about anything. (Documented it, but when i read it, i just laughed). So i went back to scratch and tried the suggestion of installing an older version of Wine. 

Found the web page:
[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

I removed everything and then downloaded and installed version 1.1.31.deb. WoW installed fine, but when starting WoW (for update) from Programs->Wine->Programs, error messages popped up all over the place. If did NOT touch the error messages, WoW actually started and downloaded and installed the updates.

Trying to start WoW from Programs -> Wine -> Programs -> World of Warcraft then led to the known error:

Error when changing to folder <</home/<username>/.wine/dosdevices/c:/Program Files/Worldof Warcraft>> (Permission denied).

I found the solution to be to change the permissions by opening a terminal window and running the command:
chmod 777 'home/<username>/dosdevices/c:/Program Files/World of Warcraft/'

I then made the directory visible by selecting menu choice Places -> Home folder. In the file browser (which i now know is called Nautilus), i selected menu choice Edit->Preferences and ticked "Show hidden files...". 

I then navigated to .wine/dosdevices/c:/Program files/World of Warcraft and started WoW. exe manually.

World of Warcarft started without any error messages.

---

