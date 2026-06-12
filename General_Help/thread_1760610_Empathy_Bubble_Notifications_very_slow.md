---
title: "Empathy Bubble Notifications very slow"
date: 2011-05-17
forum: General Help
---

### Post by xxhopingtearsxx on 2011-05-17
I like the bubble notifications when someone sends me a message.. but they're so slow. If someone sends me a lot of messages in one minute, they'll take a few minutes for a bubble with each message to popup.. and  there's no way to close it and tell it to shut up..

Is there anything I can do about this?

---

### Post by xxhopingtearsxx on 2011-05-17
Bump.

---

### Post by xxhopingtearsxx on 2011-05-19
Bump.

---

### Post by hvbakel on 2011-05-19
This is a known bug, check here for more details: [https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/769234](https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/769234) 
A fix should hopefully be out soon.

---

### Post by xxhopingtearsxx on 2011-05-19
Ugh not fixed? I've had that problem since 9.04.
I wish Canonical would test these applications more.. Pidgin does it as well.

---

### Post by xxhopingtearsxx on 2011-05-19
[http://git.gnome.org/browse/empathy/commit/?id=7078e93bbcd562175248a8fdf752f2fa92f1171c](http://git.gnome.org/browse/empathy/commit/?id=7078e93bbcd562175248a8fdf752f2fa92f1171c)
I hear that fixes it.
But I HAVE NO IDEA what that is.

---

### Post by xxhopingtearsxx on 2011-05-20
Bump.

---

### Post by linuxinstalledfromhdd on 2011-05-20
Try updating it.. 
sudo add-apt-repository ppa:telepathy/ppa
sudo apt-get update && sudo apt-get upgrade



sudo add-apt-repository ppa:telepathy/ppa
sudo apt-get update && sudo apt-get upgrade

---

### Post by xxhopingtearsxx on 2011-05-25
BUMP.

It does it on both Pidgin and Empathy.

---

### Post by hvbakel on 2011-05-25
I've installed the empathy packages from this ppa, which fixes the issue:

[https://launchpad.net/~om26er/+archive/test](https://launchpad.net/~om26er/+archive/test)

Not sure why this hasn't been released officially yet, it's such a simple patch...

---

### Post by xxhopingtearsxx on 2011-05-27
You sure it's safe?
It looks like some random test ppa.

---

### Post by xxhopingtearsxx on 2011-05-27
bump any help?

---

### Post by xxhopingtearsxx on 2011-06-06
Bump.

---

### Post by xxhopingtearsxx on 2011-06-06
Apparently there's a fix now according to 

[https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/769234](https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/769234)

I have absolutely no idea how to get to that fix.

---

### Post by hvbakel on 2011-06-06
Start "ubuntu software center", go to edit=>software sources and then select the tab 'updates'. In this tab, check the box labeled "Pre-release updates (natty-proposed)". After you have done this, you can run the update manager and the empathy packages will be listed there (together with other 'proposed' updates).

---

### Post by xxhopingtearsxx on 2011-06-08
> **hvbakel said:**
> Start "ubuntu software center", go to edit=>software sources and then select the tab 'updates'. In this tab, check the box labeled "Pre-release updates (natty-proposed)". After you have done this, you can run the update manager and the empathy packages will be listed there (together with other 'proposed' updates).

Hey. I did that, and I saw no updates for Empathy on there.

---

