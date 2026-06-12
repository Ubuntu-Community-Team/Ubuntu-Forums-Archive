---
title: "CPU 100% and Fan"
date: 2010-06-17
forum: General Help
---

### Post by avantgardaclue on 2010-06-17
Upgraded from 8.04 LTS which has been utterly reliable, to 10.04.

Has this been a mistake? Hmmm, we'll see!

Anyhow, all seems relatively ok, and then the fan starts whirring and the system monitor shows CPU usage at or near 100%. If I shut down everything it still carries on. What is going on??

Pictures are worth a lot more than my words...

[IMG]http://i393.photobucket.com/albums/pp13/ruddermanuk/watches/Screenshot.png?t=1276770985[/IMG]

[IMG]http://i393.photobucket.com/albums/pp13/ruddermanuk/watches/Screenshot-1.png?t=1276771020[/IMG]

[IMG]http://i393.photobucket.com/albums/pp13/ruddermanuk/watches/Screenshot-3.png?t=1276771055[/IMG]

Why should I have 2 CPUs? 

[IMG]http://i393.photobucket.com/albums/pp13/ruddermanuk/watches/Screenshot-2.png?t=1276771099[/IMG]

Thanks for any help, pointers, solutions etc etc!

---

### Post by gradinaruvasile on 2010-06-17
There is a bug filed of this:

[https://bugs.launchpad.net/ubuntu/+source/checkbox/+bug/556636](https://bugs.launchpad.net/ubuntu/+source/checkbox/+bug/556636)

What happens if you kill that process? Is this happening all by itself?

sudo killall -9 backend


PS. I would say to reinstall the system - there are many changes from 8.04 to 10.04 so the upgrade process may not work as expected.

---

### Post by avantgardaclue on 2010-06-17
Tried doing a new install.... but the cd or cd drive reported an error. So i installed the iso to a flash drive which installed without error.

We'll see how things go. Thanks.

Next thing to suss is to get the speakers working, but that'll be another day.

cheeeers

---

