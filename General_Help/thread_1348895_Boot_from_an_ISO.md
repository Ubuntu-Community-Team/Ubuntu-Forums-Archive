---
title: "Boot from an ISO"
date: 2009-12-07
forum: General Help
---

### Post by John Long on 2009-12-07
Is there a way I can boot from a mounted ISO? I don't have any blank DVD's and the ISO file size is >800MB. The ISO is bootable.

---

### Post by u.b.u.n.t.u on 2009-12-07
An ISO cannot be booted per se because it is an image file. Mounting the ISO and running wubi.exe will however work for installing Ubuntu 9.10.

---

### Post by spillin_dylan on 2009-12-07
If you're using GRUB 2 then this may be possible.  I think I'm going to give it a try, too, just to see!  

[http://www.panticz.de/MultiBootUSB](http://www.panticz.de/MultiBootUSB)

[http://michael-prokop.at/blog/2009/05/25/boot-an-iso-via-grub2/](http://michael-prokop.at/blog/2009/05/25/boot-an-iso-via-grub2/)

The top two results on Google.

---

### Post by ranch hand on 2009-12-07
> **spillin_dylan said:**
> If you're using GRUB 2 then this may be possible.  I think I'm going to give it a try, too, just to see!  

[http://www.panticz.de/MultiBootUSB](http://www.panticz.de/MultiBootUSB)

[http://michael-prokop.at/blog/2009/05/25/boot-an-iso-via-grub2/](http://michael-prokop.at/blog/2009/05/25/boot-an-iso-via-grub2/)

The top two results on Google.
If you get that to work on an Ubuntu ISO please post it and what your menuentry is.

I have never gotten this to work.  drs305 did but took it out of his post because of too many problems of inconsistancy in the results.

---

### Post by bodhi.zazen on 2009-12-07
boot it with Virtualbox =)

What the two above said, grub 2 has the ability to boot an iso, but the iso needs to be customized to allow this.

Take a look at an iso that has been modified to boot, grml for example. I bet SLAX or Wolvix would also boot. DSL might.

---

### Post by ranch hand on 2009-12-07
Something that Ubuntu ought to think about seeing how they are the first to use grub2.

Maybe one of the respins will do it.  One that was Xfce based would be cool.

---

