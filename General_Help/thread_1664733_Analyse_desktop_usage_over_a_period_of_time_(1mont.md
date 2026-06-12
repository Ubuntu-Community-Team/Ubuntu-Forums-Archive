---
title: "Analyse desktop usage over a period of time (1month+)"
date: 2011-01-11
forum: General Help
---

### Post by prshah on 2011-01-11
Hello,

I want to analyse the usage of my desktop machine over a period of time, such as a month+.

Background: I usually leave my home desktop machine running 24/7, since I often need to access it for information from work. However, now I have finally put in a modem, got it recognised in ubuntu, and tested the Wake-on-Ring capabilities. So now I can turn it off (hibernate/suspend) during long periods of disuse.

However, I don't want to use the fixed options for power saving (Eg, power down after 30 mins of inactivity etc). I want to study the usage of the machine over a period of time (since even my wife uses it at times), and then find the "black" periods when there is very little chance of it being used. I will then use cron-timed commands to put it to sleep appropriately.

I would like a graphical representation of computer activity (preferably hourly) over a period of a month or so. By looking at the graph, I should be able to quickly spot periods of inactivity (Eg, Mon-Sat @2:00pm ~ 4:30pm, etc) and down the machine accordingly.

I also would like suggestions as to what activity to monitor: CPU? memory? The CPU usage is usually very minimal, with practically no spikes, so I believe I won't get a true picture from that. Memory usage (of 2GB) is practically flat, even with swappiness set low. GPU thermals are incorrectly reported. Performance is set to on-demand, with rare (and very short-lived) shifts to a higher clock frequency.

Machine specs: Pentium Dual Core 1.6GHz / 2 x SATA HDDs / 2 x DVD/RW drives / 2GB RAM / etc, Tech-level: Intermediate-high. Suggestions welcomed.

---

