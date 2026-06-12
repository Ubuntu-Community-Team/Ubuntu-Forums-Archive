---
title: "Two lots of X running at once. Is it possible?"
date: 2006-02-17
forum: General Help
---

### Post by renzokuken on 2006-02-17
Is it possible to have X running on two terminals simultaneously.

I would love to have Gnome running on Ctrl+Alt+F7 with my username......and to have Fluxbox running on Ctrl+Alt+F6 under another username.

Is this possible in any way? I have tried running "startx" and "startfluxbox" from the text based terminal in Ctrl+Alt+F6 (while Gnome is running on F7) but get some message about removing a lock.....

thanks

---

### Post by heimo on 2006-02-17
```
startx -- :1
```****[http://gd.tuwien.ac.at/opsys/linux/LinuxGuide/linux-X-multiple.html](http://gd.tuwien.ac.at/opsys/linux/LinuxGuide/linux-X-multiple.html)
[http://www.tuxfiles.org/linuxhelp/multiple-x.html](http://www.tuxfiles.org/linuxhelp/multiple-x.html)

---

### Post by renzokuken on 2006-02-17
thanks.....i can get it to startx now, but the display is all screwed up. i can tell its gnome that starts up but only just. any idea how to make it a usable desktop.

i think its a grafix problem (i have a radeon 9200)

---

### Post by minisori on 2006-02-17
I dont know what is the bin for fluxbox but i suposse its just the name so try this.

sudo X :1 -ac & DISPLAY=:1 fluxbox

---

### Post by renzokuken on 2006-02-17
ok, i tried that but got the following error

Failed to open file (/usr/share/fluxbox/nls/en_GB/fluxbox.cat) for translation, using default messages.
Error: Couldnt connect to XServer

[1]+ stopped    sudo X :1 -ac

any ideas, left me clueless!!

---

### Post by minisori on 2006-02-19
Hmm i dont know if its a sudo bug, but when u do sudo X ... it doesnt ask for the pass it just ignore the sudo, try first doing sudo ls for example so it ask for your pass, and after you can type "sudo X...." and it would work i guess.

---

### Post by renzokuken on 2006-02-19
sweet. one step closer.

i can now get into fluxbox with that but the screen is still screwed up (see attachment). this is what happened to the screen when i got into gnome on the second x-session as well.

i'm pretty sure its a grafix driver/card issue....so if anyone has any ideas..... >_<

---

### Post by dcstar on 2006-02-19
[QUOTE=renzokuken]Is it possible to have X running on two terminals simultaneously.

I would love to have Gnome running on Ctrl+Alt+F7 with my username......and to have Fluxbox running on Ctrl+Alt+F6 under another username.
......[/QUOTE]
Applications-System Tools-New Login

The command is actually "gdmflexiserver" - you can do exactly what you ask for.

---

### Post by renzokuken on 2006-02-19
holy c**p, so you can. thanks

however, i still get the crappy video, all jaggedy like in the attachment above.

is the "new login" trying to use my fglrx driver or some other one?

---

### Post by dcstar on 2006-02-20
[QUOTE=renzokuken]holy c**p, so you can. thanks

however, i still get the crappy video, all jaggedy like in the attachment above.

is the "new login" trying to use my fglrx driver or some other one?[/QUOTE]
It is whatever your xorg.conf file is telling it to use.

You screen looks like too high a res/refresh combo for the monitor to handle, do:

sudo dpkg-reconfigure xserver-xorg

And let it find the maximums your screen can handle.

---

### Post by renzokuken on 2006-02-20
so if its using the same xorg.conf, how come my the main xsession works perfedtly, and the second one doesnt.......there shouldnt be any difference should there?

---

