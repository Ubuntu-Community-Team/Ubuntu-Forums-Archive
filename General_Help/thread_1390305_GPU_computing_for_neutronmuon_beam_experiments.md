---
title: "GPU computing for neutron/muon beam experiments"
date: 2010-01-25
forum: General Help
---

### Post by professor-g on 2010-01-25
Wanting to evolve current cluster to GPU-enabled and retain ubuntu (champion the cause!)
Details below; ill share all results/successes here on the forum for any interested.
How best to get started ?
Thx,
G.
---
Heterogeneous cluster of 40 quads/dual-quads w/4,8,16Gb memory
All running ubuntu 8.04 or 9.04
Quantum Mechanical computations supporting neutron and muon beam experiments on red-wine/green-tea anti-oxidants, etc...

Success of this centure would be precision independent (for now) single-precision floats are fine for now. I am more concerned with getting it going and making compatible with current codes - less concerned with accuracy of results for now. Double prcision floats will come anyways with the Fermis.
---

---

### Post by t4thfavor on 2010-01-26
That sounds very interesting, who is doing your cuda programming? and too bad you spent so much on all those quads. If your going to use Graphics cards, you will be amazed at how slow the CPU is for floating point calculations.

I'm not sure, but if the numbers are correct on the nvidia site, a couple of tesla engines would improve even your processing over the 40 machines.

The next gen is supposed to be even faster and like you mentioned have better double precision processing.

---

### Post by professor-g on 2010-01-26
Noone solid doing CUDA coding - myself + friend will work on it.

Not really waste to get all 40 quads - we have done alot of great work already on them - they simply become desktops for students or 'have-nots' if the new Teslas/Fermis will replace any of them.

Best would be to get all of them quad-Tesla'd.

All - any help is appreciated.
Thx,
G.

---

### Post by t4thfavor on 2010-01-26
Those tesla engines are marvelous, I had a pair of GTX280's in my old workstation, and they beat my q6700 by about 10kppd or more in my excursions with F@H.

---

### Post by professor-g on 2010-01-26
Cool. What is best way for me to get started?
G.

---

### Post by t4thfavor on 2010-01-26
Unless you are already versed in cuda, here
[http://www.nvidia.com/object/cuda_home.html](http://www.nvidia.com/object/cuda_home.html)

Still here, even if so as that is where you find information on how to code the language.

Still might need to buy some books, and research, as the project you have described seems difficult.

---

