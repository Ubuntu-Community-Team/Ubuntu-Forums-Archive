---
title: "[HELP] failed to execute child process &quot;gnome-appearance-properties&quot;"
date: 2010-08-03
forum: General Help
---

### Post by WarrenSH on 2010-08-03
I am using Ubuntu 10.04 & I went to change my appearance/theme & I got this error message 

**failed to execute child process "gnome-appearance-properties"**

How can I fix this? 

[CENTER][IMG]http://img225.imageshack.us/img225/18/screenshoterror.png[/IMG][/CENTER]

---

### Post by chopinhauer on 2010-08-04
```
sudo apt-get --reinstall install gnome-control-center
```

---

### Post by Flos Headford on 2010-09-17
Thank you for the suggestion, chopinhauer, but
sudo apt-get --reinstall install gnome-control-center
made no difference for me (I am trying to execute my own shell script -it used to work).
Phil

---

