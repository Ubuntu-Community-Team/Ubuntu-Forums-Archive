---
title: "Screen freezes during login"
date: 2011-03-03
forum: General Help
---

### Post by nsquaredude on 2011-03-03
I have installed ubuntu 10.10 on my dell studio 15 laptop with core i5 processor and ati graphic card. While login into the system, sometimes the screen freezes. I have to shut down the laptop by pressing the power button. This problem usually occurs 2-3 times while log in or never if i'm lucky.

---

### Post by LinuxH4x0r on 2011-03-03
tryed updating the ram?

---

### Post by oliwek on 2011-03-03
try without wifi (disconnect your wlan card) and see if your laptop freezes (of course you have no internet if you have no ethernet possibility), then tell us...

see also this reply from [http://askubuntu.com/questions/19538/how-do-you-diagnose-constant-crashing-issues](http://askubuntu.com/questions/19538/how-do-you-diagnose-constant-crashing-issues)
[COLOR="Blue"]> 
When i have a problem like that i normally do the following:

In the grub menu select the RECOVERY MODE
When the blue menu appears select to run as root in the terminal/shell
When you login in the shell as root type dmesg to see any problem of devices when you were loading the system.
To see a more specific summary type ```
cat /var/log/syslog
``` which will show you EVERYTHING when you were loading the system.
You can add | less to the command above like this ```
cat /var/log/syslog | less
``` so it shows you the info and you press down or up to see the output and press Q to quit.
If everything shows good type startx which will start the gui desktop for gnome where the actual problem appears to be.
startx will mention what problem he is having in the terminal so you can fix it.
If by some chance the computer gets stuck when loading startx press CTRL+ALT+F2 or CTRL+ALT+F3 (OR F4,F5,F6) and type in your login user and password. Then type ```
ps -ex
``` so you can see the ID for gdm process or ```
startx
``` and just ```
killall -9 startx
``` / ```
killall -9 gdm
``` or ```
kill -9 ID
``` or whatever process it was loaded when you started startx. This way you will the process and the system is not stuck anymore.
With that you have dmesg, cat /var/log/syslog and startx to see where the problem is. At least for a quick look.

Let me know if it helps somehow. This is just a quick check for problems.[/COLOR]

---

