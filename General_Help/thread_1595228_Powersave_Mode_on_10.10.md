---
title: "Powersave Mode on 10.10"
date: 2010-10-13
forum: General Help
---

### Post by syga on 2010-10-13
Trying to set my cpu to Powersave using the CPU Frequency Scaling applet. When I set it to powersave, it goes back to ondemand on its own. 

On the earlier versions of Ubuntu, I used to be able to set it from the main menu: system>powermanagement, but with 10.10, I don't get that option. Is there any way that I can set it to powersave permanently?

I was also able to set it with Ubuntu Tweak, but it does not have that option either.

---

### Post by gmc on 2010-12-12
Hi,

I don't know if you found a solution, but here's how it's done.

1) Edit /etc/init.d/ondemand (you need to be root).
2) Scroll down to line #26 which read(s) as follows:

   -n ondemand > $CPUFREQ

3) Replace the 'ondemand' with 'powersave' (no quotations)
4) Save the file
5) Either reboot or issue the following 'sudo /etc/init.d/ondemand start'

There you go. Note that it is possible for this to be changed back after a system software update.

Enjoy
Gord

---

