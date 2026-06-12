---
title: "Closed Downloads folder keeps regenerating"
date: 2011-05-21
forum: General Help
---

### Post by pquinnet on 2011-05-21
I keep closing my displayed /home/..../Downloads folder and 2 seconds later the Downloads folder reappears. Regardless of what I do, it keeps coming back. Tried Kill and still it keeps regenerating. When I Shut Down the machine and start it back up again, the Downloads folder pops up again.  I have a process called "Nautilus --sm-client-id ..." running and when killed, keeps coming back. Using Ubuntu 10.10, Nautilus Elementary 2.32.2.
I just put the "breadcrumbs" directory into my /home/.themes folder as per instructions and this issue started.

Any suggestions ??    thanks,   pat q.

---

### Post by Habitual on 2011-05-21
Did you mount something from ~/Downloads? 
Have an audio playback programs running in the tray?

Something to look for...

---

### Post by kanem on 2011-05-31
Bothering me too. It never actually has anything in it. Just keeps coming back once in a while. I'll pay attention to the time-of-creation next time it reappears. Maybe that will give a clue.

---

### Post by kanem on 2011-06-06
For me, it was the Transmission bittorrent client.
It was reported here:
[https://trac.transmissionbt.com/ticket/1902](https://trac.transmissionbt.com/ticket/1902)
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=518792](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=518792)

But these bug reports were closed. Two years ago. And the problem is still here. :roll:

---

### Post by linuxinstalledfromhdd on 2011-06-06
Do you have the transmission running in the tray?

---

### Post by andrew.46 on 2011-06-07
Do you have this set as the default download directory for Firefox?

---

### Post by kanem on 2011-06-09
> **linuxinstalledfromhdd said:**
> Do you have the transmission running in the tray?
Do you mean "Show Transmission icon in the notification area"? Nope

> **andrew.46 said:**
> Do you have this set as the default download directory for Firefox?
Firefox was set to save to Desktop

Arrggh! But now I can't reproduce the issue. 2 days ago the Downloads folder was created within a second of starting Transmission every single time I started it. Now it isn't created. Oh well.

---

