---
title: "Switching off font smoothing in FF"
date: 2010-10-11
forum: General Help
---

### Post by Coyede on 2010-10-11
Hi Everyone,

I am trying to disable font smoothing in Firefox 3.6.10 in Ubuntu 10.10.

I have disabled font smoothing in System > Preferences > Appearance > Fonts (Rendering = Monochrome)

Firefox continues  smoothing fonts and some other applications also continue to smooth them.

I have tried restarting the system ;)

---

### Post by WorMzy on 2010-10-11
Dunno if it'll have any effect, but in my [about:config]("http://mozillalinks.org/wp/resources/how-to-guides/how-to-use-aboutconfig/") I have a key called "gfx.use_text_smoothing_setting". If you have it too, try setting it to "false". If it's already false, try setting it to "True". It's naming is a little ambiguous, so it might not work as you expect it to.

---

### Post by Coyede on 2010-10-11
> **WorMzy said:**
> Dunno if it'll have any effect, but in my [about:config]("http://mozillalinks.org/wp/resources/how-to-guides/how-to-use-aboutconfig/") I have a key called "gfx.use_text_smoothing_setting". If you have it too, try setting it to "false". If it's already false, try setting it to "True". It's naming is a little ambiguous, so it might not work as you expect it to.

Had no apparent effect, true or false.

---

### Post by WorMzy on 2010-10-11
Yeah, I just did a google search on it, and it seems it only has an effect on Mac OS X. I couldn't find anything else that might control it, so I guess the solution lies elsewhere.

---

