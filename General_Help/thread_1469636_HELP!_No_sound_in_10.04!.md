---
title: "HELP! No sound in 10.04!"
date: 2010-05-02
forum: General Help
---

### Post by MrCloudHands on 2010-05-02
I just upgraded to 10.04 and I have lost all my sound! I tried installing some of the ALSA plugins from synaptic, no luck. And I also got this when trying to locate my soundcard: ```
christian@christian-laptop:~$ aplay -l
aplay: device_list:223: no soundcards found...

``` 

Please help if you can, I need to get this working! Thanks!

---

### Post by sog on 2010-05-03
Don't have an answer for you, but having the exact same issue, just not consistently. One in four or five times I start, everything is fine with sound. The rest of the time I start into an environment with no sound. 


```
aplay -l
aplay: device_list:223: no soundcards found...

```

In case it helps, when this happens I also lose access and visibility of two externally attached USB hard drives. 

This is 10.04. Nothing obvious in dmesg or lscpci. Device is:

Creative Labs X-Fi Titanium series [EMU20k2]

---

