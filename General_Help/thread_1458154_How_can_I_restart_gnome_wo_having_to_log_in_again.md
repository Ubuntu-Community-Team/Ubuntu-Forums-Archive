---
title: "How can I restart gnome w/o having to log in again?"
date: 2010-04-19
forum: General Help
---

### Post by JustSomeGuy805 on 2010-04-19
Does anyone know how I can restart gnome from the command line without having to log in again(as in selecting a user and typing in the password)?  I've tried using '/etc/init.d/gdm restart' and that tells me to use 'service gdm restart' but that forces me to log back in again.

I wouldn't mind having to start gnome using startx, then logout of x and startx again but I need to automate the process. I can't figure it out because anything I launch withing gnome gets killed when gnome goes down so that the startx part doesn't get executed. I'm using Ubuntu 9.10, can anyone help?

---

### Post by lensman3 on 2010-04-19
You might try <CNTL-ALT-BACKSPACE>.  This will kill the X11 server, and normally will restart the server.  If you login at run-level 3 and then start X11 (startx), then later do the Cntl-Alt-backspace, you don't have to log back in.  But you have to restart all the applications.

I don't think there is a "kill -HUP" for the server.

---

### Post by aysiu on 2010-04-19
I don't think it can be done.

Restarting GDM will take you back to the login screen, as will Control-Alt-Backspace (if you re-enable it).

---

### Post by nothingspecial on 2010-04-19
What is the underlying problem?

In that, why do you need to restart gnome without logging out......which I don`t know how to do.... but there maybe some other solution.

---

### Post by shaka_zulu on 2010-04-19
I am also quite sure that is not possible. Once you restart X you will be prompted to log in screen.

---

### Post by happyhamster on 2010-04-19
You could try setting an automatic login (System->Administration->Login Screen), and then restarting gdm.

---

### Post by cdaringe on 2010-04-19
nah, unfortunately that doesn't work*
:(

---

### Post by JustSomeGuy805 on 2010-04-21
> **nothingspecial said:**
> What is the underlying problem?

In that, why do you need to restart gnome without logging out......which I don`t know how to do.... but there maybe some other solution.

I needed to find an easy way for a user to change the system language.  I wanted them to just click on a launcher and have it change the language of the system so that even the panels were that language. The users are allowed to use the computer but are not allowed any passwords. Thats why I needed to restart gnome without having to log in again. The only way I know how to do that is by changing the /etc/default/locale value to the language I wanted and then restarting X.  I figured out how to do it, although it was very tricky.

Thanks for all the replies though

---

### Post by aysiu on 2010-04-21
How about restarting the Gnome Panel? ```
killall gnome-panel
```

---

### Post by JustSomeGuy805 on 2010-04-21
> **aysiu said:**
> How about restarting the Gnome Panel? ```
killall gnome-panel
```

I tried that but gnome-panel is just the gnome-panel, not too many things dependent upon that except for like 3 applets.  I guess it gets its locale values from its  existing parent gnome session so that killall gnome-panel doesn't change the language anyways.  Thanks for the reply though.

---

### Post by phil_websurfer on 2010-12-28
If you have all running smoothly (not freezed) this have worked for me:

```

gnome-panel --replace &
nautilus -q; sleep 1; nautilus &

```

But if nautilus or gnome-panel are freezed this might work:
```

killall -9 gnome-panel
gnome-panel &
killall -9 nautilus
nautilus &

```

Good luck ;)

---

