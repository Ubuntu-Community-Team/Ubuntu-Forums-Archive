---
title: "Shut off issue"
date: 2010-09-16
forum: General Help
---

### Post by mdmorash on 2010-09-16
Hello All, I am having an issue with 10.4 that is driving me a little nuts. My laptop shuts down for no reason, or warning. It does not show a power down icon, or tell me anything. It does not "cycle" down either. It is just running one second and dead the next. I thought it may be a hardware issue but it never does it while I'm in Windows 7, nor did it do it when running 9.10 or Cent OS. Is there some setting that I am missing in 10.4? Or should I just go back to using 9.10...;)

---

### Post by Grenage on 2010-09-16
I'd look at overheating first, do you have a means of monitoring the temperature?

---

### Post by mdmorash on 2010-09-16
I do, i use Xsensors . It runs between 62 and 68 degrees Celsius on average. I also have a dual fan Antec cooler the laptop sits on.

---

### Post by TBABill on 2010-09-16
Those are pretty high average temps. Do you use Flash apps or videos a lot? Perhaps you have a heat issue as well and maybe your sensor outputs are reading low? Just a guess but when your temps hit critical the machine will just dump on you.
 
A couple items that can help the heat...if you use Ubuntu, just use the Gnome panel applet for CPU frequency scaling and choose ondemand. That'll drop your speed of your CPU (if supported) to about half its normal speed and boost up to full whenever required for the extra processing power. Works flawlessly on all my machines and helps drop temps a great deal.
 
Also make sure you're using Adobe Flash and Sun Java....the open source versions run hotter on all my laptops.
 
Lastly, and most importantly, use the proprietary video driver if available. Open source drivers are ok, but in laptops they're usually causes of very high heat that will destroy components.
 
Disregard if my points are off base.

---

### Post by quadproc on 2010-09-16
> **mdmorash said:**
> Hello All, I am having an issue with 10.4 that is driving me a little nuts. My laptop shuts down for no reason, or warning.
This sounds like an overtemperature problem.  It turns out that 10.04 has a bug in the task scheduler that sometimes causes the CPU to spin; this draws a lot of power and makes the CPU hot.  I do not know if there is anything that you can do to stop the spin once it starts.

The problem is understood but the fix requires a change in the Linux kernel.  When an upgraded kernel with the fix becomes available then you could get it and install it to replace the old kernel.

In the meantime, you might want to install version 9.10.  It does not have this bug and generally runs well.

quadproc

---

### Post by mdmorash on 2010-09-16
Thanks Grenage, TBABill, and quadproc. :D

---

### Post by mdmorash on 2010-11-07
This issue was finally solved (for me anyway) when I switched from Ubuntu 10.04 LTS 32bit to Ubuntu 10.04 LTS 64bit. With 32bit simply watching a video on Hulu would stress the system to its 100 degree shut off max in minutes. With 64bit I have not yet been able to increase the temp passed 85 degrees no matter how hard I stress the system. It is kind of a drastic fix, but it worked for me. :P

---

