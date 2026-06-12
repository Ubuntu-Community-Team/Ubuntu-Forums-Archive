---
title: "hidden process consuming 50% CPU and temp is 75°C"
date: 2012-02-28
forum: General Help
---

### Post by marbertone on 2012-02-28
Hi guys,
this sounds definitely like a question to be posed to experts.
OS: Natty, PC: Sony Vaio SZ61XN/C.
Everything was perfect until some days ago, when PC fan was going at max speed. top says that 50% of CPU is busy, but even doing ps -aux no process occupies more than 2% of CPU (being idle).
By launching powertop I discovered this weird stuff:

```

The program 'mf-nowin' is writing to file 'mfput.log' on /dev/sda1.
The program 'cat' is writing to file '18359.badpos' on /dev/sda1.
The program 'firefox' is writing to file 'wikipedia-it.xml' on /dev/sda1.
The program 'grep' is writing to file '1752.errs' on /dev/sda1.
The program 'cat' is writing to file '2515.strange' on /dev/sda1.

```

The thing that scared me the most was "Firefox is writing to file 'wikipedia-it'". WIKIPEDIA.IT ?!?!?!? FIREFOX WAS CLOSED!

Guys! What's going on? Is it a virus? Or a weird indexing process?
Thanks,
Mario Alberto

---

### Post by dcstar on 2012-03-01
> **marbertone said:**
> Hi guys,
this sounds definitely like a question to be posed to experts.
OS: Natty, PC: Sony Vaio SZ61XN/C.
Everything was perfect until some days ago, when PC fan was going at max speed. top says that 50% of CPU is busy, but even doing ps -aux no process occupies more than 2% of CPU (being idle).
...........

Do you have it automatically installing updates?

---

### Post by marbertone on 2012-03-01
I don't think so, it always ask me to do updates! 
Anyway, after upgrading to the new kernel it has not shown the problem since yesterday morning. Let's cross fingers. I also installed avg antivirus, just to be more secure...even if it did not find anything.
Cheers,
M.A.:popcorn:

---

### Post by marbertone on 2012-03-01
p.s.
I also uninstalled 'timidity', it looked to be a bit problematic too...

---

### Post by Vigh on 2012-03-01
Regardless of whether there is a hidden process, it sounds like you need some arctic silver on your CPU. 75deg celcius is far too hot, unless its overclocked, you definately need better hardware cooling

---

### Post by marbertone on 2012-03-01
Do you think is it just hardware-related issue? Usually it works perfectly at T < 50 °C. I don't know if it will happen again, but it was like a sudden "turning on" of a switch, which led my laptop to 75°C constant temperature. Bah!
M.A.

---

