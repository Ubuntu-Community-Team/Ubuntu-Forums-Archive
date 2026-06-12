---
title: "difference in ram usage between 2 fresh installs?"
date: 2010-05-21
forum: General Help
---

### Post by cain071546 on 2010-05-21
i just installed 9.10 on a dell desktop p4 2.0 ghz 512ram and a dell net-book atom1.6 1gig ram the desktop says its using more ram at idle even when the net-book is running all compiz effects and the desktop none, When on the same webpage side by side it always says its using more ram. The net-book idles at about 137mbs ram usage even when playing with all desktop effects and surfing Myspace or you tube
and the desktop idle is anywhere between 160 and 220 when doing nothing at all i have compared the active processes and theres no discrepancy other than the net-books WiFi so Wye is it reading like this........and i can see what is being held as buffer and cache its just using more ram for no good reason
i understand that Linux and UNIX allocate ram differently but Wye would the idle stats be so far apart?

---

### Post by Chesamo on 2010-05-21
That's a hell of a sentence.

How much swap space did you allocate on each machine?

---

### Post by cain071546 on 2010-05-21
5 gigs on the desktop and 3 gigs for the netbook

---

### Post by Chesamo on 2010-05-21
Why do you have so much swap?

---

### Post by hvbakel on 2010-05-21
Is the desktop by any chance running the 64bit version and the netbook the 32 bit version? The same programs typically use more memory on a 64 bit system compared to a 32 bit system.

---

### Post by cain071546 on 2010-05-21
i let the live cds install automatically so..... you tell me?
there decent size HDDs

---

### Post by cain071546 on 2010-05-21
nope all 32bit

---

### Post by hvbakel on 2010-05-21
I take it you used the same livecd for both computers then, which means that they run the same version (you would need a different CD for the 64 bit version).

---

### Post by cain071546 on 2010-05-21
exactly

---

### Post by Chesamo on 2010-05-21
Since the netbook has less swap space (and more RAM), it would make sense that Ubuntu uses more RAM and less swap. Is there a performance problem? If not, then it's just Ubuntu keeping careful track of your resources.

---

### Post by cain071546 on 2010-05-21
the system monitors say neither are using any swap at all

---

### Post by Sef on 2010-05-21
Applications > Accessories > Terminal

then type in this command:

```
top
```

It will show you everything that is running.

---

### Post by cain071546 on 2010-05-21
I know this...... there is no discrepancy between the 2 systems running processes. Please read a entire thread before answering questions

---

