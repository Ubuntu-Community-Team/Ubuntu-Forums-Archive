---
title: "VNC with Java possible?"
date: 2006-06-27
forum: General Help
---

### Post by mykrob on 2006-06-27
I have an installation of Ubuntu 5.10 for a friend of mine, He wants to be able to hit it remotely through VNC. I am able to do it just fine using vncviewer, but am unable to hit it through the browser using java to port 5900..

I am not very familiar with Gnome, i'm a kde person myself..

How can i get this to allow remote access through the browser? As far as i know, there is no firewall enabled, as he is using a router anyway..
When trying this locally through the browser, using

[http://192.168.2.3:5900](http://192.168.2.3:5900)

i get a plain white screen that shows:
RFB 003.007


help?

Thanks,
-myk

---

### Post by Ack99 on 2006-12-25
Try updating the vnc server, just install the new packages

```

sudo apt get install vncserver

```

and then you can install one of the suggested packages

```

sudo apt-get install vnc-java

```

that worked for me
good luck :)

---

### Post by skalsky on 2007-11-30
Hi I am experiencing the same problem, I can connect through the VNC client, but can't through the browser - same white screen saying:

RFB 003.007

I did of course do the above steps you suggested but this did not help in solving this issue..

Any advice?

Thanks,

---

### Post by bodhi.zazen on 2007-11-30
[http://ubuntuforums.org/showthread.php?t=541656](http://ubuntuforums.org/showthread.php?t=541656)

---

