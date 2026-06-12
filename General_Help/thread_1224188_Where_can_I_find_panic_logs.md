---
title: "Where can I find panic logs ?"
date: 2009-07-27
forum: General Help
---

### Post by dbyrne on 2009-07-27
My system has become quite unstable since upgrading to 8.04, and is regularly freezing solid, or partly dying (e.g. I can get a login prompt, but having entered a username never get a password prompt).

When it gets into this state there's typically a load of info on the screen, most of which has scrolled off.

I'd like to examine it more closely, but can't find it on disk anywhere. Is there a way to enable this ?

---

### Post by khelben1979 on 2009-07-27
Maybe you're looking for this (?):

/var/log/messages

---

### Post by dbyrne on 2009-07-27
Nope, doesn't have the info I'm looking for in there (or dmesg/syslog/etc.).

This is the sort of info that gets spewed up on the console that I'm trying to capture:

---

### Post by khelben1979 on 2009-07-27
By looking at that output, I get a small suspicion that your hardware might not "feel very good".

Have you bothered to check your temperatures to see if it runs too hot in there? (Maybe you need to add more fans to your case or replace the cpu cooler?)

---

### Post by dbyrne on 2009-07-28
I did wonder if it might be temperature related as the box is up in the attic, which we've recently insulated and underfelted. However a script I run every hour on the server shows the temperature over the last year as running between 38-44 deg Celsius. It's not particularly cool I guess, but it's pretty constant. However it might be that some component has fried over time.

It's now died with the same error three nights in a row, so I'm going to run a watchdog script at regular intervals to see if it always goes down at the same time, and if so figure out what's running at that time. I'll probably take it down and give it a cleanup too in case dust has built up in the case.

---

### Post by dbyrne on 2009-08-01
I'm going to mark this solved, even though I haven't found an answer to the question. I've grepped every file in /var/log and found none of the info that was chucked up on the screen, so it's most likely that there is no file to find. Even if there was, from hours searching the web, there appears to be no documentation to help figure out what the messages reported mean anyway.

Anyway, this time my lucky call was to strip and clean the machine. I hoovered a bit of dust out of it, nothing remarkable, and also opened up a few of the PCI slot covers in the rear. The average temperature is 1-2 degrees lower, although that may be just the weather. Anyway the system has been up for three days so I'm keeping my fingers crossed.

It's disappointing (yet again) to find that the most effective tool for trouble-shooting Linux is sheer dumb blind luck ... :-|

---

### Post by khelben1979 on 2009-08-01
One more thing: if you go back to an older version of Ubuntu, the one that worked okay, then you'll know it's not a hardware problem.

There exists Ubuntu Live CD:s as you probably know where you don't need to install the whole system again just to try it out.

---

### Post by dbyrne on 2009-08-03
Good thinking, I'll try this if the problem recurs.

The system is still working fine so far (fingers crossed), so I'm inclined to think that the crashes occurring so shortly after my upgrade was a coincidence. I suspect that the problem was to do with a poor connection or dust-induced.

---

