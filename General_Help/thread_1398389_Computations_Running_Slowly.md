---
title: "Computations Running Slowly"
date: 2010-02-04
forum: General Help
---

### Post by mahsheed on 2010-02-04
I have a Core 2 Duo E6550 @ 2.33GHz. I have noticed that my computer does not utilize both the cores of my computer when processing. I wrote a c++ program that just loops continuously and when I checked the System Monitor I saw that one of the cores was being utilized 100% while the other is just used 10-15%. 

When I compared the time taken to run the same program with my friend who has a P4 with just 348MB (something like that) of RAM, his was 15-20% faster. This seems illogical.

Why is this happening? He was using windows at that time. Is it because ubuntu is not fully utilizing my cpus? and how do i correct this?

Thanks.

---

### Post by amauk on 2010-02-04
programs need to be specifically written to take advantage of multiple processors (or multi-cores)

With a single threaded program (like your test program) the OS is not able to split the tasks up over multiple processors

What you need to do is develop your program from the ground up to be multi-threaded

---

