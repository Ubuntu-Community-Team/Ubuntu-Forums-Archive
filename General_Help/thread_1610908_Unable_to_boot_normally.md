---
title: "Unable to boot normally"
date: 2010-11-01
forum: General Help
---

### Post by glen-kun on 2010-11-01
Hello
I'm running Ubuntu 10.10 and I've been having this problem for a while. Basically, whenever i turn on my pc the screen goes black and there's this white cursor pulsating for 3-4 seconds. After that the screen goes completely black like when you turn off the computer. I can't operate the hard drive keyboard mouse etc. The only thing left for me is to unplug and plug it in again and again until it finally kicks in and boots normally. 
Can someone help?

---

### Post by gordintoronto on 2010-11-01
Can you provide a detailed description of your computer? It sounds like it's crashing during boot up, but it's OK once it warms up.

You don't have a reset button?  Generally, if you push the power button and hold it for 10 seconds, even a crashed computer will power down. Unplugging can only cause more problems.

---

### Post by glen-kun on 2010-11-01
[IMG]http://oi51.tinypic.com/2uqzuv6.jpg[/IMG]

I tried holding the power button but it would not work.

---

### Post by bacardiandwatermelon on 2010-11-01
Do you know what type of graphics card it is? I had this sort of problem with some intel drivers once...

---

### Post by wilee-nilee on 2010-11-01
In the terminal will identify the graphic setup.
```
lspci | grep VGA
```

For fun just run the lspci as well, or actually identify the computer model. Many times just running the model, or the graphic setup with the distro name on google will get you some answers.

---

### Post by vsh3r on 2010-11-01
Hi,

I noticed that sometimes the computer takes longer to display something perhaps as long as 3 minitues to show a display on after returning from SLEEP MODE.  The issue may be related to some programs trying to recover their state from ACPI.

V$H.

:confused:

---

### Post by glen-kun on 2010-11-03
> **wilee-nilee said:**
> In the terminal will identify the graphic setup.
```
lspci | grep VGA
```For fun just run the lspci as well, or actually identify the computer model. Many times just running the model, or the graphic setup with the distro name on google will get you some answers.

This is what i got 00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)

---

