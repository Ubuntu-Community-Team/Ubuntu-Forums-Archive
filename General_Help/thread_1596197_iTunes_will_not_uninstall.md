---
title: "iTunes will not uninstall"
date: 2010-10-14
forum: General Help
---

### Post by 90hoursleep on 2010-10-14
new to ubuntu, been able to figure things out myself reading forums and whatnot
but i got myself in a bit of a fix today

i have 10.04 Lucid Lynx
i installed wine
i installed itunes version 10.x

so i learned AFTER i installed itunes 10, that itunes 10 simply does not work at all and crashes

so i go to uninstall itunes via wine, i highlight itunes, i click remove
and itunes **reinstalls** again, instead of uninstalling

my question is, **how do i get the itunes uninstaller to run?**
or is there a forceful terminal command to rid me of my mistake?

thanks all in advance for any feedback, much appreciated

---

### Post by aysiu on 2010-10-14
Run ```
wine uninstaller
``` [http://wiki.winehq.org/uninstaller](http://wiki.winehq.org/uninstaller)

---

### Post by 90hoursleep on 2010-10-14
will uninstalling wine also uninstall itunes/quicktime etc?

---

### Post by aysiu on 2010-10-14
> **90hoursleep said:**
> will uninstalling wine also uninstall itunes/quicktime etc?
I don't mean for you to uninstall Wine.

I mean for you to use Wine to uninstall iTunes.

---

### Post by 90hoursleep on 2010-10-14
yes i have done that already,
after doing that, the itunes INSTALLER is run, not the UNINSTALLER

i will go through the process, and take screen captures and post them here in a few minutes

(thank you for your input so far :))

---

### Post by aysiu on 2010-10-14
> **90hoursleep said:**
> yes i have done that already,
after doing that, the itunes INSTALLER is run, not the UNINSTALLER

i will go through the process, and take screen captures and post them here in a few minutes

(thank you for your input so far :))
In that case, you should go to Places > Home, press Control-H (to show hidden files) and then delete the *.wine* directory.

---

### Post by 90hoursleep on 2010-10-14
ok will try that now, posting screen captures just in case

(step6 would show the dialog box saying itunes installation was successful)

---

### Post by jengo on 2011-01-18
Ayisu this did not help, itunes is still in my applications folder along with wine. How do i fix this? 

I found this on google after searching for help and it says "SOLVED" 

**THIS IS NOT SOLVED**

---

