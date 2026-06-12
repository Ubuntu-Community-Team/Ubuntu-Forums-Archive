---
title: "synaptic package manager closes immediately in ubuntu 11.10"
date: 2011-11-17
forum: General Help
---

### Post by virtdave@mcn.org on 2011-11-17
I installed synaptic package manager, and it closes after opening for an instant.  I tried opening it with sudo synaptic in a terminal, and I get the message 
terminate called after throwing an instance of 'std::out_of_range' 
  what():  vector::_M_range_check

---

### Post by oldos2er on 2011-11-17
See this thread: [http://ubuntuforums.org/showthread.php?t=1861313](http://ubuntuforums.org/showthread.php?t=1861313)

---

### Post by virtdave@mcn.org on 2011-11-17
thanks, it works....your link eventually leads to the following link:
[https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/839219/comments/16](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/839219/comments/16)
which suggests toggling the screen reader on and off again....I suppose a future update will make this workaround unnecessary, but for now, doing this is not too onerous.

---

### Post by bmcm387 on 2012-01-08
wow that worked thanks alot

---

### Post by osarusan on 2012-03-04
I had the same problem here, and had to disable my onscreen keyboard... what gives?? So people who need accessibility options can no longer use synaptic?? I hope they fix this bug soon...

---

