---
title: "Dapper Freezing"
date: 2006-06-28
forum: General Help
---

### Post by bkb on 2006-06-28
Randomly, and commonly - more than twice a day - Dapper freezes, totally.  KVM all lock up, nothing moves, nothing makes a sound.  I have to hold down the power button on my machine to do a cold-reboot which is a terrible feeling.  I have no idea.  I have installed the Desktop install on my PC.  I have run pervious version of Ubuntu, and other distros on my machine, as well as Windows XP without every experiencing this, so I'm 99.99% sure this isn't a hardware problem.

I would appreciate some guidance on how to troubleshoot this.

Thanks.

---

### Post by Maggot on 2006-06-28
There are a lot of ppl with that problem.

Check out this thread [http://ubuntuforums.org/showthread.php?t=193283](http://ubuntuforums.org/showthread.php?t=193283) really not sure if there is a fix in that but there are a lot of replies.

My computer was freezing because of ATI drivers.

---

### Post by ddumanis on 2006-06-28
try installing the VESA driver

type in a terminal:

[B]sudo dpkg-reconfigure xserver-xorg
[/B]
and manually choose VESA as the driver


you can keep the current settings for everything else

it may help. it helped me.

good luck.

---

### Post by bkb on 2006-06-29
Thank you both.  I will look into these two suggestions and post back.

Appreciate it.

---

### Post by Titan1958 on 2006-06-30
My  Dapper freeze once a day since I installed new NVidia drivers. Coicidence????

---

