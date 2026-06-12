---
title: "Blank screen on startup"
date: 2010-09-06
forum: General Help
---

### Post by Kjeldgaard on 2010-09-06
Hi

At night I always switch off the power to my PC (ION 330, Ubuntu 10.04, nvidia driver 256.52) but recently I have got the problem that the screen is blank the first time I start the PC up after the power is switched back on. My screen is a Panasonic plasma tv. I can't see the boot screen or anything and nothing happens if I press ctrl+alt+f1 (or f2). The only way to solve this problem is to unplug the power cable from the pc and try again, disconnect the hdmi cable between the PC and the TV and reboot or hitting ctrl+alt+del a lot of times as it sometimes reboot now with a fully working display.

This log file is from a failed start up where the screen was just blank is found [here]("http://pastebin.ubuntu.com/489359/"):

I have look it through but with my limited ubuntu knowledge I am not sure what to look for. Can anybody help me on this? I think it is some edid monitor information/setting that causes this problem but I am not sure.

Just let me know if you need some more information.

Thanks in advance
Kjeldgaard

---

### Post by Julita on 2010-09-06
Is the problem persists when you use hybernate instead of switching it off?

---

### Post by Kjeldgaard on 2010-09-06
> **Julita said:**
> Is the problem persists when you use hybernate instead of switching it off?

I have now tried hibernating, rebooting  and shut down and the display as worked every time. The only way I can make the screen go blank is if I switch of the power of the PC (on the wall outlet).

---

### Post by wojox on 2010-09-06
Show us something like this command

```
grep -n "^(EE)" /var/log/Xorg*log
```

---

### Post by Kjeldgaard on 2010-09-06
grep output is:

```

/var/log/Xorg.1.log:135:(EE) Sep 06 18:18:00 NVIDIA(0): No display devices found for this X screen.
/var/log/Xorg.1.log:139:(EE) Screen(s) found, but none have a usable configuration.
/var/log/Xorg.2.log:135:(EE) Sep 06 18:18:01 NVIDIA(0): No display devices found for this X screen.
/var/log/Xorg.2.log:139:(EE) Screen(s) found, but none have a usable configuration.
/var/log/Xorg.3.log:135:(EE) Sep 06 18:18:01 NVIDIA(0): No display devices found for this X screen.
/var/log/Xorg.3.log:139:(EE) Screen(s) found, but none have a usable configuration.
/var/log/Xorg.4.log:135:(EE) Sep 06 18:18:02 NVIDIA(0): No display devices found for this X screen.
/var/log/Xorg.4.log:139:(EE) Screen(s) found, but none have a usable configuration.
/var/log/Xorg.5.log:135:(EE) Sep 06 18:18:03 NVIDIA(0): No display devices found for this X screen.
/var/log/Xorg.5.log:139:(EE) Screen(s) found, but none have a usable configuration.
/var/log/Xorg.failsafe.log:1482:(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)

```

---

### Post by wojox on 2010-09-06
You say this just started happening recently? Can you remember what changed? Driver or kernel update. Did you just start using the plasma tv as a monitor? If it's an EDID issue what does this say:

```
grep -n "EDID" /var/log/Xorg*log
```

You set up Nvidia with

```
sudo nvidia-xconfig
```

```
gksudo nvidia-settings
```

---

### Post by Kjeldgaard on 2010-09-07
My hardware (incl. my plasma tv) has not changed for at least a year, so I am pretty sure it must be a software problem.

A month ago I upgraded to 10.04 and I didn't experience any problems. I remember the first time I encountered this problem was after I ran update manager where I updated the nvidia drivers or at least some nvidia related stuff. But it only happened once so I didn't pay much attention to it. Within the last week where the problem has become VERY frequent I think I have update both the nvidia drivers and the linux kernel...

When I run the commands you suggested I get the following output:

Output of the new grep command

```

/var/log/Xorg.4.log:145:(WW) Sep 07 17:34:38 NVIDIA(0): PANASONIC-TV (DFP-0)'s EDID does not contain a maximum image
/var/log/Xorg.4.log:147:(WW) Sep 07 17:34:38 NVIDIA(0):     EDID.

```

It does not look that serious to me.

Output of the
```

sudo nvidia-xconfig

```
is
```

Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

```

I have not run this command before so I am not sure what to expect.

And the last command gives me the graphical nvidia settings which I previously used for monitor setting, but I haven't changed anything for a very long time.

Today when I started the pc I had to reboot like 10 times. None of the usual ways to active the tv worked today. Instead I removed the hdmi cable from one input in the tv to another input and the tv immediately activated. Then I moved the hdmi cable back the original input and it still worked. This some how makes me confident that the problem is edid related even though I am not able to find some error logs confirming my suspicion.

/Kjeldgaard

---

### Post by Kjeldgaard on 2010-09-14
After a nvidia update a few days ago, I have not had any problems. So it was probably a driver problem.

---

