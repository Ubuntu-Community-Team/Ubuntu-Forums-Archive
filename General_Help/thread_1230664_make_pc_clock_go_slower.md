---
title: "make pc clock go slower"
date: 2009-08-03
forum: General Help
---

### Post by berdux on 2009-08-03
hello!

there is nothing wrong with my pc, i just want to temporarily make the clock go slower, for example when a minute has passed, the pc will think that 40 seconds have passed..
is there a way to make that happen?

thanks in advance

---

### Post by physic.dude on 2009-08-03
This would be called underclocking. Here is a complete and basic how to.
[http://www.wikihow.com/Underclock-a-PC](http://www.wikihow.com/Underclock-a-PC)

---

### Post by berdux on 2009-08-04
no i do not mean underclocking, i am not talking about making the 3GHz cpu slower, (i know how to do that :) ) i mean to make the pc's 10 minutes to be 15, i want to slow the clock that counts the time. I remember many years ago in windows there was a utility that made the system do that temporarily, it was counting time slower :)

---

### Post by 3rdalbum on 2009-08-04
The PC hardware itself runs the clock, not the operating system. The only software way to do it, as far as I know, is to have a script that runs every 60 seconds, and sets the clock back 20 seconds.

---

### Post by physic.dude on 2009-08-04
You can open the PC and locate the "crystal oscillator" (a peace of courtz in a metal toob or case) responsible for the time and you can replace it with a slower one. You can also put a switch between the regular and slow one to control it on demand.
 
I did this to a GameBoy Advance and it worked, but it was too slow for me.

---

### Post by berdux on 2009-08-05
lol!
ok, thx guyz :)

---

### Post by mcduck on 2009-08-05
> **3rdalbum said:**
> The PC hardware itself runs the clock, not the operating system. The only software way to do it, as far as I know, is to have a script that runs every 60 seconds, and sets the clock back 20 seconds.

I've actually understood that Linux only uses the hardware clock to get the time when booting, and after that keeps it's own time at OS level..

But no, I don't think there's any program to slow the time down. Not a very common thing to do, really. Honestly I can't even think of any reason to do such thing. :)

---

### Post by credobyte on 2009-08-05
Save it, chmod id, launch it ( with root privileges ) .. cheers :p

**fcktime.sh**
```
while true
do
    real_sec=$(date +"%S")
    fake_sec=$(expr $real_sec - 1)

    fake_time=$(date +"%H")":"$(date +"%M")":"$fake_sec
    date -s $fake_time
    
    sleep 2
done
```

---

### Post by lethalfang on 2009-08-05
> **berdux said:**
> hello!

there is nothing wrong with my pc, i just want to temporarily make the clock go slower, for example when a minute has passed, the pc will think that 40 seconds have passed..
is there a way to make that happen?

thanks in advance

Bring your PC to the nearest black hole, which is about 1600 light years away. :-D

---

