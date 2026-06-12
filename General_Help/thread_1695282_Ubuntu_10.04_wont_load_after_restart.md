---
title: "Ubuntu 10.04 wont load after restart"
date: 2011-02-25
forum: General Help
---

### Post by eatsleepfolk on 2011-02-25
Hello all,

Everything was fine until I tried to open Jokosher and it crashed the system. So I force restarted (with the power button)and now Ubuntu will not make it past the splash screen (with the five blinking lights). It's not frozen persay, as in the lights are still blinking as though it's loading but it simply wont load. I'm a total noob and any help would be greatly appreciated.

---

### Post by Foxheadz on 2011-02-25
Try right when the purple screen pops up pressing escape, this should start printing a bunch of text. Post any error messages or whatever there is when the text stops scrolling.

---

### Post by Chibi-Chibi on 2011-02-25
I have same problem. I'm using ubuntu for abotu a year but i'm still noob enough not to stop when i know i should -.-;;

Anyway i was trying to make PCSX2 work and i was trying to install stuff that was necesary according to [this guide]("http://forums.pcsx2.net/Thread-Official-English-PCSX2-configuration-guide-v0-9-7").
I came as fare as dealing with "libasound2-dev, libbz2-dev, libgl1-mesa-dev, libglew1.5-dev". When i tried to install them through systempackage it gave me errors as i had wrong versions on which the packages depended on.
If i remeber correctly i had problems with libbz2-dev and libglew1.5-dev.
Since there is game i want to try playing, of course, i've forced to change version of the pacgakes they depand on so I could install the two as well.
Doing so most options dissapeard under "Aplication" menu, i coudln't open any folders anymore i coudlln't even reset through descotpe and had to force reset as the OP did.

After that if i wanted to start normay the system opend in terminal (no splash page with blinking lights with me) so i tried with update/upgrade but it didn't help.

I though there is no point in dealing with this so i wanted to access the files only, copy them and make a freash start. As i have dual boot i tred to acces the files through windows (trying all 3 way written in [this guide]("http://www.howtoforge.com/access-linux-partitions-from-windows")) Explore2fs failed in doing anything, Ext2 Installable File System For Windows is useless and with help of DiskInternals Linux Reader i managed to copy currently most important files so i can work on them, however, even though it shows the disc is full as it should, it shows many empty folders and all in all i can copy only 23GB of files out of around 450GB that there actually are. And thats a bit to much for me to just let it go. Helping me get the files is good enough for me but restoring the system woudl be nice as well.

So following what Foxheadz said i get: (i'm typing this of the screen so some typos might be there)

> fsck from util-linux-ng 2.17.2
/dev/sda6: clean, 298854/297451522 files, 111918873/118974464 blocks
init: Faild to spawn ufw pre-start process: unable to execute: No such file or directory
init: Faild to spawn ufw post-stop process: unable to execute: No such file or directory
init: Faild to spawn network-manager main process: unable to execute: No such file or director
init: avahi-deamon main process (774) terminated with status 2
init: avahi-deamon main process ended, respawing
init: gmd main process (773) terminated with status 2
*starting AppArmor profiles
init: Faild to spawn ufw pre-start process: unable to execute: No such file or directory
init: Faild to spawn ufw post-stop process: unable to execute: No such file or directory
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox

*Setting sensors limits
 init: Faild to spawn atd main process: unable to execute: No such file or directory
 init: Faild to spawn corn main process: unable to execute: No such file or directory
 init: Faild to spawn acpid main process: unable to execute: No such file or directory
init: irqbalance main process (857) terminated with status 2
init: apport pre-start process (856) terminated with status 1
init: apport post-stop process (871) terminated iwth status 1
*Speech-dispatcher configured for user session
*Starting the Winbind deamon winbind
*Starting Common Unix Printing System: cupsd
*Enabling additional executable binary formats binfmt-support
/etc/rc2.d/SW99acpi-support: line 7: /usd/share/acpi-support/power-funcs: No such file or directory
init: tty2 main process (864) terminated iwth status 1
init: tty2main process ended, respawning

EDIT:  After installing another ubuntu on the free space i had i could access the files again.. so i guess i'm good now.

---

