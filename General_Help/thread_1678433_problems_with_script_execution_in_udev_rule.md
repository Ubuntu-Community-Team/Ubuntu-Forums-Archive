---
title: "problems with script execution in udev rule"
date: 2011-01-30
forum: General Help
---

### Post by phanie on 2011-01-30
Good day! 

After some series of tests, I was able to make my script working whenever I insert any usb flash drive on my computer. After the script has been executed, it produced a text file where there is a written word "successful" inside it. (BTW, the script is just for testing to validate if the udev rule that I've written is working)

When I changed its code to a script that launches a command that locks the screen, it suddenly stopped working. 
I used gnome-screensaver-command -l inside the script.
The script was running the way it supposed to be by running it using the terminal.

My udev rule is:
```
SUBSYSTEMS=="usb", KERNEL=="sd??", ACTION=="add", PROGRAM+="/home/babyjessie/lock", MODE="0777"
```

and using udevadm test, I was able to see this message:
```
Failed to connect to the D-BUS daemon: /bin/dbus-launch terminated abnormally with the following error: Autolaunch error: X11 initialization failed.'
```

What's D-Bus daemon, how to connect to it and how to make my script working?

Please do help me

Thank you!

---

### Post by AlphaLexman on 2011-01-30
See [What is D-bus]("http://www.freedesktop.org/wiki/Software/dbus") for more information about the big picture.

---

