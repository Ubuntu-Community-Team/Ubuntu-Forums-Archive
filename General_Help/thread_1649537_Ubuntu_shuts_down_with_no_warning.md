---
title: "Ubuntu shuts down with no warning"
date: 2010-12-20
forum: General Help
---

### Post by amulet on 2010-12-20
I have dual boot Vista and Ubuntu Lucid on my laptop, Toshiba.
The problem is that the laptop randomly powers off without any shutting down procedure, but only when I am using the Ubuntu OS.  It never happens when I (rarely) use the Vista OS. I had the same problem with the previous karmic OS, and I had hoped that a fresh install of Ubuntu would resolve the problem, but it has not.

Any suggestions please?

Thank you

---

### Post by psihokiller4 on 2010-12-20
does it do it if you leave PC completely free? (so you don't do anything)

very strange never happened to me before

how much time remains ON until it shuts down by it's self?

---

### Post by sikander3786 on 2010-12-20
The first thing that comes to mind is heat. Make sure your Laptop is not over heating. You mentioned that you don't have any problems with Vista but you also said that you use it rarely ;-)

You can check the temperatures in Bios menu. Or for an experiment, run Vista for longer periods and see if the problem also happens with that.

And do you remember any specific software running while it shutdowns? And how much time does it take as already asked in above post?

And is it a proper shutdown or just a crash and restart?

---

### Post by tgalati4 on 2010-12-20
Monitor temperature of the CPU and more importantly the GPU and check the health of the battery.  It's possible that the battery/power circuitry is hitting a limit (low voltage or high current).  Try running the laptop with the battery completely removed and the laptop plugged into power.  See how long Ubuntu stays up.

---

### Post by amulet on 2010-12-21
Thanks for all suggestions.  
The reason I know that the problem doesn't occur with Vista is that I have had Vista running for 4 days (Windows takes SO long to boot up that I left it on as I needed it to use a mobile broadband dongle).

I know it has nothing to do with heat as it is a very random event, and this morning I booted into Karmic in my freezing cold kitchen, next to an open external door on a very windy day, and it powered off twice in the first 10 minutes, before happily running all day without a problem.

There is definitely no stress on the graphics card, I only use my Desktop for such tasks.

It is not a well-mannered shutting down of the system, it just turns off in an instant... no restart, just ...off!
It is a big mystery for sure.

---

### Post by drewsus on 2010-12-21
This worth a try: open it up and clean out dust.

---

### Post by amulet on 2010-12-21
Thanks for that drewsus, you know you're probably hitting the nail on the head, as they say: my housekeeping skills do leave a lot to be desired!
Will let you know the outcome after I have followed your advice.

:)

---

### Post by sefs on 2010-12-21
It would be interesting if Ubuntu was estimating that the battery was about to run out of juice when it was not.

---

### Post by ram2500 on 2010-12-21
I wonder if it is related to the lack of proper drivers for the fan...? If it's not shutting down when booting to Windows, but only in Ubuntu, then it might be a driver issue or an issue with the kernel "speaking" to the fan and CPU throttle so as to keep the system cool.

---

