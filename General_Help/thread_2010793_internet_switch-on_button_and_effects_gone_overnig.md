---
title: "internet switch-on button and effects gone overnight"
date: 2012-06-26
forum: General Help
---

### Post by tnob on 2012-06-26
[FONT=Arial][SIZE=2]Greetings all,[/SIZE][/FONT]

[FONT=Arial][SIZE=2]Anyone out there able to help me sort out a rather annoying glitch?[/SIZE][/FONT]

[FONT=Arial][SIZE=2]I'm running Ubuntu 10.04 LTS, in a dual-boot configuration with Windows XP, on an old Dell desktop. A Vodafone dongle is used for internet connection. [/SIZE][/FONT]

[FONT=Arial][SIZE=2]One morning, I woke up to find the internet switch-on button - on the upper bar - completely gone: Internet is still working fine, but I just can't open it in Ubuntu. Clicking on the upper bar and selectng from the drop-down menu the option supposedly bringing this switch-button back on again, as I have been advised, just doesn't work.[/SIZE][/FONT]

[FONT=Arial][SIZE=2]My beloved rotating cube and wobbly windows have disappeared as well. Someone told me that the easiest way to restore the effects aforementioned is to click anywhere on the screen (to bring on the wall paper window) and selecting the appropriate tab there. Sadly, however, this doesn't yield the desired result either - try as I may.[/SIZE][/FONT]

[FONT=Arial][SIZE=2]For online traffic, I'm resorting to the XP partition, at present - but I really hate to be forced back to Windows in this way.. So what to do now?[/SIZE][/FONT]

[FONT=Arial][SIZE=2]tnob[/SIZE][/FONT]

---

### Post by nothingspecial on 2012-06-26
Changed prefix to ubuntu.

---

### Post by prshah on 2012-06-26
> **tnob said:**
> 
rotating cube and wobbly windows have disappeared as well. 

Possibly lost compiz and it's notification section? Try this:

Open the terminal (Applications-Accessories-Terminal) and give the command```
compiz --replace
```

Please post back with your results. If it does not work, please post the output from the above command as well.

---

