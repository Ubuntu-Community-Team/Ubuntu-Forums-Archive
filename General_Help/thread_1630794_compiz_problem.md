---
title: "compiz problem"
date: 2010-11-25
forum: General Help
---

### Post by cam3roon on 2010-11-25
Hi. 
I noticed that when I change something in compiz, anything, it doesn't apply. I installed and uninstall it and even deleted the old configuration files. It still doesn't work and now I don't have any kind of visual effect. What should I do?

Thanks

---

### Post by sikander3786 on 2010-11-25
Hi.

What are you trying to change in compiz? And how?

Make sure compiz is turned on by right clicking the desktop > Change Desktop Background > Visual Effects > Extra.

And also look under System > Administration > Hardware Drivers/Additional Drivers if the drivers for your graphics card are enabled.

If that doesn't help, we will need some more info like which graphics card is there and which version of Ubuntu is this?

---

### Post by cam3roon on 2010-11-27
Hi. The "extra" is turned on and the drivers are also activated. It doesn't matter what option I change in compiz, it doesn't not apply. The strange thing is that before it worked perfectly so the graphic card couldn't be the problem. :|

---

### Post by sikander3786 on 2010-11-27
> It doesn't matter what option I change in compiz, it doesn't not apply. 

Which tool are you using for configuration of compiz?

Whichever, did you try purging and re-installing that?

Search Synaptic > Mark for complete removal and then re-install.

---

### Post by Quackers on 2010-11-27
After you have made the changes have you clicked on "Apply" at the bottom right of the CCSM window?

---

### Post by sikander3786 on 2010-11-27
> **Quackers said:**
> After you have made the changes have you clicked on "Apply" at the bottom right of the CCSM window?
Very good point :-)

Sometimes it is really simple as that.

Lets see what the OP comes up with.

---

### Post by cam3roon on 2010-11-28
The solution was to uninstall the graphic drivers, restart, uninstall compiz from synaptic, restart, install drivers, restart, install compiz and restart again. It finally worked

Thanks guys!

---

