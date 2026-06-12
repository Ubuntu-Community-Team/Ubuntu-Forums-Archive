---
title: "can't enable terminal beep sound?"
date: 2010-09-19
forum: General Help
---

### Post by blwizard on 2010-09-19
Hello there, I've been using my girlfriend's Mackbook Pro and really like the beep sound when pressing backspace at a command prompt and really would like to have it on my ubuntu. However, I've checked "Terminal bell" option in the profile settings, but there is still no beep sound. What am I missing here?

---

### Post by WorMzy on 2010-09-19
Open up a terminal, and run 'alsamixer'. Press and hold right until you get to the Beep option:

[IMG]http://img829.imageshack.us/img829/7734/20100919135107484x265sc.png[/IMG]

It it look like this, with the "MM" below the coloured bar, then press "m" to unmute it. Press Esc and try to make the beep happen again. If it works now, then save your alsa configuration by running
```
sudo alsactl store
```

---

### Post by blwizard on 2010-09-19
> **WorMzy said:**
> Open up a terminal, and run 'alsamixer'. Press and hold right until you get to the Beep option:

[IMG]http://img829.imageshack.us/img829/7734/20100919135107484x265sc.png[/IMG]

It it look like this, with the "MM" below the coloured bar, then press "m" to unmute it. Press Esc and try to make the beep happen again. If it works now, then save your alsa configuration by running
```
sudo alsactl store
```

Thanks for the detailed reply mate, but there is still no beep sound. Beep is unmuted and volume is turn to highest.

---

### Post by WorMzy on 2010-09-19
Okay, could you check that you have the pcspkr module loaded?

```
lsmod | grep pcspkr
```

---

### Post by blwizard on 2010-09-19
I found that I didn't have this module loaded, but even after I did modprobe pcspkr, it still didn't work. I added this module to /etc/modules and restarted the system, problem persists.

Oh, here is the output for lsmod | grep pcspkr:
```
pcspkr                  1998  0 
```

---

### Post by WorMzy on 2010-09-19
I'm not sure what else you can do then. Maybe your PC just doesn't have an inbuilt speaker, or maybe you have one but Ubuntu can't use it for some reason.

You could try poking around in your BIOS settings to see if there's an option for the inbuilt speaker there which is set to disabled or something, but I've never seen an option like that before.

---

### Post by Gillingham on 2010-09-19
Hi for one reason or another the pc speaker was giving a lot of people problems so in ubuntu the modules are blacklisted by default.  

Try to see if you get a beep after adding the module without restarting the system.  As any modules you add by modprobe won't be automatically loaded on a subsequent boot.  To do that you normally have to add the module to a file /etc/modules.  However, in this case other people have had problems loading the module too early - I didn't quite follow all the arguments.  But what was recommended (and works on my 10.04 system) was to add ```
modprobe pcspkr || true
``` to /etc/rc.local file

I hope this helps

David

---

### Post by blwizard on 2010-09-21
Well, I still can't get it to work. Anyways, thanks for help ppl! I'll probably give up then.

---

