---
title: "Linux headers corrupt how do i fix?"
date: 2012-10-14
forum: General Help
---

### Post by chipppy on 2012-10-14
Good Morning

I have a problem that after a lot of playing around I have finally worked out the following
My Linux-headers-3.0.0.20 is corrupt somehow.


> Package in inconsistent state

The package 'linux-headers-3.0.0-20' is in an inconsistent state and needs to be reinstalled, but no archive can be found for it. Please reinstall the package manually or remove it from the system.
I am assuming that no archive can be found due to it being an older version and no longer supported, though I though Xubuntu 11.10 would still be supported. I did try a fully upgrade but this error prevent me from doing the upgrade.

SO
How do I achieve one of the following.
1. Fix the currpot 3.0.0.20 problem.
Get a copy of linux-header-3.0.0.20 from where and where do I replace it 

2. Change my system so that it starts via the working 3.0.0.17 normally without any intervention. 
Currently starting via 3.0.0.20 and fails but can be manually selected to start from the 3.0.0.17 if I interven during the start process (boot via older linux version).  This get my system working perfectly fine without any issues

3. Manually delete linux-header-3.0.0.20 and then I can complete and upgrade to 12.04

4.  Another even better option to fix my system?

Greatly appreciate any help

Cheers
Chipppy

---

### Post by Lars Noodén on 2012-10-14
Which version of Ubuntu are you running?  I could not find version 3.0.0-20 of the headers in 12.04. 

In general, you could try removing the headers or re-installing.

```

sudo apt-get install --reinstall linux-headers-3.0.0-20

```

---

### Post by chipppy on 2012-10-16
Good Afternoon

I am running xubuntu 11.10 alternate install (RAID 5 setup)

I shall try your suggestion as soon as I get home from interstate tomorrow.
Though I wonder if the 
> but no archive can be found for it
could mean that this will not work.  
If the no archive means that the apt-get wont work is there any other option for finding a copyof that specific header.  eg is the a copy of older headers kept somewhere on the web?

Cheers 
chipppy

---

### Post by chipppy on 2012-11-07
Good Morning

Ok still not having any luck with this one.

New stuff I have figured out.  
Under user/share/doc/linux-headers-generic there is no folder for linux-headers-30.0.0.20.  I can find folders for linux-header-3.0.0.14 through to 3.0.0.17.  

I thereofre assume there is a file somewhere telling the system to look for 3.0.0.20.  

I am wondering if it is possible to edit (revert or) that file and comment out the reference to 3.0.0.20 and restore the references to 3.0.0.17.  If that worked (allowed me to start up normally) then I should be able to upgrade to 12.04 from there hopefully.

Does anyone know where I could look for this file and edit it somehow?

Cheers
chipppy

---

### Post by chipppy on 2012-11-11
bump pls

---

