---
title: "Force Feedback"
date: 2010-05-17
forum: General Help
---

### Post by IAmCorbin on 2010-05-17
I am having a nightmare of a time trying to get Force Feedback working in Ubuntu. I have a [logitech MOMO racing wheel]("http://www.logitech.com/en-us/441/320") and am using a Toshiba Satellite A135-2326 laptop.

I was running Ubuntu 8.10 but couldn't get it to work and then discovered that force-feedback support was not included in the kernel until Ubuntu 9.04. I now have Ubuntu 9.04 on this laptop, but still can't seem to get anywhere.

I am using [ff-utils]("http://www.logitech.com/en-us/441/320") to try and test force feedback

I get the following if I try fftest on /dev/input/event[1-9] (same results for each)
```

corbin@Shiba:~/Desktop/ff-utils$ sudo ./fftest /dev/input/event7
Force feedback test program.
HOLD FIRMLY YOUR WHEEL OR JOYSTICK TO PREVENT DAMAGES

Device /dev/input/event7 opened
Axes query: 
Effects: 
Number of simultaneous effects: 0
Upload effects[0]: Function not implemented
Upload effects[1]: Function not implemented
Upload effects[2]: Function not implemented
Upload effects[3]: Function not implemented
Upload effects[4]: Function not implemented
Upload effects[5]: Function not implemented
Enter effect number, -1 to exit
1
Now Playing: Constant Force
Enter effect number, -1 to exit
2
Now Playing: Spring Condition
Enter effect number, -1 to exit
3
Now Playing: Damping Condition
Enter effect number, -1 to exit
4
Now Playing: Strong Rumble
Enter effect number, -1 to exit
5
Now Playing: Weak Rumble
Enter effect number, -1 to exit

```

The MOMO racing wheel works just fine otherwise. I have even used joy2key to map joystick buttons to keyboard buttons and "drove" mario around in a NES emulator (jumping with gas pedal and ducking with brake pedal. It's quite an interesting way to play).

I just can't seem to get anywhere with force feedback.

Anyone out there that has gotten a force feedback controller working in Ubuntu?

~Corbin

---

### Post by IAmCorbin on 2010-05-17
moved to Gaming and Leisure forums - [http://ubuntuforums.org/showthread.php?t=1486348](http://ubuntuforums.org/showthread.php?t=1486348)

---

