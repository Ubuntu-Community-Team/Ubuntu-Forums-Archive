---
title: "Disable Shotdown/Reboot/Hibernate buttons on LOGIN SCREEN"
date: 2010-10-24
forum: General Help
---

### Post by kurci2 on 2010-10-24
HI!
i want to remove shutdown/restart/hibernate buttons from my gdm login screen on ubuntu 10.10.
if i disable these buttons with _ubuntu tweak_ or _gdm2setup_ it is just ignored and all buttons are still there...
any sugestions??

---

### Post by spiky001 on 2010-10-24
Do you mean the 1,s on the top right of screen?

---

### Post by kurci2 on 2010-10-24
these buttons are actually on right bottom corner...login screen
if you click that icon then additional options pops out (shotdown, restart and hibernate)

---

### Post by sisco311 on 2010-10-24
Try:
```
sudo -u gdm gconftool-2 -t bool -s /apps/gdm/simple-greeter/disable_restart_buttons true
```to disable the buttons. To (re-)enable them:
```
sudo -u gdm gconftool-2 -t bool -s /apps/gdm/simple-greeter/disable_restart_buttons false
```

---

### Post by kurci2 on 2010-10-24
sudo -u gdm gconftool-2 -t bool -s /apps/gdm/simple-greeter/disable_restart_buttons true

after that code buttons are still there...

---

### Post by Blowfish0815 on 2011-03-14
i have the same issue. i disabled the restart_buttons with gconf-tool for user gdm, my standard user and root, but it is still there.
if i disable the user list with disable_user_list, the user_list disappears, but now the restart/shutdown buttons.
do you know any fix for this? 

> Linux version 2.6.35-27-server (buildd@crested) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) ) #48-Ubuntu SMP Tue Feb 22 21:53:16 UTC 2011

GDM 2.30.5


---

### Post by Jouke74 on 2011-03-15
Surf to /usr/share/gdm/autostart/LoginWindow and move "Power Manager" to another place (somewhere in your home dir). I have NOT tried this myself, so I don't know the consequences. If it fails, put it back there.

---

### Post by Blowfish0815 on 2011-03-15
No consequences...it doesn't change anything.

---

### Post by Blowfish0815 on 2011-03-15
anybody ideas? i don't want to remove the GUI completely, but if i can't find a fix for this i will have to.

---

### Post by Krytarik on 2011-03-16
@Blowfish0815: Did you restart (at least GDM) after doing this!?

---

### Post by WlaadDyaab on 2011-03-16
> **Blowfish0815 said:**
> anybody ideas? i don't want to remove the GUI completely, but if i can't find a fix for this i will have to.

Have you tried to right-click on the red shutdown icon, then choosing "Remove From Panel"

Or is your problem worse?

(And if you want to get it back you just right-click on the panel . Add to Panel... Then click on the "shutdown" icon and choose "Add")

---

### Post by Blowfish0815 on 2011-03-16
It restarted GDM itself (service gdm restart) and the whole machine too. After each new input. But nothing helped till yet.

---

### Post by Krytarik on 2011-03-16
Thanks. May it be that those command structure works?:
[https://defect.opensolaris.org/bz/show_bug.cgi?id=12911#c5](https://defect.opensolaris.org/bz/show_bug.cgi?id=12911#c5)

---

### Post by Blowfish0815 on 2011-03-16
Hey, sorry to tell you that, but this doesn't work either.
the mandatory thing i tried before, but this config is just ignored. is there a way to check what config-variables(if there are such) are loaded and user by gdm/gnome?
PS: i've executed the commands also as root and as user gdm (via su). doesn't make any difference to the login screen.

---

### Post by Krytarik on 2011-03-16
I just yet tested it myself and it works for me. Even without the mandatory thing, my steps were:

- enter those command in a terminal:
```
gksudo -u gdm dbus-launch gconf-editor
```- enter the password, obviously
- browse down the path in the GUI to "/apps/gdm/simple-greeter/disable_restart_buttons"
- tick it
- close apps, logout
- press Ctrl+Alt+F1
- login at the console (if not already)
- enter those commands:
```
sudo service gdm stop
sudo service gdm start
```(Yeah, "restart" may do it also.)

**EDIT:** You didn't mention it so far, which version of Ubuntu do you run?

---

### Post by Blowfish0815 on 2011-03-16
except for the dbus-launch i did it exact the same and it is ticked since days...i have also unticked it and reticked it. doesn't change anything.

its ubuntu 10.10
> 
Linux version 2.6.35-27-server (buildd@crested) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) ) #48-Ubuntu SMP Tue Feb 22 21:53:16 UTC 2011


---

### Post by Krytarik on 2011-03-16
> **Blowfish0815 said:**
> 
its ubuntu 10.10
Maybe there is a change/bug in Maverick's GDM version, would not be the only one.

The only remaining option I can offer right now is to try to downgrade to Lucid's GDM version, but that may not work because of the dependencies:
[http://packages.ubuntu.com/lucid-updates/gdm](http://packages.ubuntu.com/lucid-updates/gdm)

---

### Post by Blowfish0815 on 2011-03-17
i think i will remove gnome completely. i can run GUI programs also with x11-forwarding on my win-client with xming.
but thanks for trying.

---

### Post by gfunkdave on 2011-03-18
I would also like an answer to this question. I am running two servers: one with 10.04 and one with 10.10.

I've only been trying to remove the menu with Shutdown/Restart/Hibernate on the machine running 10.10 so far, with no luck. Krytarik's suggestion of 

```
gksudo -u gdm dbus-launch gconf-editor
```

does nothing, even after a complete reboot. Before being able to run the above, I also had to add user gdm to the users allowed to connect to the X server with:

```
xhost +SI:localuser:gdm
```

But the menu in the lower right corner of the login screen is still there. Surely there must be a way to remove it??!

I've also tried putting the following lines in /etc/gdm/custom.conf, without success:

```

RebootCommand=
ShutdownCommand=

```

Are there any other ideas? I've tried everything else in this thread, and in the others I could find.

Thanks!

---

### Post by Krytarik on 2011-03-18
> **gfunkdave said:**
> 
I've only been trying to remove the menu with Shutdown/Restart/Hibernate on the machine running 10.10 so far, with no luck. Krytarik's suggestion of 
```
gksudo -u gdm dbus-launch gconf-editor
```does nothing, even after a complete reboot. Before being able to run the above, I also had to add user gdm to the users allowed to connect to the X server with:
```
xhost +SI:localuser:gdm
```
Yeah, in 10.10 you need to run those command before the other will work. I forgot to mention that, sorry.

---

### Post by gfunkdave on 2011-03-21
Since it seems this is a Gnome bug, can someone point me to the right place to report it?

---

### Post by Krytarik on 2011-03-21
> **gfunkdave said:**
> Since it seems this is a Gnome bug, can someone point me to the right place to report it?
[https://bugs.launchpad.net/ubuntu/+source/gdm](https://bugs.launchpad.net/ubuntu/+source/gdm)

Please post the URL when done so!

---

### Post by gfunkdave on 2011-03-21
Apparently it was reported long ago.

[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/494366](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/494366)

The fix from one of the Gnome developers is to run gconf-editor as root (gksudo gconf-editor) and set that /apps/gdm/gnome-simple-greeter/disable_restart_buttons to True. Then, right-click the key and choose **Set as Default** to make it a systemwide default.

This worked for me on the 10.04 server. Will try on the 10.10 one tomorrow and report back.

---

### Post by gfunkdave on 2011-03-22
As a followup, the above works fine in 10.04 but is broken in 10.10.

---

### Post by Blowfish0815 on 2011-03-22
how long does it usually take to fix such a bug?

---

### Post by gfunkdave on 2011-03-22
No idea. I presume it's something simple to fix, and I did update the bug report. But who knows when someone will decide to fix it.

---

### Post by Blowfish0815 on 2011-03-22
i see. please post it here, if you get to know anything new about this.
so long thx.

---

