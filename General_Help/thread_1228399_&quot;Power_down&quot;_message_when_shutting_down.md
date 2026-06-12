---
title: "&quot;Power down&quot; message when shutting down"
date: 2009-07-31
forum: General Help
---

### Post by jan0ng on 2009-07-31
Hi to all,  I'm a new user of ubuntu.  I've noticed that every time I shut down my notebook, after the ubuntu flash screen, it appears a message with series of numbers and the word "power down"  

Another problem I'm encountering is the kopete application installed from synaptic package mgr,  I can't connect to yahoo.

Really appreciate your comments/recommendations...  Thanks:D

---

### Post by SuaSwe on 2009-07-31
The "Power Down" message sounds a lot like a problem Alsa can cause when wireless is enabled and running during shutdown. I'm guessing that you have to power the computer down manually once the message comes up?

I have heard of this fix working for several people:

> 
Put

ifconfig wlan0 down
at the beginning of stop in: /etc/init.d/alsa-utils

See [[COLOR="Blue"]this thread[/COLOR]]("http://ubuntuforums.org/archive/index.php/t-967165.html") for more information.

---

### Post by jan0ng on 2009-08-01
> **SuaSwe said:**
> The "Power Down" message sounds a lot like a problem Alsa can cause when wireless is enabled and running during shutdown. I'm guessing that you have to power the computer down manually once the message comes up?

I have heard of this fix working for several people:



See [[COLOR=Blue]this thread[/COLOR]]("http://ubuntuforums.org/archive/index.php/t-967165.html") for more information.

Thanks SuaSwe but it did not work... do you have any 
other options?

---

### Post by SuaSwe on 2009-08-01
Hello again!

What exactly did you try? Also, what's your laptop specs? Make/model/distro etc etc. :)

Do you see any legible command line-esque text before the Power Down message? It could give clues about what's going on with it.

---

### Post by jan0ng on 2009-08-01
> **SuaSwe said:**
> Hello again!

What exactly did you try? Also, what's your laptop specs? Make/model/distro etc etc. :)

Do you see any legible command line-esque text before the Power Down message? It could give clues about what's going on with it.

This one:
Put:
ifconfig wlan0 down
at the beginning  of stop in: /etc/init.d/alsa-utils

To tell you honestly, I'm just a new user of ubuntu..

my notebook is Compaq V3770tu model  core 2 duo, 64G SSD, I've created a partition of 20g for my ubuntu and 2g swap.

really thank you for your assistance.

---

### Post by adamitj on 2009-08-01
Compaq and HP notebooks have a problem related to ACPI. In this case, if you are running older kernel versions OR you are disconnected from AC power, the computer hangs up at boot (sometimes) and every time at "power down" message.

To check out if is an ACPI problem, try to type any keyboard key repeatedly when "power down" message appears (of course, don't press power button). If the computer can turns off, it is the ACPI problem, and then you need to add a "acpi=noirq" parameter into your grub boot file, like this:```
title		Ubuntu 9.04, kernel 2.6.28-14-generic
uuid		f0eb6a78-1980-4ca5-b475-ea31840ee2a5
kernel		/vmlinuz-2.6.28-14-generic root=UUID=6df47927-d7f0-4cd1-9024-74ed74ed0bac ro locale=pt_BR quiet acpi=noirq splash 
initrd		/initrd.img-2.6.28-14-generic
quiet
```

---

