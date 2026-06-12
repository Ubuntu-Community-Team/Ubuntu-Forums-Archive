---
title: "Display"
date: 2010-12-24
forum: General Help
---

### Post by Cekoftw1 on 2010-12-24
Hello first of all Merry X-mass to all of you   what is my problem  i have an acer emachines525 or e525 the problem with ubuntu is that i can't change the brightness tried everything from power management to  an pp called flux  to adding files in /acpi/ to..you name it.. i want ubuntu so badly :( please some more ideas ?

---

### Post by noah++ on 2010-12-24
Have you tried the brightness keyboard shortcuts for your computer? (They're **Fn&#8594;** and **Fn**&#8592; I think.)

---

### Post by Cekoftw1 on 2010-12-25
Yeah i did nothing works as i said.. puted files in acpi to fix this still not working

---

### Post by dino99 on 2010-12-25
googling around i've found this problem all around: mostly its a driver issue

try this package: sudo apt-get install acerhk-source

with nautilus, look if you have:

/proc/acpi/acer/brightness_default

or something similar, and watch the settings

NEW: solution found there (latest Jamos post)
[https://answers.launchpad.net/ubuntu/+question/105323](https://answers.launchpad.net/ubuntu/+question/105323)

---

### Post by Cekoftw1 on 2010-12-25
i tried compiz..to not working..

---

### Post by dino99 on 2010-12-25
its not the only way to follow :), look at links given, then try

---

### Post by Cekoftw1 on 2010-12-25
neah no link working   but i found something  sudo setpci -s 00:02.0 F4.B=XX where XX is the lightning  0 is maximum FF lowest it truly changes but i dont have the entire list ... for 100% meanin 0, 90% meanin...idk A ??

---

### Post by dino99 on 2010-12-25
what you mean: no link working ?

[https://bugs.launchpad.net/ubuntu/+source/acpid/+bug/392948](https://bugs.launchpad.net/ubuntu/+source/acpid/+bug/392948)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/489041](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/489041)

---

### Post by Cekoftw1 on 2010-12-25
Not that links don't work they don't work in my ubuntu ..what about that list ? anyone knows ? so start at 0 - FF  ends

---

### Post by matt_symes on 2010-12-25
Hi

I don't know if you have tried something like this (if you have my apologies)...

On my laptop i can change the brightness from the command line by...

```
sudo -i
```

to enter a root shell

```
echo -n 50 > /proc/acpi/video/VGA1/LCD/brightness
```

then 

```
exit
```

The values of n are 0 - 100. The folders VGA1 and LCD might be different on your system (you will have to look) but hopefully that, or something similar, will work.

If that works maybe you could write a script to set the values at start up.

EDIT:

BTW: another variation is

echo -n 100 | sudo tee /proc/acpi/video/VGA1/LCD/brightness

Kind regards

---

### Post by Cekoftw1 on 2011-01-27
I can't see VGA or LCD or something like that what to do ?

---

### Post by Cekoftw1 on 2011-01-28
Guys figured it out  from terminal "sudo setpci -s 00:02.0 F4.B=xx" but every time i shutdown or restart goes to default anything to make this everytime ? the same way ?

---

