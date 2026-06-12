---
title: "side pane"
date: 2012-01-24
forum: General Help
---

### Post by zcartist on 2012-01-24
Can someone tell me why my nautilus side pane cuts in size by 2/3 when the trash heading is selected?

thanks

---

### Post by raja.genupula on 2012-01-24
Hi ,Giving am Image can help us better .:)

---

### Post by zcartist on 2012-01-25
here it is

---

### Post by raja.genupula on 2012-01-25
After any recent updates you getting that ?

reinstall nautilus and look what it gives .

---

### Post by zcartist on 2012-01-25
what is it sudo purge...then sudo apt-get? sorry just want to do it right

---

### Post by raja.genupula on 2012-01-25
purge gonna help us,  because we need to remove configuration files of nautilus also .

sudo apt-get remove --purge nautilus
sudo apt-get install nautilus

---

### Post by zcartist on 2012-01-25
No change with a system restart

---

### Post by raja.genupula on 2012-01-26
then we have one option for this . 
```
sudo apt-get install --reinstall ubuntu-desktop
```

---

### Post by zcartist on 2012-01-26
No change

---

### Post by raja.genupula on 2012-01-27
Hi  [FONT=Verdana]You need to install the compiz config settings manager
open your terminal 
[/FONT]```
sudo apt-get install ccsm
```
[FONT=Verdana]
type compiz in ubuntu dash and it will be there . scroll down to Window Management and click on Place Windows change the default to other options . 

all the best.
[/FONT]

---

### Post by zcartist on 2012-01-27
Loaded the manager and tried different window options nothing helped. It happens in Unity. I switched to Cinnamon which I really like. Thinking it must be nautilus. Not a big deal just strange.

---

### Post by raja.genupula on 2012-01-28
It sound like a BUGGY , try to report that to Launchpad .

---

