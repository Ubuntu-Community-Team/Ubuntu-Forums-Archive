---
title: "Running a script when the GNOME login screen displays?"
date: 2006-04-19
forum: General Help
---

### Post by LxP on 2006-04-19
Hi all,

When the GNOME login screen displays I'd like to run a script that adjusts the master volume to a sane level. (It doesn't seem that the volume can be adjusted from the login screen, and some people like to have the volume at 100% when they log out -- a nice surprise for the next person that logs in.)

Would anyone be able to offer an approach to this? (If anyone has ideas on how I'd adjust the volume via a script, that would also be quite handy.)

---

### Post by skymt on 2006-04-19
The second question is easy, so we'll start there. You probably use ALSA. If that's the case, the command to use is asound, which is a command-line mixer. See the man page for examples.

The first question is a lot tougher. It looks like the best kludge to use is to set a different X server command. Open System > Administration > Login Screen Setup; choose the XServer tab. Under "Server Definition to Modify" choose Standard. Replace the command with the path to your script (keeping the arguments the same), and apply your changes.

For your script, you'll need to set the volume, then run the X server with all the arguments your script was given. Something like: "/usr/X11R6/bin/X $@". In case you're not too familiar with Bash scripting, $@ means "every argument the script was given." This should Just Work, with any extra commands you need to run inserted cleanly in between GDM and X.

---

### Post by cskeide on 2006-04-19
I might be wrong, but wouldn't a script in /etc/init.d do the trick as well? Why run the script when GDM starts?

---

### Post by LxP on 2006-04-20
Thanks guys. Will both of these methods run the script each time the login screen is presented (i.e. each time a user logs out) or only on system startup?

---

### Post by LxP on 2006-04-24
After giving the above ideas a quick try, it seems that the script doesn't run each time the login screen appears, but rather when the computer first boots up (and only then).

Does anyone have any ideas on how to get it running every time the screen is presented? I'm planning to implement this on a PC that never gets switched off.

---

