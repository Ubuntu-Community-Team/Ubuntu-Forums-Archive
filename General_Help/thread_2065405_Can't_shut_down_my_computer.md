---
title: "Can't shut down my computer"
date: 2012-10-01
forum: General Help
---

### Post by jockyburns on 2012-10-01
My son in law called round today whilst I was at work and used my computer. Dunno what he has done , but now when I select shutdown, the computer doesn't shutdown, but goes to the login screen. I've checked the settings and am convinced it should shutdown completely when I select turn computer off.  Any Ideas ?? Only thing I can do at the moment is force a hard shutdown using the power button on my computer (which I'm loathe to keep doing)

Edit,, I can shut it down from the terminal using the command sudo poweroff

---

### Post by daslinkard on 2012-10-02
> **jockyburns said:**
> My son in law called round today whilst I was at work and used my computer. Dunno what he has done , but now when I select shutdown, the computer doesn't shutdown, but goes to the login screen. I've checked the settings and am convinced it should shutdown completely when I select turn computer off.  Any Ideas ?? Only thing I can do at the moment is force a hard shutdown using the power button on my computer (which I'm loathe to keep doing)

Edit,, I can shut it down from the terminal using the command sudo poweroff

What about when you use these sudo commands?

```
sudo shutdown -h now
```

Does this shut down your PC?

Or does this reboot your system?
```

sudo reboot
```

---

### Post by jockyburns on 2012-10-02
I shut it down using the terminal command sudo poweroff. Restarted my computer and now it shuts down correctly. Dunno why it should have done it, (unless he'd logged on as a guest and not logged out) ??
Anyway I've marked it as solved. ;-)

---

### Post by daslinkard on 2012-10-02
Awesome!  Glad it is solved for you....being a Son-in-law myself....I know how much trouble they can be....you could also be like my Father-in-law and not let any "In-Laws" near the PC.

---

