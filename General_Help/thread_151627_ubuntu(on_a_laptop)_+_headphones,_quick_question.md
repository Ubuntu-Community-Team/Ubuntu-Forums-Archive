---
title: "ubuntu(on a laptop) + headphones, quick question"
date: 2006-03-28
forum: General Help
---

### Post by LamB on 2006-03-28
im running ubuntu on a dell 630m, the thing is: when i plug in my headphones, they work fine, but both the sound from the speakers and the headphones play at the same time... 

any thoughts??? thanks

---

### Post by Zimmer on 2006-03-28
Sounds like (no pun intended) a hardware problem. Plugging a blank stereo jack into the laptop should cut out the speakers, so try a different set of phones, or a similar cable with plug (or a jack adapter) to see if that cuts out the speakers...you should be able to tell from that whether it is the headphone jack or the laptop socket that is at fault.

---

### Post by mdmarmer on 2006-03-28
This could be Alsa problem as well

Open a mixer

There should be switches for headphone sense, etc. -- make sure these are working correctly

If not, and you find this a problem you could try a newer version of Alsa

There is a known bug for AC97 sound where headphones work and speakers don't (due to sense switches not working properly) -- supposed to be fixed in newer versions

I've not heard of your type of problem, tho, so it may be hardware -- check that first

Mike

---

### Post by Zaskoda on 2006-04-21
I have exactly the same experience on my 630m. I doubt it's a broken hardware issue. LamB - if you find a resolution, please post.

---

### Post by Zaskoda on 2006-04-21
Sorry for the double post... From here:

[http://lokorn.neuf.fr/index.html](http://lokorn.neuf.fr/index.html)

"On the 4th of april, a new kernel has been issued (Linux 2.6.15-20-3 86 #1 PREEMPT) with the wright Alsa module compiled. Everything works fine now, the speakers mute when I plug my headphone!"

---

### Post by Morbett on 2006-05-31
[QUOTE=Zaskoda]Sorry for the double post... From here:

[http://lokorn.neuf.fr/index.html](http://lokorn.neuf.fr/index.html)

"On the 4th of april, a new kernel has been issued (Linux 2.6.15-20-3 86 #1 PREEMPT) with the wright Alsa module compiled. Everything works fine now, the speakers mute when I plug my headphone!"[/QUOTE]

Hi, I have the same problem.  so what do I need to do to get my Dell laptop to mute when I plug in speakers?  How do I update to this new kernel?  I'm still using Breezy by the way.

---

### Post by davebgimp on 2006-06-06
I have this same problem on my Lenovo 3000 N100 running Dapper.

---

