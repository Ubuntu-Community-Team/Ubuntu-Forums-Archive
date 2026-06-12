---
title: "Periodic &quot;high&quot; load every 21 minutes?"
date: 2011-03-10
forum: General Help
---

### Post by bsh on 2011-03-10
Hello,
I see this with Lucid 32bit:
[IMG]http://img814.imageshack.us/img814/9013/load017hourpng1623.png[/IMG]
Happens every 21 minutes roughly. I can not connect this with anything. There's no corn job that would run ath these frequency. I was watching processes with everytihng I can imagine and didn't see anything (like a swarm of small processes or something) popping up during these spikes.
I even disabled everything down to a mere console, and ran my own script to gather load statistics with higher resolution, and the spikes are still there.
I also installed lucid in a VirtualBox, and found the same spikes with the default install. Also I got confirmation from mates, who found this same behaviour.
Anyone could explain this? I know it's not a huge performance hit, but I'm curious what's causing this and how to "fix" it if possible. (Also to mention, this renders my webmin graphs of daily/weekly/monthly/yearly loads practically useless.)
Thanks in advance.

---

### Post by no2498 on 2011-03-10
you may try htop
to see if something hit your eye
type it in a terminal it tells you how to install it
after installed type htop click enter
also comes up in system tools

---

### Post by bsh on 2011-03-10
i tried that obviously, alongside iotop and atop and everything i could think of.
i think it's not a userspace process, that's why i didn't spot it yet. even thought of a backdoor, so i installed a clean install inside a VM and even the default install had this behaviour.

---

