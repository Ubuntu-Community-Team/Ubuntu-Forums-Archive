---
title: "Pause a task via command line"
date: 2010-04-04
forum: General Help
---

### Post by tuvazeock on 2010-04-04
I have a task that I need to let run while I'm away from the computer.  It's very CPU intensive and I've even had to throttle down my processor to 3GHz to keep it from overheating.

I'm using a combination of GNOME Sensors App and CPU Frequency Scaling Monitor to control the overheating problem.  I have the sensors app set to alarm and "killall" at 61 Degrees Celsius.  The sensors app has an option where you can enter a command that it will run for you.  All I need is to know what command to run that can pause this task.  So later I can resume it.

I know it can be done.   System Monitor has an option to "stop" a task.  It also has "continue".  This is how I've been doing it while I'm at the computer.   So if anyone knows what the commands are that System Monitor uses, that would be a huge help.  By the way, I'm using Ubuntu 9.10 with all current updates.

Thank you for any help!  :D

NOTE:  For anyone who is about to flame me for having a computer that overheats and wants to tell me that this is the problem I should be after.  It only overheats during this process.  Not for any games or compiling or rendering or encoding.  Nothing else.  I have even bought a new heatsink and fan.  I have redone the thermal compound on the Processor.  My processor usually runs at idle around 36-39 Celcius and under normal load around 47-53 Celsius.

---

### Post by revenant138 on 2010-04-04
Looks like you can do it this way [http://tombuntu.com/index.php/2007/11/23/how-to-pause-a-linux-process/](http://tombuntu.com/index.php/2007/11/23/how-to-pause-a-linux-process/)

---

### Post by tuvazeock on 2010-04-04
> **revenant138 said:**
> Looks like you can do it this way [http://tombuntu.com/index.php/2007/11/23/how-to-pause-a-linux-process/](http://tombuntu.com/index.php/2007/11/23/how-to-pause-a-linux-process/)

This is exactly what I needed.  Works great!  I can even set the Sensors app to continue the process after the processor cools back down.  

Thanks a lot!

---

### Post by Agent ME on 2010-04-04
Also, "killall -STOP xeyes" and "killall -CONT xeyes" work well if there's only one program running with that name (or you're fine with pausing all programs by that name).

---

