---
title: "Power Management on Intel Atom"
date: 2010-03-17
forum: General Help
---

### Post by serious7 on 2010-03-17
Hi I have ubuntu netbook remix and my battery life has been significantly lower compareed to using it on windows 7. I get around 8 hours battery life in windwos 7 but on ubuntu i'm only getting max 5 hours. What can I do to fix this? I tried disabling gnome power management and installing kpowersave. It helped a bit (gnome power management was giving me 3 hours). But I still want my 8 hour battery life. :( am I doing something wrong here?

I have kpowersave on powersave mode and its not giving me 8 hours. Note I use this laptop on idle at all times. only for msn chatting. its a netbook so im not doing anything different as compared to using windows 7. screen brightness is low and everything.

I'm using hp 210 intel atom processor.

---

### Post by serious7 on 2010-03-28
bump

---

### Post by serious7 on 2010-03-28
Upon doing some research, I realize my processor is not properly being utilized in linux. 

nicky@nicky-laptop:~$ cpufreq-info
cpufrequtils 005: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to [email]cpufreq@vger.kernel.org[/email], please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0
  hardware limits: 1000 MHz - 1.67 GHz
  available frequency steps: 1.67 GHz, 1.33 GHz, 1000 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 1000 MHz and 1.67 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 1000 MHz.
  cpufreq stats: 1.67 GHz:0.00%, 1.33 GHz:0.00%, 1000 MHz:0.00%  (248)
analyzing CPU 1:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 1
  hardware limits: 1000 MHz - 1.67 GHz
  available frequency steps: 1.67 GHz, 1.33 GHz, 1000 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 1000 MHz and 1.67 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 1000 MHz.
  cpufreq stats: 1.67 GHz:0.00%, 1.33 GHz:0.00%, 1000 MHz:0.00%  (264)



Other people have 800 mhz as thier lowest state. maybe thats why im not getting the full battery life that I expect it to have. How do I fix this?

---

### Post by serious7 on 2010-03-28
bump

---

### Post by serious7 on 2010-03-28
i forgot to mention im using intel atom n450. How come the lowest frequency is only 1000 mhz :S people have 800 mhz as thier lowest.

---

### Post by serious7 on 2010-04-03
bump

---

### Post by Meyithi on 2010-04-05
Have the same problem - Windows can drop the freq down drastically whereas lowest I can get in Linux is 1000 Mhz.  This is why our batteries drain so fast.

I've tried using acpi-cpufreq with cpufrequtils and everything, I think the processor is so new that the freqs aren't read properly.

---

### Post by jhemz on 2010-04-28
i'm havign the exact same problem with the exact same netbook. hp mini 210 and i'm ready to switch back to w7. i found something called powersaver or something but i can't figure out how to install it.

---

### Post by powerofpi on 2010-04-28
I recommend installing laptop-mode-tools and then editing /etc/laptop-mode/laptop-mode.conf as well as the individual device settings in the /etc/laptop-mode/conf.d/ directory. The cpu frequency settings can be modified by editing /etc/laptop-mode/conf.d/cpufreq.conf. Everything is surprisingly well explained inside each of the .conf files.

I was able to squeeze an additional 1 hour of battery life out of my Acer Aspire 6930 after tweaking, and I'm an absolute noob at this. Good luck.

---

### Post by Th3_uN1Qu3 on 2010-11-02
You shouldn't need laptop-mode-tools, here's a definitive solution to the problem.

[LIST=1]
[*]Open a file manager as root (open a terminal and type in sudo nautilus).
[*]Navigate to the File System/etc directory. 
[*]Scroll down and open cpufreqd.conf.
[*]Save a backup copy.
[*]Tweak to your heart's liking.
[/LIST]

I did the following:
On Performance Low i set minfreq = 0%, maxfreq = 100% and policy = ondemand
On Powersave High i set minfreq = 0%, maxfreq = 60% and policy = powersave
On Powersave Low i set minfreq = 0%, maxfreq = 40% and policy = powersave

Now scroll down and you can also set the battery intervals and if you wish you can comment out the first one and use powersave from the very start. Oh yeah and reboot when you're done.

Anyway. A message to Ubuntu developers. You bothered to create no less than THREE different battery intervals with different performance settings. That's great! And then you screwed all three up by specifying fixed CPU frequencies. **Please leave minfreq = 0% on battery!!!** Thank you.

---

