---
title: "Source list problem (Software center-amnesia)."
date: 2012-08-23
forum: General Help
---

### Post by sebastian.s on 2012-08-23
So when i try to install Amnesia:the dark decent from the software  center, or when i run the ordinary system updates i get this message.

```
W:Failed to fetch  https://private-ppa.launchpad.net/commercial-ppa-uploaders/amnesia/ubuntu/dists/precise/main/binary-amd64/Packages   The requested URL returned error: 401
, W:Failed to fetch  https://private-ppa.launchpad.net/commercial-ppa-uploaders/amnesia/ubuntu/dists/precise/main/binary-i386/Packages   The requested URL returned error: 401
, E:Some index files failed to download. They have been ignored, or old ones used instead.
```I can't install the game.

I'm not sure how to solve this problem, but is has something to do with the repositories for Amnesia.

---

### Post by Laiquendi on 2012-08-23
It seems to be some kind of a new bug (I've seen it with other games from those repositories). Check if you have the proper ones, you may also find this bug in launchpad and add to it's importance by clicking it has also happened to you.

---

### Post by sebastian.s on 2012-08-24
> **Laiquendi said:**
> It seems to be some kind of a new bug (I've seen it with other games from those repositories). Check if you have the proper ones, 

The proper ones? how do i find this out? Should i check if the URI is correct for these repositorys?


> you may also find this bug in launchpad and add to it's importance by clicking it has also happened to you.

Not quite following, do you mean [https://launchpad.net/ubuntu](https://launchpad.net/ubuntu) ?

---

### Post by oldos2er on 2012-08-24
The 401 error means you don't have permission to access that site. You would need to provide login credentials.

---

### Post by sebastian.s on 2012-08-25
Found the solution. :)

[https://help.ubuntu.com/community/Pay/FAQs/Bad_APT_Auth](https://help.ubuntu.com/community/Pay/FAQs/Bad_APT_Auth)

---

