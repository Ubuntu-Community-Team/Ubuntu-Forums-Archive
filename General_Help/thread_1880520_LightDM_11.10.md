---
title: "LightDM 11.10"
date: 2011-11-13
forum: General Help
---

### Post by sammiev on 2011-11-13
Hi folks. Looking to install LightDM on 11.10 and for some reason it will not work. My other 2 laptops both boot to the LightDM log-in screen. I'm using THIS guide but still no luck. Any ideas would be welcomed. :)
Thanks sammiev

---

### Post by linuxuser12345 on 2011-11-13
LightDM is already installed by default on Ubuntu 11.10. Anyways, try restarting your system: This usually fixes my login screen problems.

---

### Post by bluexrider on 2011-11-13
Unless you changed something Lightdm is set as default in 11.10 

If for some reason you are not able to get to the greeter screen then Alt+F2 and that will bring you to a terminal. 

Log on

sudo apt-get install lightdm $$ sudo apt-get install unity-greeter 

reboot

---

### Post by sammiev on 2011-11-13
Hi folks and many thanks for the posts. I did get it going by UN-installing and reinstalling LightDM and unity-greeter. bluexrider I noticed it did install unity-greeter which I believe was the problem. :)

---

### Post by bluexrider on 2011-11-13
Unity-Greeter shouldn't be an issue. 

Did you do a fresh install before the problems or was it an upgrade?


Just wondering where it went wrong.

---

### Post by sammiev on 2011-11-13
It was a beta 1 CD at the time. Been like that for months and I just got the time to track it down. Once again, Thanks! :)

---

