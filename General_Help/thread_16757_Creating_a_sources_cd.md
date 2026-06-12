---
title: "Creating a sources cd"
date: 2005-02-23
forum: General Help
---

### Post by oracledarren on 2005-02-23
Hi

I hope somebody can help :) I am sure there is somebody who has done this.

I want to take a copy of the downloads deb packages that seem to get stored in /var/cache/apt and create a sources cd out of them

I also want to be able to somehow tell a newly installed ubuntu installation how to effectively duplicate the installed packages on my main pc

Hence the making a sources cd question.

The reason for this is that i am currently running warty which is pretty much tailored exactly for what i want, and I know at some point either a package i install or the need to upgrade to hoary will happen and potentially damage all the work i have done so far in getting my system as i want it. :)

I know this shouldnt be rocket science to achieve, so i was wondering if anyone else has done this and what the best way to go about it was.

Thanks in advance

Darren

---

### Post by Juergen on 2005-02-24
You need the packages from /var/cache/apt/archives, I'd copy them to a work-dir.

Then create a Packages.gz:
```
dpkg-scanpackages work-dir /dev/null | gzip > Packages.gz
```If you have source packages, man dpkg-scansources.

Now just burn your work-dir and Packages.gz on CD.

Synaptic cant't create entries for such CDs (at least on my install it creates an incorrect entry in sources.lst and then disappears), 
but you can create entries for such CDs manually.

---

### Post by oracledarren on 2005-02-24
Thanks :)

Worked a treat  =D> 

Take care

Darren

---

### Post by bored2k on 2005-02-24
[QUOTE=Juergen]You need the packages from /var/cache/apt/archives, I'd copy them to a work-dir.

Then create a Packages.gz:
```
dpkg-scanpackages work-dir /dev/null | gzip > Packages.gz
```If you have source packages, man dpkg-scansources.

Now just burn your work-dir and Packages.gz on CD.

Synaptic cant't create entries for such CDs (at least on my install it creates an incorrect entry in sources.lst and then disappears), 
but you can create entries for such CDs manually.[/QUOTE]


How would i then add the CD to the repository

---

### Post by Juergen on 2005-02-24
Synaptic creates an entry in sources.lst, but it looks like> / cdrom:[cdname]/ /where it should be > deb cdrom:[cdname]/ /Just edit this line afterwards.

Or create the entry manually - I think the next 'apt-get update' should prompt you to insert 'cdname'.
I haven't tried apt-cd, maybe this works better

I let Synaptic do half the work ;-)

---

### Post by jdodson on 2005-02-26
the howto section is not the place to ask questions.  please read the forum rules before posting.

---

