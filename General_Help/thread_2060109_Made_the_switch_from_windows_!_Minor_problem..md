---
title: "Made the switch from windows ! Minor problem."
date: 2012-09-19
forum: General Help
---

### Post by Icaurs7234 on 2012-09-19
Started using Ubuntu (12.04.1 LTS) for the first time last week and after a bumpy start and then discovering Gnome I think I'm going to like it here !

My only problem/question is that my system says its only getting 3.9gb of memory... I have 6gb all functioning under Win7.

The system monitor cant detect the difference of my CPU's running at 3.07GHz or 3.71GHz though so maybe the monitor just doesn't read out properly?

Any idea's or thoughts would be welcome... but be gentle with me !

---

### Post by Slim Odds on 2012-09-19
You installed the 32 bit version.

I'd recommend a backup and reinstall the 64 bit version. That will give you access to all of your memory.

P.S. Some will recommend a PAE kernel. I don't. Go 64 bit!

---

### Post by Icaurs7234 on 2012-09-19
Uhm, It reads off as the 64bit version on system details.

---

### Post by f8l_0e on 2012-09-19
Is this an AMD FX processor?  If so, try running ```
dmesg | grep "MTRR"
``` from the terminal and see if it mentions "CPU MTRRs don't cover all of memory, losing {X}MB of RAM."

---

### Post by Icaurs7234 on 2012-09-19
Running on an i7 950.

---

### Post by f8l_0e on 2012-09-19
Is it using the X58 chipset? What model of motherboard?

---

### Post by Icaurs7234 on 2012-09-19
It's an 'Asus Rampage III Extreme', so yes... X58.

---

### Post by f8l_0e on 2012-09-19
This is apparently not exactly a Linux problem.  Watch this video:

[http://www.youtube.com/watch?v=R_9MwkZ8cjs]("http://www.youtube.com/watch?v=R_9MwkZ8cjs")

Try setting your memory your the way the video describes, or possibly better to whatever your ram's closest setting to 1600/1333/1066.  The 2133/2000/1800 are technically an overclock and there is some problems with the X58 chipset.

---

