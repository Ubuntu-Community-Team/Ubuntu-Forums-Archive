---
title: "cant get ubuntu 10.10 to boot from CD"
date: 2010-10-11
forum: General Help
---

### Post by ivh90 on 2010-10-11
hello People

I've been having this problem since I've tried installing ubuntu 10.04 on my toshiba laptop ...

whenever I tried to boot the live CD ; it starts booting , a purple screen appears then a black one with a blinking dash , and it stops there.

I read a post somewhere saying that this problem was taken care of with ubuntu 10.10 but actually it is not ! 

I really need to get Linux on my laptop as soon as possible , Please help ! 

Ps . 
my laptop has I7 core , 4GB ddr3 , nvidia 330m

---

### Post by dino99 on 2010-10-11
on the boot line, add either: noapic, nolapic, noacpi, irqpoll, nomodeset

note: always burn a cd at the lowest speed

---

### Post by ivh90 on 2010-10-11
thx for the reply 
but what do you mean with :

on the boot line, add either: noapic, nolapic, noacpi, irqpoll, nomodeset

thank you

---

### Post by dino99 on 2010-10-11
> **ivh90 said:**
> thx for the reply 
but what do you mean with :

on the boot line, add either: noapic, nolapic, noacpi, irqpoll, nomodeset

thank you

when you choose to boot on cd (or somewhere else) "edit" that choice before pressing "enter"

---

### Post by ivh90 on 2010-10-11
when i restart my laptop and get to the boot menu 
i cant edit the options (there is no edit option) the only thing that i cant do is choose one of them

---

### Post by ivh90 on 2010-10-11
ok .... i tried evey single option but no luck 
any advice ?

---

### Post by phunehehe on 2010-10-13
Hi dino99 thanks a lot I was able to get the live CD boot, probably install tonight.

@ivh90: press any button on the first screen that appears, then you should see a menu screen. There pressing ```
F6 (Other Options)
``` you can choose the modes that dino99 talked about. You can also edit the ```
Boot Options
``` line that appears afterwards.

Hope that help :)

---

### Post by ivh90 on 2010-10-13
thx a lot people .. you really made my day 
i used noacpi and it worked

I am running ubuntu from the LiveCD (havent installed it yet )
almost everything is working : wireless , sound , usb but i have some questions :

when i use the system moniter i see only one core not 8 (in windows i used to see all of them ) 

there seems to be no power management ; i cant see whether the power adaptor is plugged in or not 

after installing ubuntu do I have to use the boot paramter everytime i turn my laptop on ?

thx again

---

### Post by phunehehe on 2010-10-14
Hi ivh90,

This looks bad :( We have [another thread]("http://ubuntuforums.org/showthread.php?p=9958157") talking about it. The short answer is, you have to add acpi=off as a boot parameter. Until there is an update to fix it...

---

### Post by ivh90 on 2010-10-14
ok i will ... but what about battary indicator , can i get that fixed ?

---

### Post by phunehehe on 2010-10-14
hmm sorry that I don't know, just about as clueless as you are

---

### Post by ivh90 on 2010-10-15
bump .... 
I installed ubuntu successfully but the problem remains with acpi=off 
OS boots very very slow ! 
there is no power indicator 
ubuntu only detects 1 core out of 8 :S
multimedia buttons dont work 

please help !!!!!

---

### Post by ivh90 on 2010-10-18
Bump ... please any help ! anyone ?

---

### Post by ivh90 on 2010-10-21
ok lets start with one problem at a time : 
why is Ubuntu only detecing one core of the I7 ? 
how can this be fixed ?

---

### Post by Swiftjay on 2010-10-21
> **ivh90 said:**
> ok lets start with one problem at a time : 
why is Ubuntu only detecing one core of the I7 ? 
how can this be fixed ?
there could be some updates that might fix this issue.  Or if you check additional drivers in System> Administration see if there's drivers for the processor to be installed.

Also, another thing you could try is have a look at the intel website i'm sure they might have driver support for the processor with linux support if none of those two are the case.

---

### Post by ivh90 on 2010-10-22
ok i installed the latest updates and restarted 
but everything is the same 

and by the way my laptop heats up a lot 

please people tell me what the problem is ? 
what is acpi ? and why do i have to keep sending boot parameter ?

---

