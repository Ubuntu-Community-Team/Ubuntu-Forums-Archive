---
title: "How hot is Ubuntu on a laptop?"
date: 2011-06-16
forum: General Help
---

### Post by domfliss on 2011-06-16
Hi guys,

I am thinking of replacing Windows 7 on my laptop with Ubuntu 11.  My Lenovo laptop has a duel core Celeron cpu and a 4500m graphics card.  My question is this; will it run hotter using Ubuntu over Windows 7?  

I tried Ubuntu on my old netbook once and it almost cooked itself.  I have seen a few posts regarding heat, so it is making me a little nervous.  I don't like Window 7, but it is cool (temperature) and my machine is deafly quiet.  

As my main machine is a mac running Snow Leopard,  I really like the Unity interface as it is quite similar in some respects and would love to have it on my laptop.  

If anybody could get back to me with experience of running Ubuntu 10/11 on their laptop, then that would be great. 

Many thanks.

Domfliss

---

### Post by flipper T on 2011-06-16
can vary according to hardware

burn live cd / boot from it / use it

the answer will be revealed

---

### Post by domfliss on 2011-06-16
> **flipper T said:**
> can vary according to hardware

burn live cd / boot from it / use it

the answer will be revealed


Thanks for the reply, but to check temps I have to intall sensors (sudo apt-get install 1m-sensors) and as far I know you can't install apps to a live CD, but maybe I am wrong.

Cheers

---

### Post by Thewhistlingwind on 2011-06-16
Just use ACPI, it's preinstalled as far as I know. (I could have installed it and just forgotten though.)

acpi -t

---

### Post by mastablasta on 2011-06-16
> **domfliss said:**
> Thanks for the reply, but to check temps I have to intall sensors (sudo apt-get install 1m-sensors) and as far I know you can't install apps to a live CD, but maybe I am wrong.
 
Cheers
 
 
you CAN install to live CD only the problem is it's all lost after reboot. if if you try it again later oyu iwll need to install it again.
 
also there are a couple of GUI monitors such as gkrellm and conky. GKrellM is easy to install and light on resources. so is conky...
 
yea the heating up really depends on hardware. an oldie i have is cooler in Ubuntu and battery lasts longer than in winXP.

---

### Post by domfliss on 2011-06-16
> **mastablasta said:**
> you CAN install to live CD only the problem is it's all lost after reboot. if if you try it again later oyu iwll need to install it again.
 
also there are a couple of GUI monitors such as gkrellm and conky. GKrellM is easy to install and light on resources. so is conky...
 
yea the heating up really depends on hardware. an oldie i have is cooler in Ubuntu and battery lasts longer than in winXP.


Thanks for that, I'll give a go. So in your opinion, would a Ubuntu 10/11  machine run just as cool as the Windows 7 machine?  

My laptop specs: T3500 CPU with 4500m integrated graphics, 4GB ram.

Cheers

---

### Post by JCM_Pico on 2011-06-16
If you have a flash pen with enough space, 4 G, you can install the lice cd there and leave some space where you can install all the things that you want....

---

### Post by Mark Phelps on 2011-06-16
> **domfliss said:**
> Thanks for that, I'll give a go. So in your opinion, would a Ubuntu 10/11  machine run just as cool as the Windows 7 machine?  

My laptop specs: T3500 CPU with 4500m integrated graphics, 4GB ram.

Cheers

Unless someone else has actually tried with this laptop, it's really just a guess...

Win7 supports CPU scaling on lots of PCs -- which is why it tends to run "cooler" on laptops that have such CPUs.

If your laptop CPU supports scaling and Ubuntu implements it, then it should run even "cooler" than Win7; but if either is not the case, you will be one of those reporting how Ubuntu runs "hot".

You should be able to install lm-sensors and then gkrellm and then see what temps are reported.  Just don't reboot.

---

### Post by cloyd on 2011-06-16
I'm one of those folks who has been concerned about heat. I use Ubuntu on a netbook and a laptop. The netbook does not support cpu scaling. Yes, it gets warm, but I've never seen it climb beyond the low 60's C. Most people have told me this really isn't harmful. Two things help. One: make sure the vent are not blocked, especially if you are working with the machine on your lap. Use and stand or something like that. Two: limit flash use. Don't watch a whole movie (I don' refer to a short video here) with Flash . . . find another way. 

My laptop supports cpu scaling, and I think it really runs cooler than it did on vista. To tell the truth, I really don't know, because I never learned to monitor the cpu in Vista. The machine feels subjectively cooler. 

Lastly, like the others said, you can install sensors on a live CD or flash drive; it isn't that difficult or time consuming. They'll just go away when you shut down.

Ubuntu is worth the learning.  It teaches as well as works.

---

### Post by arukaddp on 2011-06-16
I have to say until now I haven't really assign heat to flash use, I always thought that the heat was a result of network card intense use... but yes I also can say that if I watch long flash clips it will get a little hotter. 

Why not use Wubi to install it inside windows? It will run as a native install and you can get real temps, as if you use a Live CD the temps might spike from CD use... I think (not a tech so I am just assuming).

---

### Post by dagoss on 2011-06-16
It's worth noting that you can make Ubuntu run as cool as a good beer. I have a Toshiba Portege r705 and while it CAN run KDE or Compiz with all the bells and whistles without any on-screen problems, I'll end up burning my lap. Using LXDE or a light window manager (*hugs Openbox*), or not using X at all, will make things much cooler.

I used LXDE on an ASUS Eeepc 1000ha netbook, and not only did it run cooler, battery life noticeably improved.

---

### Post by domfliss on 2011-06-16
Thanks for all your help and advice.  I think I'll install it on my laptop.  I'm sure my CPU has scaling, but it doesn't have enhanced speedstep, which I believe is different.  I might wrong on that though, lol.  I do like that unity interface, lol. 

Which program would you suggest I install to monitor the temps?

D

---

### Post by domfliss on 2011-06-16
Downloaded Xsensors and system was at 49 degrees c.  It's quite a lot hotter than Windows, so I am not sure.  Maybe it's because it hasn't installed Ubuntu.  Fan comes in at 50 and takes it back down to 42 degrees c. 

Would it run cooler if it was actually installed? lol

D

---

