---
title: "Nvidia Drivers"
date: 2009-09-08
forum: General Help
---

### Post by hoboscience on 2009-09-08
Well it comes to this, days of efforts and searching and I just haven't had any luck so I'm hoping one of you nice linux geeks can help me out.

I've spent days trying to install Nvidia drivers on my 9.04 ubuntu setup.  I have used the proprietary driver setup under system hardware/drivers, I've tried Envy, installing manually, online, offline.  Dosen't matter what I do, when I reboot the system it seems pulseaudio hangs up the boot process.  I'm active as if in single user mode (but I'm not) and there is a red asterisk noting: 

"PulseAudio configured for per-user sessions, saned diabled; edit/etc/default/saned" 
This happens every time I install the nvidia drivers.  I've been through this more than a dozen times.  Any ideas.  

Thanks

Almost forgot my specs
EVGA 780i Sli MB
Sli 8800GT Cards
Intel Q6600

---

### Post by CatKiller on 2009-09-08
> **hoboscience said:**
>  Dosen't matter what I do, when I reboot the system it seems pulseaudio hangs up the boot process. 

It doesn't, you know. That message would be there even if you got the graphical login. It's just that you aren't used to seeing it.

It's not a solution, but it might stop you chasing down a dead end.

X's log is kept at /var/log/Xorg.0.log, but I don't know if anything interesting would be in there if X failed to start at all.

---

### Post by hoboscience on 2009-09-10
Well, I figured out the problem.  It was my SLI setup.  But I'm up and running now!!  Installed the SLI properly and everything is running so Smooth.

Thanks to this thread here
[http://ubuntuforums.org/archive/index.php/t-1143419.html](http://ubuntuforums.org/archive/index.php/t-1143419.html)

---

