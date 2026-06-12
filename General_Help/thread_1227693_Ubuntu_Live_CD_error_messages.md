---
title: "Ubuntu Live CD error messages"
date: 2009-07-30
forum: General Help
---

### Post by DHamme on 2009-07-30
Hello - 
I am new to Ubuntu, and would be grateful for your help.
Please let me explain how I got here -
 
Approximately one month ago, my apartment suffered a power failure while my computer was on.
 
I run an HP Pavillion 1220a with Windows XP service pack 3.
 
Once power was restored, I restarted this machine and got through the Windows logo page, and the screen went black but retained the mouse cursor, which is responsive.
However, the logon screen never appeared - in basic mode or in safe mode (although the 'safe mode' graphics are displayed - no logon menu or start button - just a responsive mouse cursor)
 
a helpful user in another forum pointed me toward Ubuntu, suggesting that I can retrieve my feww weeks of un-backed-up data before running my Acronis True Home Image restore files.
 
I successfully burned an Ubuntu disk on another machine and ran it on the computer in question.
 
I checked the disk for errors - no errors found
I ran a memory test for eight hours - seven passes - and no errors were found
I tried to run from the disk without installing (first menu option) and waited for approximately five minutes when the following messages appeared. I hope they might indicate the nature of the problem my machine has suffered, but we cannot discern their meaning. 
:confused:
Can you please help me? Thank you for considering this matter.
The messages are as follows:
 
Ubuntu report:
*preparing restricted drivers : okay*
*Setting the system clock :*
*starting basic networking okay*
*start jernel event manager: okay*
*loading hardware drivers...*
 
*/etc/rcS.d/S10udev: 105: usplash_write: not found*
*Segmentation fault*
*/etc/rcS.d/S10udev: 1: usplash_write: not found*
*Segmentation fault*
*Segmentation fault*
*init: rcS main process (6254) killed by SEGV signal*
*init: Unable to execute "/bin/sh" for rc-default: No such file or directory*
*init: rc-default main process (7260) terminated with staus 255*
 
I then obtained a copy of a newer version of Ubuntu 9.x, and the following messages were returned;
 
** Starting kernel event manager*
** Loading harware drivers*
*sh: can't open /etc/rcS.d/S11mountdevsubfs.sh*
*/etc/init.d/rc: 390:/etc/rcS.d/S13pcmcutils: Input/output error*
*/etc/init.d/rc: 390:/etc/rcS.d/S15module-init-tools: Input/output error*
*/etc/init.d/rc: 390:/etc/rcS.d/S17procps: Input/output error*
*sh: Can't open /etc/rcS.d/S30checkfs.sh*
*sh: Can't open /etc/rcS.d/S35 mountall.sh*
*sh: Can't open /etc/rcS.d/S36 mountall-bootclean.sh*
*/etc/init.d/rc: 390:/etc/rcS.d/S37mountoverflowtmp. Input/output error*
*/etc/init.d/rc: 390:/etc/rcS.d/S37undev-finish: Input/output error*
*/etc/init.d/rc: 390:/etc/rcS.d/S39readahead-desktop: Input/output error*
*/etc/init.d/rc: 390:/etc/rcS.d/S39ufw: Input/output error*
*/etc/init.d/rc: 390:/etc/rcS.d/S40networking: Input/output error*
*sh: Can't open /etc/rcS.d/S45mountnfs.sh*
*sh: Can't open /etc/rcS.d/S46mountnfs-bootclean.sh*
*/etc/init.d/rc: 390:/etc/rcS.d/S49console-setup: Input/output error*
*sh: Can't open /etc/rcS.d/S55bootmisc.sh*
*/etc/init.d/rc: 390:/etc/rcS.d/S55urandom: Input/output error*
*/etc/init.d/rc: 390:/etc/rcS.d/S70screen-cleanup: Input/output error*
*/etc/init.d/rc: 390:/etc/rcS.d/S70x11-common: Input/output error*
*init: rc-default main process (3327) terminated with status 127*
 
I am stuck.
 
Sincerely,
DHamme

---

### Post by virtuallinux on 2009-07-31
I'm also experiencing the same (or at least similar) errors on a Toshiba Satellite Laptop (circa 2004).  I've used the same disc before, so I'm pretty sure the disc is good.  I'll try and post more details on hardware shortly.

Anyone got answers or ideas?

---

### Post by virtuallinux on 2009-07-31
Ok, hardware details are:

Toshiba Satellite 6100
1.8Ghz Pentium 4
384MB RAM
Nvidia Chipset 
(I wish I could be more specific here, but I'm having trouble finding specs from Toshiba)

This laptop does have what seem to be overheating issues; I don't know if those relate to the errors we're seeing or not.  It's also worth noting that I can boot to other cd's successfully (INSERT, gparted).

---

### Post by virtuallinux on 2009-07-31
Geforce 4 420 Go is the video chipset.
I have actually successfully booted the cd several times, but not consistently.

---

