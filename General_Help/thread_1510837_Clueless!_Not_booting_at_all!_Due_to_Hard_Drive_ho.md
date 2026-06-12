---
title: "Clueless! Not booting at all! Due to Hard Drive hopping?"
date: 2010-06-16
forum: General Help
---

### Post by aquanav on 2010-06-16
Hi!

I am in a messy situation with my ubuntu OS! I have ubuntu installed alongside windows. Due to a hardware issue in the motherboard (which turned out to be a faulty SMPS), I removed the hard drive and mounted it on to another PC. I booted the hard disk and used the ubuntu OS as it were in my PC earlier (worked seemlessly, until)...

I noticed a hardware upgrade saying an NVIDIA card was detected and ubuntu was going to download the driver. I gave a go ahead, and the system worked great after the upgrade (tried playing some games, worked great!)

My original PC was back after repairs, so mounted the hard disk back into the old PC. Now, WIndows works fine, but ubuntu doesn't! It gives an error saying the graphics card is either not found, connected properly or faulty. DO you want to load ubuntu on low graphics, or reconfigure, or troubleshoot etc. I tried all options, but none worked. Any clue how to sort this out?

---

### Post by dcstar on 2010-06-16
> **aquanav said:**
> Hi!

I am in a messy situation with my ubuntu OS! I have ubuntu installed alongside windows. Due to a hardware issue in the motherboard (which turned out to be a faulty SMPS), I removed the hard drive and mounted it on to another PC. I booted the hard disk and used the ubuntu OS as it were in my PC earlier (worked seemlessly, until)...

I noticed a hardware upgrade saying an NVIDIA card was detected and ubuntu was going to download the driver. I gave a go ahead, and the system worked great after the upgrade (tried playing some games, worked great!)

My original PC was back after repairs, so mounted the hard disk back into the old PC. Now, WIndows works fine, but ubuntu doesn't! It gives an error saying the graphics card is either not found, connected properly or faulty. DO you want to load ubuntu on low graphics, or reconfigure, or troubleshoot etc. I tried all options, but none worked. Any clue how to sort this out?

Boot from a Live CD, mount **the Ubuntu partition on the hard drive** and delete the /etc/X11/xorg.conf file.

---

### Post by aquanav on 2010-06-16
thanks dcstar. But I'm getting an error message that says permission denied. This what I did:

[LIST=1]
[*]Booted with LIVE CD
[*]entered terminal
[*]command: sudo mount /dev/sda7 /mnt
[*]then gave this command: rm /mnt/etc/X11/xorg.conf
[*]Asked for a confirmation
[*]got a error saying permission denied
[/LIST]
Any other way to workaround?

---

### Post by aquanav on 2010-06-16
dcstar! I tried the same sequence again, and it worked! Successfully booted ubuntu again :)

Thanks a ton!

---

