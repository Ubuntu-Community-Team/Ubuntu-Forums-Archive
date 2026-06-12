---
title: "Can't read CDROM in virtual box"
date: 2009-09-07
forum: General Help
---

### Post by geovino on 2009-09-07
I'm running ver 9.04 and I've installed WinXP in virtual box. WinXP runs fine in vbox except it doesn't read the CDROM. What is needed to make virtualbox read the CDROM?

---

### Post by howefield on 2009-09-07
Is the cd mounted ?

Maybe you have an iso image mounted instead.

---

### Post by geovino on 2009-09-07
> **howefield said:**
> Is the cd mounted ?

Maybe you have an iso image mounted instead.

It works fine when I'm using Ubuntu. Is there a separate mounting for being in virtualbox?

---

### Post by konqueror7 on 2009-09-07
> **geovino said:**
> It works fine when I'm using Ubuntu. Is there a separate mounting for being in virtualbox?

have you tried checking the settings if the CDROM checkbox is enabled?

---

### Post by longtom on 2009-09-07
Open up VB.

Select the virtual machine you want to start - but don't start it up.

Right click on it and select "settings"

Select "CD/DVD-Rom" and make sure that "Mount CD/DVD drive" is ticked.

Make sure "Host CD/DVD drive" is selected

That should be it.

---

### Post by geovino on 2009-09-07
> **konqueror7 said:**
> have you tried checking the settings if the CDROM checkbox is enabled?

it was set to iso image instead of host DVD drive. I changed it. Do I also need to check enable passthrough? 

thanks.

---

### Post by longtom on 2009-09-07
> **geovino said:**
> it was set to iso image instead of host DVD drive. I changed it. Do I also need to check enable passthrough? 

thanks.

If you want to write CDs, yes.

---

### Post by geovino on 2009-09-07
> **longtom said:**
> If you want to write CDs, yes.

Thanks again :)

[Solved]

---

