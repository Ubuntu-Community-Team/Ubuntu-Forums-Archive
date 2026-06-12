---
title: "me vs. compiz"
date: 2009-10-04
forum: General Help
---

### Post by tadpole1954 on 2009-10-04
I have always had trouble getting compiz to work for me, but I thought I would try it one last time since I had switched over to Ubuntu from another os.  Well, I did and it didn't work out for me again.  My ati board is to blame I believe.  Anyway, I was a little frustrated with the whole thing and I went into synaptic and uninstalled all the listings for compiz.  All the ones that showed up after I searched for compiz.  Dumb move, huh?

Now my ubuntu will not boot.  Can this be fixed without a reinstall?

---

### Post by DeMus on 2009-10-04
> **tadpole1954 said:**
> I have always had trouble getting compiz to work for me, but I thought I would try it one last time since I had switched over to Ubuntu from another os.  Well, I did and it didn't work out for me again.  My ati board is to blame I believe.  Anyway, I was a little frustrated with the whole thing and I went into synaptic and uninstalled all the listings for compiz.  All the ones that showed up after I searched for compiz.  Dumb move, huh?

Now my ubuntu will not boot.  Can this be fixed without a reinstall?

When you write Ubuntu will not boot, do you mean you do not get a graphical screen, just the black one with the command line interface?
If so try installing 2 packages:
libdecoration0
libemeraldengine0
The way to do this is:
log in
type (will need password again)
```
sudo apt-get install libdecoration0
```
```
sudo apt-get install libemeraldengine0
```
reboot

---

### Post by tadpole1954 on 2009-10-04
Thank you for the quick reply DeMus.  I should have been more clear in my description of the problem.  The boot does not get as far as that.  When ubuntu stops in the boot process, the monitor has a line of red figures across the top.  Across the middle of the screen is the word ubuntu and the ubuntu logo over and over in a line.  All of this is very fuzzy looking.  The boot stops here.

---

### Post by mexicanmusicman on 2009-10-31
Why dont you just re-install?  all you have to do is make a partition. Make it half and half. Once on your other one try to extract the files you may need from it... and then delete the partition.

---

