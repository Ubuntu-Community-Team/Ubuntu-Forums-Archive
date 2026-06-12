---
title: "cpu always consumes above 5% when idling"
date: 2009-09-22
forum: General Help
---

### Post by chrone on 2009-09-22
i start noticing this from ubuntu 8.04 and 9.04 in vary machine setup with intel 945g, g31, ati x200, and intel 945 in intel atom dual-core.

it seems ubuntu when idling still using much cpu usage around 20% or so.

how to make cpu uses near 0% when idling such as in windows machine?

i thought this had to be related with the gnome/X11/Xorg rendered through cpu instead of gpu.

is anyone having the same symptom?

---

### Post by jerrrys on 2009-09-22
is this the system monitor your looking at?  if so, in terminal enter **top **and see what you get

---

### Post by doas777 on 2009-09-22
well, first, how are you measuring CPU usage? use top from a terminal if you are not already.
```
sudo top
```

Gnome-System-Monitor (gsm) uses a lot of resources, so usually you are seeing the effect of measuring nothing.

as for your CPU, is it beefy or underpowered? an OS is never actually Idle, so if your CPU is weak, it may actually be taking up 5% of capacity to run, which on a beefier PC looks more like .25 or .5%.

hope that helps,

---

### Post by chrone on 2009-09-22
> **jerrrys said:**
> is this the system monitor your looking at?  if so, in terminal enter **top **and see what you get

> **doas777 said:**
> well, first, how are you measuring CPU usage? use top from a terminal if you are not already.
```
sudo top
```

Gnome-System-Monitor (gsm) uses a lot of resources, so usually you are seeing the effect of measuring nothing.

as for your CPU, is it beefy or underpowered? an OS is never actually Idle, so if your CPU is weak, it may actually be taking up 5% of capacity to run, which on a beefier PC looks more like .25 or .5%.

hope that helps,

oh my stupidity, it seems the system monitor consumes the cpu. lol

while monitoring through top without the system monitor, the Xorg only consumes 0-1% while sometimes spikes to 8-9%.

thanks all. it's getting all cleared here. hope in the next version of ubuntu or gnome the system monitor won't taking much cpu usage such as task manager in windows. :popcorn:

---

### Post by doas777 on 2009-09-22
if there was ever an system utilitiy I would love to see ported to linux from windows, it would be process explorer. hands down the best process info frontend i've ever seen.

---

### Post by chrone on 2009-09-22
> **doas777 said:**
> if there was ever an system utilitiy I would love to see ported to linux from windows, it would be process explorer. hands down the best process info frontend i've ever seen.

couldn't agree more. but somehow i could not manage to kill multiple process with process explorer. I found process viewer to much simpler and useful, unfortunately it could not detect x64 code. used to use process viewer to kill multiple virus process running in the memory back then. :p

---

### Post by MC707 on 2009-09-22
> **doas777 said:**
> if there was ever an system utilitiy I would love to see ported to linux from windows, it would be process explorer. hands down the best process info frontend i've ever seen.

Hmmm I find both gsm and task manager quite the same thing. Just some basic differences... maybe the cpu usage is better for task manager? Who knows. They both fulfil their roles to me.

---

### Post by chrone on 2009-09-22
> **MC707 said:**
> Hmmm I find both gsm and task manager quite the same thing. Just some basic differences... maybe the cpu usage is better for task manager? Who knows. They both fulfil their roles to me.

yeah i love the way system monitor evolves. it's getting easier and informative each release. :)

---

### Post by MC707 on 2009-09-22
> **chrone said:**
> yeah i love the way system monitor evolves. it's getting easier and informative each release. :)

Indeed. I am holding my breath for Karmic!

---

### Post by doas777 on 2009-09-22
> **MC707 said:**
> Hmmm I find both gsm and task manager quite the same thing. Just some basic differences... maybe the cpu usage is better for task manager? Who knows. They both fulfil their roles to me.


fair enough.
Task manager and process explorer are not at all alike however.
[http://technet.microsoft.com/en-us/sysinternals/bb896653.aspx](http://technet.microsoft.com/en-us/sysinternals/bb896653.aspx)

---

### Post by MC707 on 2009-09-22
> **doas777 said:**
> fair enough.
Task manager and process explorer are not at all alike however.
[http://technet.microsoft.com/en-us/sysinternals/bb896653.aspx](http://technet.microsoft.com/en-us/sysinternals/bb896653.aspx)

Oh yes definitely. My bad, I confused task manager and process explorer :oops: they are different indeed. I think functionality from process explorer *could* be emulated in system monitor, rather than making a full port from process explorer. What do you think?

---

### Post by Slim Odds on 2009-09-22
> **doas777 said:**
> well, first, how are you measuring CPU usage? use top from a terminal if you are not already.
```
sudo top
```Gnome-System-Monitor (gsm) uses a lot of resources, so usually you are seeing the effect of measuring nothing.

There is no need to run top with sudo.

also, try htop

---

### Post by doas777 on 2009-09-22
> **MC707 said:**
> Oh yes definitely. My bad, I confused task manager and process explorer :oops: they are different indeed. I think functionality from process explorer *could* be emulated in system monitor, rather than making a full port from process explorer. What do you think?

very likely. the frontend is mostly there. good idea

---

### Post by doas777 on 2009-09-22
> **Slim Odds said:**
> There is no need to run top with sudo.

also, try htop

I do, because some services do not show up when running as a normal user. it's like ps -ef as sudo versus as normal user.

---

### Post by MC707 on 2009-09-22
> **doas777 said:**
> very likely. the frontend is mostly there. good idea

Sounds like a plan! :cool: ;)

---

