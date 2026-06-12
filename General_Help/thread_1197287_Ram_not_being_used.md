---
title: "Ram not being used"
date: 2009-06-25
forum: General Help
---

### Post by supertails on 2009-06-25
I believe that ubuntu is either using too much ram or not letting enough ram in. Back when I was using windows I never had problems playing my old school games but when I switched to ubuntu all of them crash. How do I fix it?

---

### Post by izizzle on 2009-06-25
Try running your games in a terminal and see if they throw out any errors. Have you checked the system monitor too see how much RAM is actually being used?

---

### Post by cariboo on 2009-06-25
Linux does not use memory the same way Windows does. It uses all the memory it can to cache programs, after-all unused memory is wasted. To check memory usage open a terminal and type:

```
free -m
```

the output should look something like this:

```
free -m
             total       used       free     shared    buffers     cached
Mem:          2990       2942         48          0         56       2354
-/+ buffers/cache:        531       2458
Swap:         4559          1       4557
```

As you can see from the above, actual ram usage is 531MB, even though cached prgrams use 2942MB.

I would suggest that your problem with your games, is a video problem rather than a memory problem.

---

### Post by supertails on 2009-06-25
CPU1 25% CPU2 35% when I ran the game they both shot up to 100% which makes me think that ubuntu isn't using enough of my ram, cause this is a brand new computer and the games I'm trying to play are old.

---

### Post by Bucky Ball on 2009-06-25
'Old school' games for Windows or Linux? If they are for Windows, they ain't gonna work without Wine, and possibly not then.

---

### Post by izizzle on 2009-06-25
What happens when you run them through the terminal? Which games are they?

---

### Post by supertails on 2009-06-25
So it only uses enough ram to run the browser and other programs but not games? So how do I increase it?

---

### Post by supertails on 2009-06-25
They are NES. I got a NES emulator from the add/remove programs button.

---

### Post by Bucky Ball on 2009-06-26
This might be of interest:

[http://linuxgamingtoday.wordpress.com/2008/09/14/how-to-install-emulators-on-ubuntu-nes-edition/](http://linuxgamingtoday.wordpress.com/2008/09/14/how-to-install-emulators-on-ubuntu-nes-edition/)

Read post #3 again. Don't think this is a RAM problem either. The RAM is either there or it is not; it is not really a matter of throttling it up or down or telling the system how much to use. It will just cache to however much is there. Think of a bucket. You can fill it to capacity but that capacity depends on the size of the bucket. In this case, it overflows to the swap.

Open System->Admin->System Monitor and see how your machine is chugging along when you try and run a game. See how much of the memory is being used or if anything untoward is happening.

---

### Post by mcduck on 2009-06-26
> **supertails said:**
> CPU1 25% CPU2 35% when I ran the game they both shot up to 100% which makes me think that ubuntu isn't using enough of my ram, cause this is a brand new computer and the games I'm trying to play are old.

Games are always designed to run as fast as they can, which means that they will use 100% CPU no matter what system you run them.

Processor usage has nothing to do with RAM usage. That's comparing two completely different things.

---

### Post by Yellow Pasque on 2009-06-26
> **supertails said:**
> So it only uses enough ram to run the browser and other programs but not games? So how do I increase it?
If you don't have enough RAM, the only way to get more is to physically add more or increase the size of your swap and use some disk space as RAM. That said, you probably aren't running out of RAM.

Heavy CPU usage under graphic load might indicate that you don't have the proper video driver or don't have it installed correctly.

If you are running games in WINE and having issues, check the database on WINE's site to see what other users say about those programs. Also, you might want to try the latest development version of WINE.

Off-topic:
> ...but a foolish man listens to an opinion and **except** it as fact. 
'except' should be 'accept' (that might just be my opinion though)

---

