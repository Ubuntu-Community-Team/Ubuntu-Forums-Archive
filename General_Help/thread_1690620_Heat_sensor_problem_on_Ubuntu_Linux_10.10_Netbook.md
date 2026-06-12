---
title: "Heat sensor problem on Ubuntu Linux 10.10 Netbook"
date: 2011-02-18
forum: General Help
---

### Post by TheOne_CZE on 2011-02-18
Hi,

I have a MSi Wind Netbook that broke a while back. XP would not boot on it because of a heat sensor that fried itself, so i tried to install Ubuntu netbook edition on it yesterday and that worked. When it boots it says that critical temp 130 Celsius system shutting down but it boots.  

However, I still have a problem because the ACPI sensor reads 130 Celsius thus the fan is running on max all the time. The CPU temp is around 20 to 25 Celsius max.

Is there a way to slow the fan or tell  it to ignore the sensor?

I tried everything I could but because I am a newbie in linux i did not succeed. I have tried using lm sensors to change the limits but i don't see that sensor in the file. I have tried to follow how to turn of ACPI but again the file i have found does not match what was told to do.    

Any help is greatly appreciated and Thanks in advance!

---

### Post by cloyd on 2011-02-18
If the sensor is fried, I'd think it is doing you a favor by running all the time. It may be noisy, and it uses power, but if your processor is fried, you're out of business.

---

### Post by TheOne_CZE on 2011-02-18
The CPU temp sensor still works ans is around 20 Celsius but the ACPI sensor is gone. 

I know it's better than if no fan was running but it is loud and it just seemed like it could be fixed.

---

### Post by cloyd on 2011-02-18
I am over my head here to help much. You might look at the ubuntu community documentation. One page I found is this:
[http://manpages.ubuntu.com/manpages/hardy/man4/acpi.4.html](http://manpages.ubuntu.com/manpages/hardy/man4/acpi.4.html)

There may be more. Much of this is out of my league . . . 
I've seen fan/temperature issues generate lots of discussion, but they haven't always come to final conclusions. 

Anybody else?

---

### Post by TheOne_CZE on 2011-02-18
> **cloyd said:**
> I am over my head here to help much. You might look at the ubuntu community documentation. One page I found is this:
[http://manpages.ubuntu.com/manpages/hardy/man4/acpi.4.html](http://manpages.ubuntu.com/manpages/hardy/man4/acpi.4.html)

There may be more. Much of this is out of my league . . . 
I've seen fan/temperature issues generate lots of discussion, but they haven't always come to final conclusions. 

Anybody else?

Thanks, I have looked it earlier but its maybe too complicated for me. But thanks again.

---

