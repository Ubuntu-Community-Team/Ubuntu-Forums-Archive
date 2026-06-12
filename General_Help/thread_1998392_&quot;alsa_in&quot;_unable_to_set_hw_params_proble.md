---
title: "&quot;alsa_in&quot; unable to set hw params problem"
date: 2012-06-06
forum: General Help
---

### Post by sirriffsalot on 2012-06-06
Hi!

I've had this problem back and forth for a while, but now I can't ignore it any longer and I want to get this bugger sorted out. I have USB-driven amps and whatnot that I get into JACK and Ardour by doing "alsa_in -dhw:1" for example, but with 12.04 and 11.04 and 11.10 the problem has always been the same, though at curiously random times.

Whenever I do the command now, on a fresh 12.04 LTS install, I get this error: ```
Unable to set hw params for playback: Input/output error
Setting of hwparams failed: Input/output error
```

So... What's this and how do I resolve it? Thanks for taking the time!!

--> Leo

---

### Post by sirriffsalot on 2012-06-10
Alright, for now it seems the problem mysteriously decides to disappear when using a lowlatency kernel, in my case it is 3.2.0-23-lowlatency-pae, so grab that one with all it's dependencies (right click it in synaptic package manager > properties > dependencies) and hopefully Bob's your uncle as he watches you become as happy as Larry, however happy he is! Happy recording :)

-->

---

