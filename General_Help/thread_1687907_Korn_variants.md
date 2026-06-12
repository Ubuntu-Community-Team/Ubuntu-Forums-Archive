---
title: "Korn variants"
date: 2011-02-14
forum: General Help
---

### Post by stuntman on 2011-02-14
newbie question:

I have Korn installed on Ubuntu (usr/bin/korn)
At work they have korn installed on an AIX box (usr/bin/korn)

(work korn) != (home korn)

for instance
-find -name "hello.txt" (at home) does not work on the AIX box
-find /home -name "hello.txt" works on the AIX box

iname does not work on the AIX box either.

How do I go about getting the at work version of korn on my home box?

yeah...that is me..the green guy
):P

---

### Post by hawkmage on 2011-02-14
Find is an application so it is more likely an issue with the version of find on the different systems and not the shell you are running.  

Although the version of the korn shell was traditionally  on AIX and Solaris 10 and earlier are what is usually referred to as ksh88  which is what they licensed from AT&T and have never updated but in Linux you are probably using what is referred to as ksh93.

---

### Post by stuntman on 2011-02-14
> **hawkmage said:**
> Find is an application so it is more likely an issue with the version of find on the different systems and not the shell you are running.  

Although the version of the korn shell was traditionally  on AIX and Solaris 10 and earlier are what is usually referred to as ksh88  which is what they licensed from AT&T and have never updated but in Linux you are probably using what is referred to as ksh93.

Thanks....it is making more sense now.  The Unix guys have been there for 30 or 40 years.  Why fix it if it is not broken.  Maybe they installed bash or something like that.

I found kornshell.org but they only have the KSH93 version for download.

How do I get ksh88 on Ubuntu?  

OR

Do I need to install another OS like Solaris?


sm

---

### Post by stuntman on 2011-02-14
turns out it is an AIX thing and not a korn thing.

oh well....so much for a lab environment

---

### Post by hawkmage on 2011-02-14
What do you mean when you say it is an AIX thing.  Is it something that is different with the AIX version of find?

---

