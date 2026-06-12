---
title: "Ubuntu 12.04 problems with suspending laptop"
date: 2012-07-16
forum: General Help
---

### Post by jakepc123 on 2012-07-16
I have a problem with my laptop in Ubuntu 12.04. When I try to suspend the screen will go black but the backlight stays on and the fan continues to spin until I turn it completely off.

CPU: i5 2450M
Graphics: NVIDIA GT 540M 1GB

I did have some problems with the graphics but that was fixed by instaling [bumblebee]("http://bumblebee-project.org/") and now this is the only problem.

Thanks in advance.

---

### Post by SigmaSanti on 2012-07-16
I had a similar problem on my dell xps 15. My laptop would fail to suspend if the nvidia card was turned off. I solved this by renabling the nvidia card before suspending, and then turning it off again on resume.

bbswitch, which is part of the bumblebee project, handles the power saving functions.
Check if bbswitch is installed and can turn off the nvidia card, if its working correctly these options might fix it:
This tells bbswitch to disable the card on boot, and renable it on shutdown/suspend.
```

modprobe bbswitch load_state=0 unload_state=1

```
This page has the commands to check the status of bbswitch.
[https://github.com/Bumblebee-Project/bbswitch]("https://github.com/Bumblebee-Project/bbswitch")

---

### Post by jakepc123 on 2012-07-16
> **SigmaSanti said:**
> I had a similar problem on my dell xps 15. My laptop would fail to suspend if the nvidia card was turned off. I solved this by renabling the nvidia card before suspending, and then turning it off again on resume.

bbswitch, which is part of the bumblebee project, handles the power saving functions.
Check if bbswitch is installed and can turn off the nvidia card, if its working correctly these options might fix it:
This tells bbswitch to disable the card on boot, and renable it on shutdown/suspend.
```

modprobe bbswitch load_state=0 unload_state=1

```
This page has the commands to check the status of bbswitch.
[https://github.com/Bumblebee-Project/bbswitch]("https://github.com/Bumblebee-Project/bbswitch")

I have tried this but it didn't change anything.

---

### Post by SigmaSanti on 2012-07-16
After reading the project page again I saw this:
> 
    You're not allowed to disable a card if a driver (nouveau, nvidia) is loaded.
    Before suspend, the card is automatically enabled. When resuming, it's disabled again if that was the case before suspending. Hibernation should work, but it not tested.


Are you running anything on the nvidia card when you suspend?
Is bbswitch working?
To get the status of bbswitch:
```
 
cat /proc/acpi/bbswitch

```
Then run a program using "optirun", check bbswitch, then quit, and check bbswitch again to see if it is disabling the nvidia card correctly.

Additionally what model laptop is it?

---

### Post by jakepc123 on 2012-07-16
> **SigmaSanti said:**
> After reading the project page again I saw this:


Are you running anything on the nvidia card when you suspend?
Is bbswitch working?
To get the status of bbswitch:
```
 
cat /proc/acpi/bbswitch

```
Then run a program using "optirun", check bbswitch, then quit, and check bbswitch again to see if it is disabling the nvidia card correctly.

Additionally what model laptop is it?

Running 'cat /proc/acpi/bbswitch' returns '**0000:01:00.0 OFF**' every time including when a program launched with optirun is running.

And the laptop is a [NovaTech nSpire Pro 2450]("http://www.novatech.co.uk/laptop/range/nspirepro2450.html")

---

### Post by SigmaSanti on 2012-07-16
> **jakepc123 said:**
> Running 'cat /proc/acpi/bbswitch' returns '**0000:01:00.0 OFF**' every time including when a program launched with optirun is running.

That is the problem, the nvidia card is not being turned "on" at all, even when it should be. 

This also means that bumblebee is not working properly, if you ran a program with optirun it would be using the intel card instead of the nvidia one. You should not be seeing any increase in frame rate when using optirun because of this.

Does optirun show any error messages when you run it?

Did you install bumblebee from the ubuntu ppa or from source?
[https://wiki.ubuntu.com/Bumblebee]("https://wiki.ubuntu.com/Bumblebee")

This is a strange problem since the nvidia card should default to being "on", since it is "off" this suggests that the bbswitch is working, at least partially.

[Bumblebee troubleshooting]("https://github.com/Bumblebee-Project/Bumblebee/wiki/Troubleshooting") - bumblebee's troubleshooting page might help.

---

### Post by jakepc123 on 2012-07-16
> **SigmaSanti said:**
> That is the problem, the nvidia card is not being turned "on" at all, even when it should be. 

This also means that bumblebee is not working properly, if you ran a program with optirun it would be using the intel card instead of the nvidia one. You should not be seeing any increase in frame rate when using optirun because of this.

Does optirun show any error messages when you run it?

Did you install bumblebee from the ubuntu ppa or from source?
[https://wiki.ubuntu.com/Bumblebee]("https://wiki.ubuntu.com/Bumblebee")

This is a strange problem since the nvidia card should default to being "on", since it is "off" this suggests that the bbswitch is working, at least partially.

[Bumblebee troubleshooting]("https://github.com/Bumblebee-Project/Bumblebee/wiki/Troubleshooting") - bumblebee's troubleshooting page might help.

Sorry I tried again and running optirun is turning on the graphics card as it should. Although to answer your question it was installed with the ubuntu ppa.

I have also tried hibernating with 

```
sudo pmi action hibernate

```

and this again didn't turn off the computer once it had gone into hibernate, it did however wake up after being turned off and back on so I think it is just not turning off once it has suspended/hibernated.

---

### Post by SigmaSanti on 2012-07-16
Hmmm... If it's not optimus then it could be some other hardware on the laptop that is not being disabled properly on suspend. 

Look at "Debugging Suspend" on this page:
[https://wiki.ubuntu.com/DebuggingKernelSuspendHibernateResume]("https://wiki.ubuntu.com/DebuggingKernelSuspendHibernateResume")

That might help you narrow down the problem to something more specific.

---

### Post by alanesq on 2013-01-11
I had a similar problem with my laptop and after trying endless suggestions found on the internet, I tried removing xfce4-power-manager and then re installed it

so far this seems to have done the trick?

---

