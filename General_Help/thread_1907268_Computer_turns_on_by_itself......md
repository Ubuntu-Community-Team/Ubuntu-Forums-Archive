---
title: "Computer turns on by itself....."
date: 2012-01-11
forum: General Help
---

### Post by eduardo911 on 2012-01-11
hello guys, i berly install Ubuntu x32 on a vista Desktop and when i turn the computer OFF from the shutdown bottom on the right like you normaly shut down a ubuntu computer, it turns off and then 5 seconds later it turns back on, and i have no idea what is going on, i turn off the computer with the power bottom and it stays off, it only happens when i do it with the normal safe turn off bottom, if any one can help me will be nice :)


thanks, Eduardo

---

### Post by MadsRC on 2012-01-11
I'm confused by your post, is it the physical (hardware) button that you press or the virtual (software button inside ubuntu)?

Because if it's the hardware, then it could be a defect, and if it's the software, then it's probably a bug or something?

---

### Post by eduardo911 on 2012-01-11
> **MadsRC said:**
> I'm confused by your post, is it the physical (hardware) button that you press or the virtual (software button inside ubuntu)?

Because if it's the hardware, then it could be a defect, and if it's the software, then it's probably a bug or something?



im sorry is the software i ment

because when i physically turn it off it turns off,

but when i try to turn it off with the software it turns back on

is that clear, sorry for that

---

### Post by adityamagadi on 2012-01-11
is it on ur virtual box or hardisk dual boot??

---

### Post by prshah on 2012-01-11
> **eduardo911 said:**
> when i turn the computer OFF from the shutdown bottom on the right like you normaly shut down a ubuntu computer, it turns off and then 5 seconds later it turns back on, 

Check your BIOS settings to see if you have WoL (Wake on LAN) or WoR (Wake on Ring) activated.

I had this problem too, and the solution was to disable WoL/WoR.

Please post back if you need more details.

---

### Post by eduardo911 on 2012-01-11
> **adityamagadi said:**
> is it on ur virtual box or hardisk dual boot??


i deleted the Vista system , and replace it with ubuntu

---

### Post by eduardo911 on 2012-01-11
> **prshah said:**
> Check your BIOS settings to see if you have WoL (Wake on LAN) or WoR (Wake on Ring) activated.

I had this problem too, and the solution was to disable WoL/WoR.

Please post back if you need more details.

ok i already checked it and no is still turning on by it self i put the booting sequence to its default and the computer is still turning on by its self

---

### Post by eduardo911 on 2012-01-21
still; having problems everything is correctly how it's suppost to be but the computer keeps turning on by itself

---

### Post by WorMzy on 2012-01-21
Are you shutting down or suspending/hibernating?

Ubuntu does not have the power to boot up a shut down PC; only the bios has that capability.

---

### Post by eduardo911 on 2012-01-21
> **WorMzy said:**
> Are you shutting down or suspending/hibernating?

Ubuntu does not have the power to boot up a shut down PC; only the bios has that capability.

im shutting it Down completely, and the Bios is to its default, i dont know why is turning on

---

### Post by alphaamanitin on 2012-01-21
Have you tried command line to turn it off?

```
sudo shutdown -P now
```

AlphaA

---

