---
title: "who changes my cpufreq governor settings !?"
date: 2009-09-08
forum: General Help
---

### Post by demiurg on 2009-09-08
My Ubuntu boots with performance cpufreq governor enabled, which is what I want. However, a few seconds after I login into Gnome environment something changes it to ondemand !? 

Why you are doing this to me :) !?

---

### Post by SoftwareExplorer on 2009-09-08
Welcome to the ubuntu forums :) Does it stick when you set it to something else, or does it just get reset only over reboots? (Cause if that's the case, there's a simple fix:just don't reboot. :) (I'm kidding!))
I set it to always be at a certain setting once, but that was on a different install, and now I need to be unlazy enought to figure it out again.

---

### Post by demiurg on 2009-09-09
It gets reset after reboot, but this is not a correct way to describe it. Performance governor is the default kernel governor as far as I recall and the kernel boots with this governor enabled. After that something in Ubuntu changes it to ondemand even though I never configured any power management option at all!

---

### Post by P4man on 2009-09-09
Not an answer to your question, but.. whats wrong with on-demand?

---

### Post by demiurg on 2009-09-09
It is horribly slow :)

Link desktop response time is far from being perfect even with performance governor, ondemand makes it unusable.

---

### Post by kotnik on 2009-09-09
Open up a file /etc/init.d/ondemand and it'll be obvious to you.

What you can do is to remove it from startup (install sysv-rc-conf, console sysv init manager), or adjust it so it sets the governor you prefer (change ondemand in line ```
echo -n ondemand > $CPUFREQ
``` to your favorite governor).

If you have an AMD processor ondemand is quite unusable (at least in my experience), but it works just fine with Intels.

---

### Post by demiurg on 2009-09-09
I removed ondemand script from the boot sequence long time ago. The problem is, as I described above, that after the boot sequence it is configured to performance. I mean, after all initi scripts are finished. However, it switches to ondemand after I login into Gnome.

And yes, I have an AMD CPU and ondemand is horrible.

---

### Post by dcstar on 2009-09-09
> **demiurg said:**
> I removed ondemand script from the boot sequence long time ago. The problem is, as I described above, that after the boot sequence it is configured to performance. I mean, after all initi scripts are finished. However, it switches to ondemand after I login into Gnome.


[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/156472](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/156472)

---

### Post by demiurg on 2009-09-30
Apparently the solution mention in this bug no longer works, cpufreq configuration files are no longer part of gnome-power-manager

---

### Post by demiurg on 2009-10-08
I can't believe that the only working way to change cpufreq settings is to have a crontab entry to set it every 5 minutes or so. 

This distro sucks.

---

### Post by parrado on 2009-10-08
Hi,

I have solved same problem removing all ondemand script calls.

```
sudo update-rc.d -f ondemand remove 
```

---

### Post by parrado on 2009-10-08
Hi, 

I have solved same problem removing all "ondemand" script calls 

```
sudo update-rc.d -f ondemand remove 
```

---

### Post by dcstar on 2009-10-09
> **demiurg said:**
> Apparently the solution mention in this bug no longer works, cpufreq configuration files are no longer part of gnome-power-manager

Really?, they are quite present in my system. The default cpufreq key is there to be changed as required.

---

### Post by demiurg on 2009-10-09
> **parrado said:**
> Hi, 
I have solved same problem removing all "ondemand" script calls 

I don't know what do you mean by "some", but the script is not the problem, the init scripts set the cpufreq to what I want. The problem is that something changes it to "ondemand" sometime after the init scripts are finished.

---

### Post by demiurg on 2009-10-09
> **dcstar said:**
> Really?, they are quite present in my system.
root@borjch:~# dpkg -L  gnome-power-manager | grep cpufreq
root@borjch:~#

---

### Post by parrado on 2009-10-09
> **demiurg said:**
> I don't know what do you mean by "some",.

After the boot, "something" was changing my "performance" governor to "ondemand", it's your problem? or it doesn't?

> **demiurg said:**
>  but the script is not the problem, the init scripts set the cpufreq to what I want. The problem is that something changes it to "ondemand" sometime after the init scripts are finished.

Yeah, after removing theese calls, governor "performance" is not changed to "ondemand" longer.

---

