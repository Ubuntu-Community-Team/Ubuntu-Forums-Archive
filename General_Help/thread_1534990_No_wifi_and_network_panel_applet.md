---
title: "No wifi and network panel applet"
date: 2010-07-20
forum: General Help
---

### Post by chaosx9 on 2010-07-20
Hi everyone:

Basically, I chose to give Ubuntu Studio another try (after it had annoyed me with it's lack of wifi), but the problem is that there's no network manager applet in the indicator area (i added it in the top right, the panel's set up as it would be in normal Ubuntu)

Using Wifi Radar, i think that the wifi card works in the preempt kernel, it's just that i don't want to use Wifi Radar all the time, can prove to be annoying.

When i start nm-applet, a small space opens up in the indicator applet. I'm not sure if that's something important.

Has someone managed to get this to work? (i've installed network-manager and network-manager-applet)

---

### Post by varunendra on 2010-07-21
Have you tried -> Upper panel>Right Click>Add to Panel....>Notification Area

If this doesn't help, please post a screenshot of your desktop, and output of:
```
ps -ef
```

---

### Post by claracc on 2010-07-21
I would use wicd to control the wifi.

You can use synaptic to install it. In karmic koala, when you click on install wicd through synaptic, automatically uninstalls gnome network manager and installs wicd.

---

### Post by chaosx9 on 2010-07-21
I, somehow, managed to fix the problem.

The tiny space that was made when i started nm-applet was the applet in the indicator applet. Maybe it didn't have an icon or something. I clicked on the small space (took about 5 mins to get the pointer right) and the menu for the connections came up!

I'll mark this as solved

Thanks for the help guys

---

### Post by dabnotu on 2010-09-10
installed ubuntu studio 10.04 with a physical wlan connection & operating modem i.e. internet connection open
used this connection once the installation was complete to install wicd via the synaptic package manager
worked like a charm... wicd identifies the wifi connection which allows the network manager to switch between connections
can't remember where i found the wicd tip, but my (linux) hat is off to him or her
enjoying my new installation with the handy wireless connection
peace

---

