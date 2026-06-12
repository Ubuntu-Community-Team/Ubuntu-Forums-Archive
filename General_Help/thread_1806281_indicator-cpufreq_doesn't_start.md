---
title: "indicator-cpufreq doesn't start"
date: 2011-07-17
forum: General Help
---

### Post by Nigggo on 2011-07-17
Hi there, i noticed that my cpu is running on full scale all the time and tried to install inducator-cpufreq to get it under control.
The problem is that thr indicator doesn't show up.
I installed is from ppa:
```

sudo add-apt-repository ppa:anton-sudak/indicators
sudo apt-get update && sudo apt-get install indicator-cpufreq

```
and tried to run it by simply executing indicator-cpufreq.
If i try to run it from terminal it gives me the following errors:
```

nigggo@nigggo-desktop:/$ sudo indicator-cpufreq
Traceback (most recent call last):
  File "/usr/bin/indicator-cpufreq", line 81, in <module>
    ind = MyIndicator()
  File "/usr/lib/pymodules/python2.7/indicator_cpufreq/indicator.py", line 99, in __init__
    self.update_ui()
  File "/usr/lib/pymodules/python2.7/indicator_cpufreq/indicator.py", line 110, in update_ui
    fmin, fmax, governor = cpufreq.get_policy(FIXME_CPU)
  File "/usr/lib/pymodules/python2.7/indicator_cpufreq/cpufreq.py", line 143, in get_policy
    policy = (p.contents.min, p.contents.max, p.contents.governor)
ValueError: NULL pointer access

```
What am i doing wrong? I am running natty x64 with latest kernel and stuff...
thanks for your help

---

### Post by japq7b on 2011-07-17
I'm not sure if it will help but check this out
[http://www.omgubuntu.co.uk/2010/12/indicator-cpufreq-cpu-frequency-scaling-indicator-applet/]("http://www.omgubuntu.co.uk/2010/12/indicator-cpufreq-cpu-frequency-scaling-indicator-applet/")

You might try installing the natty deb and then running
```
indicator-cpufreq
```

---

### Post by Nigggo on 2011-07-17
As I said... indicator-cpufreq [0.1.2] is installed but not working....

---

### Post by robboguy on 2011-09-13
I'm having exactly the same problem, anyone knows any workaround? I'm trying to give it a try to Unity!

---

