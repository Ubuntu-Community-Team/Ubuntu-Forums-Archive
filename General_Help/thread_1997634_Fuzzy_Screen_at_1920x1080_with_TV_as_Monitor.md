---
title: "Fuzzy Screen at 1920x1080 with TV as Monitor"
date: 2012-06-05
forum: General Help
---

### Post by terminator14 on 2012-06-05
I have recently been forced to switch to a 26 inch TV as my monitor at work, and I am having some trouble setting higher resolutions on it - specifically 1920x1080. 

While modes like 1360x768 and below work and look ok on the TV, everything is just too big. When I try to set the resolution to 1920x1080, text (desktop icon text, Applications/Places/System menu items, etc.) becomes barely readable, panel icons become worse quality, and the login screen is unreadable. I would take a screenshot, but screenshots turn out looking normal and do not capture this problem at all.

My video card is a 9800GT (plenty of power to run 1920x1080), the TV is a Toshiba 26AV502RZ, and I'm using a cable that's DVI on the computer end and HDMI on the TV end to connect the two.

I have tried using the default video driver, the NVIDIA 295.53 driver, and the NVIDIA 302.07 beta driver, and none have automatically fixed the problem, so I've had to resort to playing around with xorg.conf. I have spent the last 3 days modifying xorg.conf to try to fix this, but so far I've gotten nowhere. 

I have almost no experience with xorg.conf slowing down my progress considerably. For example, how do I get the correct modeline for the TV? And do I even need a modeline? Some people online say that the modeline does not effect DFP devices - is this true? In case it was not (and because I have no other ideas) I've been trying to generate one using any one of several online modeline generator tools, or the amlc program I have downloaded. amlc seems like a great tool, but for some reason, it asks for 

```
Minimum HSync, in kHz: 
Maximum HSync, in kHz: 
Minimum VSync, in Hz:  
Maximum VSync, in Hz:  
```

While the only information the TV manual gives me is what I've attached, which has no ranges.

I have also tried running "nvidia-xconfig --tv-standard=HD1080P", which adds a few lines to xorg.conf, but appears to do nothing else.

Any advice would be highly appreciated.

---

### Post by ragtag on 2012-06-05
Your TV has a maximum resolution of 1366 x 768 according to [this link]("http://reviews.cnet.com/flat-panel-tvs/toshiba-26av502r-26-lcd/1707-6482_7-33912155.html").

So when you feed it a full HD 1920 x 1080 signal, it's simply scaling down the picture to 1366x768 making everything look fuzzy. Nothing you can do about it, but get a different TV or screen.

In general TV's are not that great computer monitors. They tend to be too bright and contrasty, and reading text of them for extended periods at a time can be quite tiring.

---

### Post by terminator14 on 2012-06-05
> **ragtag said:**
> Your TV has a maximum resolution of 1366 x 768 according to [this link]("http://reviews.cnet.com/flat-panel-tvs/toshiba-26av502r-26-lcd/1707-6482_7-33912155.html").

So when you feed it a full HD 1920 x 1080 signal, it's simply scaling down the picture to 1366x768 making everything look fuzzy. Nothing you can do about it, but get a different TV or screen.

In general TV's are not that great computer monitors. They tend to be too bright and contrasty, and reading text of them for extended periods at a time can be quite tiring.

It's manual states that it can do 1080p, and if I set the computer to 1920x1080, the recall button on the remote makes a bar appear on top that literally says "1080p", which changes at lower resolutions to things like 720p, or others depending on the resolution being used. This is why I assumed that it could handle 1080p, and didn't look much further into it.

The thing is - the manual is not written specifically for this TV - it was written for a line of similar TVs, including this one. It is quite possible that the other, bigger TVs in the same linup can support 1080p while this one can't. It is also possible, and even likely that the lineup of TVs all use the same firmware, which can recognize a 1080p signal, while this specific TV doesn't have the hardware to actually display it properly.

None of this occured to me until I saw the page you linked to, which caused me to question my assumption. Looking into this further, I found that Amazon has this same TV model for sale, and states it can do only 720p and a maximum of 1366 x 768. I guess I'm switching back to a monitor - either that or getting used to the 1366x768 resolution - I haven't decided yet.

Thanks for looking into this - you saved me a lot of time and energy, as I would have been focused on xorg.conf for several more days, and would have never thought of taking a step back to see the problem. I really appreciate it.

---

