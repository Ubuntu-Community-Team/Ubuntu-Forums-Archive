---
title: "CPU usage too high"
date: 2009-12-01
forum: General Help
---

### Post by tripler on 2009-12-01
My ubuntu 9.04 has recently gone super slow after working fine since installing a few months ago. The only possible change was installing some updates suggested by Update Manager. After booting it works fine for about 30 mins then becomes painfully slow. Running "top" in Terminal, I can see CPU usage spikes every few seconds a 80-95% for Firefox, Xorg and hal-system-smbi. Only apps I have open are Firefox, Evolution and Terminal. 

Is there a way to go back to the last working configuration? I'm assuming the problem was introduced by one of the Update Manager updates because nothing else has been installed recently.

---

### Post by dcstar on 2009-12-01
> **tripler said:**
> My ubuntu 9.04 has recently gone super slow after working fine since installing a few months ago. The only possible change was installing some updates suggested by Update Manager. After booting it works fine for about 30 mins then becomes painfully slow. Running "top" in Terminal, I can see CPU usage spikes every few seconds a 80-95% for Firefox, Xorg and hal-system-smbi. Only apps I have open are Firefox, Evolution and Terminal. 

Is there a way to go back to the last working configuration? I'm assuming the problem was introduced by one of the Update Manager updates because nothing else has been installed recently.

You should be able to look in the Synaptic History to see what packages were installed, and manually roll them back to older versions.

---

### Post by ed-koala on 2009-12-01
Those processes that are spiking seem to be video related. (Am I right?)

Check for updates affecting video if so.

---

### Post by tripler on 2009-12-02
> **ed-koala said:**
> Those processes that are spiking seem to be video related. (Am I right?)

Check for updates affecting video if so.
They happen without me watching videos so I'm guessing they're not video related, but i don't know. They happen even with firefox closed. 

Interestingly today it was fine for 4+ hours from boot before going slow. Thought it had fixed itself, but no...

---

### Post by ed-koala on 2009-12-02
That was just an observation based on what you reported.  Not necessarily the actual issue of course.  Perhaps you should monitor the cpu spikes a bit more and keep track of what is spiking?  I'll bet a common cause reveals itself that way.

---

### Post by tripler on 2009-12-02
> **dcstar said:**
> You should be able to look in the Synaptic History to see what packages were installed, and manually roll them back to older versions.
Sorry to ask a novice question, but where can I see Synaptic History? I've looked in Synaptic Package Manager but can't see it there.

EDIT: found Synaptic History in File -> History in Synaptic Package Manager. Next question: how do I manually roll back to the older version? The only upgraded package for the relevant time was "cups (1.3.9-17ubuntu3.2) to 1.3.9-17ubuntu3.4"

---

### Post by ed-koala on 2009-12-02
Cups deals with your printer. I seriously doubt it's your culprit.

I still recommend monitoring the spikes for awhile, and noting which processes spike high.  It is almost certain to reveal some sort of commonality to the  problem.

---

### Post by tripler on 2009-12-02
> **ed-koala said:**
> I still recommend monitoring the spikes for awhile, and noting which processes spike high.  It is almost certain to reveal some sort of commonality to the  problem.
When it goes slow it's firefox, Xorg and hal-system-smbi each spiking at 20-85% of cpu, often together, resulting in close to 100% cpu use. When it's running normally they take less than 5%, usually 1% and hal-system-smbi doesn't feature at all.

The laptop is a Dell D420. People talk about setting "nolapic acpi=off" but I don't know where to do that.

---

