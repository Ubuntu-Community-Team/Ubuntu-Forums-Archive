---
title: "all programs crash"
date: 2011-02-17
forum: General Help
---

### Post by vikngo on 2011-02-17
Hello everyone. First say that I come to this forum hoping to find more answers in the above where I state. My problem seems so consulted, however much they've looked at do not get it solved.

I do not know whether to divide the problems, but it seems incredible that everything happens at once, so I leave it all in case anyone related.
Issues: All programs end up closing themselves. At times a segmentation fault (thunderbird, ICEcat), others do not return anything (firefox, openoffice), at other times returns Inconsistency detected by ld.so: ../sysdeps/x86_64/dl-machine.h: 46 ... ( firefox, openoffice)
and other Gdk-WARNING **: XID collision, trouble ahead (I've already seen this reported in Launchpad and without fix) ..

Well, to see if I can run 15 minutes one day in a row.

I hope to be posting in the appropriate forum and in the right way.

My PC: Ubuntu lucid 10.04, GNOME 2.30
AMD64 Phenom x4, ati radeon 8500GT.

Thank you very much.

---

### Post by Grenage on 2011-02-17
Greetings.

First things first, have you run a memtest check?  Such wide-ranging problems are often caused by hardware problems.

---

### Post by vikngo on 2011-02-17
> **Grenage said:**
> Greetings.

First things first, have you run a memtest check?  Such wide-ranging problems are often caused by hardware problems.

Ok, i'll do it and i tell you. 
Thanks

---

### Post by vikngo on 2011-02-17
Hello, i run memtest and i got this:

[http://ubuntuforums.org/attachment.php?attachmentid=183700&stc=1&d=1297950725](http://ubuntuforums.org/attachment.php?attachmentid=183700&stc=1&d=1297950725)

I've 4071 errors!  it's normal? or that's mean that my ram is almost dead?.

---

### Post by Grenage on 2011-02-17
Ok, looks like we have a possible cause!

Turn off your computer, remove the ram and blow out the memory slots.  The RAM may be damaged, or it may just have a bad contact.  Put the RAM back in, and run another scan; if you still get errors and you have more than one stick of RAM, try testing one stick at a time.

---

### Post by vikngo on 2011-02-17
> **Grenage said:**
> Ok, looks like we have a possible cause!

Turn off your computer, remove the ram and blow out the memory slots.  The RAM may be damaged, or it may just have a bad contact.  Put the RAM back in, and run another scan; if you still get errors and you have more than one stick of RAM, try testing one stick at a time.

Ok, I'll do it and i tell you. 
Thanks

---

### Post by vikngo on 2011-02-17
Actually i got one stick of Ram bad!. At the moment i'm working fine for  this 15 minutes. That's a record!. We'll see how it's going on.
I understand that segmentation fault is related with an address memory problem, so maybe it's solved a lot of issues.

I'll report details about how it's going on. I'm a bit skeptical that  only eliminating the bad ram all is fine..i wish that. If everything is  ok tomorrow, i'll close this threat with solved.

Thank you Grenage!

---

### Post by Grenage on 2011-02-17
I'm glad that at least one of the sticks is ok.  Ram is so important to the operation of a computer, a small amount of damage can lead to a horrible experience.

---

### Post by vikngo on 2011-02-18
Well, finally i could to solved a lot of problems of dependencies and dpkg because with the problem of the Ram i never could install well anything and i have broken packages. So, it' working fine!!.
Thanks again.

---

### Post by Grenage on 2011-02-18
Great news; best of luck. :)

---

