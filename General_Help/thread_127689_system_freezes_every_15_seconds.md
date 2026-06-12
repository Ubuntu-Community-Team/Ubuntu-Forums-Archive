---
title: "system freezes every 15 seconds"
date: 2006-02-09
forum: General Help
---

### Post by afx on 2006-02-09
My system got this annoying habbit of freezing every 15-20 seconds. It makes working in kde very uncomfortable... The mouse, sound, video, everything, freezes for a moment, and again, and again... Any suspicions?

---

### Post by schdefan on 2006-02-09
need some information about your hardware. Do you use usb mouse or keyboard. If so maybe your X,org configuration has some errors. 
Can you post the output of some logfiles by typing the following commands in a terminal
```
$ tail -n 10 /var/log/syslog
```
and
```
$ less /var/log/Xorg.0.log|grep EE
```
schdefan

---

### Post by milou on 2006-02-10
Is DMA activated ? If it isn't, it may cause such troubles (when accessing cdrom though) ...

---

### Post by afx on 2006-02-12
Servus ;-)

```
$ tail -n 10 /var/log/syslog
Feb 12 20:14:03 localhost gconfd (vanja-10936): Resolved address "xml:readwrite:/home/vanja/.gconf" to a writable configuration source at position 2
Feb 12 20:14:03 localhost gconfd (vanja-10936): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 3
Feb 12 20:14:03 localhost gconfd (vanja-10936): Resolved address "xml:readonly:/usr/share/gconf/local.defaults" to a read-only configuration source at position 4
Feb 12 20:14:03 localhost gconfd (vanja-10936): Resolved address "xml:readonly:/usr/share/gconf/cdd.defaults" to a read-only configuration source at position 5
Feb 12 20:14:03 localhost gconfd (vanja-10936): Resolved address "xml:readonly:/usr/share/gconf/debian.defaults" to a read-only configuration source at position 6
Feb 12 20:14:03 localhost gconfd (vanja-10936): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 7
Feb 12 20:15:47 localhost kernel: [4303191.980000] psmouse.c: Wheel Mouse at isa0060/serio4/input0 lost synchronization, throwing 3 bytes away.
Feb 12 20:17:01 localhost /USR/SBIN/CRON[11708]: (root) CMD (   run-parts --report /etc/cron.hourly)
Feb 12 20:19:17 localhost kernel: [4303402.274000] psmouse.c: Wheel Mouse at isa0060/serio4/input0 lost synchronization, throwing 3 bytes away.
Feb 12 20:22:17 localhost kernel: [4303582.629000] psmouse.c: Wheel Mouse at isa0060/serio4/input0 lost synchronization, throwing 3 bytes away.
root@stardestroyer:/#

```

and...
```
$ less /var/log/Xorg.0.log|grep EE
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER

```

And yes...
this psmouse.c, it must have someting do to with my (PS/2) mouse "running away" unexpectedly. I suppose it conflicts with touchpad (I have a laptop machine)... I personally think it has nothing to do with it, because I connected a USB mouse and though it doesn't do any weird things, the sound and video are still annoying... I've also noticed that the problem does not occur all the time... :confused:

---

### Post by schdefan on 2006-02-13
can you send a private message with the xorg.conf. 
schdefan

---

### Post by infernova on 2006-02-15
I had exactly the same problem when I first used Kubuntu after installation.
It took me many ways of trying this and that, and I managed to solve it.

What I did was to look up to my /etc.init.d contents
I created a folder and move all services that's unnecessary to this folder 
(I refer to one article to speed up performance - within Customization, Tips & Tricks section)

I think I moved half of them to this disable folder, and restarted my PC again.

I noticed the boot up process was slightly faster, and it solved this "constant and quick freeze every few seconds)

Care to try?

---

### Post by afx on 2006-02-15
I would like to... but I don't know what they actually are for! I might mess things up?!

---

### Post by afx on 2006-02-19
I shut down some of the services I really don't need but the problem persists... It's really killing me. I'm having thoughts on reinstalling the whole system which is really pain in the.... Help!

---

