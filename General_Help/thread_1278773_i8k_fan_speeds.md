---
title: "i8k fan speeds"
date: 2009-09-29
forum: General Help
---

### Post by sleepyjon on 2009-09-29
I'm trying to control the fan speeds on my Dell 1420, bios revision A10.

I have i8kmon temperatures set up the way I think I want them. However every time i8kmon adjusts the fan speed, the fans go back to the minimum speed within a few seconds. A few seconds later, i8k will set the fan speed back making for a constant start-stop of the fan.

Running i8kmon from the terminal and setting the fan speed to 2 gives:
> 
1254281219 acpi: state:                   on-line
1254281219 1.0 A10 4VKWRD1 36 -22 1 922 2602 1 -22
# exec /usr/bin/i8kfan - 2
1254281229 1.0 A10 4VKWRD1 35 -22 1 922 2574 1 -22
# exec /usr/bin/i8kfan - 2
1254281239 1.0 A10 4VKWRD1 35 -22 1 922 2574 1 -22
# exec /usr/bin/i8kfan - 2
1254281249 1.0 A10 4VKWRD1 34 -22 1 922 2548 1 -22
# exec /usr/bin/i8kfan - 2


I think i8k is fighting with something to set the fan speed, does anyone have any way I can find out?

> 
$ uname -a
Linux GnuMachine 2.6.28-15-generic #52-Ubuntu SMP Wed Sep 9 10:48:52 UTC 2009 x86_64 GNU/Linux


---

### Post by admelfo on 2009-09-29
Don't know if [this]("http://www.robotsystematic.com/2009/ubuntu/howto-fan-control-in-ubuntu") will help -- stumbled across it earlier today.

Good luck.

---

### Post by sleepyjon on 2009-09-30
> **admelfo said:**
> Don't know if [this]("http://www.robotsystematic.com/2009/ubuntu/howto-fan-control-in-ubuntu") will help -- stumbled across it earlier today.

Good luck.

Thanks for the quick reply and the link, but unfortunately:

> 
$ sudo pwmconfig
This program will search your sensors for pulse width modulation (pwm)
controls, and test each one to see if it controls a fan on
your motherboard. Note that many motherboards do not have pwm
circuitry installed, even if your sensor chip supports pwm.

We will attempt to briefly stop each fan using the pwm controls.
The program will attempt to restore each fan to full speed
after testing. However, it is ** very important ** that you
physically verify that the fans have been to full speed
after the program has completed.

/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed


---

### Post by wilee-nilee on 2009-09-30
The easiest way to use the i8k is with gkrellm. here is a link.  [http://ubuntuforums.org/showthread.php?p=5275415#post5275415](http://ubuntuforums.org/showthread.php?p=5275415#post5275415)  Follow the 1st 4 steps then open gkrellm turn on the i8k plugin and adjust the temps from  there.

---

### Post by sleepyjon on 2009-10-01
> **wilee-nilee said:**
> The easiest way to use the i8k is with gkrellm. here is a link.  [http://ubuntuforums.org/showthread.php?p=5275415#post5275415](http://ubuntuforums.org/showthread.php?p=5275415#post5275415)  Follow the 1st 4 steps then open gkrellm turn on the i8k plugin and adjust the temps from  there.

Same issue there, but thank you.

---

### Post by wilee-nilee on 2009-10-01
You maybe having the same issue due to having written a file to control i8k if you remove all that you have done and follow the 1st 4 steps it should work I hope at least. Also if you try this a restart of Gkrellm is needed to get it to work,and of course hitting the apply button as you setup the plugin. You can then set Gkrellm in the startup menu with the name gkrellm as the command.

---

