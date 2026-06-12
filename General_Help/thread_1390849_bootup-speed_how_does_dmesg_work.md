---
title: "bootup-speed: how does dmesg work?"
date: 2010-01-26
forum: General Help
---

### Post by alexito84 on 2010-01-26
Dear ubuntu-forum,

REASON: I want to find out how to improve my boot-up and hibernate-awake time for ubuntu (it is 300% slower as hibernate on windows xp on the same machine:() 

QUESTION: well my question is concerning the tool dmesg. As I understood from reading the quite brief >>man dmesg 
 this tool will show the messages the kernel put out during the boot-up. true? 

A typical line on my dmesg output I receive would look like this:

```

[...]
[   39.632219] i915 0000:00:02.0: LVDS-1: EDID invalid.
[   46.964733] wlan0: authenticate with AP 00:23:08:20:58:6f
[   46.965988] wlan0: authenticated
[...]

```subquestion: 
a) the number in the beginning (is it the time between the two kernel messages?)
   --> in the example it wold be about 7 seconds
b) if it is the time in seconds: does it mean the kernel was abusing 7 dseconds for the output of the line? how can I track what causes the delays?

PS: maybe I should post this in a different ubuntuforums subgroup (if so which?)
PSS: is there any good webpage (I have not found any yet) on this topic?

---

### Post by cayliffe on 2010-01-26
dmesg does show the bootup messages (actually the kernel ring buffer messages).

The timestamp is seconds since startup of the system.

So yes it was 7 seconds between the messages.

As for why it is taking that long between them I am not sure.
Possibly your system was doing stuff in that 7 seconds but just not printing out any messages about what it was doing.

Cheers,

Craig

---

### Post by alexito84 on 2010-01-26
thank you for your answer Graig! 
To improve my "self-helping"-abilities, where should/could I have looked up this information (that it is the time in seconds after the system start?).

Does it seem a "good plan" to use dmesg to detect ways to improve my boot-up speed? 
Or better said - How can we find out what actually took 7 seconds? I am puzzled now if dmesg can be of any help at all.

thank you! alex

---

