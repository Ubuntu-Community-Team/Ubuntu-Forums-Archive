---
title: "shutdown now command does not shut the computer down"
date: 2010-09-08
forum: General Help
---

### Post by neoargon on 2010-09-08
```
sudo shutdown now 
```command does not shut the computer down

When  the command is typed a , all the programs are closed and proceeds to shut down . But after some time, screen gets stuck(plymouth animation stops moving) . But the computer is still working . Fan is running , Power LED is on . LED showing hard disk usage blinks at equal time interval 

There is no problem in shutting  down using the button on panel  . So I suppose it is not a hardware problem . More over there is no problem in windows

The graphics card is Nvidia Geforce 7300GS . Iam using proprietary Nvidia driver

Please help

---

### Post by ks07 on 2010-09-08
Try shutting down using the -P switch (you could also try -h or -H)

```
sudo shutdown -P now
```

---

### Post by neoargon on 2010-09-08
> **ks07 said:**
> Try shutting down using the -P switch (you could also try -h or -H)

```
sudo shutdown -P now
```

That works . Thanks . Can you please tell what those P ,h ,H switches are?

---

### Post by mcduck on 2010-09-08
-h tells shutdown to either halt or power off the system after shutdown process is complete. (the system itself decides which one to do)

-H tells it to halt at the end of the process, and -P tells it to power off.

(I must admit I'm not absolutely sure what's the difference between halting and powering off, but if I'm right halt switches hard drives to standby mode before powering off)

You can also just use "sudo halt" instead of "sudo shutdown -h now".

edit: -r would be for restart, and like "sudo halt", it also has a simpler alias, "sudo reboot"

---

### Post by ks07 on 2010-09-08
> **neoargon said:**
> That works . Thanks . Can you please tell what those P ,h ,H switches are?
I don't know much but from what I can tell the shutdown command on its own only stops all running programs and services etc but doesn't actually shut down the computer - possibly akin to the old days of Windows' "It is now safe to turn off your computer"

The switches H and P tell the computer to halt or power down respectively. The difference between the two? I have no idea, but they seem to achieve the same job.

The lower case h switch allows the computer to choose whether it powers down or halts the system. For me, all 3 options seem to work interchangeably. :p

---

### Post by neoargon on 2010-09-09
Thanks

---

