---
title: "can't load gnome after bootup"
date: 2006-02-23
forum: General Help
---

### Post by raul on 2006-02-23
hi all

i hibernated my computer (saving my session), and it froze when i restarted it. i turned it off manually, and turned it back on. it seemed to be booting up normally, but instead of loading the gnome login screen it went onto a terminal-like environment. i was able to enter my  user name and password there, and to log in as i would normally do in a terminal (user@computer: enter command).  i haven't managed to load gnome from there though; i can't access the desktop. i've restarted the computer manually a few times (i don't know what the command is for restart or shutdown), but it always boots  back into the terminal-like screen. any help on how to get back to gnome would be much appreciated.

---

### Post by joshuapurcell on 2006-02-23
You can try to start the gdm service manually by running this command:```
sudo /etc/init.d/gdm start
```That should also take you to the terminal located at F7 (where X windows likes to run). If X doesn't start up the right way, then press Ctrl-Alt-F1 to go back to the original terminal, and see if there are any errors printed. If so, post your errors here.

---

### Post by raul on 2006-02-24
thanks for replying. i just tried to do what you said. nothing happened when i entered the command; it just went onto the next command line in the terminal.  and nothing happened either when i entered crtl+alt+f1...

---

### Post by joshuapurcell on 2006-02-24
What happens when you give this command:```
startx
```

---

### Post by raul on 2006-02-24
it works! i'm in now! 

thanks a bunch!

btw, i was reading that other people have had trouble hibernating... i guess i should avoid it from now on.

---

### Post by nanotube on 2006-02-24
and by the way, to shut down from command line, issue "sudo shutdown -h now"
to reboot, its "sudo shutdown -r now"

for more options on the shutdown command, see "man shutdown". :)

just in case you ever end up in commandline mode again. :)

---

### Post by raul on 2006-02-24
cool, thanks; i was actually going to ask about that.

---

