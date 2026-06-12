---
title: "Default monitor issue in 11.10"
date: 2011-10-14
forum: General Help
---

### Post by Hugh971 on 2011-10-14
Hi,

I've installed 11.10 on my computer and am having an issue with my dual screens. My left display is an old 17" monitor that I use as a secondary screen and my right is a 24" one that I use as my main monitor. In 11.04 I could run

```
xrandr --output <display> --primary
```

to set it as primary and therefore move the unity panel across to it. In 11.10 this doesn't appear to work. I can run the command and it doesn't bring back any errors but the unity panel remains on the left monitor. If I move the monitors in the display config so the 24" is on the left the panel appears on the 24".

Has anyone else ran into this and do you know of a work around? I am using the default driver by the way, I found it to work fine in 11.04 and have had issues with the ATI drivers. I'm using a Radeon 4870.


Thanks

Hugh

---

### Post by Hugh971 on 2011-10-15
I've installed gnome shell and the panel thing and activities thing show up on the primary display as defined by xrandr. I'd guess it's designed so that you can't move the launcher away from the left screen which is a shame because I do like unity but this is something I couldn't just get used to so I think my answer is to stick with shell.

On another note Gnome Shell seems really sleek and responsive. I think I have found my new window manager. Only time will tell. 

Anyway, I'm going to mark this as solved as I think it's like this by design.

---

