---
title: "Execute a program into a runing VNC session"
date: 2011-02-27
forum: General Help
---

### Post by zacharytcutler on 2011-02-27
Hello, sorry if this is around but I couldn't find it, although I'm probably just not using the correct terminology.

So I administer my Ubuntu Server heavily through webmin as my server is headless, and using webmin I set up cron jobs to run at boot. One of the programs I run on my server is Calibre Ebook manager which I have configured to run an ebook browser/downloader server; unfortunately if I simply try to run calibre as a cron job, or even from putty it gives me some error about how it couldnt graphically load, so I've been manually opening vnc and starting it from a vnc session, so my question is:

Can i start a program inside a vnc session while not being in the session, so my session is myservername:1 could I like somehow do sudo myservername:1 calibre or something?

Its vncserver from the package vnc4server.

Thanks!:guitar:

---

### Post by gsgleason on 2011-02-27
I have no idea if this will work, but see what your $DISPLAY environment varialbe is in VNC, and set that in your cron job.

So, from vnc session, start terminal, and "echo $DISPLAY"

then, whatever that is, in your cron job, put "DISPLAY=whaterver" in front of the command.

---

### Post by zacharytcutler on 2011-02-27
hmm, it definitely tried something, the usual error message "calibre: cannot connect to X server" changed to "calibre: cannot connect to X server 1.0", where 1.0 was the $DISPLAY value of my vnc. Unfortunantly it did not work

:(

thanks for your suggestion though!

---

### Post by anglican on 2011-02-28
> **zacharytcutler said:**
> Hello, sorry if this is around but I couldn't find it, although I'm probably just not using the correct terminology.

So I administer my Ubuntu Server heavily through webmin as my server is headless, and using webmin I set up cron jobs to run at boot. One of the programs I run on my server is Calibre Ebook manager which I have configured to run an ebook browser/downloader server; unfortunately if I simply try to run calibre as a cron job, or even from putty it gives me some error about how it couldnt graphically load, so I've been manually opening vnc and starting it from a vnc session, so my question is:

Can i start a program inside a vnc session while not being in the session, so my session is myservername:1 could I like somehow do sudo myservername:1 calibre or something?

Its vncserver from the package vnc4server.

Thanks!:guitar:After connecting to myservername by putty you could try:
```
xterm -display :1 -e calibre
```

But why not just put calibre into your $HOME/.vnc/xstartup file?

H

---

### Post by anglican on 2011-02-28
> **zacharytcutler said:**
> Hello, sorry if this is around but I couldn't find it, although I'm probably just not using the correct terminology.

So I administer my Ubuntu Server heavily through webmin as my server is headless, and using webmin I set up cron jobs to run at boot. One of the programs I run on my server is Calibre Ebook manager which I have configured to run an ebook browser/downloader serverBTW doesn't:
```
sudo calibre-server --daemonize
```work without needing a vnc (I don't know the answer to this - I'm not using calibre as a server)?

H

---

### Post by zacharytcutler on 2011-02-28
Thank you Anglican! I encounter a 'segment' error when daemonizing but if I visit the server it is actually running so this is a much better solution than I was seeking:).

I couldnt seem to get calibre to graphically load by executing it from the .vnc startup file or by using xterm, but I never did encounter an error so theres something.


Thanks again!

---

