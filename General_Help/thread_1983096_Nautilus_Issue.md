---
title: "Nautilus Issue?"
date: 2012-05-19
forum: General Help
---

### Post by uRock on 2012-05-19
I find myself not being able to cut/copy/move files on my desktop via right clicking in 12.04. Has anyone ran into and found a fix to this issue?

---

### Post by uRock on 2012-05-27
This is still and issue for me. Any suggestions would be great.

---

### Post by gimcrack on 2012-05-27
Run Nautilus as root.

Open Terminal and type: gksudo nautilus

You can even do this:

Create an Application Shortcut to Open Nautilus as Root in Ubuntu
[http://lifehacker.com/5596006/create-an-application-shortcut-to-open-nautilus-as-root-in-ubuntu](http://lifehacker.com/5596006/create-an-application-shortcut-to-open-nautilus-as-root-in-ubuntu)

---

### Post by mc4man on 2012-05-27
To d.check - there has been a long standing bug in 12.04 where the mentioned context items can appear greyed out but are functional if you go ahead and use them anyway. Is this the case here or are they actually unusable?

---

### Post by uRock on 2012-05-27
> **mc4man said:**
> To d.check - there has been a long standing bug in 12.04 where the mentioned context items can appear greyed out but are functional if you go ahead and use them anyway. Is this the case here or are they actually unusable?

Thank you for posting. Same problem here. Being Mr. Naive I had not tried clicking the greyed out options, but I just did and they do still work. 

Thanks again for posting this.

---

### Post by mc4man on 2012-05-27
I 1st. reported back in Feb. but someone came along & made the bug  report a mess so sorta abandoned it
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/933744](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/933744)

Re-opened & currently active here though a solution that doesn't break something  elsewhere isn't in site yet
[https://bugs.launchpad.net/ubuntu/precise/+source/gtk+3.0/+bug/973491](https://bugs.launchpad.net/ubuntu/precise/+source/gtk+3.0/+bug/973491)

---

### Post by uRock on 2012-05-27
Thanks. Clicked "effects me". Hopefully they get it fixed.

---

