---
title: "How fast is SAMBA server?"
date: 2006-06-19
forum: General Help
---

### Post by jethro10 on 2006-06-19
Hi,
I was thinking of buying a Network Attached Storage NAS device and after looking at prices, it occured to me a Ubunto box with samba is similar in price. 

How fast is samba, is this a worthwhile alternative?
It does give me scope for other things as well.

Jeff

---

### Post by glenndavy on 2006-06-19
A couple of years back we did some simple tests across a few boxes and platforms to settle a 'friendly' bet we had going. We just used what we had - a range of basic desktop generic boxes and a couple of laptops with various o/s on them incl: debian woody/samba, win 98, win2k and win XP - we boot each machine off the woody inst cd - and recorded the bogomips of the machine, then usinging 1 windows machine as a client carried out some tests i.e drag a particularly large directory accross and run a particular process (which was the cause of the whole bet in first place)  we had in microsoft access on each server,which  'served' the back end.

We learned 2 things - 1) (which surprised us) the cpu speed is actually relevant regardless of os - infact results were linear according to the bogomips i.e if bogomips were on machine A were 3 x that of machine B, then the jobs finished in 1/3 of the time and 2) on that line samba had a marginal advantage - so my guess its not going to be anyworse than what ever your nas is running
Glenn

---

### Post by jethro10 on 2006-06-19
Looks like it's probably a good idea to give it a go then.
Jef

---

### Post by glenndavy on 2006-06-19
garn... you know you want to :D

---

### Post by jethro10 on 2006-06-20
[QUOTE=glenndavy]garn... you know you want to :D[/QUOTE]
Absolutley...
J

---

