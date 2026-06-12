---
title: "Norwegian chars won't show in aMSN after upgrade to 10.04"
date: 2010-05-08
forum: General Help
---

### Post by atzz on 2010-05-08
I upgraded from 9.10 to 10.04 and then the norvegian characters stopped working in aMSN.

I can past them into the program, but not write them with the key on the keyboard. 
I've tried the[ aMSN]("http://www.amsn-project.net/forums/index.php/topic,7901.0.html") forums but the couldn't help me.

So I wounder if anyone here has a solution?


EDIT: I just discovered that the characters don't work in any program in Wine either.

---

### Post by atzz on 2010-05-10
No one?

---

### Post by VyseN on 2010-05-11
I have the same problem, and I would really like to see it fixed. It worked perfectly before I upgraded to Lucid Lynx, and since I'm a Linux n00b, I have no idea what to do to fix it.

---

### Post by Zorael on 2010-05-11
Okay. Could you paste the output of the following, entered in a terminal?
```
echo -e "\nGTK:\t$GTK_IM_MODULE\nQt:\t$QT_IM_MODULE\nXMOD:\t$XMODIFIERS\n"; im-switch -l
```
One line for easy copy/pasting.

If you're on an en_US locale, you could try the following instead for a shorter, summarized output. Also all in one line. Either will do.
```
SYSTEMWIDE=$(im-switch -l | grep "currently points to" | awk '{ print $5 }');USERSPECIFIC=$(im-switch -l | grep -B1 supersede | grep -v supersede);if [ "x$USERSPECIFIC" == "x" ]; then USERSPECIFIC="(not set)";fi;echo -e "\n^ Ignore errors above this line ^\n\nGTK:\t\t$GTK_IM_MODULE\nQt:\t\t$QT_IM_MODULE\nXMOD:\t\t$XMODIFIERS\nuser-specific:\t$USERSPECIFIC\nsystem-wide:\t$SYSTEMWIDE"
```
How's that for code obfuscation? :3

(The commands are safe.)

---

### Post by atzz on 2010-05-13
> **Zorael said:**
> Okay. Could you paste the output of the following, entered in a terminal?
```
echo -e "\nGTK:\t$GTK_IM_MODULE\nQt:\t$QT_IM_MODULE\nXMOD:\t$XMODIFIERS\n"; im-switch -l
```

Here you got it: 
```
GTK:    
Qt:    
XMOD:    

Your input method setup under nb_NO locale as below.
=======================================================
No private "/home/sigve/.xinput.d/nb_NO or /home/sigve/.xinput.d/all_ALL" is defined.
=======================================================
The system wide default is pointed by "/etc/alternatives/xinput-all_ALL" .
xinput-all_ALL - auto mode
 lenke peker for øyeblikket til default
default - prioritet 10
default-xim - prioritet 0
none - prioritet 0
Nåværende  «beste» versjon er default.
=======================================================
The available input method configuration files are:
/usr/bin/find: `/home/sigve/.xinput.d': No such file or directory
default default-xim ibus lo-gtk none th-gtk th-xim 
=======================================================

```

---

### Post by Zorael on 2010-05-13
Right. Try this.
```
$ sudo im-switch **-s** default-xim
```
You'll need to log out and back in (or reboot) for the changes to take proper effect.

---

### Post by vetlea on 2010-05-15
> **Zorael said:**
> Right. Try this.
```
$ sudo im-switch -c default-xim
```You'll need to log out and back in (or reboot) for the changes to take proper effect.

yea... come again?

---

### Post by Zorael on 2010-05-15
> **vetlea said:**
> yea... come again?

Apologies, that's supposed to be an **-s**.
```
$ sudo im-switch **-s** default-xim
```

---

### Post by atzz on 2010-05-17
When using that command, the terminal outputs:

```
No system wide default defined just for locale nb_NO .
Use "all_ALL" quasi-locale and set IM.
update-alternatives: using /etc/X11/xinit/xinput.d/default-xim to provide /etc/X11/xinit/xinput.d/all_ALL (xinput-all_ALL) in manual mode.

```


EDIT: It still don't work!

---

### Post by atzz on 2010-05-28
When im typing this command in the terminal, it is working:

```
LANG="nb_NO.UTF-8" amsn
```


But when starting from the icon, not working.

---

### Post by VyseN on 2010-05-29
> **atzz said:**
> When im typing this command in the terminal, it is working:

```
LANG="nb_NO.UTF-8" amsn
```


But when starting from the icon, not working.

That fixed it man, thanks. What you do is to right click on the aMSN icon on your panel and hit Properties/Egenskaper, then paste this in Commando/Kommando:

```
env LANG=nb_NO.UTF-8 amsn
```

That fixed it for me anyway, and we had the exact same problem. Takk for hjelpen kompis! ^^

---

### Post by atzz on 2010-07-11
There! IT WORKS :popcorn:


Takk :)

---

