---
title: "How do I share upgrades between machines"
date: 2010-09-30
forum: General Help
---

### Post by ki4jgt on 2010-09-30
I don't want to consume so much bandwidth. I've tried apt-catcher, aptitude says there's no such program available. What next?

---

### Post by spiky001 on 2010-09-30
have a look at apt oncd

---

### Post by sikander3786 on 2010-09-30
[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

You can also setup a local apt-mirror.

[http://www.howtoforge.com/local_debian_ubuntu_mirror](http://www.howtoforge.com/local_debian_ubuntu_mirror)

---

### Post by ki4jgt on 2010-10-02
Is there something a little more user friendly? APTONCD is kind of pointless when you're doing a distro upgrade, and apt-mirror is kind of complex. Don't get me wrong, I'll take what I can get, but I just don't like messing with system settings much.

---

### Post by sikander3786 on 2010-10-03
You can also use Keryx.

[http://keryxproject.org/](http://keryxproject.org/)

---

### Post by ki4jgt on 2010-10-03
Thanks

---

### Post by Elfy on 2010-10-03
There's nothing wrong with just copying the packages from the apt cache.

---

### Post by ki4jgt on 2010-10-03
Tell me how and I'll love you forever and follow you around like a puppy :-)

---

### Post by Elfy on 2010-10-03
I have run nautilus as root - gksudo nautilus - navigate to /var/cache

copy archive to whatever you want to copy it to - open nautilus on the other machine (as root again) copy the cache over and do an apt-get update.

Obviously if one machine needs a package the other doesn't it will need to go get it - but it should remove a lot of duplication

Works for me ;)

Though I will also say that when I had all my machines here up and running with the same version apt-cacher-ng worked well [http://ubuntuforums.org/showthread.php?t=981085](http://ubuntuforums.org/showthread.php?t=981085)

---

