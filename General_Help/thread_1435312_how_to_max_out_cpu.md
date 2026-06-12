---
title: "how to max out cpu"
date: 2010-03-21
forum: General Help
---

### Post by linden940 on 2010-03-21
is there a program or a simple way to max out my cpu power (make it go 100%) so i see at what temp my cpu is when its maxed out?

I am thinking about overclocking my laptop to get some more speed..but be4 i do that i need 2 know how hot my cpu will get when its maxed out so i wont over heat it when i go to over clock it

if you know a command that will do that...lol give me the command that i could use to stop it as well lol

---

### Post by Sin@Sin-Sacrifice on 2010-03-21
```
man nice
```

---

### Post by linden940 on 2010-03-21
lol i dont see how that would work....

---

### Post by cascade9 on 2010-03-21
DVDrip (or any otehr video encoding program) does a pretty good job at giving you CPU full load for a while. You cant just run at 100% load for 10 minutes and get any idea how much heat it will output, you need a while to see how hot things can go- 2-3 hours at least, longer is better. 

BTW, laptops + overclocking is normally a Bad Idea.

---

### Post by _h_ on 2010-03-21
> **cascade9 said:**
> laptops + overclocking is normally a Bad Idea.

Overclocking in general is a bad idea, regardless of it being a desktop or laptop.

---

### Post by cascade9 on 2010-03-21
> **_h_ said:**
> Overclocking in general is a bad idea, regardless of it being a desktop or laptop.

Bah! to that. :P I ran an overclocked system for years. I could even run cooler overclocked on that system than I could @ stock levels. AMD 2500+, stock = 1826Mhz  (166 x 11) @ 1.65v. I could run at  1920Mhz  (167 x 11.5) @ 1.525v, never had a problem. That was a very good CPU though. ;) 

Going for major overclocks isnt a good thing, but minor overclcocks on a desktop dont normally cause any problems.

---

### Post by kio_http on 2010-03-21
There is its called cpuburn

Install with

```
sudo apt-get install cpuburn
```

---

### Post by Locke_99GS on 2010-03-21
Or you could just compile something.

---

### Post by Sin@Sin-Sacrifice on 2010-03-21
Oh... overclock. I was thinking just **max out** cpu. Like using 100% of the cpu. The nice command helps with that.

---

### Post by DarkN00b on 2010-03-21
Or you could play a flash video in Firefox. :D

---

### Post by linden940 on 2010-03-21
hmmm i installed cpuburn but cant find it in application list...

yea i want to max out my cpu to see what the temp is if it is low..then i would like to over clock it....*i have my laptop on a cool mat all the time..so it stays pretty cool*

---

### Post by jocko on 2010-03-21
> **linden940 said:**
> hmmm i installed cpuburn but cant find it in application list...

yea i want to max out my cpu to see what the temp is if it is low..then i would like to over clock it....*i have my laptop on a cool mat all the time..so it stays pretty cool*
cpuburn is a collection of different cpu stress tests, run them in a terminal by one of these commands:
```
burnBX
burnK6
burnK7
burnMMX
burnP5
burnP6
```

If you have a multi core cpu you need to start one process per core, so to run burnMMX on both cores of a dual core:
```
burnMMX & burnMMX &
```
And to stop it:
```
killall burnMMX
```

---

### Post by linden940 on 2010-03-21
lol nm...i found the readme file

---

### Post by cascade9 on 2010-03-21
> **linden940 said:**
> hmmm i installed cpuburn but cant find it in application list...

yea i want to max out my cpu to see what the temp is if it is low..then i would like to over clock it....*i have my laptop on a cool mat all the time..so it stays pretty cool*

High temps are something to avoid if you do overclcock, but low temps are not a sign of overclcockablity. Also, you can still kill CPUs overclcocking, even if they do stay cool.

BTW, most laptops dont even have the ability to adjust the settings for the CPU /FSB etc in the BIOS, and thats the only way to overclock CPUs with linux. Really, BIOS overclcocking is the only good way to overclock at all IMO.

---

### Post by linden940 on 2010-03-21
"BTW, most laptops dont even have the ability to adjust the settings for the CPU /FSB etc in the BIOS, and thats the only way to overclock CPUs with linux. Really, BIOS overclcocking is the only good way to overclock at all IMO."


yea this laptop dos not have that setting...bummer..

yea heat is not the only thing...if you get the settings wrong on the cpu your in some trouble...I was going to see what the temp was at now and then look to see what other ppl did when they overclock and had a stable cpu....anyway i cant over clock it and that sucks

*i'll never software overclock...thats dumb as hell*

---

### Post by wizard10000 on 2010-03-21
I use folding@home - the SMP version runs eight threads on this Core i7 and works the machine pretty hard but is at a low enough priority that anything else you run takes precedence.

---

### Post by beeno on 2010-05-23
> **DarkN00b said:**
> Or you could play a flash video in Firefox. :D

hahahaha best call...

---

