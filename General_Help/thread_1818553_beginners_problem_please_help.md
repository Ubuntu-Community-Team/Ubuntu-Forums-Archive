---
title: "beginners problem please help?"
date: 2011-08-04
forum: General Help
---

### Post by mizy on 2011-08-04
what does creating a launcher do?how can install my wireless modem on ubuntu.

---

### Post by Wim Sturkenboom on 2011-08-04
When you create a launcher, it will give you an icon that you can click and something will happen (usually an application is started).

On the modem:
are you talking about a 3G dongle? Or wifi dongle? Some details ther would help (e.g. make/model, usb or ethernet connection to the device).

---

### Post by wildmanne39 on 2011-08-05
Hi, run these commands in a terminal please:
```
sudo lshw -C network
```
```
lspci -nn | grep 0280
```
```
iwconfig
```
```
rfkill list all
```
```
lsmod
```
and post the outcome here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

