---
title: "NTP time zone wrong"
date: 2011-03-19
forum: General Help
---

### Post by moaxey on 2011-03-19
since the upgrade tzdata (2011c-0ubuntu0.10.04) to 2011d-0ubuntu0.10.04
which I installed on Saturday, ntp updates seem to put me in GMT time.

I've switched to manual time settings, as it does horrific things to my mythtv database!

I'm not sure if its the upgrade, or the ntp time servers. My timezone is Australia/Tasmania.

---

### Post by wt8008 on 2011-03-21
See if you can get any hints/ideas from here: [https://help.ubuntu.com/community/UbuntuTime](https://help.ubuntu.com/community/UbuntuTime)

What is your current time zone settings according to the  /etc/timezone file?

---

### Post by SeijiSensei on 2011-03-21
'sudo tzselect' looks like a good option.  See "man tzselect" for details.

---

