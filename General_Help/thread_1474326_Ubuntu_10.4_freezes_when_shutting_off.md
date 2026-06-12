---
title: "Ubuntu 10.4 freezes when shutting off"
date: 2010-05-05
forum: General Help
---

### Post by holycow131415 on 2010-05-05
Hey everyone,

I have a laptop here with win 7 and decided to dual boot with ubuntu just for fun. Win 7 starts up, works, and shutdown/restarts fine. Ubuntu starts up, works great, but freezes at the splash screen showing "Ubuntu" with the bar scrolling when logging off to restart. Please help. I dont think holding down the power button to turn it off is too good. i searched google but found nothing =/

Edit: Shutting off works fine now... its just the restarting problem

---

### Post by utnubuuser on 2010-05-06
Start here:> [http://ubuntuforums.org/showthread.php?t=1474384]("http://ubuntuforums.org/showthread.php?t=1474384")

---

### Post by holycow131415 on 2010-05-06
so its a plymouth problem?

is the best option to uninstall it and reinstall it from synaptic?

---

### Post by holycow131415 on 2010-05-06
:popcorn:

---

### Post by holycow131415 on 2010-05-06
When restarting the splash freezes at the second dot under the Ubuntu and does not turn off.

---

### Post by timepilot on 2010-05-07
I'm having the same problem! ):P

I tried adding acpi=force to grub and that doesn't work! ](*,)

---

### Post by holycow131415 on 2010-05-07
/me cries

---

### Post by utnubuuser on 2010-05-09
report the issue at launchpad so it can be fixed...   Hardy had some serious issues at release .0 to, and turned out to be a great LTS...

---

### Post by timepilot on 2010-05-09
> **utnubuuser said:**
> report the issue at launchpad so it can be fixed...   Hardy had some serious issues at release .0 to, and turned out to be a great LTS...

Could you provide me with a link to report this? :)

Note: I do have this issue with other linux distros too. :oops:
         (Problem was never solved.)

Here are my computer specs:

 Cpu - Intel 2.6
 Ram- 1.5gb
 Hd - 500gb
 Chipset - Intel 82845G

---

### Post by holycow131415 on 2010-05-16
ttt

---

### Post by holycow131415 on 2010-05-21
anyone?

---

### Post by holycow131415 on 2010-06-18
ttt

---

### Post by holycow131415 on 2010-07-04
TTT, some one help!

---

### Post by ericepsylon on 2010-07-28
Same problem here. Is there any solution known?

---

### Post by amsterdamharu on 2010-07-28
When you get a message saying "will now halt" you have to manually press the power button to shut it down. This normally happens when you have acpi=off in grub.
Maybe this is what happens but you only see the  gui tty. Press control+alt+F1 to see another tty you have about 7 or 9 of them (control+alt+F1 to F9). Is there any output on any of these tty's?

If gdm hangs you can kick it by pressing control+alt+backspace, this will shutdown x server (the graphic/windowed environment) and have you at a terminal (DOS looking screen) or will automatically restart gdm and have you in a graphic login screen.

What happens when you try any of  these things?

When you try to reboot and the system hangs there were several suggestions what to do:

What happens when you press control+alt+F2 log in and type:
```
sudo /etc/init.d/gdm stop                      
sudo reboot
```Did you try to re-install [plymouth]("https://launchpad.net/+search?field.text=plymouth")?

Type in a console:
```
apt-get purge plymouth
apt-get install plymouth
```

---

### Post by ericepsylon on 2010-07-28
> **ericepsylon said:**
> Same problem here. Is there any solution known?

I solved the problem re-installing the video drivers using this tutorial:
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1444738](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1444738)

---

### Post by wallpaper_thief on 2010-07-28
> **holycow131415 said:**
> TTT, some one help!

press escape during the shutdown process, and report what it says to this bug:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/576204](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/576204)

it seems to be a known bug

---

### Post by archeryrob on 2010-07-30
I was having the same problem with 10.04 and I I went to the top right and hit shutdown it froze. I started doing restarts and pulling the cord on restart. One day I hit the power button you use to start and instant shutdown. Been using that for  now.

---

