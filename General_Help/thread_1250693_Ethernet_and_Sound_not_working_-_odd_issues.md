---
title: "Ethernet and Sound not working - odd issues"
date: 2009-08-26
forum: General Help
---

### Post by charliehorse55 on 2009-08-26
As the title suggests, my Ethernet and sound does not work. 

Both of these items originally worked on a fresh install of 64 bit 9.04. 


I moved my entire boot dir from one hard to another. 

I used to have only a 1 TB drive. Now I have an SSD and a 1 TB. 

I have correctly setup fstab to mount the SSD to "/" and the 1 TB to "/home/"

Only problem is, after this upgrade, my ethernet and sound not longer work. 

However, right after boot if I run ```

sudo /etc/init.d/networking restart

```

My Ethernet works again. I've added my correct sound module, snd-hda-intel to /etc/modules

And going to the sound panel shows "ALSA Intel HDA Audio" or something. When I click test - It gives me an error 

"Could not open audio device for playback."

Again, both of these things worked on my original install, but broke when I transferred by boot directory to my SSD.

Maybe there is a way to rescan my hardware and re-add the support for my ethernet and sound?

Thanks in Advance,

--Evan


EDIT: I went to use pidgin and every time I send a message to someone, it crashes!

---

### Post by soapBAR2 on 2009-08-26
It's possible that the correct modules aren't loading. If I correctly understand what's happening here, it seems that your system is trying to get the modules from somewhere they aren't anymore. If you use

```
dmesg
```

It will give you the system logs. Unfortunately, the system logs are quite large, and most of it won't be useful here - so if you could peruse it and post any useful information (I imagine there'll be some error messages related to your ethernet and sound card), that would be great. Some other useful information would be the outputs to

```
lspci
```

or the relevant sections of

```
lshw
```

Alternatively, you could just add the /etc/init.d/networking restart command to your autostart (or to cron), and work out what driver your card uses and add a modprobe command to autostart. It wouldn't be pretty, but it'd get the job done ;)

---

