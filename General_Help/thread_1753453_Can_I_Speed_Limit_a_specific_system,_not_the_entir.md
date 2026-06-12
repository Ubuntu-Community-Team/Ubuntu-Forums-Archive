---
title: "Can I Speed Limit a specific system, not the entire network?"
date: 2011-05-09
forum: General Help
---

### Post by magiceffects on 2011-05-09
Hey,

I have been reading through most of the speed-limit forum posts I can find but nothing seems to match what I am trying to do.

I have this new flatmate who uses all my Internet data up before the end of my monthly clockover... Instead of having to buy heaps of data top-ups at the end of the month, is there a way I can limit the speed of his computer through the network?

I have tried looking through my router settings (which is a Thomson router) but there doesn't seem to be any options in regards to limiting activity of a system on the network.

I read into using trickle or wondershaper, although I am not looking to limit the speed of my own system... just another system connected to my router.

---

### Post by jamesjenner on 2011-05-09
I have used IPCop very successfully to manage downloads for students that I've been looking after. 

IPCop is a distro of Linux, all you need is two network ports on the box and to run it all the time. I brought a really cheap system, threw in a couple of network cards and set it up.

By default it doesn't support management on a per system. I had to add a plugin (which there are quite a few) which allowed me to define how much per day a person can download. If they exceeded that download then it cut them off the internet until the 24 hour period was up.

I cannot remember which plugin it was, but I can try and check for you if you like. The advanced proxy plugin is a must have, nice for white and black list banning.

Personally I think that using DD-WRT is the best option, but i'm not sure if it's available for your router. It's firmware you load onto your router that allows for all sorts of options. I've never used it, even though I wanted to (apparently the version of the router I had wasn't supported due to something or other). So if you can use DD-WRT I would recommend it, just check out the router database:

[http://www.dd-wrt.com/site/support/router-database](http://www.dd-wrt.com/site/support/router-database)

In both options what your looking to do is effectively restrict downloads. I found that trying to just packet shape is extremely difficult, though the adv proxy plugin for IPCop does allow some reduction of speed (if someone tries to get around via third party proxies it can cause problems). 

Hope that helps mate.

Cheers,

James.

---

### Post by magiceffects on 2011-05-09
Thanks James, I will look into the possibility of setting up DD-WRT; I guess being a Linux newbie will make that task loads of fun either way! ;)

---

### Post by jamesjenner on 2011-05-09
> **magiceffects said:**
> Thanks James, I will look into the possibility of setting up DD-WRT; I guess being a Linux newbie will make that task loads of fun either way! ;)

No worries, happy to help.

I should clarify. DD-WRT is a firmware replacement for your router, while IPCop is a linux distro specifically to be a firewall/router in a pc (or embedded device if you have one that can run it I spose). 

I haven't played with DD-WRT, only because I had the wrong version of a router. It seems quite painless to install from what I've read, but I would recommend only doing it if you have a backup. You will need to do some research using this because there are hardware requirements in terms of memory, depending on what you want.

Good luck and have fun.

---

