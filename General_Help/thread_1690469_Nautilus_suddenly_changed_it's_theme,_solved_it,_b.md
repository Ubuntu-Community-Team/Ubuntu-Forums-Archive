---
title: "Nautilus suddenly changed it's theme, solved it, but one question remains"
date: 2011-02-18
forum: General Help
---

### Post by rhoparkour on 2011-02-18
Well, an image says a lot more than words...

Take a look at bad.png, then at solved.png

So, through some light googling, I solved the problem by deleting all nautilus conf files,

```

rm -vr ~/.gconf/apps/nautilus && killall nautilus

```Nevertheless, I am still bothered by the simple question: Why the ** did nautilus do this in the first place?

What I was doing at the time of the "anomaly:"

- Browsing the internet, I was just about to download cygwin for windows and terminator (no machine is complete without a good shell). By the way, not for me, for my sister, she must use windows apps for work (all hail the monopoly, man). Funny, when I opened a new tab, the toolbars on top and bottom became "gray," after a second they came back to normal, but I opened nautilus to find the problem.

- I was also installing imaxima through apt-get.

- I'm running two big processes, both simulations which take up almost all of my CPU (been running them for days now). 

- Additionally, this ubuntu install is a few days old (needed a clean install to clean up my garbage and repartition my hard drive, feels nice, to tell the truth).

That's about it, WHY DID NAUTILUS DO THIS? Any thoughts?

Be happy.

---

### Post by redenex on 2011-02-18
This used to happen to be a while ago, but now everything seems to work fine.

---

### Post by rhoparkour on 2011-02-18
Nice to hear it was fixed for you (automatically, manually?). It is not a problem anymore, but it would be nice to know what caused it, wouldn't it?

---

### Post by bastos77 on 2011-04-13
Just the same thing happens to me today (Lucid). Thanks for the fix.

---

