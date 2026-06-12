---
title: "How to use memtest"
date: 2009-08-24
forum: General Help
---

### Post by kehon on 2009-08-24
I used memtest 86(?) that came with ubuntu and i just let it run. it said there was an error so what exactly does that mean and how does it affect me and my computer

---

### Post by nikhilk on 2009-08-24
> **kehon said:**
> I used memtest 86(?) that came with ubuntu and i just let it run. it said there was an error so what exactly does that mean and how does it affect me and my computer

memtest basically test/stress-tests your RAM. It is recommended that you run it when you suspect that there is some problem with your RAM. So errors probably indicate some problem with the RAM, although I am not sure of the credibility of these tests. IIRC, the best method is to do a 24 hour run of memtest to throughly test your RAM.

I do not have any experience using this tool so  till someone with more experience comments on this, you can read the [Wikipedia article]("http://en.wikipedia.org/wiki/Memtest86") for some more information.

---

### Post by P4man on 2009-08-24
If memtest reports an error for a memory range, its most likely at least one of your memory sticks has gone bad. How it affects you? It will cause any OS to freeze or crash or spontaneously reboot. not good.

You can try removing one memory stick (if you have >1) and run memtest again. Do the same for the other stick(s), so you can isolate the faulty stick. You can also try changing some bios settings (decrease memory speed, increase latency settings, slightly increase dimm voltage).

That said, it may be false alarm. Can you give the exact error memtest gave you? How much ram do you have? IM not sure how memtest copes with 4GB or more.

---

### Post by automaton26 on 2009-08-24
You need to find which module is bad, by removing them one at a time and re-running memtest. Also, if you've ever altered the BIOS memory timings, or overclocked anything via software, then you should restore it all to the factory defaults.

To understand the problems duff memory will cause, imagine a friend gave you directions to his house, and a single instruction was randomly changed from "Turn left..." to "Turn right...". The end result of the instructions would not be slightly wrong, they would be *completely* wrong, because the instructions are always done in sequence.

With duff memory, you'll get random problems in random places and your machine will never be reliable. Rock-solid memory is always the first thing to check on any machine.

---

### Post by kehon on 2009-08-24
i'm not sure what the exact error is because i didn't write it down but i'll write it down next time (tomorrow night) and get back to you.

i only have 2GB of ram

---

### Post by P4man on 2009-08-24
If you got 2GB, then I know for fact memtest should work fine. If it gave you an error, then you got a problem. Follow the above advice to isolate and/or cure the problem.

---

### Post by Topsiho on 2009-08-24
The memory test tests your memory (the computer's memory :) ) with a number of tests during a long time. The longer the more chance that an existing error will be found. If an error is found you know that there is an error, and you will have to find out what stick is the culprit and replace it. If no error is found the only thing you know is that no error was found. To be really sure that there is no error, you should run the test an infinitely long time. No one does that.

Usually one or two complete passes is sufficient, however.

In your case you are "lucky": an error was found. So do what the others told you: find out what memory stick is the culprit by removing the sticks one by one, and repeating the test. And if you need the memory, replace the faulty stick.
As sometimes different makes or kinds of memories do not cooperate quite well together, you might consider replacing all memory sticks.

The error message itself might be nice to know, but the real thing is that there was a message at all ...
Only if you are an expert you would benefit from knowing the contents of the message.

Topsiho

---

### Post by XCan on 2009-08-24
Remember that you most likely have a lifetime warranty on your sticks as well. :)

---

### Post by automaton26 on 2009-08-24
The memtest error will just be a particular bit pattern that failed once. But a single wrong bit can be the difference between a huge positive number in memory, and a huge negative number.

With memory, absolute reliability is everything - so go for the best & don't touch "Value" brands. Also, memory providers like Crucial or Kingston usually have websites that let you specify your machine or motherboard exactly, so you definitely get the right modules.

Finally, make sure you observe static electricity precautions (ground yourself often) when handling memory modules, and don't touch the gold connectors at all.

---

### Post by CatKiller on 2009-08-24
> **P4man said:**
> How it affects you? It will cause any OS to freeze or crash or spontaneously reboot. not good.

Actually, it's worse than that. If the memory is bad then there's the possibility that any of the files that are on the hard drive could be corrupted as well. Anything that's been through the RAM could have been altered by the RAM fault - think loading a file and then saving it. Memory problems are *nasty*.

---

### Post by automaton26 on 2009-08-24
> any of the files that are on the hard drive could be corrupted

+1. Exactly.

An intermittent fault is so much worse than a complete failure. Lots of corrupted files obviously makes things unusable, but the occasional switched bit here and there might seem OK for a while...

(/shudder)

Once you've cured your memory problem, I would backup all data, and then go for a complete reinstall of ubuntu. Then restore the data, but also compare it (where possible) to older backups, in case it has been corrupted too.

---

