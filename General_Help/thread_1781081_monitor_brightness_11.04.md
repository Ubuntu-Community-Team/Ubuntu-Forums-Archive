---
title: "monitor brightness 11.04"
date: 2011-06-12
forum: General Help
---

### Post by syoung27 on 2011-06-12
so every distro i've had so far i couldn't seem to be able to adjust the monitor brightness but never really explored...is it possible? the system monitor app was poorly rated.

---

### Post by Toz on 2011-06-12
Can we get some specs on your system?
What does:```
lspci | grep VGA
```return?

---

### Post by syoung27 on 2011-06-13
spencer@spencer-ltp:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)

---

### Post by Toz on 2011-06-13
What does the following return?```
cat /sys/class/backlight/acpi_video0/brightness
```

Also, what model (model number) of Acer do you have?

---

### Post by syoung27 on 2011-06-13
that returns '9'
Acer Aspire 5742. i can't find the same one anymore, last year model i suppose.
if you're looking for a rough match simple specs of mine are in my signature

---

### Post by Toz on 2011-06-13
Try to issue:```
sudo setpci -s 00:02.0 F4.B=96
```and see if the brightness changes. If it does, you can set it back to the original setting with```
sudo setpci -s 00:02.0 F4.B=ff
```

Lets see if these codes work for you.

---

### Post by syoung27 on 2011-06-13
nope nothin. howcome they can't make it simple?  my media hotkeys work with no configuration at all

oh and if you happen to have the answer, i was looking at phones today, anything particularly good with linux? im interested in the android platform

---

### Post by Toz on 2011-06-13
Have a look at this link: [http://ubuntuforums.org/showthread.php?t=1617362]("http://ubuntuforums.org/showthread.php?t=1617362")

---

### Post by syoung27 on 2011-06-13
> **Toz said:**
> Have a look at this link: [http://ubuntuforums.org/showthread.php?t=1617362](http://ubuntuforums.org/showthread.php?t=1617362)

worked like a charm! thanks

---

### Post by inearlygaveup on 2011-06-13
Glad your sorted out 

I have an acer Aspire 5100 and had the same *'monitor brightness'* problem until I found this 
[http://www.lazyscripter.com/2010/04/how-to-setup-redshift-for-ubuntu/](http://www.lazyscripter.com/2010/04/how-to-setup-redshift-for-ubuntu/)

Just in case you need extra control

---

### Post by jackn on 2011-07-17
> **Toz said:**
> Try to issue:```
sudo setpci -s 00:02.0 F4.B=96
```and see if the brightness changes. If it does, you can set it back to the original setting with```
sudo setpci -s 00:02.0 F4.B=ff
```

Lets see if these codes work for you.

This works perfectly for me, on a Samsung NC110.

The next tweak, to which you provide a link below, namely modifying Grub, does not allow me to modify brightness either through system settings or the function keys.

jackn

---

### Post by Toz on 2011-07-17
Have a look at this potential solution: [http://ubuntuforums.org/showpost.php?p=10926719&postcount=6]("http://ubuntuforums.org/showpost.php?p=10926719&postcount=6") that has worked on a number of other notebooks.

---

