---
title: "Ubuntu 11.04 freezes doing nothing"
date: 2011-06-07
forum: General Help
---

### Post by turbocookie on 2011-06-07
Hey, i recently added Ubuntu 11.04 64bit and i have it on dual boot with winXP.

After running from anywhere between 15 mins and a few hours, it will freeze everything without warning, except the mouse, but all input is unresponsive.

I am new to ubuntu and not very experienced. Id like to know why i am having this problem, the only way i can bring it out of a freeze is to reboot. Please help!

---

### Post by kpholmes on 2011-06-07
next time ubuntu freezes, try pressing crtl + alt + f1. that will close the windows manager and bring you to a command line. login using your username and password. from there you can do 3 things. you could restart the computer properly by typing into the command line "sudo reboot". "sudo" is superuser, or the admin of the machine in other words. the superuser password in ubuntu is the same password you use for your username by default in ubuntu. you normally only use it when changing system settings and installing/upgrading. typing "sudo halt" will turn the computer off. next option is to try and restart your window manager, you can do that on the command line after logging in and typing in "sudo /etc/init.d/gdm restart". if you want to go further and troubleshoot the problem you can try the next step, this option would be to check the system logs to try and figure out whats happening thats causing the computer to freeze. you can get to the system logs located at /var/log/ by typing in "cd /var/log" into the command line. once there you can type "nano syslog", or "nano + the name of the log file" to view the log file, press "control + v" to scroll down and see the most recent input. press "control + x" to exit. i would also recommend checking the Xorg.0.log file in that same directory. thats just a start to troubleshooting but it will put you into the right direction. if you see something interesting in your log files post them back on the board and the community might be able to be of further help.

---

