---
title: "compizconfig"
date: 2010-05-24
forum: General Help
---

### Post by anarchywolf46 on 2010-05-24
I set up my friend's laptop with Ubuntu originally, but installed kde into it for fun and since it seems to be prefered by a lot of people. He likes it but I ran into a problem with it. I have compizconfig installed, but it does not give the option for KDE comptability. Because of this, it is very limited to what he can do with it. I have searched around Google for a few hours now and all the methods for installing it are outdated and do not work, in fact most of the packages do not exist.

I have installed nearly everything for compiz I can find, restarted and still nothing. The option for compatability just is not in the settings. Anyone have any idea what is wrong?

Also, I was unsure of where this should go in the forum, so I'm put it here, hopefully it is in the correct section.

---

### Post by inso_741 on 2010-05-24
have you tried this:
```
sudo apt-get upgrade
```

---

### Post by anarchywolf46 on 2010-05-24
> **inso_741 said:**
> have you tried this:
```
sudo apt-get upgrade
```
That's a no go good sir. Nothing upgraded, it's a recent install. I also decided to try out KDE and compiz together, it seemed relatively broken. No effects worked, but it was late at night so I didn't really try to get it to work. Anyways, is it possible some settings outside of compiz somewhere need to be changed maybe?

---

### Post by cgroza on 2010-05-24
> **anarchywolf46 said:**
> That's a no go good sir. Nothing upgraded, it's a recent install. I also decided to try out KDE and compiz together, it seemed relatively broken. No effects worked, but it was late at night so I didn't really try to get it to work. Anyways, is it possible some settings outside of compiz somewhere need to be changed maybe?

Do you have compiz-kde package installed?

---

### Post by anarchywolf46 on 2010-05-24
> **cgroza said:**
> Do you have compiz-kde package installed?
Of course, that's the first thing I installed when the problem arose. Installed everything I could find for compiz kde related, restarted it, and still nothing.

---

### Post by inso_741 on 2010-05-24
remove compiz from synaptic run ```
sudo apt-get update
``` and then install compiz again.
what version of kde have you installed?

---

### Post by anarchywolf46 on 2010-05-25
> **inso_741 said:**
> remove compiz from synaptic run ```
sudo apt-get update
``` and then install compiz again.
what version of kde have you installed?
I will try that next time I can get on his computer, probably tomorrow since he doesn't want to do it himself on the off chance he might break his computer.

As far as version goes... no idea, it's whatever I got from doing
```
sudo apt-get install kubuntu-desktop
```
like, the day I posted this thread. If you know what I can do to check the version, do tell, I don't know how and haven't taken the time to look into it.

I'll get back to you when I try out your suggestion.

---

### Post by anarchywolf46 on 2010-05-25
Okay, got my friend to attempt it. Still nothing. I can't think of what the problem is. I had him install compiz and the kde parts of compiz but still nothing. It only shows compatibility for gnome. With my luck, I am overlooking something simple.

---

### Post by inso_741 on 2010-05-25
Is gnome still installed?
if yes does he still need it?

---

### Post by maski on 2010-05-25
hi, sorry for barging in on your thread can you help me im new here how do you start a new topic, i installed 'ubun ulti' 2.6 on another partition with win,7. anyway is there a link or how to for the 'affects settings' ive found most but the shrinking desktop cube?? where are /is the ''super button'' any help would be great thanks mark:)EDIT:both windows 7,pro+'ubuntu running fine no problems 'i can run a software program called ''desk-space'' the 3D affects are outstanding, so not a hardware or graphics issue.

---

### Post by inso_741 on 2010-05-25
> **maski said:**
> hi, sorry for barging in on your thread can you help me im new here how do you start a new topic, i installed 'ubun ulti' 2.6 on another partition with win,7. anyway is there a link or how to for the 'affects settings' ive found most but the shrinking desktop cube?? where are /is the ''super button'' any help would be great thanks mark:)EDIT:both windows 7,pro+'ubuntu running fine no problems 'i can run a software program called ''desk-space'' the 3D affects are outstanding, so not a hardware or graphics issue.

[here]("http://ubuntuforums.org/forumdisplay.php?f=331") is the general help forum.....to start a new thread click on 'New Thread' button
'super button/key' is the one with windows logo on it

---

### Post by anarchywolf46 on 2010-05-25
> **inso_741 said:**
> Is gnome still installed?
if yes does he still need it?
Gnome is indeed still installed, and I no he does not need it, but he may want it to stay installed. However, I can remove it and install it later if he really wants it. I'm guessing your suggestion is to uninstall gnome and then install compiz?

---

### Post by inso_741 on 2010-05-25
yes uninstall both compiz and gnome
run sudo apt-get update/upgrade
then install compiz

and just out of curiosity does compiz still works with gnome?

---

### Post by anarchywolf46 on 2010-05-26
Yeah, it works with gnome just fine. It also works with KDE, it is just severely limited and basically none of the keyboard shortcuts want to work for it. It is almost like the keys are not responding, but they show up when I have compiz grab keyboard input. Even when I change the default shortcuts, most of the things in compiz still won't work.

---

