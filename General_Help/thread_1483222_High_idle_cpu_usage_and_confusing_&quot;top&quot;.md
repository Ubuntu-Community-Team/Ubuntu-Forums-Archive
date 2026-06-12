---
title: "High idle cpu usage and confusing &quot;top&quot;"
date: 2010-05-14
forum: General Help
---

### Post by cbecker78 on 2010-05-14
I am having some issues with performance with ubuntu server installed on a toshiba laptop that is about 10 years old. specs: pentium iii, 1.00 GHz, 380 MB ram.  xorg and gnome are installed. The OS is slow and fairly unresponsive (more so than WinXP), and seems to heat up more than i would prefer.

If I look at "top", it shows that about 5-10 % cpu is being used by user (us), and ~20% by system (sy), when nothing else is running. So the sum works out to around 25-30% and that agrees with the CPU usage that conky reports.

HOWEVER, if I add the %CPU for individual tasks, either from top or conky, I get a value that is much lower than that...  I'm guessing whatever these processes are that I can't see are giving me performance issues.

How can I see them, and why aren't they shown by default?  Or am I misunderstanding something?  Thanks for any help!

Example top (abbreviated to show only processes which report a %CPU greater than 0.0 :

```
top - 16:39:50 up 35 min, 2 users, load average: 0.60, 0.56, 0.48

  Cpu(s): 6.0%us, 18.3%sy, 0.0%ni, 64.5%id, 11.3%wa, 0.0%hi, 0.0%si, 0.0%st
  Mem: 377252k total, 261812k used, 115440k free, 9956k buffers
  Swap: 714884k total, 0k used, 714884k free, 126412k cached

  PID   | USER | %CPU    | %MEM     | COMMAND
  3708 | root   | 6.3     | 0.0     | ntos_wq
  4588 | root   | 5.6     | 4.2     | Xorg
  4811 | cbeck  | 0.7     | 4.4     | sensors-applet
  4548 | root   | 0.3     | 0.3     | hald-addon-stor
  4937 | cbeck  | 0.3     | 3.8     | gnome-terminal
  5066 | cbeck  | 0.3     | 0.7     | conky
  5072 | cbeck  | 0.3     | 0.3     | top
```

---

### Post by cbecker78 on 2010-05-16
Bump... anyone?

---

### Post by Oasu4g on 2010-05-16
What version of Ubuntu are you using? And also, if your PC is running slowly, I would look at another DE other than Gnome or KDE. Xfce is a good choice.

I have been wondering about this as well. Is it just that all of the processes add up, or are there other things running in the background that also take up CPU resources?

---

### Post by cbecker78 on 2010-05-16
Thanks for the suggestion... I actually went with gnome on this laptop because network manager seems to be the only one that can satisfy all the necessary fields to connect to our wireless MS enterprise network at work.  I figure if the laptop can handle WinXP ok, it ought to be ok with gnome...:confused:

---

### Post by Oasu4g on 2010-05-16
Sounds reasonable to me. Gnome works better than XP on my desktop PC. You don't have desktop effects enabled by any chance do you?

It would also really help if you could let us know what version of Ubuntu you're using.

---

### Post by cbecker78 on 2010-05-16
Sure thing (i missed that request on your first post, sorry), and thanks for the interest and help.  This is Ubuntu 8.04 server edition on a toshiba 1805 satellite.  And no, no desktop effects are enabled.

---

### Post by Oasu4g on 2010-05-16
Hmm... I'm sorry I can't help you any more with your original question. I'm curious to see if someone has a good answer to it though. Like I said I've been wondering about it myself.

Have you tried newer versions of Ubuntu? It might just be my imagination but I think Jaunty is faster than 8.04. You should get confirmation on that though. I would hate for you to upgrade and find out it really *was* just my imagination.

30% doesn't sound *too* unreasonable on a laptop like that...

---

### Post by cbecker78 on 2010-05-17
True, 30% may be as expected, but it just seems a little too high for idle.  I guess if it's a bunch of invisible background processes adding up, it is what it is.  But then, if it is all from one, then maybe I can fix it.

I haven't tried any other versions yet because a problem with the graphical environment out of the box prevents any live cds from loading.  So I'll probably hold out for a bit and see if someone might come along and explian the differences between cpu(s) and %cpu in top before I try.

Thanks again!

---

### Post by cbecker78 on 2010-05-18
I still don't have an answer to why the two cpu(s) don't add up to the right numbers if you add total %cpu for individual processes, I have since learned that the slugishness I was experiencing is being caused by my wireless networking.  If I boot up and disable wireless, the %sy value in top stays down around 0.3-0.7%, the cpu stays cool, and the desktop stays responsive.  

I don't know if this is an issue with network manager, the nm-applet, ndiswrapper, or the wireless card itself... but I guess one of those.  

Does anyone have any ideas how to start troubleshooting which one it is?

---

### Post by rnerwein on 2010-05-18
hi
the cpu usage comes from the ntos_wq - this process ( it's not really a process ). ntos_wq comes from the ndiswrapper.
as cbecker78 say the usage iis going down when he stops his network.
if you add the cpu usage of your processes you ain't get - in your behavior - 100%. that's because you also have
11.3 % wait-io and this value depends not to a single process.
i hope this will help you a little bit 
ciao

---

### Post by cbecker78 on 2010-05-19
> **rnerwein said:**
> hi
the cpu usage comes from the ntos_wq - this process ( it's not really a process ). ntos_wq comes from the ndiswrapper.
as cbecker78 say the usage iis going down when he stops his network.
if you add the cpu usage of your processes you ain't get - in your behavior - 100%. that's because you also have
11.3 % wait-io and this value depends not to a single process.
i hope this will help you a little bit 
ciao

Hi, thanks for the input. But you are misunderstanding my question just a bit i think.  I know if you add all the %s on CPU(s) you get 100%.  Where I am confused is why the sy and us can not be calculated from the individual processes.  

For example, you say my cpu usage is coming from ntos_wq, but Top shows 6.3% fro ntos_wq, whereas sys is 18%.  In fact, if you add all of the processes up, the total is still less than even just sy.  

Sorry If I'm just being dense or missing something obvious here.

---

### Post by chris1379 on 2010-05-19
Have you tried installing and running "htop" instead? I don't have the answer to your question but that may give you a little more insight. What I can tell you is I am running Ubuntu Lucid on a 700 MHz PIII laptop with 384 MB and it does just fine.

---

### Post by pizza-is-good on 2010-05-19
I am wondering, is there a particular reason as to why you want ubuntu server on a laptop. I've never used it, but it occurs to me that the server version might require more powerful hardware than that of a laptop. I could be wrong, so please correct me if I am.

~pizza

---

### Post by cbecker78 on 2010-05-20
> but it occurs to me that the server version might require more powerful hardware than that of a laptop. I could be wrong, so please correct me if I am.

As far as I know, the backbone of both the server and desktop are the same.  I installed server because a lot of what I need it to do can be done from scripts in a text console.  the other part of the reason was because I wanted gnome as lightweight as possible and it was easier to install it vanilla than trying to remove and deactivate a bunch of software and unnecessary services that I would never have a need for.  It's actually quite responsive if I don't activate the wireless internet.

> Have you tried installing and running "htop" instead? I don't have the answer to your question but that may give you a little more insight. What I can tell you is I am running Ubuntu Lucid on a 700 MHz PIII laptop with 384 MB and it does just fine.

Thanks for the input, I'll give HTOP a try and report back later today...

---

