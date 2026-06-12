---
title: "Newbie installation .. getting laserjet 2100 to connect"
date: 2011-03-15
forum: General Help
---

### Post by dragonfly41 on 2011-03-15
[SIZE=2]I'm trying to connect Ubuntu (wubi installation on Windows) to an HP LaserJet 2100M printer via a USB cable which worked on Vista (I'm migrating away from Vista into Ubuntu).[/SIZE]
 
  [SIZE=2]System > Administration > Printing  .. I could not see or add any printer.[/SIZE]
 
 [SIZE=2]I searched around and followed these instructions ..[/SIZE][SIZE=2]
[/SIZE] 
 [B][SIZE=2]How to Install HP Printer Driver onto Ubuntu 10.10[/SIZE]
[/B]  
  [SIZE=2][http://www.downloadatoz.com/driver/articles/how-to-install-hp-printer-driver-onto-ubuntu-10-10.html](http://www.downloadatoz.com/driver/articles/how-to-install-hp-printer-driver-onto-ubuntu-10-10.html)[/SIZE]
 [SIZE=2]
[/SIZE] 
 [SIZE=2]$ dpkg -l hplip[/SIZE]
 
 [SIZE=2]shows ...[/SIZE][SIZE=2]
[/SIZE] 
 [SIZE=2]rc  hplip          3.10.6-1ubuntu HP Linux Printing and Imaging System (HPLIP)[/SIZE]
 
 [SIZE=2]I downloaded hplip-3.11.1.run[/SIZE]
 [SIZE=2]but in following installation instructions I think I may have needlessly removed a previously installed hplip driver ..3.10.6 .. and various dependencies were loaded with these errors ..[/SIZE] 
 [SIZE=2]
[/SIZE] 
 [SIZE=2][COLOR=Navy]warning: HPLIP removal failed. The previous install may have been installed using a tarball or this installer. [/COLOR][/SIZE]
 [SIZE=2][COLOR=Navy]warning: Continuing to run installer - this installation should overwrite the previous one. [/COLOR][/SIZE]
 [SIZE=2][COLOR=Navy]warning: An optional dependency 'xsane (xsane - Graphical scanner frontend for SANE)' is still missing. [/COLOR][/SIZE]
 [SIZE=2][COLOR=Navy]warning: Some features may not function as expected. [/COLOR][/SIZE]
 [SIZE=2]
[/SIZE] 
  [SIZE=2]Now when I go to System > Administration > Printing[/SIZE][SIZE=2]
[/SIZE] 
 [SIZE=2]in troubleshooting there is &#8220;no connection to CUPS server&#8221;.  The "Add" button is no longer green as before I started dabbling.  No discovered printers.
[/SIZE]
[SIZE=2]How do I start again to get HP LaserJet 2100M connected (USB cable) .. and printing?[/SIZE]

---

### Post by dragonfly41 on 2011-03-15
[SIZE=2]I've solved my problem thanks to this thread[/SIZE]
 
 [SIZE=2][http://ubuntuforums.org/showthread.php?t=1475058&highlight=CUPS+services](http://ubuntuforums.org/showthread.php?t=1475058&highlight=CUPS+services)[/SIZE]
 
 [SIZE=2]$ sudo aa-complain cupsd[/SIZE]
 [SIZE=2]$ sudo /etc/init.d/cups restart[/SIZE][SIZE=2]
[/SIZE] 
 [SIZE=2]After this I could use System > Administration > Printing[/SIZE][SIZE=2]
[/SIZE] 
 [SIZE=2]Add Printer[/SIZE]
[SIZE=2]saw "unknown printer" listed [/SIZE] 
  [SIZE=2]select LaserJet 2100M[/SIZE]
 
 [SIZE=2]I saw that there were two sets of drivers .. 3.10.6.1 and 3.11.1 .. in a list [/SIZE] 
 
 [SIZE=2]I pointed to hpcups 3.10.6[/SIZE]
 
 [SIZE=2]and this got the printer to work!   Printed a test page.
[/SIZE]
 [SIZE=2]So my earlier installation of 3.11.1 was needless.[/SIZE]

---

