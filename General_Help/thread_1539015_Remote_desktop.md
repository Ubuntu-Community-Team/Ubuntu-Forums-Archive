---
title: "Remote desktop"
date: 2010-07-26
forum: General Help
---

### Post by pstoh on 2010-07-26
How/where can I configure remote desktop so that other PC can access my lubuntu, since lubuntu doesn't has "System -> Preferences -> Remote Desktop".

---

### Post by pstoh on 2010-07-26
Ok, I found the way.

Install "vino" from synaptic package manager then run "vino-preferences" in run.

Thanks.

---

### Post by moteprime on 2010-12-27
Hi.
Thanks for writing your tip. I got Vino installed on Lubuntu and it seems to run.
But when it is checking for network connectivity it end up telling me that others can connect to it only as "local Host". when i connect to it via IP adress the connection gets closed.
I have two Ubuntu machines on the same network, and they connect just fine with each other, so it not related to my network.
Did you perform anything else to get it working on Lubuntu?

---

### Post by SteveDee on 2010-12-27
I recommend x11vnc server for use with Lubuntu, which you can download via Synaptic.

It can be run for single use from a terminal:-
```

x11vnc -display :0

```
...but is more useful when run like this:-
```

x11vnc -forever -display :0

```
...so you can connect/disconnect/reconnect when needed.

I run it from a simple script that auto runs on startup.
Create a new file called "startvnc.sh" and add this:-
```

 #!/bin/sh
 x11vnc -forever -display :0

```
...then put it in /usr/bin (which is in the $PATH) and make it executable.

Then to autostart, in terminal:-
```

sudo leafpad /etc/xdg/lxsession/Lubuntu/autostart

```
...and add this at the end of this file:-
```

@startvnc.sh

```

You should be able to connect via almost any remote vnc client like this: {IP}::{port}
e.g. 192.168.0.7::5902

---

### Post by moteprime on 2010-12-29
Thanks!
It works well, but the server complains about that i dont use a password. Will anybody be able to access it from the internet?

---

### Post by SteveDee on 2010-12-30
> **moteprime said:**
> Thanks!
It works well, but the server complains about that i dont use a password. Will anybody be able to access it from the internet?

If you are using a firewalled router, the vnc ports are probably blocked, but read the notes here: [http://www.karlrunge.com/x11vnc/faq.html#faq-passwd](http://www.karlrunge.com/x11vnc/faq.html#faq-passwd) ...and use password protection if required.

The full reference for x11vnc is here: [http://www.karlrunge.com/x11vnc/](http://www.karlrunge.com/x11vnc/)

---

### Post by moteprime on 2010-12-30
Ok, I will.
And thanks for the fast reply.

---

### Post by alek66 on 2012-08-13
> **pstoh said:**
> How/where can I configure remote desktop so that other PC can access my lubuntu, since lubuntu doesn't has "System -> Preferences -> Remote Desktop".

I am about to switch to Lubuntu, it does not have the remote desktop as it has on ubuntu? but It can be installed?

---

### Post by moteprime on 2012-08-13
Yes. It's not a problem.
I do not remember what was wrong, but now i use vino server on Lubuntu and Remmina on Ubuntu (client). It works just as in Ubuntu.

---

