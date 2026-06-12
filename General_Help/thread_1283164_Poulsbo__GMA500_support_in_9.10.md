---
title: "Poulsbo / GMA500 support in 9.10?"
date: 2009-10-05
forum: General Help
---

### Post by TomaszC on 2009-10-05
Does Ubuntu 9.10 natively support Poulsbo / GMA500 graphics chipset?

For 9.04, it was necessary to do some manual configuration (adding 3rd party repositories etc. - I don't see related kernel modules in these repositories for Ubuntu 9.10).

---

### Post by lovinglinux on 2009-10-05
This should be posted in the [Karmic Koala Testing and Discussion](http://ubuntuforums.org/forumdisplay.php?f=359), not the General Help.

---

### Post by michael37 on 2009-11-05
Since Karmic 9.10 is out, we can revive this thread.

There is a fairly good unofficial support for Poulsbo in Karmic 9.10.

**Very short version.**
Download and run [this script]("http://ubuntuforums.org/showpost.php?p=8182373&postcount=87").  
I strongly recommend to read it and understand it first, which will involve reading the script and reading:

**Long version.**
Read [thread=1253406]this[/thread] and [thread=1229345]this[/thread] threads.  OP has the instructions.

---

### Post by metalfan_ on 2009-11-10
Did anyone succeed to get a fit-pc2 running with this driver?
my screen only flashes slowly after reboot, going from black to white for a very short time. cant even changet o a console.

---

### Post by michael37 on 2009-12-04
> **metalfan_ said:**
> Did anyone succeed to get a fit-pc2 running with this driver?
my screen only flashes slowly after reboot, going from black to white for a very short time. cant even changet o a console.

I dont have fitpc, but I've seen people post blogs running with this driver.  Run lspci | grep VGA
If you see SCH Poulsbo there, this driver should work.

---

