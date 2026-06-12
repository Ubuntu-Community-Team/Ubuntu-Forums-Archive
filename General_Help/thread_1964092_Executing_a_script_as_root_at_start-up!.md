---
title: "Executing a script as root at start-up!"
date: 2012-04-23
forum: General Help
---

### Post by MutantJohn on 2012-04-23
Okay, so I've started undervolting and every time I start-up, my cpufreq's ondemand governor sets the CPU scaling range from 3.2Ghz to 3.2Ghz.

Now, it's a simple fix for me to type in

```
cpufreq-set -c 0 -g ondemand -u 3.20Ghz -d 0.80Ghz

```

And then repeat that for processors 1,2 and 3 as I'm using one of them fancy quad-cores.

So, what I think will be a successful workaround is if I bust open gedit and have it run this script file on start-up every time. But I need to run it as root as well.

Does anyone know how to do this? Or, does anyone have any idea what happened to my cpufreq settings that it resets every time I restart the computer?

---

### Post by 2F4U on 2012-04-23
Have you already tried to put your code into /etc/rc.local?

---

### Post by JKyleOKC on 2012-04-23
Simply add your commands to the /etc/rc.local file, just before the line that reads "exit 0" and they will automatically run as root the next time the system boots. That's the whole purpose of this file!

---

### Post by MutantJohn on 2012-04-24
Thank you so much, you guys. It worked perfectly! 

And I'll never cease to be amazed at how far ahead the linux distro programmers have thought ahead. It's almost like they've done this before and count on people needing to make their own workarounds...

Either way, they're worthy of the PhD's or experience they've gathered.

---

