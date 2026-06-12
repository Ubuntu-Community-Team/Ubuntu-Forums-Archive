---
title: "Turning off X Terminal"
date: 2006-03-29
forum: General Help
---

### Post by StevenB on 2006-03-29
I am running a really old (Pentium 133, maybe?) computer as an X terminal.  It's running pretty well, but I don't have a good way to turn it off.  I am using an XDMCP chooser on the terminal.  I currently have to click cancel on the chooser, and during the short time the terminal flickers up, try to log in and kill gdm.  Is there some way to tell the computer (not the X server) to turn off without doing this?
Thanks!

---

### Post by Video Toaster on 2006-03-29
I guess you could try shutting down the computer in a terminal window using sudo while logged on in Gnome.  I've been able to successfully reboot through XDMCP by doing that.  I believe the command is halt, but I'm not sure.

---

### Post by StevenB on 2006-03-29
If I log into GNOME with a terminal, and type "sudo poweroff", it turns off the X server, since that's what the the command terminal is running on.  Is there a different command (halt?) that turns off the X terminal?
Thanks for the quick response!

---

### Post by Video Toaster on 2006-03-29
[QUOTE=StevenB]If I log into GNOME with a terminal, and type "sudo poweroff", it turns off the X server, since that's what the the command terminal is running on.  Is there a different command (halt?) that turns off the X terminal?
Thanks for the quick response![/QUOTE]

Hmm... I just couldn't remember the poweroff command :D  I'm pretty sure I was able to reboot remotely using "sudo reboot" about a week ago, but I've never actually tried shutting down remotely.

---

### Post by StevenB on 2006-03-30
sudo reboot turns off the server as well.
Do I need set up the X terminal as a server so it can log onto itself?  Are there other tricks I need to do with gdm.conf to make this work?

---

### Post by Video Toaster on 2006-03-30
[QUOTE=StevenB]sudo reboot turns off the server as well.
Do I need set up the X terminal as a server so it can log onto itself?  Are there other tricks I need to do with gdm.conf to make this work?[/QUOTE]
I just tried "sudo halt" in a terminal window during an XDMCP session and the system immediately shut down.  Completely.  Have you tried that yet?

(I'd also like to note that I tried it on Dapper Drake... I don't think it should make a difference, though.)

EDIT:  I just tried "sudo poweroff" as well and that also worked for me.  I'm not quite sure what's going on for you, then.  I'm even able to see the shutdown messages locally on the Ubuntu machine (If you don't see them, press CTRL+ALT+F7 to switch to TTY7).

Also, I don't think this should make a difference either, but I'm using cygwin/X for XDMCP.

---

### Post by IYY on 2006-03-30
I always used 'sudo shutdown -h now'

---

### Post by StevenB on 2006-03-31
When I log in on the X terminal (on the old computer), I am logged in as "steven@amd64"  So, when I type poweroff, halt, reboot, etc, it turns off the "amd64", not the old computer I am actually on.  How do your setups work, and what am I doing differently?
Thanks!

---

### Post by patrixl on 2006-03-31
You need to be logged in on the local machine in order to issue a shutdown or reboot command on that machine.

A few ways you can do this:

press ctrl-alt-f1: this will get you to the  text console, where you can login and execute commands on the local machine

logout and do a graphical login on the local machine through gdm : meh, first method is faster though ;)

open a gnome-terminal window, ssh to the old machine and issue the shutdown/reboot command there.

Patrix.

---

