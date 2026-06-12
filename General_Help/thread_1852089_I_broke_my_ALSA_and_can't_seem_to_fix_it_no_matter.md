---
title: "I broke my ALSA and can't seem to fix it no matter what. aplay -l shows no soundcards"
date: 2011-09-29
forum: General Help
---

### Post by indstr on 2011-09-29
Hi all. I am having some trouble with my ALSA. 

System info: 
Intel Core 2 duo
OS Version: Xubuntu 10.04
Sound card: M-audio Delta
Kernel: Not sure what Kernel version (I'm not at my Linux machine right now).

It all started about a month ago when I tried upgrading ALSA from 1.0.22 to 1.0.24. For some reason, sound just stopped working completely. 

I tried downgrading the alsa-base to the previous version and locking it... Still didn't work. 

So I tried compiling ALSA from source:
 OK, so it "successfully" installed. I did aplay -l and it still said ```
"aplay: device_list:240: no soundcards found..."
```When I do lspci, my soundcard is definitely there: ```
"00:0c.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)" 
```I don't understand very much about Linux drivers, but I have a more knowledgeable friend who suggested I look in /var/log/messages. I went through that and couldn't find anything about sound, so I gather that it's not actually loading the drivers for some reason. I tried modprobe & rmmod (or was it insmod?) to manually load, this does not work either. (gave some error messages)

So my friend suggested I try this tutorial on how to install latest ALSA version:
[http://www.atoztoa.com/2010/01/install-alsa-latest-version-in-ubuntu.html](http://www.atoztoa.com/2010/01/install-alsa-latest-version-in-ubuntu.html)

It looked like a pretty comprehensive script, so I was hoping it would work. It took a while to install, but when it was finally finished, it still didn't work. 

aplay -l still shows the frustrating message: ```
"aplay: device_list:240: no soundcards found..."
```That was about 3 weeks ago. I really haven't had a bunch of extra time to mess with it, so sadly I've been using my Windows XP boot a lot more frequently lately. 

Does anyone have any suggestions on what I could do?

I'm almost to the point of reinstalling Ubuntu, which I know isn't a very "elegant" solution, but at this point I just want it to work!

---

### Post by indstr on 2011-09-30
Bump of desperation   ](*,)

---

### Post by indstr on 2011-10-05
Last cry for help before I reinstall Ubuntu?    :cry:

---

