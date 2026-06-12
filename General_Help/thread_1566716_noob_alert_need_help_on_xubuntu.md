---
title: "noob alert need help on xubuntu"
date: 2010-09-02
forum: General Help
---

### Post by niemann999 on 2010-09-02
hey guys i install xubuntu 10.4 last night and worked great then i let it update last night and now im really stuck 
 
img340 is what i get on desktop last night 
img 343 what i get now everytime idk how to get out of it plz help

---

### Post by Autodidact on 2010-09-02
Try to run:
 ```
sudo restart gdm
```

---

### Post by niemann999 on 2010-09-02
All I get is 
Restart: unknown instance: that's it

---

### Post by Autodidact on 2010-09-02
Oops, my mistake :)

Must be:
```
sudo service gdm start
```

---

### Post by niemann999 on 2010-09-02
K I typed that in all it did says
Gdm start/running, process 1519
And flashed a few times but still on this screen

---

### Post by llamabr on 2010-09-02
When you let it update, what, or how, did you do that?

If gdm doesn't restart, it might have been removed.  Check to see that it's there with

```
which gdm
```

If not, do a 

```
sudo apt-get install gdm
```

then reboot.  And report back.

But before that, try holding down ctrl-alt, and pressing f7.

---

### Post by niemann999 on 2010-09-02
I updated it last night after i installed it with the update manager
 
i typed which gdm
it says 
usr/sbin/gdm
 
and the pic shows you what it says when i push ctrl alt f7
 
and i just did the sudo apt-get install gdm it says i have the current gdm
 
if this helps i have 328mbs of ram
intel pentium 3 processor 
nvdia geforce 5800
 
but after seeing what it says ctrl alt f7 im guessing its having issues with plymouth

---

### Post by Smart Viking on 2010-09-02
What happens if you press <alt>+F7, or <alt>+F8 ?

I see you get to a tty promt, what happens if you launch
```
/usr/sbin/gdm
```
In there? :)

---

### Post by niemann999 on 2010-09-02
Alt f7 I get the same thing as In the last pic I put up 
Alt f8 I get a black screen with a blinking _

And I typed in /usr/sbin/gdm I get
** (gdm-binary:1244); WARNING **: failed to acquire org.gnome.displaymanager: connection ":1.20" is not allowed to own the service "org.gnome.DisplayManager" due to security policies in the configuration file

** (gdm-binary:1244): WARNInG ** could not acquire name; bailing out

What it mean by that?

---

### Post by niemann999 on 2010-09-02
I'm also just wondering if I should just reinstall it?

---

### Post by niemann999 on 2010-09-03
Okay I got it working I downgraded to xubuntu 9 working great after all the updates are done so just something in 10.4 that didn't work right on my computer after the updates something with gnome but idk

---

