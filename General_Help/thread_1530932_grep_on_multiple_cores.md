---
title: "grep on multiple cores"
date: 2010-07-14
forum: General Help
---

### Post by john1923 on 2010-07-14
Hi

How do I make grep use all 4 cores?

I am using it to parse a 13GB text file, and it is taking a really long time.

Any help is appreciated as I will probably be doing this again.

ps. I have checked the manpage and there is no mention of running it across multiple cores/processors/CPUs.

---

### Post by Zorgoth on 2010-07-14
You could always split it into 4 files and run 4 greps

- if you are producing this file with your own code or have a way to do this with however you are getting the file it would be best to do that when the file is created.

---

### Post by endotherm on 2010-07-14
my guess is that there isn;t a lot of CPU involved in grepping, but that IO would be your biggest bottleneck on a 13GB file, in addition to the small matter of paging it into ram and all the IO involved in virtual memory management.
what does top or htop show while you are performing your grep?
how about iotop? is the file on the local hdd or a network location? if network what does iftop show?

---

### Post by john1923 on 2010-07-15
Thanks for the replies,

In the end I went and had a cup of coffee while it ran, it only took 23min.

Next time I will make 4 output files and run 4 instances of grep, but it is not a very elegant solution.

As for the CPU load. One core was running flat out, while the others idled. (the core that was running flat out was switched every few seconds or so to even the wearing on the CPU)

What is the IO bottleneck that you mentioned, as I think that I may be running into that when I run BLAST using all four cores. (the CPU load is 400%, then every few seconds it drops to 100%, then rises back up to 400% (400% = all cores running at 100%))

Thank you for all of your help.

---

