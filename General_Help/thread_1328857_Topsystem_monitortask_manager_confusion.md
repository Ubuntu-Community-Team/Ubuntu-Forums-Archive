---
title: "Top/system monitor/task manager confusion"
date: 2009-11-16
forum: General Help
---

### Post by rob86 on 2009-11-16
I notice that sometimes weird things happen, my computer starts going very slow and becomes unresponsive, my CPU panel monitors start showing full cpu usage and when I try to find the culprit, it's not so easy. When I open up Task manager (either xfce's or Gnomes system monitor)  it shows "CPU USAGE:100%" but when I looked at the list of processes, and sort by CPU, it looks like hardly anything is using much CPU. For example, the most active programs will be like, 7%, 3%, 2% 1%, and in general, it doesn't just doesn't add up to the 100% something is obviously using. When I open up the CLI top, it acts like nothing is wrong, it will say something like CPU USAGE:12% or something really low, considering my computer lights are flashing non stop and takes 2 minutes just to switch to  tty1 or another workspace . 

Sometimes, like right now, I have a good idea what's causing the problem. In this instance, it was obviously the large IDE I had open. According to any of my process monitors, this app was fluctuating between using a mere 35% and 0% despite the total usage staying at a constant 100%. Terminating this process freed my CPU and it went back to normal, back down to a constant <5%.

I don't get it? Why do the task/process managers on Ubuntu/Linux not seem to work right? When it says 100% usage, that seems to be right, because my computer is slowed to a crawl, but nothing in the process ever adds up to 100%.

---

### Post by r+9 on 2010-01-11
I think there are a lot of folks with this issue, I run into it a lot, sometimes I fix it, sometimes I'm frustrated.

whatever is messing with things is not showing up on top.

---

### Post by rnerwein on 2010-01-11
hi
i'am not really sure what's the behavior for the differents cause, but i think thats the way how the monitors retriefe the values. i have written my own monitor and this one shows me all the 9 possible cpu states wich are: user user_nice kernel wait idle iowait interrupts softinterrupts stolen_time and guest_time. the last 5 values comes first with kernel 2.6 and up. it seems that those values are not noticed from some monitors (i have to change my too). rob86 say the lights of his box are flashing non stop --> this looks like interrupts ??. did you get a hw problem rob86 - check your /var/log/messages kern.log and execute: demesg | less or so. for description of proc use:           man 5 proc
ciao

---

