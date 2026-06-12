---
title: "GRUB menu not coming after GRUB-UPDATE"
date: 2011-04-19
forum: General Help
---

### Post by plastichero on 2011-04-19
I updated my grub yesterday using the command:
> sudo grub-update

and I rebooted and grub menu not coming now. I have a dual boot with Win7. Ubuntu 10.04 is installed with WUBI. I can run WIN7 but can't run Ubuntu now. 

Guys, help me please.

---

### Post by ashickur.noor on 2011-04-19
> **plastichero said:**
> I updated my grub yesterday using the command:


and I rebooted and grub menu not coming now. I have a dual boot with Win7. Ubuntu 10.04 is installed with WUBI. I can run WIN7 but can't run Ubuntu now. 

Guys, help me please.
First of all ther is no command like sudo grub-update
it will be > sudo update-grub

---

### Post by plastichero on 2011-04-19
Oh sorry ... Thanks, Ashickur. I mistyped it :P

anyway, any help on that?

---

### Post by Mark Phelps on 2011-04-19
Wubi does NOT use GRUB; instead, it uses a derivative known as GRUB4DOS.  Furthermore, you do not use a GRUB menu to access multiple OSs in a Wubi install; instead, you use a Windows boot menu.

So, if you forced an installation of GRUB into your Win7 OS partition, you probably hosed up the Windows boot big time.

Of course, you had the foresight to create a Win7 Repair CD ahead of time, right?

Since you probably did NOT, then go to the link below, download and burn the appropriate Win7 repair CD:

[http://neosmart.net/blog/2009/windows-7-system-repair-discs/]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

When you have that, boot using that and run Startup Repair three times -- that's right, three times.

---

### Post by bcbc on 2011-04-19
Please see the [wubi megathread]("http://ubuntuforums.org/showthread.php?t=1639198"), problem #2, solution #1. Once booting apply the Permanent Fix.

PS since windows boots fine, you don't need to run the windows repair.

---

### Post by plastichero on 2011-04-19
Thanks, bcbc. I'll do it shortly and give the update. 
And yes, as win7 is running fine, nothing to do with that.

---

### Post by plastichero on 2011-04-27
Thanks bcbc, it worked wonder. SOLVED. :D

---

### Post by bcbc on 2011-04-27
> **plastichero said:**
> Thanks bcbc, it worked wonder. SOLVED. :D

Great. You're welcome :)

---

