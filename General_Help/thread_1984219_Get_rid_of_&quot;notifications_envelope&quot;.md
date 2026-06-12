---
title: "Get rid of &quot;notifications envelope&quot;"
date: 2012-05-21
forum: General Help
---

### Post by defaria on 2012-05-21
How do I get rid of this notifications envelope? This is not the indicator app and I can't seem to find a way to remove it. It's totally useless in that it collects notifications and has to constantly be cleared.

See attachment to see what I mean.

---

### Post by dino99 on 2012-05-21
are you using gwibber or likes ? seems to be a preference choice setting to set.

---

### Post by Frogs Hair on 2012-05-21
```
sudo apt-get remove indicator-messages
``` Logout-in or restart afterwards.

---

### Post by defaria on 2012-05-21
Not using gwibber. Trying to remove indicator-messages reports

```
sudo apt-get remove indicator-messages
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package indicator-messages is not installed, so not removed

```

---

### Post by Frogs Hair on 2012-05-21
Check synaptic for residual package/s and remove if need and make sure to logout and in or restart The indicator will remain if you don't .

This is the command I used prior to using a mail client in Ubuntu. There is also a file in file system/usr/lib/indicator messages, but I don't the consequences of removing this folder.

---

### Post by defaria on 2012-05-21
I believe you are thinking about a different indicator. There was also an envelope icon in the notification area but IIRC that was only for email messages. This is yet another envelope icon that appeared after updating to 12.04 and it annoyingly seems to gather all of the notifications including tons I'm just not interested in. 

As for /usr/lib/indicator... indicator what? Under /usr/lib I have indicator-applet, indicator-application, indicator-appmenu, indicator-sound and indicators3. Which do you suggest I remove?

As for synaptic, what do you mean by residue packages? You mean broken? If so I have no broken packages. If you mean something else then kindly tell me how to find them and remove them.

I've logged out and back in many times.

---

### Post by defaria on 2012-06-14
Bump! 

Anybody...

---

### Post by defaria on 2012-07-18
Bump again. I find it hard to believe that I'm the only one experiencing this...

---

### Post by Svalorzen on 2012-08-26
I'm having the same problem too. I don't know how to remove the icon since I can't find the indicator's name anywhere.

---

### Post by defaria on 2012-08-26
I found out more about this. The software is called notification-daemon and it controls the nicer looking popup notifications but however it's not very configurable at all.

I also found out that my Pidgin notifications of "user logged in" were cluttering up that menu of notifications from the notification-daemon. For those notifications the popup is all I need. If I happen to be in front of the computer and somebody logs in that I want to talk to I can easily respond to that popup. But I don't care about it if it happened say at 10 Am when I was at work and I get back home and it's in the menu. So I turned the pidgin notifications off in pidgin and that's my compromise.

Note if you remove notification-daemon you'll still get notifications but they don't look as good.

---

