---
title: "Running command at startup - Under specific user, and in background."
date: 2011-01-31
forum: General Help
---

### Post by voltaic on 2011-01-31
I have spent some time working on this but can't quite wrap my head around this, so here it goes.

I have a perl script that I would like to run on bootup, under a specific user. The script never ends, it is am infinite loop that constantly checks for connection attempts to a specific port on the machine. I need this script to be running at all times, so I would like to just have it issued at bootup. I would also like the command to be run by a specific user on the machine, for logging purposes, process ID, etc.

for example say the machine 'stagingmachine'
user I want to issue the command 'scriptuser'
perl script I want to run '/home/scriptuser/script.pl'

I could issue the command as something like 'sudo -u scriptuser perl /home/scriptuser/script.pl'
but that doesn't run in the background....

If I try changing 'perl' to  'perl&' I get an error saying permission denied.

I have a feeling I'm overlooking something very simple here, or going about it in entirely the wrong manner, but if someone could nudge me in the right direction I'd greatly appreciate it.

Cheers!

---

### Post by drewsus on 2011-01-31
what if you put the & on the very end like so?
> sudo -u scriptuser perl /home/scriptuser/script.pl &

---

### Post by voltaic on 2011-01-31
drewsus:

I just tried that, and I think it seems to work, dropped it into rc.local and rebooted the machine, so we'll see if it's good ;)

Thanks

EDIT: seems to be working :D

---

### Post by gmargo on 2011-01-31
If you're monitoring a network port, you could launch the program from a script under **/etc/network/if-up.d/** so that the program is started when the network comes up.

---

