---
title: "force metacity to open all windows at a specified size, can i?"
date: 2012-03-05
forum: General Help
---

### Post by Dreamer Fithp Apprentice on 2012-03-05
Is there any way to force metacity (assuming I'm correct that metacity would be the program to look at) in Maverick to open all windows at a specified, non maximised size, like x pixels by y pixels?

---

### Post by dcstar on 2012-03-06
> **Dreamer Fithp Apprentice said:**
> Is there any way to force metacity (assuming I'm correct that metacity would be the program to look at) in Maverick to open all windows at a specified, non maximised size, like x pixels by y pixels?

```
man wmctrl
```

---

### Post by Dreamer Fithp Apprentice on 2012-03-09
Thanks. I'm studying it. I can see it certainly deals with similar stuff but I haven't been able to see how to use it to do this yet. Maybe it's there. I'll keep plugging. But most of it seems to be directed toward affecting windows already up. I'm looking for something to make metacity open use a certain size and location by default AUTOMATICALLY. Ideally to use the specified size and location as the "mazimized" size. I would expect it to be in a config file somewhere. I doubt there is a PERFECT software solution to this because even if I can figure out how to do this it still wouldn't address the problem of windows drawn without horizontal scroll that leave out buttons (like "next", "ok", or "exit"). For those windows the only way I've been able to cope is to gradually lengthen them in several steps until the horizontal dimension is several times the monitor's width and then drag them back over to the left to get to the buttons. I'm not sure if this means something in my monitor or graphics card is going bad or if it has to do with slack programmers assuming everybody's monitor has the same aspect ratio their's has. Probably not as simple as the latter, even if that kind of oversight is unfortunately way too common, because surely nobody has a monitor THAT wide.

Right now I have to demaximise and hand resize almost every window and even then I wind up having to use the horizontal scroll a lot and occasionally even the stretch and drag trick described above.

---

