---
title: "Shutdown timer"
date: 2010-06-05
forum: General Help
---

### Post by 7Sasha on 2010-06-05
Hello.

In ubuntu 9.10 when clicking the shutdown button in the indicator-applet-session
a confirmation dialog with a countdown timer had appeared.

In 10.04 the dialog would appear without the countdown. 
Could you help me adding that timer back to the lucid's shutdown dialog?

Thanks in advance.

[IMG]http://habreffect.ru/files/4e6/7e6c30580/Untitled.png[/IMG]

---

### Post by acrazyplayer on 2010-06-05
It already has it, you just probably didnt see it. When you click on "shut down" way at the bottom you will see it says "the system will be automatically shut down in 60 seconds" and it counts down by 10's

Edit: if the indicator-applet doesn't have the countdown then right click on the panel and choose "add to panel" then type in "shut down" and choose that nice big red power button and move it to the far right to have a much better shut down experience.

---

### Post by 7Sasha on 2010-06-06
That didn't work either. 
I choose to reboot and the reboot was immediate. 
No countdown timer appeared either.

--

> It already has it, you just probably didnt see it. When you click on "shut down" way at the bottom you will see it says "the system will be automatically shut down in 60 seconds" and it counts down by 10's

I see no counter at the bottom either.
Moreover, it wouldn't shutdown (checked waiting 3 minutes for that to happen)
unless I confirm the shutdown .

---

### Post by lucifer1 on 2010-10-31
just use this command in the terminal its faster and easier 
code 

shutdown -h 12:00

that will shutdown ur machine at 12 o'clock
or 
shutdown -h +50
that will shutdown after 50min and you can put the num that you want or the time that you want 
\\regards

---

### Post by VQIF on 2010-12-27
With respect, lucifer1, that's not exactly what the question was. 

On older versions of Ubuntu the computer would automatically shutdown after 60sec once you selected "shutdown" from the menu. On Lucid, it doesn't; it just sits there. 

I can see arguments in favour of both, but what I think 7Sasha wants (and I would quite like to have, too!) is a way to get the old version back, where you could just select "shutdown" and walk away, knowing that your computer would turn itself off in one minute's time.

---

### Post by stinkeye on 2010-12-27
For the OP's question.
In the terminal...
```
gconftool-2 --set /apps/indicator-session/suppress_logout_restart_shutdown --type bool FALSE
```

---

### Post by alastairpetrie on 2011-01-13
> **stinkeye said:**
> For the OP's question.
In the terminal...
```
gconftool-2 --set /apps/indicator-session/suppress_logout_restart_shutdown --type bool FALSE
```

Useful tip, thanks. However, setting this value to FALSE simply means that the dialogue (without the countdown) does appear and setting to TRUE means that the system shuts down (or restarts, logs out) immediately without showing any dialogue at all.

---

