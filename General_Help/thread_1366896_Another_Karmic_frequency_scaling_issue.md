---
title: "Another Karmic frequency scaling issue"
date: 2009-12-28
forum: General Help
---

### Post by tgeer43 on 2009-12-28
I've seen a fair number of frequency scaling issues related to 9.10 Karmic but not the specific question that I'm dealing with. In fact, my problem seems relatively minor compared to some.

Under 9.04 JJ, the CPU frequency scaling on my HP DV9500T notebook worked as advertised. The system defaults to the 'OnDemand' scaling governor and I have no problems changing it whether through the panel applet or some quick and dirty scripts that I wrote.

Under 9.10 KK scaling still works and can be changed easily as well but the problem is that the default governor is 'Performance' and my attempts to set it to 'OnDemand' at boot up have been unsuccessful. So far I have tried adding a new item to 'Startup Applications' with the following commands:
```
echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
echo ondemand > /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor
```(both with and without prefixing the commands with 'sudo')

Additionally I've tried adding the above two lines to /etc/rc.local and making the script executable. Neither method has any effect on the scaling governor yet entering these same commands in a terminal works just fine. Note also that I previously edited a file (can't remember which one at the moment) that allows me to change the frequency without requiring a password. That part works perfectly. I just can't seem to make the changes to the CPU frequency scaling governor automatically at system start.

I understand that the functions of frequncy scaling have been moved to the kernel under 9.10 Karmic but this doesn't shed any light on the problem for me.

Can anyone offer any assistance in this matter? All I want to do is start the computer with the governor automatically set to 'OnDemand'.

Thanks in advance,

tgeer

---

### Post by nstgc379 on 2009-12-28
nevermind.

---

### Post by tgeer43 on 2009-12-29
> **nstgc379 said:**
> nevermind.

You know, nstgc379 that if someone were just casually browsing this thread they might think that I was the one that wrote 'nevermind' and not be inclined to answer my question. If you mistakenly start a reply and then change your mind, next time just don't hit the 'Submit Reply' button, please. This will avoid any confusion.  Anyway, the plot thickens. As stated in my original post, if I enter the line:  ```
echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor 
```  at the command line, it works just fine. If I try to enter the same command via any other method such as in a script, with the 'Run Application' panel applet, or via a custom Application Launcher in the panel, it fails with no output or error message of any kind. This makes no apparent sense and didn't behave this way in Jaunty.  tgeer

---

### Post by samrat1985 on 2009-12-29
echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
echo ondemand > /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor

Why don't you put the above lines in /etc/rc.local

---

### Post by philinux on 2009-12-29
```
gksudo gedit /etc/init.d/ondemand
```

line 27 change to the governor you want

---

### Post by tgeer43 on 2009-12-29
> **samrat1985 said:**
> echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
echo ondemand > /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor

Why don't you put the above lines in /etc/rc.local
In my original post above I stated that I had tried exactly that (as well as some other methods) to no avail.

I can deal with the fact that the default governor under Karmic is 'Performance' whereas it is 'OnDemand' under Jaunty if only I could change it automatically at boot time. ALL of the methods I've tried work just fine under Jaunty, even though it isn't necessary since Jaunty defaults to the governor that I want anyway.

I know it's got to do with the kernel taking over the scaling responsibilities but that fact alone doesn't bring me any closer to a resolution.

tgeer

---

### Post by nstgc379 on 2009-12-29
> **tgeer43 said:**
> You know, nstgc379 that if someone were just casually browsing this thread they might think that I was the one that wrote 'nevermind' and not be inclined to answer my question. If you mistakenly start a reply and then change your mind, next time just don't hit the 'Submit Reply' button, please. This will avoid any confusion.  

Its bad to assume that I simply changed my mind. I see your point, but next time I'll make it clear that I was the one said that and the previous poster. I said something stupid, then realized my mistake after having posted.

---

### Post by tgeer43 on 2009-12-29
> **nstgc379 said:**
> Its bad to assume that I simply changed my mind. I see your point, but next time I'll make it clear that I was the one said that and the previous poster. I said something stupid, then realized my mistake after having posted.
No problem, nstgc379.

---

### Post by TheNessus on 2009-12-29
> **tgeer43 said:**
> You know, nstgc379 that if someone were just casually browsing this thread they might think that I was the one that wrote 'nevermind' and not be inclined to answer my question. 

True, I almost skipped the thread after reading the 'nevermind'!

---

### Post by tgeer43 on 2009-12-29
> **philinux said:**
> ```
gksudo gedit /etc/init.d/ondemand
```line 27 change to the governor you want
Thanks, philinux.
Before I saw your post I found something else that's working for me and can also be used in other ways besides setting the initial governor on boot up. Instead of using:
```
echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
echo ondemand > /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor
```I used:
```
cpufreq-selector -c 0 -g ondemand
cpufreq-selector -c 1 -g ondemand
```This works in /etc/rc.local and in 'Startup Applications' for setting the default governor at boot time. Additionally it can be used for a custom application launcher in the panel for making on-the-fly governor changes after system startup.. It takes up a lot less real estate in the panel than having to use two separate CPU Frequency Scaling applets.

I'll try your method on my machine later just to make sure it works for my installation.

tgeer

---

