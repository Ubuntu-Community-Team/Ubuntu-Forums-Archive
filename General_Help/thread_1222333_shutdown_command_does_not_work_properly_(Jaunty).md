---
title: "shutdown command does not work properly (Jaunty)"
date: 2009-07-24
forum: General Help
---

### Post by Wopple on 2009-07-24
I can shutdown the computer just fine using the logout button in the panel. However, when I use:

sudo shutdown now

in a terminal, it ends up frozen. It begins shutting down fine, but when it gets to the loading bar with the Ubuntu logo, the bar stops part of the way through and then it goes to a blank screen. From there it is unresponsive and never actually turns the computer off. I am then forced to perform a hard shutdown using the power button on my laptop.

Does anyone know what could be wrong?

---

### Post by LepeKaname on 2009-07-24
check your /var/log/syslog to see if you find any clue there. Check the timing and writedown when the halt occurs. If that doesnt't help too much, post that log part here.

---

### Post by wojox on 2009-07-24
Needs a switch

Shutdown and power off
```
sudo shutdown -h now
```

Shutdown and restart
```
sudo shutdown -r now
```

---

### Post by aesis05401 on 2009-07-24
> **Wopple said:**
> I can shutdown the computer just fine using the logout button in the panel. However, when I use:

sudo shutdown now

in a terminal, it ends up frozen. It begins shutting down fine, but when it gets to the loading bar with the Ubuntu logo, the bar stops part of the way through and then it goes to a blank screen. From there it is unresponsive and never actually turns the computer off. I am then forced to perform a hard shutdown using the power button on my laptop.

Does anyone know what could be wrong?

Are the results different if you include the '-P' ?

I think this changed in Ubuntu a release or two ago - now it requires the poweroff option or it just halts.

```

sudo shutdown -P now

```

@wojox - we keep meeting like this ;)

---

### Post by Wopple on 2009-07-26
I have tried -h with the same problem. I have not tried -P and will be sure to test it out. Unfortunately, the laptop in question recently got rained on and I need to let it dry before turning it on again. I will be back with the results later.

Thanks for your help.

Edit:

Yeah, I needed the -P argument. I feel kind of silly now. I expected the default functionality to work like the shutdowns I'm used to.

Thanks again.

---

