---
title: "disable Failsafe Gnome and/or unlock login preference window"
date: 2010-07-09
forum: General Help
---

### Post by dulce on 2010-07-09
just got my own computer, first time and already goofed up.:)

when i called up the login screen to change to automatic login, i apparently changed my preference from GNOME to Failsafe GNOME (knew i made an extra click but didn't know where, dumb, i know). with Failsafe the network manager applet and all the other default prefs disappeared. the worst is that i can't connect to wireless without the nm.

these are preferences, right? you should be able to go right back anytime and change them but now when i go settings > admin > login the window is locked. only the unlock button is lit up and that won't budge. 

so as the thread title says, how do i unlock login preference window and/or disable Failsafe Gnome?

or do i even understand the problem, lol?

hope you good people can help me with what appears to be a simple thing, right? i will be in touch with the guy who built it this weekend and will be looking around for someone around here who knows ubuntu. 

thanks. i look forward to having more respectably complex problems to lay on you!:D

---

### Post by dulce on 2010-07-09
update- partially solved:

i was able to get the nm applet back onto the panel with info from nothing special (thanks ns):

right click panel, choose add applet, press alt+F2 and type  [  nm-applet  ]

it asked me for my keyring password then restored me to internet.

however i still need to unlock the login screen, disable Failsafe GNOME and enable GNOME. at least i'm on my own machine again.:)

---

### Post by dulce on 2010-07-12
am i allowed to bump?

---

### Post by dulce on 2010-07-15
the more i research this in the various resources the more it seems like a common problem and has been for some time back. is that true?

---

### Post by dulce on 2010-07-19
is this a bug then?

---

### Post by sisco311 on 2010-07-19
Try:
```
/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1 &
gdmsetup
```

---

### Post by dulce on 2010-07-20
jeez, thanks. was getting ready to take it to xubuntu but will try this. 

ummmmm does that mean open a terminal? absolute beginner here. am in mexico and no one around here knows ubuntu.

---

### Post by sisco311 on 2010-07-20
I'm sorry, I was a little busy when I posted my first reply. Yes, you have to run the commands in a terminal, while you are logged in in a GNOME Failsafe session. The first one:
```
/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1 &
```
should activate the "unlock" button(s) ( you may have to press Enter after you run it) in application which use policykit, such us gdmsetup (System -> Administration -> Login Screen). 

And the second one starts gdmsetup, the application from where you can disable the automatic login. 

HTH

OFF TOPIC: Nice username, it means *sweet* in Romanian. :)

---

### Post by dulce on 2010-07-20
ok i did that and got this:

rabana@rabana-laptop:~$ /usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1 &
[1] 5837
rabana@rabana-laptop:~$ 
(polkit-gnome-authentication-agent-1:5837): GLib-GObject-WARNING **: cannot register existing type `_PolkitError'

(polkit-gnome-authentication-agent-1:5837): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

sounds dire, lol*. but *all i know is i'm logged in, connected to wireless manually, able to use the internet and not much else. does that mean i'm in a failsafe GNOME session?

---

### Post by sisco311 on 2010-07-20
Hmmm, let's try a different approach. 

Edit the /etc/gdm/custom.conf file:
```
gksu gedit /etc/gdm/custom.conf
```
and replace
```
AutomaticLoginEnable=**true**
```
by
```
AutomaticLoginEnable=**false**
```

If you can't use gedit to edit the file, then try nano:
```
sudo nano /etc/gdm/custom.conf
```
press Ctrl+x, y, Enter to save the file and exit.

Log out or reboot the computer:
```
sudo reboot
```

---

### Post by dulce on 2010-07-21
thank you that did it. you're a genius.:D

for some reason it did already say 'automatic login enable false'

the last line said something about enable gnome-failsafe, and with great trepidation i erased '-failsafe', rebooted and voila, i'm in business.

thanks again. i will mark this thread 'solved'.

---

