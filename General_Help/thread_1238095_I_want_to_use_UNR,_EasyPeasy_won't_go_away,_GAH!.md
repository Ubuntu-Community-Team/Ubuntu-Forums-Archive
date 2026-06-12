---
title: "I want to use UNR, EasyPeasy won't go away, GAH!"
date: 2009-08-12
forum: General Help
---

### Post by UncannyValleyGirl on 2009-08-12
Hi.  I'm a noob, but capable of following specific directions.  A while back I (and an experienced friend) put easy peasy on my eeePC in place of the Xandros atrocity it came with.   Then it stopped working, full stop. It'd boot up to a black screen. Mkay. Time to go to a grown-up distribution. I got Ubuntu all ready to install, set everything up, ran the installer...  and...  what? Now it boots up to the long lost easy peasy. I do not *want* to use easy peasy. I want to use Ubuntu. How do I make this so, preferably taking easypeasy off in the process? It still runs Ubuntu off the flashdrive if I leave that in, b/c it's set to boot from the drive first, but that's thoroughly impractical for regular use.

---

### Post by dcstar on 2009-08-12
> **UncannyValleyGirl said:**
> Hi.  I'm a noob, but capable of following specific directions.  A while back I (and an experienced friend) put easy peasy on my eeePC in place of the Xandros atrocity it came with.   Then it stopped working, full stop. It'd boot up to a black screen. Mkay. Time to go to a grown-up distribution. I got Ubuntu all ready to install, set everything up, ran the installer...  and...  what? Now it boots up to the long lost easy peasy. I do not *want* to use easy peasy. I want to use Ubuntu. How do I make this so, preferably taking easypeasy off in the process? It still runs Ubuntu off the flashdrive if I leave that in, b/c it's set to boot from the drive first, but that's thoroughly impractical for regular use.

Install and manually select the "Use entire disk" option to wipe what is already there.

---

### Post by bodhi.zazen on 2009-08-12
You should take UNR for a spin (boot it from a live cd / usb) before you install it. On my netboot I found it bloated and so slow it was unusable.

A standard install of Ubuntu is much faster. Fedora 11 is even faster, but fedora does not recognize all my hardware.

---

### Post by UncannyValleyGirl on 2009-08-12
dcstar: That's what I did. Apparently it lives on a different part of the HD, because the memory on this charming thing is a couple of SD cards. The only thing I can think of to do to get rid of easypeasy is to pull out the one that's on, stick in in a cardreader, and delete the whole thing manually.   bodhi.zazen: The netbook remix running off the flashdrive-which is what I have now-is a lot faster than Xandros was (and more usable. And not ugly). Since this is my first serious foray into linuxland I've got a fairly high bloat tolerence I think.

---

### Post by bodhi.zazen on 2009-08-13
Glad it works for you, it is nice they are working on it. My experience was not so good.

Regardless, IMO best to test a new distro.

You can boot from a USB ? If so you can wipe the entire hard drive with dd (just make sure you have the correct device)

dd if=/dev/zero of=/dev/sda

I am assuming your HD is /dev/sda [[COLOR=#980101]****[/COLOR]]("http://ubuntuforums.org/member.php?u=17635")

---

