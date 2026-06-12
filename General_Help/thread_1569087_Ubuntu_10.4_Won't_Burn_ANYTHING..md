---
title: "Ubuntu 10.4 Won't Burn ANYTHING."
date: 2010-09-06
forum: General Help
---

### Post by Zubb on 2010-09-06
So I've recently installed Ubuntu 10.4
I've used Ubuntu for a bit in the past and never had this problem.
Basically I insert a blank CD into my drive, I want to burn Ubuntu server onto it, but it just isn't working.

It's a regular ISO file, I right click and "Write to disc" it goes through the process, finishes and ejects the drive. I close it again and it says the disc is still blank after finishing, I thought the disc was faulty so I tried another, same problem, it burns but keeps it blank.

I even tried k3b, same problem.

What do I do? :(

Jason.

---

### Post by rtimai on 2010-09-06
Jason,

You didn't say what model your CD burner was, which matters. I have an old HP CD-Writer Plus 8210, and found that GnomeBaker worked with it when no other did -- it depends on wodim which is installed automatically with GnomeBaker if not present. I forget what the current default CD burner front-end uses, but some hardware don't respond to the required calls. The main indication of this is that a blank CD is not recognized as unformatted media, but reported as "no media."

HTH

---

### Post by mziskandar on 2010-09-06
Having the same problem before.. and haven't test it yet due to running out of cd/dvd. You can try this:
[http://ubuntuforums.org/showthread.php?t=1549008](http://ubuntuforums.org/showthread.php?t=1549008)
[https://bugs.launchpad.net/ubuntu/+source/hal/+bug/531901](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/531901)

---

