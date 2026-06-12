---
title: "VERY extended chroot"
date: 2005-01-26
forum: General Help
---

### Post by TravisNewman on 2005-01-26
OK I'm about to ask a question that may not go here, but I can't really decide where it should go, I don't think there's a good place for it.

I get very quixotic with my PC, some of you already know this... anyway:

I'm wondering if it's possible to have, for example (though I don't intend to do it like this, just using two separate distros to simplify things) Ubuntu installed in one partition, and Fedora installed on another. I know I can chroot into Fedora from Ubuntu, but that keeps the kernel from Ubuntu, and I can't really figure out how to open an xserver from Fedora, on a different virtual terminal OR in an xnest, if it's possible. So basically here's what I'd like to do, and feel free to laugh if this is completely ridiculous...

On startup of Ubuntu, not only would it start up GDM for Ubuntu, but it would chroot into the Fedora partition and start up its GDM on another VT. So I can hit Ctrl+alt+F7 to get to Ubuntu, and Crtl+Alt+F8 to get to Fedora.

IDEALLY I'd like to be able to run different kernel versions for each but I'm almost positive that's impossible. For that matter, I'd also like to be able to reboot them separately, like leave Fedora going while I reboot Ubuntu, even though I first booted up in Ubuntu, but again, I know that's insane.

I also really don't know the specifics about reprobing modules like the nvidia driver, etc.

I'd use VMWare or something like that, but the performance hit is insane with VMWare and other emulators like it.

No, I don't want to use Fedora, I want to have a testing chroot of Ubuntu that I don't mind completely screwing up, but using Fedora as an example would be clearer than saying Ubuntu 1 or Ubuntu 2 or whatever.

---

### Post by TravisNewman on 2005-01-27
OK I've figured out a lot since I posted this. I was using this reference:

[http://www.debian.org/doc/manuals/reference/ch-tips.en.html#s-chroot](http://www.debian.org/doc/manuals/reference/ch-tips.en.html#s-chroot)

However, the parts about setting up virtual terminals for CLI and GDM sessions don't seem to work for me at all. If anyone can clue me in I'd greatly appreciate it.

---

### Post by jdong on 2005-01-27
Ok, chrooting and changing kernels is IMPOSSIBLE -- you'd need Usermode Linux or another virtualization layer to do so.

As far as starting X from a chroot, You need to:

```

mount -t proc none /chroot/proc
mount -o bind /dev /chroot/dev
mount -o bind /tmp /chroot/tmp

```

---

### Post by TravisNewman on 2005-01-27
OK I've gotten vt8 to be the CLI login for Debain Sid (using the example given in the documentation just to learn). I can startx, as long as GDM isn't running in Ubuntu, but even if GDM isn't running anywhere, I can't use GDM in Sid for some reason. What I was hoping to achieve (and what the documentation I referenced above said was possible I thought) was to be able to hit ctrl+alt+f7 to get to graphical hoary and ctrl+alt+something(I guess f9) to get to, in this case, graphical Sid. IS this possible?

BTW Documentation on the web for this is less than spectacular, but if you've got any references that could get me going, I'm all ears...er... eyes.

---

### Post by TravisNewman on 2005-01-27
OK I'm very stumped here. You'd think that setting GDM to auto allocate vt's and setting the first vt to an unused one would work, but it doesn't. I really really don't get it.

---

### Post by RavenOfOdin on 2006-07-18
(EDIT: Never mind, I didn't see the forum section I was putting this post under, someone please delete this. :D)

---

