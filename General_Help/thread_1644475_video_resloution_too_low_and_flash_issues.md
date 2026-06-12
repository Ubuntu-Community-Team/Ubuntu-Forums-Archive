---
title: "video resloution too low and flash issues"
date: 2010-12-13
forum: General Help
---

### Post by englehanif on 2010-12-13
Everything seems to be in working order but resolution is very low. and I can't seem to get flash working in google chrome or firefox and I tried several things in system/preferences, too. Flash 10 and higher resolution needed please help.
My netbook is acer "aspire one" I downloaded ubuntu 10.10 ( I am surprised it is a little slow maybe should have downloaded netbook edition?)[not too slow though]
video out is intel ?something or other version of intel I will have to look for it but it is the stock one from the store
anyways by the time someone responds I should have video card names and #'s thanks anyone who can help

---

### Post by BlueSpecial on 2010-12-13
Low resolution must be a driver and/or system config. Check if there's an available driver for you graphic card: System->Administration->Hardware Drivers.

Install "Ubuntu Restricted Extras" on Software Center to solve the multimedia issues... it usually gets Flash, DVD Movies, etc to play perfectly!

---

### Post by thameera on 2010-12-13
Perhaps you may need to install the vendor's drivers for your video card. Go to System->Administration->Additional Drivers and install the drivers if any. 
Also have you installed *ubuntu-restricted-extras* package?
Usually the resolution of the monitor is set using System->Preferences->Monitors.
And, yes, the Ubuntu Netbook Remix may suit your netbook better.

---

### Post by snowpine on 2010-12-13
Open a Terminal (Applications->Accessories->Terminal) and copy & paste the following command:

```
lspci | grep VGA
```

Copy & paste the results here. This will tell us exactly which graphics card you have, so we can help you.

Switching to the Netbook Edition will not solve the problem, as both versions have the same graphics card drivers.

---

### Post by realzippy on 2010-12-13
*maybe should have downloaded netbook edition?*
+1 for netbook edition.

*lspci | grep VGA*
..since it is an aspire one,very likely
an intel integrated graphics chipset,950 or so...

---

