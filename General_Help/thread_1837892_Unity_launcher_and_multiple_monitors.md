---
title: "Unity launcher and multiple monitors"
date: 2011-09-02
forum: General Help
---

### Post by schuetzler on 2011-09-02
So, I've searched for solutions, but nothing I've found has worked for me. I use a Dell XPS laptop with Ubuntu 11.04, and I'm having a really hard time getting the Unity launcher (the Mac-like Dock, thingy) to show up on the external monitor that I place to the left of my laptop monitor. I have them arranged properly in the Monitors preferences, and it showed properly on the left hand side one time, but never again.

I have tried the following with no success:

[LIST]
[*]This one did absolutely nothing.
[/LIST]
```
xrandr --output VGA-0 --primary
```
[LIST]
[*]Editing the monitors.xml file in my home folder would be great, except that monitor is not always plugged in (as I'm on a laptop). When it's in, things are peachy. When it's not, my display is totally jacked up.
[/LIST]
So, how can I get the Unity launcher to show up up on the external monitor when it's plugged in, and on my laptop monitor when it's not?

---

### Post by schuetzler on 2011-09-07
Can anyone help?

---

### Post by schuetzler on 2011-09-13
Can anyone help me here? Did I post it in the wrong place?

---

### Post by sulobanks on 2011-09-19
I have the same problem.  All I've found is this: [https://bugs.launchpad.net/unity/+bug/742520](https://bugs.launchpad.net/unity/+bug/742520)

It appears to be a known bug, but it doesn't look like anyone is addressing it yet.

---

### Post by schuetzler on 2011-09-19
As further clarification, it appears that the launcher always appears on the right (not left) screen. I used the Monitors settings to move the external monitor to the right side, and the launcher moved to the external monitor. I really need help getting this figured out.

Thanks.

---

### Post by schuetzler on 2011-09-19
I found a temporary workaround at [https://bugs.launchpad.net/unity/+bug/742544](https://bugs.launchpad.net/unity/+bug/742544)

1. Run ```
xrandr
``` to find the NAME of the output you would like to make primary.

2. Run: 
```
xrandr --output NAME --primary && nohup unity --replace &
```

Better than nothing, I suppose.

---

