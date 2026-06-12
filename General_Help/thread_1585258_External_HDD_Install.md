---
title: "External HDD Install"
date: 2010-09-30
forum: General Help
---

### Post by jinba.ittai on 2010-09-30
I want to setup my External HDD with multiple operating systems on it. My first question is, If i am running an AMD box at home, will my External drive boot on an intel machine some where else? 

Second; How would i go about installing them on my external?

---

### Post by oldfred on 2010-09-30
Ubuntu only has 32bit & 64bit differences. Both AMD & Intel 32bit work with the 32bit version and same with the 64bit version. 

Your biggest issue will be video cards. You can install a generic driver but then may not have the best video. You can edit the video parameter on a boot that may help:

Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
    * Older Intel video card: i915.modeset=1 or i915.modeset=0
    * nVidia: nomodeset
    * Generic: xforcevesa
    * Radeon: radeon.modeset=0

use the uvesafb to fix all the problems
[http://idyllictux.wordpress.com/](http://idyllictux.wordpress.com/)

One user created a little script:
Create Portable Ubuntu for 2 different Video Cards - script
[http://ubuntuforums.org/showthread.php?p=8107778](http://ubuntuforums.org/showthread.php?p=8107778)

Besure to install grub2 to the external drive:
Advanced button
[http://members.iinet.net.au/~herman546/p24/022f.png](http://members.iinet.net.au/~herman546/p24/022f.png)
Dual boot 2 drives, windows & Lucid 10.04
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

---

### Post by jinba.ittai on 2010-10-03
> **oldfred said:**
> Ubuntu only has 32bit & 64bit differences. Both AMD & Intel 32bit work with the 32bit version and same with the 64bit version. 

Your biggest issue will be video cards. You can install a generic driver but then may not have the best video. You can edit the video parameter on a boot that may help:

Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
    * Older Intel video card: i915.modeset=1 or i915.modeset=0
    * nVidia: nomodeset
    * Generic: xforcevesa
    * Radeon: radeon.modeset=0

use the uvesafb to fix all the problems
[http://idyllictux.wordpress.com/](http://idyllictux.wordpress.com/)

One user created a little script:
Create Portable Ubuntu for 2 different Video Cards - script
[http://ubuntuforums.org/showthread.php?p=8107778](http://ubuntuforums.org/showthread.php?p=8107778)

Besure to install grub2 to the external drive:
Advanced button
[http://members.iinet.net.au/~herman546/p24/022f.png]("http://members.iinet.net.au/%7Eherman546/p24/022f.png")
Dual boot 2 drives, windows & Lucid 10.04
[http://members.iinet.net.au/~herman546/p24.html]("http://members.iinet.net.au/%7Eherman546/p24.html")
Thanks! got everything i needed done!

---

