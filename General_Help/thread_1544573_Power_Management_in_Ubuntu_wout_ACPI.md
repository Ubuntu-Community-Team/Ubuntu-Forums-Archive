---
title: "Power Management in Ubuntu w/out ACPI"
date: 2010-08-02
forum: General Help
---

### Post by ChosenDev on 2010-08-02
Hello,

I recently installed Ubuntu 10.04 Lucid and I couldn't run the installer or anything on Ubuntu unless I disabled ACPI (acpi=off).

The problem now is since I'm using a laptop (Toshiba Satellite L505D Series), I don't have the battery meter or any power control, so my laptop dies when I'm not expecting, etc.

Is there any way I could keep Power Management while having ACPI disabled, since I can't use it.

Thanks, ChosenDev.

---

### Post by ChosenDev on 2010-08-02
Bump. Please help =P

---

### Post by Maverick_Meerkat on 2010-08-02
Greetings,

I am running Ubuntu 10.04 on a Toshiba Satellite A55-S106 & this works for me. You might give it a try.

```
sudo apt-get install sysv-rc-conf

sudo sysv-rc-conf
```

Make certain that in the row "acpi-supp$" columns 2,3,4,5 have an X under them and all others are blank.

Make certain that in the row "acpid" all columns are blank.

In the desktop drop down menu navigate System>Preferences>Startup Applications

Make certain that Power Management checkbox IS selected.

BTW additional Power Settings are available thru Ubuntu Tweak. Get it here: [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/) 

Hope this helps you out!

---

### Post by ChosenDev on 2010-08-02
Thanks for trying, but I still can not get it working.

All of the things you said that needed to be checked were checked, etc.

The problem with ACPI that I get is it loads a list of random memory regions like

acpi_support
child_rip

on a Black Console Window. And then it pauses permanently.

---

### Post by Maverick_Meerkat on 2010-08-02
Alrighty, then! Let's look to someone who knows more than I.

Toshiba Specific Utlities for Linux
[http://www.buzzard.me.uk/toshiba/index.html](http://www.buzzard.me.uk/toshiba/index.html)

Advanced Advanced Power Management (APM/ACPI)
[http://www.linux.org/docs/ldp/howto/Ecology-HOWTO/ecology-howto-power-management.html](http://www.linux.org/docs/ldp/howto/Ecology-HOWTO/ecology-howto-power-management.html)

Perhaps these will get us moving in the right direction.

---

### Post by colinwhipple on 2010-08-03
Look in this message thread for a solution:

[http://ubuntuforums.org/showthread.php?t=1301101&highlight=l505d](http://ubuntuforums.org/showthread.php?t=1301101&highlight=l505d)

---

