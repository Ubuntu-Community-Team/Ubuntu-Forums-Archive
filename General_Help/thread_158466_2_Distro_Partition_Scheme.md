---
title: "2 Distro Partition Scheme"
date: 2006-04-11
forum: General Help
---

### Post by domino on 2006-04-11
I have a 24gig primary partition I can spare to use for Linux. I want to install a stable Ubuntu and also the edgy Dapper/Xgl/Compiz. I have this all planned out and I hope someone can give feedback on it. Notice that I have the */home* and the *swap* partition shared between the two OS. Will this pose a problem?

```
Second Primary Partition

Ubuntu Breezy:

/boot 	- hda2				100mb
/swap 	- hda3 (shared with Dapper)	500mb
logical partition - hda4		
/	- hda5				6,000mb
/home 	- hda6 (shared with Dapper)	12,000mb

Dapper:

/boot 	- hda7				100mb
swap 	- hda3 (shared with Dapper)		
/	- hda8				5,000mb
/home	- hda6 9 (shared with Breezy)
```

---

### Post by Sef on 2006-04-11
How much ram do you have?  Swap should be double your ram though if you got a gb of ram then you don't need 2 gb of swap.

---

### Post by domino on 2006-04-11
Yea, thats what I wanted to point out. I have 1.5gig of ddr. In the past running Breezy and conky, I haven't noticed the swap partition using more than 2mb. It's kinda depressing to see all that unused space going to waste.

Edit: If I had Breezy running of 48hrs non stop, My memory consumption would only have about 800mb - 900mb, still having enough for a vmware winxp session. I have not noticed any dramatical speed loss setting swap at 500mb.

---

