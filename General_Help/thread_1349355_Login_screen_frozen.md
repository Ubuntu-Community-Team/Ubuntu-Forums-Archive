---
title: "Login screen frozen"
date: 2009-12-08
forum: General Help
---

### Post by Cyric on 2009-12-08
Hey guys,

I've been running Ubuntu 9.10 on my laptop ever since it came out now but I suddenly can't login anymore. My battery is broken for sometime now and when my cable gets plugged out my laptop goes off in an instant. This happened to me while doing software upgrades and now when I reach the login screen it looks old school broken white and blue and neither my mouse nor my keyboard works. At the time of the crash my laptop was acting as a synergy client, maybe that broke my keyboard/mouse?

I've tried running it in recovery mode which gives me the Recovery menu but then it tries to give an error message about how it can't mount my network drive through the screen and throws me into a commandline, rendering the recovery menu unusable.

Anyone know what I can do to fix this besides reinstalling?

Edit: From the broken recovery mode that drops me to a maintenance commandline i've managed to use 'startx' to get something graphical going. It now shows a normal desktop for root user but my keyboard and mouse still don't work :(

---

### Post by alienclone on 2009-12-08
maybe try an external mouse while in the graphic interface and reinstall the software you were upgrading

---

### Post by Cyric on 2009-12-08
Tried using an external keyboard and mouse but it didn't help, it still froze right away. I wasnt updating anything specific, it was just the standard weekly ubuntu updates.

I was able to reach a console with networking through the menu somehow. Does anyone know how I can reset any/all keyboard options/features?

---

### Post by bchurchill on 2009-12-08
> **Cyric said:**
> 
Edit: From the broken recovery mode that drops me to a maintenance commandline i've managed to use 'startx' to get something graphical going. It now shows a normal desktop for root user but my keyboard and mouse still don't work :(

Hopefully you won't need to reinstall; there are quite a few things worth trying.

First, try starting the same synergy server you had on before, with the same IP address, then starting your computer and see if synergy can control your mouse.  It sounds like every time you start the x server it tries to connect back to that synergy server.

If that doesn't work, then:

From the shell, run the following commands and type up the output so we can get an idea what's going on:

ping 4.2.2.4  (determine if internet is working - this is a standard DNS server)
lsof | grep -i synergy
cat /etc/fstab
dmesg | tail -n25
tail -n25 /var/log/syslog

After that, plug in an external mouse/keyboard and run the last two commands again.  Post any additional lines that show up in the output of either command.

---

### Post by Cyric on 2009-12-08
There doesnt seem to be any synergy running and those tails only show networking stuff (ill try running root without network :P )

Arent there any keyboard/mouse settings files I can delete or reset?

Edit: I have a fresh ubuntu running next to my not working one now so I can edit most files with ease. I can even overwrite folders from my fresh install back to my broken one if I knew what the important files were that could influence this.

Edit2: Found this page: [https://wiki.ubuntu.com/X/Config/Input](https://wiki.ubuntu.com/X/Config/Input)
Tried the troubleshooting part to put GDM on a higher priority but sadly that didn't help.

Edit3: Reinstalling xserver-xorg-input-all according to this bug from last year which has the same symptoms didnt work either.
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/271138](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/271138)

---

### Post by hart02 on 2010-03-16
I had a similar issue where my keyboard would be frozen but my mouse worked at login. As it turns out this is a dbus issue. I wrote something as a tutorial but it ended up in general help.I think it is because it is a workaround and not a permanent fix. You will have to do it at every reboot. You may find it [here]("http://ubuntuforums.org/showthread.php?t=1430176&highlight=keyboard+frozen+login"). Hope this helps.:D

---

