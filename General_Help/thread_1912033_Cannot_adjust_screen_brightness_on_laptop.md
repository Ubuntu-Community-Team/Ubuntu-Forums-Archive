---
title: "Cannot adjust screen brightness on laptop"
date: 2012-01-19
forum: General Help
---

### Post by Norred on 2012-01-19
Hi all..  

 I installed ubuntu 11.10 a month or so ago but only recently realized (I usually leave my laptop plugged in) that I cannot adjust my screen brightness.

  I have looked up this issue on google but have not found a viable solution to this problem.   I appreciate any kind of help...


Thank you.. 


  My laptop is an Acer Aspire 5750-6589

---

### Post by raja.genupula on 2012-01-19
[http://askubuntu.com/questions/94515/cant-adjust-brightness-on-a-hp-pavillion-dv3](http://askubuntu.com/questions/94515/cant-adjust-brightness-on-a-hp-pavillion-dv3)

i hope it will work for you

---

### Post by Norred on 2012-01-19
Already tried that previously ...  a couple others too when i google searched.   

Thank you for the quick reply however..

---

### Post by DevinMcElheran on 2012-01-19
try the command "xbacklight -set y" where y is the percent value you want your backlight to be set to, like "xbacklight -set 100" for full.

---

### Post by Toz on 2012-01-19
> **Norred said:**
> Already tried that previously ...  a couple others too when i google searched.   

Thank you for the quick reply however..

Have you tried the **acpi_osi=Linux** kernel parameter? Or a combination of **acpi_osi=Linux acpi_backlight=vendor**

---

### Post by Norred on 2012-01-20
Thanks but, Neither one works...   

it kills me to go through this i want to be able to use it without using the power adapter all the time and not kill my battery.

---

### Post by raja.genupula on 2012-01-20
i have a way , i mean a old way . install gnome panels and then add brightness applet . i think it will make the job . i hope it will save for every time . try it .

EDIT:[http://askubuntu.com/questions/65981/how-can-i-get-gnome-panel-in-ubuntu-11-10](http://askubuntu.com/questions/65981/how-can-i-get-gnome-panel-in-ubuntu-11-10)

may be help you.

---

### Post by Toz on 2012-01-20
> **Norred said:**
> Thanks but, Neither one works...   

it kills me to go through this i want to be able to use it without using the power adapter all the time and not kill my battery.

Thats interesting because there are a few links on the web that show that these kernel parameters work for this model of laptop. See:
- [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/863156]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/863156") (similar laptop)
- this: [http://ubuntuforums.org/showpost.php?p=11179176&postcount=10]("http://ubuntuforums.org/showpost.php?p=11179176&postcount=10") verifying that this: [http://ubuntuforums.org/showpost.php?p=9291657&postcount=1]("http://ubuntuforums.org/showpost.php?p=9291657&postcount=1") worked.

Can you try those parameters again, and after you boot with them, post back the results of:
```
cat /proc/cmdline
```

---

### Post by Norred on 2012-01-21
Sorry about wasting your time with this...  I found out that I entered the code in wrong and now it works.

Thank you...

---

