---
title: "Memory management: how can I make Ubuntu run like new again?"
date: 2012-06-11
forum: General Help
---

### Post by hubertofliege on 2012-06-11
My computer is running slowly.  I think it is wasting memory.

I'm running 11.04 on a 7 year old Dell Latitude D610 laptop.  When I first installed Ubuntu, it breathed new life into a computer that had slowed to the limits of usability.  It slowed down over time, but it returned to its best performance when I formatted it again while I was upgrading to 11.04.

Its gotten pretty slow once more.  I suspect I could restore it again the way I did before, but is there a way to remove all the crap slowing down my computer without wiping the whole thing clean?

---

### Post by zombifier25 on 2012-06-11
You could install BleachBit to clean the junk files in your system. You would be surprised at how much junk it collects.

---

### Post by snowpine on 2012-06-11
My advice is to collect data so that you can approach the task intelligently. If you use the System Monitor or terminal command **top** you can see what the top processes are in terms of CPU and RAM usage. Post back with the results, and we might be able to give you advice which services can be disabled to improve performance. :)

Also keep in mind that 11.04 is a few releases out of date and will be "end of life" in a few months. You might try the current 12.04, which is a long term support through April 2017, using a lightweight desktop such as Xfce or LXDE. That would be my recommendation for a good balance between speed and long-term stability.

A final word of advice is that hardware ages quickly these days (you may have heard of "Moore's law"). It may just be that your computer seems "slow" because it is slow compared to modern hardware. A hardware upgrade is the single best way to improve performance. ;)

---

### Post by black veils on 2012-06-12
> **snowpine said:**
> 
Also keep in mind that 11.04 is a few releases out of date and will be "end of life" in a few months. You might try the current 12.04, which is a long term support through April 2017, using a lightweight desktop such as Xfce or LXDE. That would be my recommendation for a good balance between speed and long-term stability.



yes these are good points. you want to freshen the system, but you would be best insalling anew. as for speed, try Xubuntu (with xfce desktop), it is like gnome 2 but more integrated and intuitive, light on resources but with plenty of settings.

if you dont want 12.04 while it is still potentially buggy, you could install 11.10 of Xubuntu, which end of life is april 2013. 

performance can decrease due to the apps you install, all the libraries they bring.

---

### Post by hubertofliege on 2012-06-14
I think I'll probably just upgrade to 12.04 soon.  Still, I'm interested in understanding the causes for my own computer education.

Its not just relative to a new computer.  When I first turn my computer on, it runs rather swiftly.  As the day goes on, it tends to slow down.  Right now, its running well.  I'm using 59% of my memory (around 300 of 500 MiB) to browse the internet.  I'm only using 14.7% of my swap (~75 of 500 MiB).  

Is there an easy way to output the processes list besides typing it out? Thx.

---

### Post by Henkdroid on 2012-06-14
> around 300 of 500 MiB
This seems like hardly any memory to go on, try Xubuntu or Lubuntu. I think Ubuntu recommends 1GiB in memory for Ubuntu.

---

