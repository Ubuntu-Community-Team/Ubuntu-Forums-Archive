---
title: "Ubuntu 10.04 install bug &quot;running dpkg&quot; at 95%"
date: 2010-04-30
forum: General Help
---

### Post by Black Bart on 2010-04-30
I've downloaded official release 10.04 i386 Desktop DVD from Ubuntu site and tried to install.

From 0% to 95% installation is about 20 minutes. At 95% "running dpkg" starts and n0thing happens about one hour. I've tried two times but without success to install yesterday's release of 10.04.

(By the way, Server edition CD is okay.)

What's up, dudes? How to install 10.04?

---

### Post by Yeso on 2010-05-01
I have this problem too :-(
Loading of CPU is about 90% by install.py process...

---

### Post by arngrimur on 2010-05-30
Any solution to this.  I'm experiencing the same problem, dpkg fails during installation with error code 1. 

After restart I'm able to drop in to a prompt but no GUI. It hangs on the splash screen.

Computer is a Mac2-1 (Intel), triple boot
[Solved] 
Reinstallatin of system without my old /usr/local

---

### Post by mvidberg on 2010-06-02
I also had this same issue on 4 computers I recently installed on with the same ubuntu 10.04 32bit DVD.  Was doing a complete install (overwrite everything on the HD) on all 4.  Each got stuck at 95% but I managed to get it installed.  

At 95%, if you are in live mode and doing the install from there, just cancel it.  If you are in boot installation mode, press CTRL-F1 to get the shell and then type "shutdown -r now".  Now boot ubuntu from the HD and it looks ok until you try to install something at which point it complains.  Open a terminal and type "sudo dpkg --configure -a" and then go to your administration menu and select "Software sources". Uncheck the CD or DVD rom and click close.  Not sure why I had to remove the DVD from sources but it seems that it kept thinking it wasn't in the tray even though it was.  Then go back to terminal and type "sudo apt-get install -f".  Then you can run the Update Manager and install the latest patches. 

So is this just a wacky version of the install media that we are all using here?  I can't imagine 10.04 is this annoying to install for everybody or we'd be hearing a lot more about it?

---

### Post by arngrimur on 2010-06-03
Thanks for the reply but this would not have solved my errors. 
First of all I was not able to start X-server so all references to 'Adminstration panel' and other gui is applicable, although everything you can do in a gui you can do in a terminal. 

I basicly did everything you suggested except droping in to a shell after 95% and restart the computer.

In my case I wanted to keep my old partition of /usr/local (contained my subversion repository and other important stuff). The problem was that it also contained an old  version of gtk. This version was probably used when trying to install programs with depencies to GTK so the installation failed.

A reinstallation of 10.04 where I created a new partition for /usr/local fixed the problem. It probably had been enough to remove the old GTK files.

---

### Post by mvidberg on 2010-06-04
So does this mean that if your computer has an older version of Linux on it (like the 4 I installed on), the installation fails?  I chose to use the entire disk for install, wouldn't it format or delete the HD partitions?  I can understand why you had the issue as you opted to keep your /usr/ dir but don't understand why I had the problem.

---

### Post by 6DeXTeR9 on 2010-08-03
[SIZE=3]I had the same problem and solved it this way.
[/SIZE][SIZE=3]you enter the BIOS (depending on the motherboard) and look for "Plug and Play" you put "enable" and is already
I  hope it helps you too :D[/SIZE]

---

### Post by fetchdesigns on 2011-08-18
I had this same issue when trying to install 10.04 on a virtual machine using VirtualBox.  I tried twice with the same issue and then I tried increasing my storage space from 8GB to 10GB and the next time I tried to install it worked!

---

