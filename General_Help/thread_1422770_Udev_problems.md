---
title: "Udev problems"
date: 2010-03-05
forum: General Help
---

### Post by chaanakya_chiraag on 2010-03-05
I'm using Ubuntu with Fluxbox and logging in with tty1 and using startx. For some reason, udev has taken it upon itself to create all new device nodes as only accessible by root I.e. I can't access a webcam as normal user. Any ideas?  Thanks in advance!
- Chiraag

---

### Post by chaanakya_chiraag on 2010-03-06
*Bump*. Someone PLEASE HELP!!!!!!!!!!!!

---

### Post by chaanakya_chiraag on 2010-03-06
Please????  Someone?????????????? I can provide whatever files/output you need.  This thing is driving me CRAZY!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by flippo on 2010-03-06
What do you get from:```
sudo ls -al /dev/ | grep <device>
```
For example if I had a serial-usb device:```
sudo ls -al /dev/ | grep ttyUSB0
```

---

### Post by chaanakya_chiraag on 2010-03-07
I don't have it plugged in right now, but basically, only the root user and the root group (whatever that's called...I don't remember) have read/write access to the device.  Essentially, udev is giving it 660 permissions.  I'm not sure why though...

---

### Post by falconindy on 2010-03-07
udev only follows the rules its given. If you don't like the rules, write a new one and drop it in /etc/udev/rules.d.

'man udev' has ample info about writing rules.

---

### Post by chaanakya_chiraag on 2010-03-07
@falconindy: the funny thing is that, while gdm was working, none of this happened.  Now, since gdm refuses to let me enter in my password, I use startx.  This has borked things such as policykit and udev, mainly because gdm does some secret magic to allow policykit to work.  However, since startx doesn't run these routines, policykit fails to work anymore and I need to start stuff using gksu instead of just unlocking as I would do when logging in with gdm.  Yes, I know this is off-topic.  However, I'm starting to wonder if gdm does something special...

---

### Post by falconindy on 2010-03-07
> **chaanakya_chiraag said:**
> @falconindy: the funny thing is that, while gdm was working, none of this happened.  Now, since gdm refuses to let me enter in my password, I use startx.  This has borked things such as policykit and udev, mainly because gdm does some secret magic to allow policykit to work.  However, since startx doesn't run these routines, policykit fails to work anymore and I need to start stuff using gksu instead of just unlocking as I would do when logging in with gdm.  Yes, I know this is off-topic.  However, **I'm starting to wonder if gdm does something special...**
Sure it does. If you're going to be using startx and an .xinitrc file, launch gnome-session indirectly as:
```
exec ck-launch-session gnome-session
```

---

### Post by chaanakya_chiraag on 2010-03-07
The problem is that I'm using fluxbox... :(

---

### Post by chaanakya_chiraag on 2010-03-07
...and I DON'T want all my fluxbox stuff being overridden by gnome-session.

---

### Post by falconindy on 2010-03-07
then exec ck-launch-session /usr/bin/fluxbox ...

---

### Post by chaanakya_chiraag on 2010-03-07
So that would fix my policykit/udev woes?  Thanks!  I'll try it later and report back.

---

### Post by chaanakya_chiraag on 2010-03-21
Thank you!!  That worked like a wonder :)  I even figured out that putting ```
/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1 & disown
``` in my Fluxbox startup file fixed PolicyKit!!! :)  Marking this thread solved.  Again, thank you SO MUCH for your help :)
- Chiraag

---

