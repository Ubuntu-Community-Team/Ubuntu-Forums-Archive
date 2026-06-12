---
title: "top and bottom bar disappeared"
date: 2010-08-25
forum: General Help
---

### Post by fchartier on 2010-08-25
[SIZE=4]Hi all, 

Everything was working fine and on a new session the panel and bottom bar are no longer showing.
I am running xubuntu latest version, with compiz fusion and emerald. I always have to reload windows when i start as I have made it default (perhaps thats part of the pb). 
Just before it disappeared I installed new updates from the automatic updates. 
i know i can still access pretty much everything from the right click but the pb is that i can only run one application at a time. as i cannot flip between them nor does the cube or alt tab work.

thanks for your help!!:popcorn: 
[/SIZE]

---

### Post by bobcollard on 2010-08-25
Open Terminal and type the following command:
```
sudo xfce4-panel
```That will startup the panel again.  You may need to add xfce4-panel to your startup applications to make it work all the time or you can reinstall Xubuntu.

---

### Post by Smart Viking on 2010-08-25
> **bobcollard said:**
> Open Terminal and type the following command:
```
sudo xfce4-panel
```That will startup the panel again.  You may need to add xfce4-panel to your startup applications to make it work all the time or you can reinstall Xubuntu.

And you can probably just press "alt+F2" to launch that command if you can't access the terminal. 

May i ask why you put sudo infront? It usually works to just write "xfce4-panel". :)

---

### Post by Gleboff on 2010-08-25
After recent updates (proposed/backports on) my xfce4-panel is disappeared too.
In logs:
```
xfce4-panel[1377] trap divide error ip:7fce7807c126 sp:7fff5a4c8af0 error:0 in libxfce4panel.so.1.1.2[7fce78073000+11000]
```
Backport xfce4-panel 4.6.4 from debian fixed this error.

---

### Post by bobcollard on 2010-08-25
> **Smart Viking said:**
> And you can probably just press "alt+F2" to launch that command if you can't access the terminal. 

May i ask why you put sudo infront? It usually works to just write "xfce4-panel". :)
Force of habit using Terminal, either way works most of the time.

---

### Post by fchartier on 2010-08-25
Thanks a lot buddies, it worked (without the the sudo)

Ubuntu is really great ! thanks to you all!!

---

### Post by bobcollard on 2010-08-25
> **fchartier said:**
> Thanks a lot buddies, it worked (without the the sudo)

Ubuntu is really great ! thanks to you all!!
It is customary to Edit your first Post and in the Title add [Solved] so others may benefit from your experiences.

---

### Post by fchartier on 2010-08-26
is that the correct way of writing solved ? in the top message

---

### Post by Spice Weasel on 2010-08-26
> **fchartier said:**
> is that the correct way of writing solved ? in the top message

Thread tools > Mark as solved.

---

