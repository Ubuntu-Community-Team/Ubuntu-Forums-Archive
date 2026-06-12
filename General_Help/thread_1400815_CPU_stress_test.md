---
title: "CPU stress test"
date: 2010-02-07
forum: General Help
---

### Post by 98cwitr on 2010-02-07
anyone got a link/source for a decent cpu stresser app? did a search and didnt really find anything :/

---

### Post by mohitchawla on 2010-02-07
Mprime.

Its the linux version of the popular stress testing software, Prime95.

---

### Post by n0dix on 2010-02-07
Cpu-burnin, here the link: [http://www.howtointernets.com/wiki/index.php/Simple_CPU_Stress_Test_for_Linux](http://www.howtointernets.com/wiki/index.php/Simple_CPU_Stress_Test_for_Linux)

---

### Post by MooPi on 2010-02-07
I prefer Mprime as it stops on error which gives an indication that something is either wrong or that your CPU may be overclocked to high.

---

### Post by 98cwitr on 2010-02-07
ok downloaded and untar'd mprime and there is an executable in the tar, executed and it opened another folder with another like executable, double clicked it and system froze. Dont think I did it right and the website and readme aren't very helpful. Sorry to be such a n00b with this

---

### Post by serpentracer on 2010-02-07
> **98cwitr said:**
> ok downloaded and untar'd mprime and there is an executable in the tar, executed and it opened another folder with another like executable, double clicked it and system froze. Dont think I did it right and the website and readme aren't very helpful. Sorry to be such a n00b with this

look for a readme file it might have instructions.

---

### Post by tgalati4 on 2010-02-07
sudo apt-get install cpuburn htop
man cpuburn

For multiple processors: (say a quad core)

burnP6 &
burnP6 &
burnP6 &
burnP6 &

htop

---

### Post by 98cwitr on 2010-02-07
^^^thanks! That works great. 29C idle 57C full load on e6750 @ 3.6 w/ Zalman 9500 and holding stable :D

---

### Post by tgalati4 on 2010-02-07
When building a new machine, or replacing old heat paste, it's a good idea to burn in slowly, to allow the paste to settle and to also verify stability of your cooling hardware.

I rebuilt a dell poweredge 1750 with 2 dual-core xeon processors.  I put in Artic Silver paste then burned in each processor (using one core only) for an hour.  Then I ran both cores in each for an hour.  I also noticed different temperatures with the different workloads--burnMMX, burnP5, and burnP6.  It's a handy tool.

---

### Post by 98cwitr on 2010-02-08
not a new system or new proc...just wanted to see how far I could go with Ubuntu, used to bluescreen XP @ 3.70, I always assumed it was the memory. Ubuntu is a bit for resourceful/stable though ;)

---

### Post by tgalati4 on 2010-02-08
If you want more throughput on your system, try lowering (slightly) the memory CAS wait cycles (say 15-5-5-5 to 12-4-4-4).  I was able to get a 9% throughput improvement using name-brand memory, with built-in heatsinks.  Intels can take a fair amount of overclocking--more so than the motherboards that they are put in.  It's usually the IO chips that fail.  Use your finger to measure them.  If you can't keep your finger on the north/southbridge chip for more than 10 seconds then you are at risk of frying the motherboard.

---

### Post by 98cwitr on 2010-02-08
dont see that capability in BIOS, I can manually set the memory multiplier, which will change the freq of the memory but I see nothing relating to the CL

---

