---
title: "lirc sending unwanted keyboard input out of the box"
date: 2011-04-24
forum: General Help
---

### Post by trevelyan on 2011-04-24
Hi guys, im using the natty beta two, everything is working better than i expected, except for lirc.
i had everything working great on 10.10 and XBMC, so i just used the same XBMC files and the new stock files for windows media remote on lirc (was using stock lirc files on 10.10).

It's a long story so basically i was getting double input on XBMC (direction keys). where i am now is i've removed the remote control files from lirc and now i still get input from the controller when running irw in a terminal (only the direction keys, that im aware of), it works for all applications so it must be keyboard input.

obviously this shouldnt be happening, the remote should just not work anymore after removing the config files, at all. i think this is why i get the double input on XBMC. Does anyone know of anything new or something in Lirc for Natty? maybe there is a module that needs blacklisting.

Thanks.

---

### Post by trevelyan on 2011-04-24
Ummm... I've completly removed lirc and i still can use the remote to scroll web pages. i guess lirc is not the issue here, what is new in Natty that does this? i need to get rid of it.

---

### Post by trevelyan on 2011-04-24
alright, so i decided to just work around this issue and disable the lirc UP, Down, Left, Right buttons for my remote, now it works with no repeats. What the hell is that other thing receiving IR input? Maybe i'll never know. :S

---

### Post by trevelyan on 2011-04-24
oh damn, the repeat is also there for the play, pause, back, forward, stop buttons i had to disable these buttons in lirc too, and its still not working that well.

im thinking this is some new multimedia crap they thought would be nice but it's only getting in my way.

---

### Post by trevelyan on 2011-04-24
finally found the answer somewhere else.
i had to add &#8220;rmmod -f ir_rc6_decoder&#8221; to my rc.local file.

---

### Post by Kipee on 2011-04-28
Thanks, this was driving me mad.

This kind of things really shouldn't be enabled by default, at least if there exists .lircrc -file etc, which tells that lirc has been configured.

---

### Post by Hlund on 2011-04-30
Hi,

I upgraded my MythTV frontends to Mythbuntu 11.04 yesterday and now I'm also having problems with double keypresses from the remote...

I've tried your solution and the other proposed solution to place "echo lirc > /sys/class/rc/rc0/protocols" in rc.local, but if i try them the remote stops working completely in both cases.

When I get the double keypresses in mythfrontend, irw still reports only one keypress.

Any ideas?

/Hlund

---

### Post by anwmalos on 2011-04-30
The thing I love about ubuntu is that for most problems I experience, someone had the same problem before me and already found a solution.

Thank you, it works perfectly

---

### Post by kwek on 2011-05-01
> **trevelyan said:**
> finally found the answer somewhere else.
i had to add “rmmod -f ir_rc6_decoder” to my rc.local file.

Thanks, this also fixed my remote problems in xmbc. There should be an easier way to turn this off.

---

### Post by Triptol on 2011-05-10
You could blacklist the module as well, to prevent the loading of it.

---

