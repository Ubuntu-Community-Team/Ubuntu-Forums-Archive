---
title: "Schedule bleachbit ? Options from GUI ?"
date: 2012-08-09
forum: General Help
---

### Post by Jethro_uk on 2012-08-09
Hi all,

currently running BleachBit from the GUI. Is there an *easy* way to work out what CLI parameters it is generating, so I can schedule a daily run with the same parameters I have selected from the GUI ?

---

### Post by raja.genupula on 2012-08-09
you can use cron and gnome-schedule .

[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

```
sudo apt-get install gnome-schedule

```

---

### Post by Andrew.Z on 2012-08-16
BleachBit has a documented CLI option --preset which uses the options selected in the GUI.  Use it with caution in case you ever choose new options.

---

