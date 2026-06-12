---
title: "Secondary Mirrored Monitor Resolution (Laptop)"
date: 2012-06-09
forum: General Help
---

### Post by SipSomeSalt on 2012-06-09
Hello, guys!

I've got a question: recently my laptop's display died, so I attached a monitor via VGA, and the display is mirrored although my laptop's display is dead.

Here's were the problem comes into play -- I want to resolution to be better than 1024 x 768. I don't know how to do this as it's not listed under Configure Display Settings.

What do I do?

P.S. I hope someone can help me this time considering I usually get no response.

---

### Post by papibe on 2012-06-09
Hi SipSomeSalt.

Could you post the content of these files?
```
/etc/X11/xorg.conf

/var/log/Xorg.0.log
```
Please paste them separately here: [http://paste.ubuntu.com/]("http://paste.ubuntu.com/"), and then post back the links here.

Regards.

---

### Post by SipSomeSalt on 2012-06-09
The first one is: 

[http://paste.ubuntu.com/1031603/](http://paste.ubuntu.com/1031603/)

The second one is:

[http://paste.ubuntu.com/1031604/](http://paste.ubuntu.com/1031604/)

Thank you!

---

### Post by papibe on 2012-06-09
Thanks.

I took a quick look and it looks promising since both monitors are recognized.

It's little late around here, so tomorrow I'll give it another look.

In the meantime, I would like you to generate a new xorg.conf because the one you have now doesn't even consider the 2nd monitor.

First, back it up:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```
Then, generate a new one:
```
sudo Xorg -configure
```
that will create a file named ~/xorg.conf.new. You have to move it then:
```
sudo mv ~/xorg.conf.new /etc/X11/xorg.conf
```
Then, restart.

There's a chance that this would allow you to see the external monitor resolutions. If that's not the case, please post again the current version of both files (as before).

Tell us how it goes.

Good Night. 
Regards.

---

### Post by SipSomeSalt on 2012-06-09
Ok -- I figured it out myself........

I just went to System > Administration > Multiple Screens.

---

