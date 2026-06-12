---
title: "how to stop a daemon?"
date: 2009-09-02
forum: General Help
---

### Post by diafanos on 2009-09-02
Hello everybody,

I'm experiencing the following problem. Some days ago, I installed a program named 'unclutter' (It makes an idle cursor disappear after a specific amount of time).
I executed once in the terminal, and since then it runs at startup.
I searched for it in 'Startup applications' in order to remove it, but in vain. There isn't there, so I have to execute a 'killall unclutter' command, whenever I log in to ubuntu. And it's really frustrating :(

Doesn't anyone know how can I make it stop executed by default, when I log in to the system (I don't want to uninstall it, because it's quite useful sometimes)? 

Or even better, does anyone know, which configuration file (?) "holds" the startup services/daemons?

Thanks in advance.

---

### Post by VCoolio on 2009-09-02
Check if it is in /home/user/.config/autostart (user configuration folder for startup apps). 
If not, check if it is in /etc/xdg/autostart (system folder for startup apps). If it is, either remove it (requires root permission) or copy to the mentioned user folder, open in text editor and add a line "GNOME-Autostart-enabled=false" (or change the line where this says "true").

---

### Post by diafanos on 2009-09-02
Thanks for your answer VCoolio, but there is nothing in these 2 locations, and your third suggestion, didn't work, either :(

---

### Post by Whiffle on 2009-09-02
Have a look at /etc/X11/Xsession.d/90unclutter

Thats a file that is installed when you install the program, and I bet thats where it starts from.

---

### Post by diafanos on 2009-09-02
> **Whiffle said:**
> Have a look at /etc/X11/Xsession.d/90unclutter

Thats a file that is installed when you install the program, and I bet thats where it starts from.


You just scored a bull's eye, Whiffle...=D>=D>=D>
Thanks a lot...

---

### Post by Whiffle on 2009-09-02
> **diafanos said:**
> You just scored a bull's eye, Whiffle...=D>=D>=D>
Thanks a lot...

No problem.  Here's the fancy trick I used:

Went to packages.ubuntu.com

Searched for unclutter

Looked at the file list for the package

and found that file, saw it went in Xsessions, and said...AH HA!

:)

---

### Post by diafanos on 2009-09-02
You're right. It didn't cross my mind to look into synaptic, in order to see where it is get installed, because I thought that this behaviour started as soon as I executed it for the first time.
Instead, it started just when I installed it. 

Quite strange, isn't?
Thanks, anyway...

---

