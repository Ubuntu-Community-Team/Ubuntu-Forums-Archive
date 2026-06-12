---
title: "How to install Microsoft font on ubuntu"
date: 2012-03-30
forum: General Help
---

### Post by mjsilverstri on 2012-03-30
How to install microsoft font on ubuntu

I have tried doing these 
```
$sudo apt-get install msttcorefonts
$sudo apt-get install ttf-mscorefonts-installer

```
and then 
```
$sudo fc-cache -fv
```

and the reboot my machine.
but I still don't see microsoft in my ubuntu environment.
e.g. I go to terminal and change font. I don't see microsoft font.

Thank you.

---

### Post by garvinrick4 on 2012-03-30
Did you agree to the EULA. If not purge and reinstall.
```
sudo apt-get purge ttf-mscorefonts-installer
```
```
sudo apt-get install ttf-mscorefonts-installer
```
When it gets to EULA use tab, arrows and enter to make selections.

You can purge in terminal and then use Ubuntu software center to install.

I believe if you do not say yes to EULA you do not get another chance to do so without the purging. 
Not real sure but just something I think was in a thread at one time or another.

---

