---
title: "Help: System hangs after login"
date: 2009-09-23
forum: General Help
---

### Post by marcio_mi on 2009-09-23
Hi everybody,

I am having a problem with the system. When using my laptop today, the electricity went away, and having no battery, the computer shut down. When I tried to restart it, it went into scan disk, and found some problems. By running fcsk I replied yes when it asked me to fix some problems (I don't remember exactly which one, unfortunately). After that I rebooted the computer and new problems started.

The system boots up nicely until the login screen, but then hangs with a black screen if I log in with the normal xclient session. I can see the pointer of the mouse and can move it around, but nothing else. 

However, if I log in in the Failsafe GNOME or Failsafe Terminal, everything works fine. Do you have any idea how to solve the problem? I am quite new to Ubuntu, therefore I have no idea even where to start. I think it might be something related to the changes fcsk made, probably it's trying to read on some part of the hard disk but the data are not there.

Thanks a lot guys, any sort of help is really appreciated.

---

### Post by marcio_mi on 2009-09-23
So, thinking that it was something fsck did, I went to look for the log file in 
/var/log/fsck

however it keeps the log of only the last scan done, and I did it once more after it asked me to fix something. Do you know if previous logs are kept somewhere else?

Any other suggestion? By running my computer in Failsafe GNOME it's even hard to look for information on the web, many websites now make the browser stall.

---

### Post by marcio_mi on 2009-09-24
Sorry if I bump it up, but it seems that I haven't been still able to understand what's going on, and I need my laptop in order to work.

after login, there must be a startup script that says which software to load and other stuff, do you know where is this file?

I am trying to understand in this way why after log in the computer stalls...

---

### Post by Bucky Ball on 2009-09-24
boot into recovery and see if it fixes things.

---

### Post by marcio_mi on 2009-09-24
I already tried that, doing both fcsk again and xfix. It does not find any problem. Still after log in I see only the pointer of the mouse. I tried also accessing the terminal by doing ctrl+alt+F1, I can access it, but there are no messages. Apart from the graphical interface, everything seems to be working fine.

---

### Post by Bucky Ball on 2009-09-24
When you get to a terminal have you tried:

```
startx
```?

---

### Post by marcio_mi on 2009-09-24
Thank you Bucky Ball for taking some time.

I just tried ```
startx
``` in the tty terminal and it spits out:

```
Fatal Server Error:
Server is already active for display 0
If this server is no longer running, remove /tmp/.X0-lock and start again
```

there is a file put in the lost+found directory by fcsk which points to some pulsa file. Might that be the problem?

---

