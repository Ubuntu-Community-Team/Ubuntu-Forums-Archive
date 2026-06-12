---
title: "Firefox Seems Very Laggy/Choppy on 11.04"
date: 2011-07-27
forum: General Help
---

### Post by rhugga on 2011-07-27
I have two Ubuntu 11.04 systems, both on pretty beefy machines. One 32-bit with Nvidia grpahics and one 64-bit with ATI graphics (and a solid state drive) On the ATI machine I'm using the recommended 3rd party drivers.

Using Firefox 5.0 and it feels very laggy and cumbersome. Switching between tabs results in a 1-2 second lag time. The content of the tabs does not seem to matter, simple HTML only with no javascript/flash/java content etc...

Using flash-based ontent like Hitachi's command suite is especially laggy -- its pretty much unusable.

Is this a known issue or is there a better version to run? I tried to find the 4.x version of firefox and can only find the 3.x version in the older versions section.

FYI: I also replaced openjdk with sun's jdk and the baehavior was identical with both. (had to replace open-jdk for other reasons anyway)

Thx for any help..

---

### Post by dino99 on 2011-07-27
i've not seen this issue, you may have other problems: grahic drivers deactivated or missing codecs

watch the logs to find usefull errors (/var/log/ & xsession-errors)

---

### Post by lovinglinux on 2011-07-27
I have seen this issue a long time ago with Ghostery add-on. That extension doesn't cause any problems nowadays, but it could be another extension.

Start Firefox in safe mode and report if the problem persists:

```
firefox -safe-mode
```

---

### Post by 3602 on 2011-07-27
Does it lag on both machines or just the one with an ATI card?
If it's just for the ATI card, install *ccsm* and in OpenGL, disable Sync to VBlank.

---

### Post by lovinglinux on 2011-07-27
For the Flash issue, install [Flash-Aid](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/) and run the extension wizard. It will detect installed flash plugins, remove them and install the latest Beta. Additionally, it will apply some tweaks that should improve performance and fix common issues.

---

### Post by LordFury on 2011-07-27
install and run chromium its superb...

---

### Post by linuxuser12345 on 2011-07-27
I would recommend removing the ATi drivers if you are running 11.04. I have had a similar problem on my 11.04 system, but it all fixed as soon as I got rid of the 3rd Party drivers.

---

### Post by 3602 on 2011-07-27
What would you use without FGLRX?

---

### Post by Nesnej Trick on 2011-08-06
I'm also experiencing the same problem in Kubuntu 11.04. What I find most annoying is that there is a 1-2 second lag in text entry. You type something in and it takes ages for it to appear on the screen.

The same problem seems to exist in Thunderbird too. Could it be a general Mozilla problem?

Nvidia 7900 GT using proprietary drivers here.

EDIT: I also noticed that if I go into full screen mode, right-clicking makes the entire screen blink.

---

