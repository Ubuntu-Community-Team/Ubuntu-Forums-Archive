---
title: "Few issues with Natty."
date: 2011-05-02
forum: General Help
---

### Post by eldonkr on 2011-05-02
I just upgraded from Maverick to Natty and I have a couple of small issues with the new Unity interface. The first one is that my panel applets have vanished from the top panel. That's not normally too big of a deal, I've managed to adjust to the thing on the side just fine but there are a few panel applets that I'm missing and can't seem to find an alternative for.

I'm used to having a system monitor applet on the top panel so I can watch my memory and processor and network graphs. I also had the applet that let me adjust my processor, I'd switch it to power save mode when the netbook is on battery power. I can't figure out how to do this without the panel applet and as a result my battery is draining faster than normal on battery power. I also can't seem to find the force quit applet.

Also sometimes when I switch Desktops or use Expo in any way or use the super button to search my top panel dissapears when I go back to the desktop.

---

### Post by eldonkr on 2011-05-02
Bump.

---

### Post by 3rdalbum on 2011-05-03
Gnome panel applets aren't supported anymore, because Ubuntu doesn't use the Gnome panel anymore.

I'd like a system monitor indicator too, actually, but I don't think one exists. I do believe there might be CPU frequency indicators available; maybe you just need to look through Google and find one that lets you change the clock speed.

---

### Post by mc4man on 2011-05-03
As far as the unity login applets are history, there are starting to be some appindicators, though not a whole lot yet. (some may work fine, some may not.
I'd expect more down the road and maybe built-in replacements for some things in the 11.10 release 
here's a listing of some
[http://www.webupd8.org/search/label/appindicator?max-results=20](http://www.webupd8.org/search/label/appindicator?max-results=20)

---

### Post by eldonkr on 2011-05-03
I can live without the resource monitor but I really need to know how to change my clock speed to power save when I'm on battery power. I'm losing an hour off of my battery when I'm not plugged in since upgrading because I can't change my clock speed.

A google search turned up results for cpufreq and I obtained it using an apt-get but I can't figure out how to work it in terminal.

---

### Post by eldonkr on 2011-05-03
I got cpufreq figured out.

To change your clock speed open terminal and enter
```

cpufreq-selector -c (core number e.g. 0 or 1) -g (powersave or performance)

```

You can also set the speed of both proc cores simultaneously. Here's an example of what I entered a couple minutes ago:
```

cpufreq-selector -c 0 -c 1 -g powersave

```

There's also an -f variable to set the frequency e.g. 1.00 Ghz.

---

### Post by mc4man on 2011-05-03
Even with a lower clock speed, (i just use ondemand here), you may notice a shortened battery life in 11.04 due to a kernel bug. (depends on hardware

---

### Post by eldonkr on 2011-05-03
I won't be able to tell until I have this thing on battery again. I think I got 3 hours per charge prior to upgrade but I think I only got a couple hours today.

What about a kernel bug?

---

### Post by Guilden_NL on 2011-05-03
Dell Latitude D810, 2 week old battery.
Lucid = 3:10 batt life
Natty = 1:15 batt life

Call it 50% worse.

To the point where I searched for "kernel battery bug 11.04"

I'd say that there is a serious kernel problem. I'll go to kernel.org to check it out, I haven't seen details listed here on the Ubuntu forums yet.

---

### Post by mc4man on 2011-05-03
links about bug
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/760131](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/760131)
[http://ubuntuforums.org/showthread.php?t=1739770](http://ubuntuforums.org/showthread.php?t=1739770)

---

### Post by eldonkr on 2011-05-03
I can't seem to access my NAS on the router anymore since the upgrade. It gives me an error message saying it can't mount the windows share.

---

### Post by eldonkr on 2011-05-03
Also, I guess this kernel bug doesn't effect me. I just took it off battery and it looks like I can get an hour more than I normally do. I usually only get three hours a per charge but I took it off of the charger and it said 3:55 hours remaining...

or maybe it's messed up because I just checked it again on battery power and it said that I had seven hours remaining.

---

### Post by Guilden_NL on 2011-05-03
eldonkr,  It apparently is Intel focused and perhaps Radian too.  Just breezing through the doco at present, so apologise if that isn't the case.

Here's another link with good info:
[[COLOR="Blue"]http://www.phoronix.com/scan.php?page=article&item=ubuntu_natty_power&num=1[/COLOR]]("http://www.phoronix.com/scan.php?page=article&item=ubuntu_natty_power&num=1")

---

### Post by eldonkr on 2011-05-03
Turns out the inability to access the NAS was an issue with the NAS itself as I wasn't able to get to it on the other computer either. That's been handled.

I've found a replacement for the system monitor applet in Conky. But I'm actually having a few issues with Conky as far as configuration. I'd appreciate it if you could direct yourselves to another one of my threads and maybe you could help me figure out how to do what I'm trying to do here.

[http://ubuntuforums.org/showthread.php?t=1748631](http://ubuntuforums.org/showthread.php?t=1748631)

---

### Post by eldonkr on 2011-05-05
I've got pretty much everything figured out now and I'm totally digging 11.04. So far the only remaining question I have is:

Is there any way to remove the Applications and Files & Folders buttons from the Ubuntu launcher/dock/thing/whatever its called?

---

