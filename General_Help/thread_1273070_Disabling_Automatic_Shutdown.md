---
title: "Disabling Automatic Shutdown"
date: 2009-09-23
forum: General Help
---

### Post by bungrudi on 2009-09-23
Hi All,

I installed 9.04 x64 on my Compaq Presario V3221 AU laptop (AMD Turion64 x2 1.6GHz, 4GB RAM).
I got everything worked out of the box, including internet using Sierra Compass 885. My compliments go to ubuntu teams.
But I still have one problem that makes Window$ stay in the box. 

I have load of MKV videos that i need to convert to AVI format. When in the middle of converting using mencoder, the laptop always shutdown automatically. Searching trough the net and this forum I suspect that this has something to do with CPU temperature. 
The question is, how do I disable the auto shutdown feature related to temperature detection?
(yes Im aware of the consequences, including frying my CPUs. Its fine on windows so it should be fine in linux too, i suppose)

I tried the solution here [http://burnz.wordpress.com/2009/02/23/ubuntu-auto-shutdown-due-to-high-cpu-temperature/](http://burnz.wordpress.com/2009/02/23/ubuntu-auto-shutdown-due-to-high-cpu-temperature/) but there is no "options" file in /etc/modprobe.d/ folder.
I tried to create one and do all the step mentioned there but to no effect. Any clue?

Thanks,

Rudi

---

### Post by SteveDee on 2009-09-23
I suggest you try to monitor the cpu temperature first to see if this is a problem (your cpu could get hotter running different software on any OS, its just a question of cpu %usage).

Try installing "X Sensors" to monitor cpu temperature. Even if you have an overheating cpu, I'd try to rig up some external cooling rather than disable your only protection. Maybe force cool air into the laptop with a desk fan.

---

### Post by bungrudi on 2009-09-24
That's exactly what I did. I put a desk fan that blows directly to the upper side of my laptop, put my laptop on a cooler pad, and put the air conditioning to the coolest it can get. By doing this I was able to convert 50% of the movie, compared to just 4% before. :)
I decided to take the most practical step available for me, which is stopping to get MKV (matroska) movies and get DivX movies instead.

Anyway, for those interested in this, I was able to make the temperature stable at an acceptable measure by lowering the CPU frequency (by issuing "cpufreq-selector powersave" command). Its just I can't stand the time it needs to convert 2 hours movies when the laptop operating on powersave mode.

Thanks for the reply.

---

### Post by peterthinking on 2009-09-24
put bookshelf in front of air conditioner and laptop on shelf.

---

