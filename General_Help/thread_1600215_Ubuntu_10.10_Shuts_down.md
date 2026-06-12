---
title: "Ubuntu 10.10 Shuts down"
date: 2010-10-18
forum: General Help
---

### Post by tareqazan on 2010-10-18
I have installed Ubuntu 2 days ago, when i watch a movie or surfing the net after awhile it shuts down. it happened more than 4 times. plus my laptop gets over-heated.

I tried windows 7 and i did not face any problems with it even if it runs for 24hrs.

Any ideas?:confused:

Thanks

---

### Post by Hippytaff on 2010-10-18
you can check if the cpu is overheating with

```

acpi -V

```but might be worth installing some software to monitor it to see if thats whats causing the problem

heres a thread with a solved overheating problem to help...might not be your problem but should be able to help you diagnose it :-) [http://ubuntuforums.org/showthread.php?t=539365](http://ubuntuforums.org/showthread.php?t=539365)

> 
hippytaff@hippytaff:~$ acpi -V
Battery 0: Full, 100%
Battery 0: design capacity 4000 mAh, last full capacity 3770 mAh = 94%
Adapter 0: on-line
Thermal 0: ok, 48.0 degrees C
Thermal 0: trip point 0 switches to mode critical at temperature 82.0 degrees C
Thermal 1: ok, 52.0 degrees C
Thermal 1: trip point 0 switches to mode critical at temperature 100.0 degrees C
Thermal 1: trip point 1 switches to mode passive at temperature 95.0 degrees C
Cooling 0: Processor 0 of 3


you might have to

```

sudo apt-get install acpi

```

---

### Post by tareqazan on 2010-10-18
Thanks a lot. I'll give it a try.

Thanks again:)

---

### Post by tareqazan on 2010-10-19
Hey thanks a lot now i guess it works fine.. ive tried the link u gave me.. 

and its good for now.

Thanks a lot.:popcorn:

---

### Post by Hippytaff on 2010-10-19
> **tareqazan said:**
> Hey thanks a lot now i guess it works fine.. ive tried the link u gave me.. 

and its good for now.

Thanks a lot.:popcorn:
Excellent...if you mark the thread as solved in the thread tools at the top of the page others can benefit from what you did :-)

---

