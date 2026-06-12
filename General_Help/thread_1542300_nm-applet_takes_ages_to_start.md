---
title: "nm-applet takes ages to start"
date: 2010-07-30
forum: General Help
---

### Post by gwurst on 2010-07-30
hi, i'm using 64bit xubuntu 10.04. I think I upgraded it twice from original 9.04.

So, since my upgrade to 10.4 nm-applet takes ages to start when i login to my account and I therefore don't have any connectivity in the first minutes, which is really annoying. my computer doesn't seem to do anything in those 2 minutes either, no blinking leds, overall good responsiveness, ...
i see that it's started by the xfce autostart system. 

so, is this a known issue? how can i fix it?

thanks in advance

---

### Post by Smart Viking on 2010-07-30
What happens of you launch it from the terminal after you boot up, will it launch?

---

### Post by dino99 on 2010-07-30
ive no experience with xfce but into a console, try:

sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

sudo dpkg-reconfigure network-manager
sudo dpkg-reconfigure net-tools

metacity --replace

---

### Post by gwurst on 2010-07-30
should have tried that earlier...

it starts immediately when entered in a terminal.

so it must be xfce. I noticed there are a lot of entries in the autostart-menu but just a few in ~/.config/autostart/ where they used to be. where did they go?
is there some way to influence the order in which they are started?

---

### Post by Smart Viking on 2010-07-30
You can make a script, like this:

```
#!/bin/bash
sleep 10
<whatever you enter in the terminal to launch the applet>
```

then save it as something like "file.sh" and mark it as executable, and then add it to startup applications, then the script will tell it to launch the applet 10 secounds after you have logged in. :)

---

### Post by gwurst on 2010-07-30
this doesn't seem very useful... in the end it would just make the networkmanager start 10 seconds later...

i removed all the other autostarted applications, but still the same result, which means, it's not some other application blocking the whole autostart-process.

---

### Post by gwurst on 2010-07-30
yay, see, someone else had this problem before: [http://sbornitux.wordpress.com/2009/03/06/xfce-slow-problem-solved/](http://sbornitux.wordpress.com/2009/03/06/xfce-slow-problem-solved/)

---

