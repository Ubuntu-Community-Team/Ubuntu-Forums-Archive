---
title: "Ubuntu Sometimes Won't Shutdown?"
date: 2009-09-22
forum: General Help
---

### Post by zane.sims on 2009-09-22
Hey everyone,

I installed Ubuntu 9.04 Desktop about a week or so on the following machine:

HP Workstation XW6200
Video Card: NVidia Quadro FX 3400
4 GB RAM
2x 3.2 Intel Xeon 64-bit Processors

When I first tried to shutdown Ubuntu, it went to a black screen and nothing happened.  I had to use the switch.  I thought that it might be an ACPI issue so I made sure that ACPI was enabled in the BIOS and added the grub boot option acpi=force.  When I tried to shutdown the next time, it worked!....then I tried again thinking it was fixed.....it didn't work.  It seems to break and fix randomly.  I tried a bunch of startup and shutdowns without any real hardcore OS use in between.  Again, at seemingly random times, it will not shutdown properly, while at others, it shuts down just fine.

Does anyone have any idea about the cause and solution for my problem?

Thanks very much in advance!
Zane

---

### Post by zane.sims on 2009-09-25
**Update:** I have started to notice that after using the computer for an extended period of time (30 mins - 1 hr) it almost never shuts down correctly. This is an extremely annoying problem! Can anyone please help me with this?
 
Thanks for any help you can provide,
Zane

---

### Post by darknight2183 on 2009-09-25
what happens when you switch to a terminal and issue "sudo shutdown -h now" (w/o quotes)?  Also, is there anything in your logs indicating an error with the shutdown?

---

### Post by zane.sims on 2009-09-25
>  what happens when you switch to a terminal and issue "sudo shutdown -h now" (w/o quotes)? Also, is there anything in your logs indicating an error with the shutdown?

 
I haven't tried that command yet, but I have tried using init and got the same results. I will try your suggestion when I get home this evening. What log files should I review?
 
 
> 
[SIZE=1][SIZE=1]Shutdown failures (and crashes) are fairly common not only with Ubuntu but with any other distro or operating system. Computers are temperamental and one never knows what the next problem is going to be from one day to another. I wouldn't worry about it. If it doesn't shutdown just push the button and forget it. :smile:[/SIZE] 
[/SIZE][SIZE=1]
 
I appreciate your response, but this is not how I solve problems, nor is it how others should solve problems. Some system settings are saved at shutdown. When the computer does not shutdown fully, it does not save those settings. Small example, but I had that problem with my volume settings. I realize that computers are tempermental, but I was trying out Suse before Ubuntu, and did not experience problems shutting the computer down. If everyone took your approach to solving problems, nothing would ever be fixed![/SIZE]

---

### Post by zane.sims on 2009-09-25
I tried:

```
sudo shutdown -h now
```but it seemingly did the same thing - goes to black screen and must hold in power button to shutdown.  I reviewed several of the logs in "/var/log", and while I didn't notice anything particular, I don't know exactly what I am looking for either.  Is there a particular log file that I should be looking in?  Thanks for your suggestions.  Any additional help would be very appreciated.

Zane

---

