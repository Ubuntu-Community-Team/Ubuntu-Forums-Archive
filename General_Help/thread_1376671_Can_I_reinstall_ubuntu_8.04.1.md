---
title: "Can I reinstall ubuntu 8.04.1"
date: 2010-01-09
forum: General Help
---

### Post by sellewe on 2010-01-09
I have this on my computer butit will not boot up. Is it possible to re install this?

---

### Post by Jesus_Valdez on 2010-01-09
What version do You have, 8.04?

What don't You try something more recent?

---

### Post by DeMus on 2010-01-09
> **sellewe said:**
> I have this on my computer butit will not boot up. Is it possible to re install this?

What happens when you boot up? What do you see, what not?
What did you do prior to this error? Try to describe it as well as possible.

---

### Post by SecretCode on 2010-01-09
You certainly can reinstall - but there may be other better options.

---

### Post by sellewe on 2010-01-09
> **DeMus said:**
> What happens when you boot up? What do you see, what not?
What did you do prior to this error? Try to describe it as well as possible.

On boot I have a black screen which loads till the point of asking for my user name then password.  When I enter these it will proceed no further without further instruction (which I do not know)  I do not have any desktop visual.  It worked fine until I updated it some weeks ago but now on everb boot I have the same problem.  If I put the CD in the drive I cannot get it to run.
I am completly new to ububtu and this is on an old machine and is the only OS on this computer.

---

### Post by SecretCode on 2010-01-09
If you put the CD in the drive and reboot, does it offer to install 8.04? I.e. can you boot from CD at all?

I don't think 8.04 had live CD capability. Can you download the Ubuntu 9.04 iso and burn to a CD?

---

### Post by Iowan on 2010-01-09
Can you access the BIOS on boot-up? If so, you can check boot order (maybe) and verify/set the CD to boot first.

---

### Post by dcstar on 2010-01-10
> **sellewe said:**
> On boot I have a black screen which loads till the point of asking for my user name then password.  When I enter these it will proceed no further without further instruction (which I do not know)  I do not have any desktop visual.  It worked fine until I updated it some weeks ago but now on everb boot I have the same problem.  If I put the CD in the drive I cannot get it to run.
I am completly new to ububtu and this is on an old machine and is the only OS on this computer.

When you see the Login screen press CTRL-ALT-F1 and you should get a text login screen, you can then login and run these commands:

```
sudo update-initramfs -u -k all
sudo reboot
```

---

