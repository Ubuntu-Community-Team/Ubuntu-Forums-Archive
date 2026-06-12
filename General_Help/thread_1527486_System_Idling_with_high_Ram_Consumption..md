---
title: "System Idling with high Ram Consumption."
date: 2010-07-09
forum: General Help
---

### Post by DavidG24 on 2010-07-09
Hi Guys,

I'm fairly new to Ubuntu so please pardon my terminology and general ignorance - I've installed Ubuntu 10.04 (64 bit) about a week ago and when first installed with a few software programs it use to idle at about 0.5-0.6GB of Ram (DDR3 1600MHz Triple Channel), I've added a few (not a lot software apps) and now with only Google Chrome Running I'm at 1.5-1.8GB ...which has me worried....how can it Idle with so much!
I'm sure its due to software that I have installed working in the background, however when accessing the Processes running via System Monitor I only have Chrome and System Monitor as 'Running' ; Now I know that even when a software app is 'Sleeping' is still may be using resources - but in my fear/ignorance of the new OS I am apprehensive about uninstalling anything that may cause other applications to die...

Given I'm running Ubuntu with 12GB of said Ram, I'm not overly worried about this - however I am worried about falling into bad habits for the future.

What would you recommend in terms of identifying what is causing this massive increase in memory consumption?

Thanks in Advance,

David

---

### Post by philinux on 2010-07-09
> **DavidG24 said:**
> Hi Guys,

I'm fairly new to Ubuntu so please pardon my terminology and general ignorance - I've installed Ubuntu 10.04 (64 bit) about a week ago and when first installed with a few software programs it use to idle at about 0.5-0.6GB of Ram (DDR3 1600MHz Triple Channel), I've added a few (not a lot software apps) and now with only Google Chrome Running I'm at 1.5-1.8GB ...which has me worried....how can it Idle with so much!
I'm sure its due to software that I have installed working in the background, however when accessing the Processes running via System Monitor I only have Chrome and System Monitor as 'Running' ; Now I know that even when a software app is 'Sleeping' is still may be using resources - but in my fear/ignorance of the new OS I am apprehensive about uninstalling anything that may cause other applications to die...

Given I'm running Ubuntu with 12GB of said Ram, I'm not overly worried about this - however I am worried about falling into bad habits for the future.

What would you recommend in terms of identifying what is causing this massive increase in memory consumption?

Thanks in Advance,

David

Open a terminal Apps>Accessories.

```
free -m
```

Post back what it shows.
Also see this. [http://www.linuxatemyram.com/index.html](http://www.linuxatemyram.com/index.html)

---

### Post by DavidG24 on 2010-07-09
hey mate,

thanks for the prompt response - as asked :


```

david@david-desktop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:         12035       1010      11025          0         54        312
-/+ buffers/cache:        643      11391
Swap:        35254          0      35254
david@david-desktop:~$ 

```

Thanks again,

David

---

### Post by philinux on 2010-07-09
```
free -m
total used free shared buffers cached
Mem: 12035 1010 11025 0 54 312
-/+ buffers/cache: **[COLOR="Red"]643[/COLOR]** 11391
Swap: 35254 0 35254
```

643 mg actually in use. Linux uses ram differently than windows.

Swap seems a bit OTT .

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by DavidG24 on 2010-07-09
the output is now under Code Tags....a lot more easy to read I imagine!

---

### Post by DavidG24 on 2010-07-09
> **philinux said:**
> 
643 mg actually in use. Linux uses ram differently than windows.

Thanks, just read the link you put on your first post (**feeling mighty stupid atm - haha**) ; Sorry just one last question, is 643 mg an okay figure?

Cheers,

David

---

### Post by philinux on 2010-07-09
No stupid question here at all.

```
free -m
             total       used       free     shared    buffers     cached
Mem:          2009       1763        245          0        182        988
-/+ buffers/cache:        592       1416
Swap:         1906          0       1906

```

Running 64 bit here too, depends what apps are running. Virtualbox would bump it up.. A 32 bit install would be less.

I've got swap = to ram, so I can use suspend.

---

