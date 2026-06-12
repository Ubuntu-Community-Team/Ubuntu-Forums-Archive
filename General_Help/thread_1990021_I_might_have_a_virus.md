---
title: "I might have a virus"
date: 2012-05-29
forum: General Help
---

### Post by machdohvah on 2012-05-29
I think I might have a virus. Several times a day, a message pops up on the screen interrupting wharever is going on. See screenshot. It says "System Program Problem Detected". I sent the report immediately after the screenshot. This is a crop for it would have been too large. But, it is just in the middle of the desktop with an Ubuntu default wallpaper background. Please find the report and tell me that it is not a virus for it could have come from a program run in Wine that from taken from a CD that I burned with Windows 2000. It is just a Monopoly Game direct from Hasbro. I may have had a virus on the machine at the time.

---

### Post by zombifier25 on 2012-05-29
It's normal. Just clean the /var/crash directory.

---

### Post by wilee-nilee on 2012-05-29
There is a bug with apport the reporting app I believe, I would suspect that is what is going on. I have a system error show up in 12.04 and 12.10 the development daily.

Does not hurt to look at the web info on apport bugs and errors.

---

### Post by machdohvah on 2012-05-29
> **zombifier25 said:**
> It's normal. Just clean the /var/crash directory.

I just did what you suggested above and I will see if that solves the problem, but I wonder if your colleague is also having the same problem occurring all the time on his machine.

---

### Post by 3rdalbum on 2012-05-29
Windows viruses generally don't even work on Wine, and it's practically impossible for one to have any effect on the host Ubuntu system. There are no known Linux viruses at the moment nor have there been for a few years. No Linux viruses in history have ever caused this behaviour.

However, little bugs and glitches in Ubuntu sometimes cause this logging program to fire up and give you the message in your screenshot. It's nothing to worry about. You can disable Apport if they bother you.

---

### Post by dcstar on 2012-05-29
> **machdohvah said:**
> I think I might have a virus. Several times a day, a message pops up on the screen interrupting wharever is going on. See screenshot. It says "System Program Problem Detected".
...........

Did you bother to look at the "Details" when you reported it?

---

### Post by kurt18947 on 2012-05-29
> **dcstar said:**
> Did you bother to look at the "Details" when you reported it?
+1.  I used to get that frequently from 'indicator-weather'.  While there are no 'in the wild' Linux viruses my understanding is that java and browser exploits **can** affect Linux systems.  Hence the need to keep your system updated.

---

### Post by PeterP24 on 2012-05-29
viruses are very rare on a GNU/Linux based operating system. At the very best, they can wipe your /home directory. Which, I admit, it is very sad indeed, but they usually leave you with a functional OS, and with the possibility of correcting the issue. Malware and social engineering are a very different sort of threat.

---

