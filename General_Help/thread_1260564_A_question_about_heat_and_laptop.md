---
title: "A question about heat and laptop"
date: 2009-09-07
forum: General Help
---

### Post by stuart.reinke on 2009-09-07
I've heard it mentioned in other threads about how laptops tend to run hotter using Ubuntu and a cooler with Xubuntu.

Why is this? 

I currently have Ubuntu on my laptop, should I be concerned, how do I tell if it is too hot?  

Should I switch to Xubuntu?

I just need a little clarification.

Thanks

---

### Post by benerivo on 2009-09-07
You can use the command```
acpi -t
```to get a temperature reading. More complex programs use the processor more and so there is more heat generated. Xubuntu uses lighter/smaller programs and so the temperature reading and battery life should be a little better. I'm not sure what a dangerous temperature is. I've heard 50 deg.C is okay.

---

### Post by stuart.reinke on 2009-09-07
> **benerivo said:**
> You can use the command```
acpi -t
```to get a temperature reading. More complex programs use the processor more and so there is more heat generated. Xubuntu uses lighter/smaller programs and so the temperature reading and battery life should be a little better. I'm not sure what a dangerous temperature is. I've heard 50 deg.C is okay.

Thanks. I show 52 degrees C at Idle. Firefox open with one tab.

---

### Post by gamerchick02 on 2009-09-07
> **stuart.reinke said:**
> I've heard it mentioned in other threads about how laptops tend to run hotter using Ubuntu and a cooler with Xubuntu.

Why is this? 

It's probably because Ubuntu has more intensive graphics requirements than Xubuntu.

Xubuntu is supposed to be lighter than Ubuntu, running Xfce and all.  :)

Amy

---

### Post by benerivo on 2009-09-07
You can do a few things from here. Check at what temperature your fan kicks in. Also try and check what a dangerous temperature is for a latop is (?). Also you can look in to cpu frequency scaling. I'm sorry that i can't give specific advice on how to do this on Ubuntu (only my desktop is Ubuntu and i haven't done any power management on it) but have a look at...

[http://www.thinkwiki.org/wiki/How_to_use_cpufrequtils](http://www.thinkwiki.org/wiki/How_to_use_cpufrequtils)

Frequency scaling involves lowering the power running through the cpu when it is idle. It is usually used to prolong battery life, but it also redcues cpu temperatures. I use it on my arch linux laptop ([http://wiki.archlinux.org/index.php/Laptop#Power_Management](http://wiki.archlinux.org/index.php/Laptop#Power_Management))

---

### Post by stuart.reinke on 2009-09-07
According to yahoo answers, I should be concerned at anything above 60 and something needs to be done if temp gets over 70 .

I seem to get as high as 77 while streaming video.

Any suggestions? 

Do you guys agree with Yahoo answers?

---

### Post by winotree on 2009-09-07
Here [http://www.digipedia.pl/man/acpi.1.html](http://www.digipedia.pl/man/acpi.1.html) is something that'll help you get a bit deeper into the subject.  (Can't say one way or the other what I believe about Yahoo Answers as I've not used that service).  I do know my little device runs at a steady 53C and I believe it was acpi that said 90C was critical for it -- but would, no doubt, be too hot to touch!  :D

---

### Post by alejaaandro on 2009-09-07
i was playing with viewing info from /proc today
i stumbled upon this

cat /proc/acpi/thermal_zone/TZ01/trip_points
critical (S5):           102 C
passive:                 95 C: tc1=0 tc2=10 tsp=5 devices=CPU0 CPU1

i figured my critical temp is 102oC?? (that seems too high!!)

check if you have the same files and see if you can get that info from there..

---

### Post by stuart.reinke on 2009-09-07
Thanks for the advice. I'm currently downloading Xubuntu Karmic. 

Think I'll test it for a while and compare temps with my Ubuntu Hardy install.

---

### Post by winotree on 2009-09-07
> **alejaaandro said:**
> i was playing with viewing info from /proc today
i stumbled upon this

cat /proc/acpi/thermal_zone/TZ01/trip_points
critical (S5):           102 C
passive:                 95 C: tc1=0 tc2=10 tsp=5 devices=CPU0 CPU1

i figured my critical temp is 102oC?? (that seems too high!!)

check if you have the same files and see if you can get that info from there..
Guess **stuart.reinke** is going to be busy for awhile.  :)  This is the information I mentioned a bit earlier

user@PasturePrime:~$ cat /proc/acpi/thermal_zone/TZ00/trip_points
critical (S5):           90 C

but note that it's on an ASUS netbook.  It's currently 53.  ;)

---

### Post by alejaaandro on 2009-09-07
@ winotree: does it have fans? i have mini 9 and it doesn't have fans, so i would guess it's natural to be tolerant to higher temps.. but, on the other hand, they both have intel atom, right? mine at least has..

---

### Post by winotree on 2009-09-07
Yeah -- one small one that operates nicely on its own but can't be controlled externally.  Are you having problems or just concerns about what you've read?

EDIT - Celeron M 900mHz factory underclocked to 630mHz  :(

---

### Post by alejaaandro on 2009-09-07
no, no problems at all.. just curious why the critical temp would be different on the same processor.. anyway, as long as it works ok.. ;)

EDIT: just saw your edit..

---

