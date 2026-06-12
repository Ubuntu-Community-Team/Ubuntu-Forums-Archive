---
title: "Screen resolution"
date: 2011-11-26
forum: General Help
---

### Post by venugopaljee on 2011-11-26
I have recently installed Ubuntu 11.10.
My screen resolution is 1024 x 768.
Everything is looking shorter and wider.
I need to change it to a better screen resolution. But the only other option that is permissible now from the display screen is 800 x 600, which is no better.
The system is not able to detect any more display options.
How to get decent screen resolution?

---

### Post by BC59 on 2011-11-26
Did you try to install the proprietary drivers?

---

### Post by SteveDee on 2011-11-26
> **venugopaljee said:**
> ...The system is not able to detect any more display options....

Have you tried opening a terminal and typing:-
```

xrandr

```
...this will show what resolutions are currently supported for your display.

---

### Post by venugopaljee on 2011-11-26
> **SteveDee said:**
> Have you tried opening a terminal and typing:-
```

xrandr

```
...this will show what resolutions are currently supported for your display.
Yes, It gives like this:
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768       61.0* 
   800x600        61.0  
   640x480        60.0 
Therefore, what is the next step?

---

### Post by venugopaljee on 2011-11-26
Yes, I tried a graphic card driver. That might have been a mistake. I dont know.

---

### Post by BC59 on 2011-11-26
You could try to change resolution through the AMD or NVIDIA apps of your video card

---

### Post by venugopaljee on 2011-11-26
How does one do that? Could u please help me?

---

### Post by BC59 on 2011-11-26
Well you can google but for Nvidia I found this

[http://forums.nvidia.com/index.php?showtopic=73027](http://forums.nvidia.com/index.php?showtopic=73027)

---

### Post by BC59 on 2011-11-26
And from here you can change your resolution according to the command  SteveDee mentioned before.

---

