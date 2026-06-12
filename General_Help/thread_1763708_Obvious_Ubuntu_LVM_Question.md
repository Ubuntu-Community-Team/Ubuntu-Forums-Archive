---
title: "Obvious Ubuntu LVM Question?"
date: 2011-05-20
forum: General Help
---

### Post by Drak3 on 2011-05-20
Hello,

first post here, but long time lurker.

In the not too distant future, I plan to build a multi-purpose server.  Specifically, a file, video processing/rendering, and minecraft server.  My question relates to the file serving side.

In a nutshell, I was hoping someone with knowledge of ubuntu 10.04LTS's LVM would know if it is within its capability to have several individual hard drives appear logically as a single drive?  (and obviously split *intact* files between them)

I ask because most levels of RAID (other than RAID1) make me extremely nervous; I'd rather loose the contents of a single drive with a failure, than have ALL data gone.  also, if this can be done, could it be done with RAID1 sets?  (basically, i'm looking for something like unRAID, but dont want to build a dedicated file server--being a college student, this is impractical)

i would try to test this myself, but i dont have any spare hard drives lying around, and dont have convenient access to an Ubuntu machine.

now, i've tried searching for my answers using the almighty google, but if somehow i've missed something obvious, a link would be highly appreciated

edit:  i apologize if this thread would be better placed in another section.  I did not really see anything that seemed suitable

---

### Post by ttoilleb on 2011-05-20
I have used the following link with 8.04 to 10.04.  Works for LVM2

[http://www.howtoforge.com/linux_lvm](http://www.howtoforge.com/linux_lvm)

Good luck

---

### Post by Drak3 on 2011-05-21
Thanks a bunch!  pretty much looks exactly like what i was looking for!

---

