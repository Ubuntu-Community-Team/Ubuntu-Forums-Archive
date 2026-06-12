---
title: "Gnome Desktop Locks Every 30 Sec. for 1-2 Secs."
date: 2006-05-07
forum: General Help
---

### Post by MrRockabilly on 2006-05-07
I am definitely new to the Linux world, and I have just decided to dump my XP OS for Ubuntu on my Laptop. The installation went fine, no errors to speak of. And the Ubuntu Wiki is a life saver for people new to the Ubuntu/Linux world.

I am running the Breezy release of Ubuntu, and for one reason or another the machine becomes un-responsive every 30-45 seconds and only stays that way for a second or two. I am not sure if it can be because I am running Ubuntu on an older system, PIII 1.0ghz with 512 RAM, or if it is as simple as a video driver issue. 

Anyone willing to point me in the right direction? Or any help in general would be greatly appreciated. Thanks in Advance! :eek:

---

### Post by towsonu2003 on 2006-05-07
It could be a process getting too much cpu... open a terminal (alt+f2 and type gnome-terminal) and type ```
top
``` and hit enter. Monitor the CPU and memory coloums to see what program is causing the problem. top is much like the "Task Manager" in Windows. A similar one can also be found under Applications > System Tools > System Monitor but it is a resource hog itself, which will make its output less reliable. 

Also, check if you are using swap, which tends to slow down things: ```
free -m
```. Swap is a kind of RAM but it is a hard disk partition. I don't think swap usage would cause hangs, but you never know. 

Also check out /var/log/messages (a text file that logs some system messages) to see if there are specific errors in there. You can use the Application > System Tools > System Log for that. 

And lastly, and most boringly, you could check dmesg to see if it's saying anything woth seeing. To do that: ```
dmesg | tail
``` right after the hang... To read all of it, do: ```
dmesg | less
``` and use PageDown PageUp to navigate. Hit q to quit.

---

### Post by MrRockabilly on 2006-05-07
Thanks for the guidance dude. Im not expert, but I did check the processes and nothing looks out of the norm. And I am using swap space, but I dont know what I am looking for. 

I checked the system logs, and under /var/log/syslog - System Log Viewer, I keep seeing the same logs: 
localhost kernel [4294993.108000] psmouse.c: TouchPad at isa0060/serio1/input0 - driver resynched.
localhost kernel [4295050.565000] cpufreq: change failed with new_state 0 and result 0.

Any ideas what thay can mean, if anything? It is showing up multiple times, the log is filled with it, and nothing elese it seems like. Any ideas on these errors? 

Thanks again to anyone with help.

---

### Post by towsonu2003 on 2006-05-07
[QUOTE=MrRockabilly]
localhost kernel [4295050.565000] cpufreq: change failed with new_state 0 and result 0.
[/QUOTE]
are u sure top doesn't reveal a process making your cpu 98-100% worked? that's weird.

any  way. the error above signals something is wrong with frequency scaling of your cpu. Unfortunately ,I'm clueless n that. try a search on the forums?

---

