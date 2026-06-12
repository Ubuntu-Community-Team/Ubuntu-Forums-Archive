---
title: "Clean Printheads HP Deskjet  F2210"
date: 2012-06-11
forum: General Help
---

### Post by frank cox on 2012-06-11
I am running Ubuntu 11.04 and I plugged in an old HP Deskjet F2210 All in One Printer/Scanner. It installed instantly and it went through the print test page normally but did not print , The scanner works well with XZane.

The HP site says it supports print head cleaning but I find no where to initialize it. 
Is it possible I need to remove the driver Ubuntu installed an replace it with the one from the HP site or is there another possibility?

TIA

---

### Post by oldfred on 2012-06-11
Do not know about software to clean the heads. Every driver is different.

But I find if older print head really needs cleaning a q-tip and some alcohol work wonders. On brand of printers I had said not to remove printer head but it still worked.

---

### Post by hansdown on 2012-06-11
Hi frank cox.

You also may need to install 
```

hplip-gui
```

This will give you access to the print head cleaner.

[http://www.hplipopensource.com/hplip-web/models/deskjet_aio/deskjet_f2200_series.html](http://www.hplipopensource.com/hplip-web/models/deskjet_aio/deskjet_f2200_series.html)

---

### Post by frank cox on 2012-06-11
Thanks
I will try that.

---

### Post by frank cox on 2012-06-11
I downloaded the driver and set the permissions to read write execute but it says no such file.

---

### Post by frank cox on 2012-06-12
I compiled the driver and same thing, I see no setting to initialize head cleaning.

---

### Post by hansdown on 2012-06-12
> **frank cox said:**
> I compiled the driver and same thing, I see no setting to initialize head cleaning.

If you install

```
hplip-gui
```

you will get the option for head cleaning.

---

### Post by frank cox on 2012-06-12
> **hansdown said:**
> If you install

```
hplip-gui
```you will get the option for head cleaning.

Thanks!

I had to add a place on the panel but now I can access the maintenance tools, thanks again!

---

### Post by hansdown on 2012-06-12
Glad tou fixed it, frank cox.

---

