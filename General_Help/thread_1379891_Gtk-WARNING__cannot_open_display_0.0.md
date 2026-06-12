---
title: "Gtk-WARNING **: cannot open display: :0.0"
date: 2010-01-13
forum: General Help
---

### Post by krishnamohan on 2010-01-13
When I become root and try to run gedit, I get the error:

[I]No protocol specified

(gedit:2198): Gtk-WARNING **: cannot open display: :0.0


[/I]This does not happen from my user profile....*xhost + *   actually solves the issue....so I guess I just need to add the host root to the list of hosts allowed to access the x server...

I try xhost +root......but that does not work....

how do I....?????

---

### Post by Locutus_of_Borg on 2010-01-13
try putting

export DISPLAY=:0.0

into your /root/.bashrc

create the file if it does not exist

if I recall, thats what fixed the same problem i was having

---

### Post by krishnamohan on 2010-01-14
Tried that..not working....

Besides, sometimes when I switch on the comp, I see just two dots on the top part of the screen..and I have to restart to bring everything back to normal..

---

### Post by krishnamohan on 2010-01-14
I got the following from google..it seems to work..

echo $DISPLAY                  # you'll be needing this value 3 lines below
sudo -i                        # or "su -" on older Slackwares
xauth merge ~alien/.Xauthority # use your own username here instead of "alien"
export DISPLAY=:0.0            # use the value of DISPLAY you've seen 3 lines before

I still have to wait and see if I still get the problem at startup.......

---

### Post by barnex on 2010-01-14
instead of:

```

sudo su
gedit

```

(which I assume you did), try:

```

sudo gedit

```

which should work.

---

### Post by Yellow Pasque on 2010-01-14
Use gksu for graphical applications....
```
gksu gedit
```

---

### Post by Saiko Berry on 2010-01-14
Warnings dont matter. Get used to them.
When it says ERROR, then you care.

---

