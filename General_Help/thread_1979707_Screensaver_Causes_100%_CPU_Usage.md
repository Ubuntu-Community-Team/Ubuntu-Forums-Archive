---
title: "Screensaver Causes 100% CPU Usage"
date: 2012-05-13
forum: General Help
---

### Post by uRock on 2012-05-13
I am using ubuntu 12.04. When the screensaver kicks in the CPU usage jumps up and causes the fans to wind up. Does anyone know of a fix for this?

---

### Post by uRock on 2012-05-14
I started System Monitor then let the screensaver kick in, then took a screenshot as soon as I logged back in.

---

### Post by brainwash on 2012-05-14
Might be related to *compiz*. Are you using it?

Run this command to monitor the running processes while the screensaver is active:
```
top -d10 -i -b > top.txt
```[FONT=Courier New]
d: interval (every 10 seconds)
i:     show only non-idle processes
b:    batch mode (output format)

[/FONT]

---

### Post by bruno9779 on 2012-05-14
Do you really need a screensaver?

I mean, if you aren't using a CRT monitor it is pretty much useless and power-consuming.

The gnome team has come to this conclusion and I completely agree with them

---

### Post by uRock on 2012-05-14
> **bruno9779 said:**
> Do you really need a screensaver?
I do not have a screensaver.

---

### Post by uRock on 2012-05-14
> **brainwash said:**
> Might be related to *compiz*. Are you using it?

Run this command to monitor the running processes while the screensaver is active:
```
top -d10 -i -b > top.txt
```[FONT=Courier New]
d: interval (every 10 seconds)
i:     show only non-idle processes
b:    batch mode (output format)

[/FONT]

I like that. I will run it and find the culprit to make bug reporting and this thread more in depth.

Thanks!

---

### Post by uRock on 2012-05-14
Compiz is the culprit. 

```
PID USER       PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
2170 urock     20   0 1400m 108m  51m R  100  1.8  34:36.18 compiz
```

Any ideas on how to fix this?

---

### Post by uRock on 2012-05-14
Yay, I found a fix here, [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/969860](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/969860)

The CCSM fix is the one which worked for me.> WORKAROUND:
1. Open Catalyst Control Center.
2. Go to 3D > More Settings.
3. Set "Wait for vertical refresh" to "On, unless application specifies".
And if that doesn't work, then also do:
[COLOR="Indigo"]4. Run "ccsm"
5. In Workarounds, enable "Force full screen redraw (buffer swap) on repaint"[/COLOR].

TEST CASE:
1. Monitor compiz CPU usage (from /proc/<pid of compiz>/stat or top in batch mode)
2. In "brightness and lock" settings set "Turn screen off when inactive" to 1 minute
3. Wait until screen turns off
4. Move mouse or press a key to turn screen back on
5. Check the CPU usage from the monitor

ACTUAL RESULT:
When screen turns off compiz goes to 100%
When the screen turns back on, cpu usage drops immediately to a normal value
The graph attached shows %CPU of compiz with a sample per second. The graph has been captured on a system with a Radeon HD5770 and fglrx if that matter

---

