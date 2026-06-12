---
title: "Screen blanking issues"
date: 2010-02-22
forum: General Help
---

### Post by SwedishWings on 2010-02-22
Hi folks, I'm loosing my hair over this ](*,)... hope someone can help. 

I have tried everything i can come to think about to disable screen blanking on my target system. I only use X, so is suppose GNOME is not to blame (gnome-power-manager is not running). 

An excerpt from xorg.conf:

```
Section "Monitor"
	Identifier	"Configured Monitor"
	Option		"DPMS"
	Option		"BlankTime"	"0"
	Option		"StandbyTime"	"0"
	Option		"SuspendTime"	"0"
	Option		"OffTime"	"0"
EndSection
```

I have also set this manually in .bashrc, just before my app is loaded:

```
xset s noblank
xset s 0
```

This should, as far as i understand, disable any screen blanking.

Or, perhaps I'm totally wrong about the screen blanking - are there other power save modules running?

Thanks,
Mike

---

### Post by dwhitney67 on 2010-02-22
I have the opposite desire; I want DPMS to work on my system so that the monitor is placed into "sleep" mode after the system has been idle, for say 10 minutes.

A few weeks ago this feature was working; now it does not.  I suspect the anomaly came about because of a system update that I performed.

I have played around with the gnome-power-manager settings, but nothing appears to be working.  It is as if my 'requests' are being ignored.

The screen-saver, which I prefer having a blank one, works fine.

---

### Post by SwedishWings on 2010-03-02
I still have not solved this, anyone have some ideas?

Thanks,
Mike

---

### Post by eradiate on 2010-03-03
The best way to disable screen blacking is this:

1. Turn off dpms 
```
xset -dpms
```

2. Turn off screen saver for good measure 
```
xset s off
```

3. Check with xset q

---

### Post by SwedishWings on 2010-03-04
> **eradiate said:**
> The best way to disable screen blacking is this:

1. Turn off dpms 
```
xset -dpms
```

2. Turn off screen saver for good measure 
```
xset s off
```

3. Check with xset q

Many thanks! This solved the problem :KS

Regards,
Mike

---

