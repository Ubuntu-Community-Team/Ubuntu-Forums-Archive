---
title: "How to set up an xorg.conf file to forcelowpowermode"
date: 2009-10-29
forum: General Help
---

### Post by linux4life88 on 2009-10-29
I went to setup my xorg.conf file by doing:

```
# Xorg -configure
```

and it failed with errors. I'm guessing that I need to turn off xorg first before I do this but I'm not sure how to. I was just needing help with setting the file up.

The reason being is that I read this article ([http://www.phoronix.com/scan.php?page=news_item&px=NzIwNg](http://www.phoronix.com/scan.php?page=news_item&px=NzIwNg)) that there is an option that could help you save battery life. That option is [FONT="System"]forcelowpowermode[/FONT]. So I was wanting to know how to add this to my xorg.conf file after I get it set up. I have an ATI Radeon HD4650 graphics card in my laptop and I defiantly don't need it to be at full power. I'm hoping that this option will help me save battery life. Thanks ahead for any help.

---

### Post by linux4life88 on 2009-10-29
My whole goal is power savings. I've already done the following:

in /etc/laptop-mode/laptop-mode.conf
LM_AC_HD_IDLE_TIMEOUT_SECOUNDS=300
LM_BATT_HD_IDLE_TIMEOUT_SECONDS=300
BATT_HD_POWERMGMT=254
LM_AC_HD_POWERMGMT=255
NOLM_AC_HD_POWERMGMT=255

in /etc/default/acpi-support
ENABLE_LAPTOP_MODE=true

The first is basically to save my hard drive so it lasts longer. The second is so I can save battery life. Any more suggestions would be much appreciated.

---

### Post by reloweb on 2010-06-04
I have your same problem!

---

### Post by reloweb on 2010-06-25
Have you resolved the problem?

---

### Post by dcstar on 2010-06-26
> **reloweb said:**
> Have you resolved the problem?

Maybe he did a forum search and just didn't wait for the answer?:

[http://ubuntuforums.org/showthread.php?p=9359849](http://ubuntuforums.org/showthread.php?p=9359849)

---

### Post by reloweb on 2010-07-16
In that topic, he talks about fglrx driver, not radeonhd...

---

