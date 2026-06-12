---
title: "Many sh-zombies after upgrade to Precise"
date: 2012-04-29
forum: General Help
---

### Post by apochry on 2012-04-29
Hello,

after upgrading from Oneiric to Precise I have a strange issue with a lot of 'sh-zombies' displayed under Processes in my system monitor. I can not end or kill them, nothing happens. It is not a big problem since they cause no cpu or memory usage, but it is still strange and kind of annoying. With the time the system is up they become more and more.
Here is a screen shot after ~24 hours of up time:

[IMG]http://dl.dropbox.com/u/21440680/sh-zombies.png[/IMG]

Maybe someone would have an idea what is this all about... or how to get rid of these zombies.

Thanks,
Christo

---

### Post by apochry on 2012-04-30
](*,) ...bump

---

### Post by apochry on 2012-05-02
No one has any idea or the same issue after an upgrade, really??? :(
Well, I guess I can leave with that until I decide to try some cool stuff, that I see on the forum, brake the system and that do a clean install.
I'm giving up on that.

Cheers!

---

### Post by michalt on 2012-05-04
I have same issue after upgrade. After startup I have no sh-zombies but their number is growing gradually. I'm tring to figure out which app or service is the culprit.

---

### Post by michalt on 2012-05-10
Found that my sh-zombies were created by failed tomboy synchronization with ubuntu one server. There is some problem with tomboy synchronization addin.

---

### Post by fozturk on 2012-05-28
I have the same issue with Ubuntu 12.04 on dell latitude e5520m. 
I have seen that it is related to synchronization. 
There is a bug report for this problem:
[https://bugs.launchpad.net/ubuntu/+source/tomboy/+bug/956893]("https://bugs.launchpad.net/ubuntu/+source/tomboy/+bug/956893")

---

