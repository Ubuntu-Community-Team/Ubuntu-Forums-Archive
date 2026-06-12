---
title: "Panels sometimes not loading on reboot"
date: 2011-05-15
forum: General Help
---

### Post by An Sanct on 2011-05-15
Hello people!

I have a small problem with panels sometimes not loading on startup, it seems, that they don't load if I log in too quickly (this should not be a problem!).

Let me elaborate a bit on the "not loading" part: the panel with launchers shows, info icons are present, but launcher icons have no visible representation (they have a hint, but no icon) so the panel *looks* empty.

basic info: Ubuntu 10.10 Maverick 64bit, all updates

I am searching for a way to re-ignite the panels through terminal or a way to fix this altogether.

---

### Post by ShadowWraith on 2011-05-15
Running
```

killall gnome-panel

```
In the terminal should restart the panel. If it just disappears completely, run
```

gnome-panel

```

---

### Post by An Sanct on 2011-05-15
> **ShadowWraith said:**
> Running
```

killall gnome-panel

```In the terminal should restart the panel. If it just disappears completely, run
```

gnome-panel

```

Thank you ShadowWraith!

I was thinking about something like this. :)

That's the way to "reboot" panels, I would be really happy if someone would point me in the right direction of "how to troubleshoot" this problem, maybe a complete fix?

---

### Post by An Sanct on 2011-05-16
Great, the *killall* idea works, tested right now...

But, has anyone any idea why this happens?

---

### Post by ShadowWraith on 2011-05-16
You said that this only happens when you log in too quickly. So if you wait a while, there is no issue with the icons? If so, there must be some part of the panel or icon data that's loaded beforehand, during gdm's login screen (though this isn't what I'd expect, considering that panel is a userspace program, as I understand it.) Maybe opening the first terminal while gdm is going with ctrl-alt-f1 and see what goes on as gdm is onscreen, or reading dmesg will shed some light on the issue.

---

### Post by An Sanct on 2011-05-17
Kudos to you ShadowWraith :)

I'll check whats loading/running/happening during gdm login, maybe I'll find something interesting.

Well, its kind of a nuisance to *have to wait* for everything to load up, to see the correct desktop environment...

Anyhow, you covered both questions, thank you!****

---

