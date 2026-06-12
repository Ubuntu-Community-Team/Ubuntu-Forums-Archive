---
title: "Brightness fn keys not working for Sony VGN NR21S"
date: 2011-07-26
forum: General Help
---

### Post by rebeus on 2011-07-26
Hi there,

The function keys regarding the brightness do not work on my laptop. I am using Ubuntu 10.4 Lucid Lynx LTS 32 bit version.

I've looked on the internet for help regarding my laptop but I cant find any solutions regarding the brightness function keys for my laptop **Sony Vaio VGN NR21S**. The graphics card in my laptop is** NVidia Geforce 8400M GT**.

I've tried writing brightness-up and brightness down scripts along with a bash script but even those don't work.

I tried Gnome Power Manager but that didn't solve any issues.

The wireless and sound functions work.

Are there any solutions available for this particular laptop model? I would really appreciate your input regarding the above.

Thanks in advance.

---

### Post by 3602 on 2011-07-26
Try installing *xbacklight* and 
Increase with [I]xbacklight -inc 10
[/I]Decrease with [I]xbacklight -dec 10
[/I]If that doesn't work, maybe *xgamma*. If not, you're stuck.
Sorry about that.

---

### Post by tredegar on 2011-07-26
There's a long thread [here]("http://ubuntuforums.org/showthread.php?t=88611") that may give you some ideas.

Otherwise, if you are using the NVIDIA driver, you can control brightness from the "NVIDIA X Server Settings" application.

You can also take a look in **/proc**

I have **/proc/acpi/video/NGFX/LCD/brightness** to which I can echo numbers to change the brightness:```
tred@vaio:~$ cat /proc/acpi/video/NGFX/LCD/brightness
levels:  4 16 28 40 52 64 76 88 100
current: 100
tred@vaio:~$ sudo sh -c 'echo 52 > /proc/acpi/video/NGFX/LCD/brightness'
[sudo] password for tred: 
tred@vaio:~$ sudo sh -c 'echo 100  > /proc/acpi/video/NGFX/LCD/brightness'
tred@vaio:~$ 
```

---

