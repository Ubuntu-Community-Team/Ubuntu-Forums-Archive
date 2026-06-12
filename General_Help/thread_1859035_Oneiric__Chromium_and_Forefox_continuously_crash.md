---
title: "Oneiric : Chromium and Forefox continuously crash"
date: 2011-10-13
forum: General Help
---

### Post by sonnet on 2011-10-13
As per title I'm having continuous crashes with Firefox and Chromium.
Chromium crashes very frequently (once per minute, even now when I was simply typing it crashed) , firefox less frequently, and I don't understand the reason.
Flash 11 was installed through the repositories
The system is a ubuntu server cli installation on top of which I installed gnome-shell and the applications I needed.

I have attacked /var/log/Xorg.0.log, /var/log/syslog and /var/log/dmesg 
hoping this could help to understand the problem.

---

### Post by sonnet on 2011-10-13
nobody had the same problem?

---

### Post by zasq on 2011-10-14
Same problem here. After upgrading from natty to oneiric (amd64) firefox, chromium and thunderbird crash right after starting them and are not usable. That even happens in safe mode. I thought it had to do with the flashplugin-installer but removing it didn't help either. Has someone found a solution?
All the best

BTW, when I upgraded, the upgrade didn't end by itself properly, so I had to restart. Fortunately, the system started, but before the login screen launched for the first time, there was a message saying "Trying to configure network", and then "starting without configuring network". The only browser that works for me now is epiphany. I hope this information helps to find a solution. Please let me/us know what else you need.

---

### Post by zasq on 2011-10-15
Okay, I think I've got it. 

When I started firefox from terminal I saw there was a problem mit the gecko-mediaplayer and found this bug:

[https://bugs.launchpad.net/ubuntu/+source/gecko-mediaplayer/+bug/812053]("https://bugs.launchpad.net/ubuntu/+source/gecko-mediaplayer/+bug/812053")

So, this is what I did:

```
sudo apt-get remove --purge gecko-mediaplayer gnome-mplayer
```

Afterwards, I rebooted to be sure everything is cleaned up and then reinstalled both as well as the adobe-flashplugin:

```
sudo apt-get install gecko-mediaplayer gnome-mplayer adobe-flashplugin
```

Now, everything works fine. I hope this works for you, too. While in natty my laptop heated up very quickly, even this problem seems to be solved. The fans even stop once in a while ;)

Good luck!

---

### Post by deeporbit on 2011-10-18
I can type in Facebook for about 7 seconds and Chromium crashes. I tried Firefox and it's worse. 
I checked for the gecko-media player and it is not installed on my machine. Still stuck.

---

### Post by caracolasem77 on 2011-10-26
I have the same problem, continuosly crashes on firefox and chromium, and it does impossible to navigate.

Any solution?

I checked for the gecko-media player and it is not installed on my machine too.

---

