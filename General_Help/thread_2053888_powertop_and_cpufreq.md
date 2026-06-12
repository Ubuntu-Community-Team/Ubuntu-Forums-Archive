---
title: "powertop and cpufreq"
date: 2012-09-06
forum: General Help
---

### Post by qwertyjjj on 2012-09-06
I leave my desktop on most of the time and am looking at ways of cutting power.
I installed powertop and toggled all the settings it said was bad to good.
Firstly, some of the settings recommend autopowersave on USB ports like mouse, keyboard, IR receiver. Will they come on again automatically when used?

Secondly, I was thinking about installing indicator-cpufreq and throttling down to the lowest CPU when not using it to play video etc...all it does is download video, music, etc, overnight.
I installed it but it does not start from the command line when I type indicator-cpufreq. Any ideas what I can do to get it working?

---

### Post by qwertyjjj on 2012-09-08
> **qwertyjjj said:**
> I leave my desktop on most of the time and am looking at ways of cutting power.
I installed powertop and toggled all the settings it said was bad to good.
Firstly, some of the settings recommend autopowersave on USB ports like mouse, keyboard, IR receiver. Will they come on again automatically when used?

Secondly, I was thinking about installing indicator-cpufreq and throttling down to the lowest CPU when not using it to play video etc...all it does is download video, music, etc, overnight.
I installed it but it does not start from the command line when I type indicator-cpufreq. Any ideas what I can do to get it working?

any ideas?

---

### Post by dcstar on 2012-09-08
> **qwertyjjj said:**
> 
.........
I installed it but it does not start from the command line when I type indicator-cpufreq. Any ideas what I can do to get it working?
You **do not** start it. It starts automatically when booted.

So what is the extra icon in the Indicator Applet doing?

---

### Post by qwertyjjj on 2012-09-08
> **dcstar said:**
> You **do not** start it. It starts automatically when booted.

So what is the extra icon in the Indicator Applet doing?

There is no icon at all.

---

### Post by lordievader on 2012-09-08
If you reboot the indicator should show up. What I recommend is that you use the on-demand or the conservative CPU profile, this will clock down the cpu if it is idling.
Read this if you want to know more about CPU-scaling: [http://www.kernel.org/doc/Documentation/cpu-freq/governors.txt](http://www.kernel.org/doc/Documentation/cpu-freq/governors.txt)

In disabling USB devices within power-top it has been my experience that if I toggle the switch for my mouse it turns off after a while, and the only way of getting it back on is to press a button, moving the mouse doesn't help. 
I guess best way to find out is to experiment with the switches.

---

### Post by qwertyjjj on 2012-09-08
> **lordievader said:**
> If you reboot the indicator should show up. What I recommend is that you use the on-demand or the conservative CPU profile, this will clock down the cpu if it is idling.
Read this if you want to know more about CPU-scaling: [http://www.kernel.org/doc/Documentation/cpu-freq/governors.txt](http://www.kernel.org/doc/Documentation/cpu-freq/governors.txt)

In disabling USB devices within power-top it has been my experience that if I toggle the switch for my mouse it turns off after a while, and the only way of getting it back on is to press a button, moving the mouse doesn't help. 
I guess best way to find out is to experiment with the switches.

Also, my fan seems to be on constantly. I'm not sure if it's even connected to a sensor. I tried installing fan tools and pwdconf but they couldn't control the speed.

---

### Post by lordievader on 2012-09-08
Perhaps you simply cannot control your fan speed. However before messing with fan speeds I recommend installing lm-sensors, if your CPU is running hot it is probably a bad idea to turn down the cooling. To install lm-sensors I refer you to the following guide: [http://www.cyberciti.biz/faq/howto-linux-get-sensors-information/](http://www.cyberciti.biz/faq/howto-linux-get-sensors-information/)

---

### Post by qwertyjjj on 2012-09-08
> **lordievader said:**
> Perhaps you simply cannot control your fan speed. However before messing with fan speeds I recommend installing lm-sensors, if your CPU is running hot it is probably a bad idea to turn down the cooling. To install lm-sensors I refer you to the following guide: [http://www.cyberciti.biz/faq/howto-linux-get-sensors-information/](http://www.cyberciti.biz/faq/howto-linux-get-sensors-information/)

it's not running hot, it's running loud.
cpu is 35 degrees

---

### Post by lordievader on 2012-09-08
Does lm-sensors detect a fan? In my case it didn't and I never found a way to control my fan.

---

