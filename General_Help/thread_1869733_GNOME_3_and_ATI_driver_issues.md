---
title: "GNOME 3 and ATI driver issues"
date: 2011-10-26
forum: General Help
---

### Post by telekipper on 2011-10-26
I've been using Ubuntu for 4 years now and I'm finally stumped enough to join the boards and ask a question. I couldn't get a straight answer from searches, so here I go.

I made the switch on one of my machines to 11.10 so I could give Gnome Shell a try. I wasn't so big on Unity and was looking forward to the switch up. I've since been using my other machine with Pinguy to search for answers.

I'm encountering the apparently common problem of my AMD/ATI drivers being incompatible with Gnome 3. I've tried uninstalling the fglrx/Radeon/nvidia and replacing it with the updated ATI through the terminal. I've essentially used [this method]("http://linux-software-news-tutorials.blogspot.com/2011/10/ubuntu-1110-oneiric-problems-with-ati.html") with the only error I noticed being this:

cryptsetup: WARNING: failed to detect canonical device of /dev/sda1
cryptsetup: WARNING: could not determine root device from /etc/fstab

It now boots up, the screen goes distorted, then black, and I have to restart or move into terminal. I can still access it by booting in safe graphics mode to work on it.

I'm kinda over it at this point unless someone can see whats going on here with a simple fix. For now I'm wondering if I can just restore my xorg.conf to what it was and start off fresh from where I was. Is this an option? Maybe I can wait to try Gnome Shell when it's a bit easier for me. I prefer to USE my OS rather than spend all of my time tweaking it. I'm also pretty open minded to new distributions at this point. 11.10 was unimpressive even before these troubles. Thanks in advance.

---

### Post by telekipper on 2011-10-27
Nevermind. Did a fresh install of Mint. I'll wait for stability to try Shell

---

### Post by oldtimer7777 on 2011-10-27
> **telekipper said:**
> Nevermind. Did a fresh install of Mint. I'll wait for stability to try Shell

I've always found ATI drivers to be a pain in linux.. It is better to use something else for a video card if you can swap it out.

---

### Post by typhoon_tip on 2011-10-27
It is a known bug in ATI driver. There is a proposed update already in queue in Ubuntu 11.10. I have the same issues.

If you want to try out Gnome 3 in Ubuntu, you can do a fresh install and use the stock ATI driver, which should provide enough 2D acceleration and 3D openGL for Gnome 3 to work (it works on my HD Radeon 3400 and Lenovo T400 laptop).

---

