---
title: "Notification CLI"
date: 2009-09-07
forum: General Help
---

### Post by sliggy on 2009-09-07
Hey everyone,

I'm writing a shell script that uses unison to sync my macbook and my eeepc. Since this is just going to be running in the background without me monitoring it, I was wondering if there was any way I could have the shell script trigger a notification (using ubuntu's growl-like system) when syncing is complete. Is there a command that can trigger notification that I can call in my script?

Thanks in advance

---

### Post by smain on 2009-09-07
you could install libnotify-bin and then use the notify-send command... eventually here's the manpage: [http://www.digipedia.pl/man/notify-send.1.html](http://www.digipedia.pl/man/notify-send.1.html)

---

### Post by sliggy on 2009-09-07
> **smain said:**
> you could install libnotify-bin and then use the notify-send command... eventually here's the manpage: [http://www.digipedia.pl/man/notify-send.1.html](http://www.digipedia.pl/man/notify-send.1.html)

Yep that did the trick, thanks!

---

