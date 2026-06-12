---
title: "resolution won't go above 800x600"
date: 2009-12-11
forum: General Help
---

### Post by washable mist on 2009-12-11
i'm kind of a newbe to linux so patience with my n00b-ness please

so i have installed xubuntu 9.10 on my computer, everything runs fine exsept the fact that i can't set my monitor resolution above 800x600. i had it at 1280x1024 when running windows xp, i'm not sure if i need different drivers because i haven't worked out how to install new drivers yet, and its quite hard doing homework when the screen is messed up.

i am using the onboard graphics on my motherboard which is a gigabyte GA 8VM800M

thanks in advance to anyone who can help me with this

---

### Post by ST3ALTHPSYCH0 on 2009-12-11
Alright, if there's a proprietary driver for your chipset you'll see it if you click on System>Administration>Hardware. I'd suggest installing it if there's a recommended driver. If that doesn't give you the configuration options you're after, try the cheater's option that's linked in my sig.

---

### Post by washable mist on 2009-12-11
> **ST3ALTHPSYCH0 said:**
> Alright, if there's a proprietary driver for your chipset you'll see it if you click on System>Administration>Hardware. I'd suggest installing it if there's a recommended driver. If that doesn't give you the configuration options you're after, try the cheater's option that's linked in my sig.

i checked in hardware but there is nothing listed there, i also checked on the gigabyte website and can't seem to find anything :(

---

### Post by ST3ALTHPSYCH0 on 2009-12-11
Try my link.... no promises. I've only run Ubuntu on ATI and Nvidia hardware.

---

### Post by lykwydchykyn on 2009-12-11
Can you open a terminal and post the output of:
```

lspci |grep -i vga

```

That will give the exact make/model/chipset of your graphics card, which will be essential in pointing you to a solution.

---

