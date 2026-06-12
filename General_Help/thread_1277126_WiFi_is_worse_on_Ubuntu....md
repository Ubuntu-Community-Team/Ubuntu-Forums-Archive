---
title: "WiFi is worse on Ubuntu..."
date: 2009-09-27
forum: General Help
---

### Post by AznTiger on 2009-09-27
I just installed Ubuntu on my inspiron, but my room is somewhat far away from the wireless router. 

The internet works just fine on Vista (about 60% strength), but hardly works at all on Ubuntu...

Not sure how to fix this... help please?

---

### Post by sleepitoff on 2009-09-27
What type of wireless card is it? 

Maybe, under "hardware drivers" select a different one if you have multiple options? I do not have this problem.

---

### Post by overdrank on 2009-09-27
> **AznTiger said:**
> I just installed Ubuntu on my inspiron, but my room is somewhat far away from the wireless router. 

The internet works just fine on Vista (about 60% strength), but hardly works at all on Ubuntu...

Not sure how to fix this... help please?

Hi and welcome, what is the model of the wireless card?
You can use the command ```
lspci
``` to identify and then search the forums. It may be as simple as to enable the backports repos. :)

---

### Post by AznTiger on 2009-09-27
I'm currently on vista right now, I'll post the specs you get from ubuntu tomorrow when I can sit in front of the router, but the wireless card is the just the one that comes with the inspiron 1545.

Sorry, I kind of noob at ubuntu.

Thanks

---

### Post by AznTiger on 2009-09-27
The hardware update gives me a blank list

---

### Post by 3rdalbum on 2009-09-28
> **AznTiger said:**
> The hardware update gives me a blank list

Hardware Drivers gives you a blank list? Have you reloaded your package list yet? (go to System > Administration > Synaptic Package Manager and click Reload). The Hardware Drivers program won't find a drive unless it has the package list (you need to be in range and connected to your router, BTW).

We might need the output of lspci, and possibly lsusb - it looks like some of those machines have Broadcom, and some have Atheros. But first try what I suggested, and look in Hardware Drivers afterwards, and you might be given access to a different driver.

The other thing to try is install the "linux-backports-modules-jaunty-generic" package in Synaptic, which could contain a later driver for you which will be enabled on restart.

---

### Post by ram2500 on 2009-09-28
When you say "it works hardly at all", does it at least get you to your homepage, or does it just say 'Connected' but your browser (Firefox) proves otherwise?

Does your laptop contain Centrino technology (???)

---

### Post by P4man on 2009-09-28
> **3rdalbum said:**
> 
The other thing to try is install the "linux-backports-modules-jaunty-generic" package in Synaptic, which could contain a later driver for you which will be enabled on restart.

+1

And contact Dell and tell them to provide better drivers for linux.

---

### Post by 3rdalbum on 2009-09-28
> **P4man said:**
> +1

And contact Dell and tell them to provide better drivers for linux.

+1, and then contact the wireless chipset manufacturers and tell them to create a standard like USB Mass Storage or Universal Video Class, but for wireless cards, so in the future all new wireless cards will be supported out-of-the-box by all operating systems.

---

