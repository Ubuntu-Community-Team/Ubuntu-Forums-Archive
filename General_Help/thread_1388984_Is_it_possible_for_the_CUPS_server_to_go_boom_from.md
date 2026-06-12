---
title: "Is it possible for the CUPS server to go boom from purging...?"
date: 2010-01-23
forum: General Help
---

### Post by bobleny on 2010-01-23
I went to print out a paper this morning, and I got an error. It said it could not print. Oh great... When I go to system settings and click on printers to get a better idea of what is going on, I get this error message:
```

Unable to retrieve the printer list. Error message received from manager:
Connection to CUPS server failed. Check that the CUPS server is correctly installed and running. Error: localhost: read failed (14).

```

So I though maybe this has something to do with my printer or something. It only takes a few minutes to install, so I tried to reinstall it. When I get to the part where I install the CUPS driver for my printer, I get this error:
```

Preparing to replace mfc230ccupswrapper 1.0.1-1 (using mfc230ccupswrapper-1.0.1-1.i386.deb) ...
lpadmin: Unable to connect to server: Connection refused
Unpacking replacement mfc230ccupswrapper ...
Setting up mfc230ccupswrapper (1.0.1-1) ...
lpinfo: Unable to connect to server: Connection refused

```

In addition, when I try to load localhost:631, Godfox (Fun little nickname for Firefox) tells me that it can't establish a connection. So now, it seems that the problem is indeed with the CUPS server, but get this, I can't find any relevant information on CUPS??? It appears as though most people who have a problem with CUPS is a result of their printer drivers and newbieness, if I can say that... lol

Is there anyone around here who can tell me what to do about this? Maybe I can try a manual restart of the CUPS server or even a re-instillation of the CUPS server? I don't know how to do any of that of course...

Is it possible for the CUPS server to go boom from purging and reinstalling Apache and or PHP? I'm not entirely sure what happened because it has been so long ago since I've used my printer. I have recently purged and reinstalled both Apache2 and PHP5 and because it is a CUPS server, maybe the reason I am having this issue is because of that? I don't know...

I am running Kubuntu 8.04 on a 64bit machine, and in case relevant, my printer is a Brother MFC-230C.

Thanks for any and all help! School started up again, and I need my printer... :'(

---

### Post by no2498 on 2010-01-23
my usb webcam went to 1 frame per second today
not 20 like it has been

---

### Post by bobleny on 2010-01-23
That sucks...

Any other ideas?

lol, wow...

---

### Post by amsterdamharu on 2010-01-25
Do you have the loopback adaptor? (give command ifconfig) It is probably localhost 127.0.0.1

Restart cups server:

sodo /etc/init.d/cupsys start|stop|restart|force-reload|status

And what is the status?

---

### Post by bobleny on 2010-01-27
Thank you very much amsterdamharu. Your post is exactly what I needed to figure out what was going wrong.

I do have loop back, but when I would run the command to start or stop cupsys, I would not receive any message. I checked the file, it existed...

I figured maybe it isn't installed after all. Now knowing that the CUPS server is called cupsys, or I would have done this from the start, I noticed it wasn't installed so I installed it.

Relatively long story short, my printer now works.

Thank you very much!

---

