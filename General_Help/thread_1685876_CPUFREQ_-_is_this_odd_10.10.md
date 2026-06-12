---
title: "CPUFREQ - is this odd? 10.10"
date: 2011-02-11
forum: General Help
---

### Post by TBABill on 2011-02-11
I reinstalled Ubuntu the other evening and decided to install 10.10 again instead of 10.04, which I had used and enjoyed for quite some time. However, my fan on my laptop was running full throttle, just like it did when 10.04 initially released, but it was fixed in 10.04.1 with the setting of CPUFREQ to ondemand automatically. I have since used Mint 9, Debian 6 and others, and they all default to ondemand, which is perfect.

Anyway, in 10.10 with all updates applied my machine was getting hot so I ran cpufreq-info in a terminal and was amazed to find cpufreq-utilities was not even installed so my CPU was just running at max. I quickly installed cpufreq utilities and set it to run ondemand and all is well.

Why was it not automatic in 10.10 if it is in 10.04? The system is running perfectly otherwise, but this seems odd and I'm wondering if the kernel update that happens after install of 10.10 is missing that tweak?

---

### Post by 3Miro on 2011-02-11
The governor for the CPU frequency is in the kernel, it is installed so long as you have the kernel installed. Cpufreq-utils just gives you control over it. Ondemand should be the default setting.

Which version of Ubuntu are you using Desktop/Server/Netbook?

---

### Post by TBABill on 2011-02-11
Desktop and it always works  perfectly to "ondemand" since it's a kernel setting, but the fresh 10.10 works flawlessly except for that. Had to install cpufreq-utils and set it manually to bring down my CPU freq and temps.

---

