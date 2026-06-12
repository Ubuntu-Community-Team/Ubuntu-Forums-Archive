---
title: "can't update Ubuntu"
date: 2012-04-18
forum: General Help
---

### Post by mulceber on 2012-04-18
A few days ago, I was trying to create a desktop slideshow and so I tried to download crebs (which I now realize is ridiculously out of date) using the terminal. It didn't work and so I gave up. Unfortunately, now, whenever I try to check for updates on the update manager, I get the following error message:

```
W:Failed to fetch http://ppa.launchpad.net/crebs/ppa/ubuntu/dists/oneiric/main/source/Sources  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/crebs/ppa/ubuntu/dists/oneiric/main/binary-amd64/Packages  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/crebs/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.
```Could anyone give me advice on how to remove the crebs files I have, or in some way to fix this error?

Thanks,            -M

---

### Post by drs305 on 2012-04-18
There are several ways you can 'fix' this.

One way is to use Ubuntu Tweak, a handy app that can accomplish a variety of system tweaks. One is to cleanup PPAs. 
[http://ubuntu-tweak.com/]("http://ubuntu-tweak.com/")
The link takes you to a professional-looking site but the app is free.

Another way is to edit your sources list. You can do this via the Ubuntu Software Center. Open it and from the menu select Edit > Software Sources and click the Other Software tab and deselect the PPAs you no longer want.

---

### Post by mulceber on 2012-04-18
I tried the third option and it worked like a charm. Thank you!

---

