---
title: "Shutdown takes unusually long"
date: 2011-05-16
forum: General Help
---

### Post by Rodayo on 2011-05-16
Using Natty(not beta)

So as the title says shutdown time takes unusually long. Upwards of 4-6 minutes. 

I'm used to my linux systems taking about 10 seconds to shutdown, 20 tops. In fact this problem seemed to stem from the natty release because I didn't have this issue with the betas or 10.10....

It seems the longer I use my laptop the longer it takes to shutdown. When I do a quick task like a file backup the shutdown takes 10seconds or so, but if I open up a browser and start surfing for a few hours it takes more like 5 minutes.

Is anyone else having this issue?

---

### Post by ChipOManiac on 2011-05-16
I had a problem like this on my Kubuntu system once... it turns out that «GTK-KDE4» was running renegade and eating up disk... does the disk activuty indicator flash a lot or keep on?

---

### Post by CrushingYourHead on 2011-05-16
Throughout the last several versions of Ubuntu, I have had variable shutdown times as well that I haven't really put much thought into. But I'm talking a range of from 3 to 10 seconds. 5 to 10 minutes??

I would suggest temporarily paring down your running programs at boot time (startup application) and seeing if that improves anything. I always found my systems much quicker to boot/shutdown the less unneeded crap I have running.

---

### Post by Rodayo on 2011-05-16
> **ChipOManiac said:**
> I had a problem like this on my Kubuntu system once... it turns out that «GTK-KDE4» was running renegade and eating up disk... does the disk activuty indicator flash a lot or keep on?

I'm sorry what do you mean by "disk activity indicator"?

But I had a though, is there a way I can call a shutdown from the terminal with verbose messages. Maybe that can pinpoint what specifically is taking long.

---

### Post by Rodayo on 2011-05-16
> **CrushingYourHead said:**
> Throughout the last several versions of Ubuntu, I have had variable shutdown times as well that I haven't really put much thought into. But I'm talking a range of from 3 to 10 seconds. 5 to 10 minutes??

I would suggest temporarily paring down your running programs at boot time (startup application) and seeing if that improves anything. I always found my systems much quicker to boot/shutdown the less unneeded crap I have running.

I doubt it's the startup applications. I should've pointed out the issue started right form the get-go when I installed the natty release, so even when I didn't have additional software.

---

### Post by bagender on 2011-05-17
> **Rodayo said:**
> Using Natty(not beta)

So as the title says shutdown time takes unusually long. Upwards of 4-6 minutes. 

I'm used to my linux systems taking about 10 seconds to shutdown, 20 tops. In fact this problem seemed to stem from the natty release because I didn't have this issue with the betas or 10.10....

It seems the longer I use my laptop the longer it takes to shutdown. When I do a quick task like a file backup the shutdown takes 10seconds or so, but if I open up a browser and start surfing for a few hours it takes more like 5 minutes.

Is anyone else having this issue?

Smoke less weed. Or more. See if that helps.

---

### Post by CrushingYourHead on 2011-05-17
> **Rodayo said:**
> I doubt it's the startup applications. I should've pointed out the issue started right form the get-go when I installed the natty release, so even when I didn't have additional software.

Yeah, probably not. But I've found that even with a fresh install, there are services running that you may have no use for. Maybe one of those new Natty services is causing your hiccup. Un-checking a couple to test is easy work. I started going bare bones down to:

Network-Manager
Power-Manager
PulseAudio Sound System

Works like a charm. Snappy boot-up and shutdown.

---

