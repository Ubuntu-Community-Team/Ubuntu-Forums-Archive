---
title: "Dual boot from an SSD with Hard Drive for data?"
date: 2011-11-18
forum: General Help
---

### Post by natpat on 2011-11-18
Hey,
I've finally got all the parts for my new build ready, including a 64GB SSD and a 1TB HDD. On my previous laptop, I dual booted Ubuntu and 7, and would like to still do this - however, I would like both OSes to be on the SSD for speed, with the data and programs stored on the HDD.

Is this possible, and if so, what's the easiest way of doing this?

Thanks :)

---

### Post by Lars Noodén on 2011-11-18
Make the partitions for /home and /usr on the HDD, if that is what you want.  /home is where the data goes and /usr is where most of the programs go.  You can get a full overview of what goes where by looking at [hier](http://manpages.ubuntu.com/manpages/precise/en/man7/hier.7.html).  Myself, I'd put all the programs on the SSD, too, and just leave only the data on the HDD  The whole system is unlikely to go over 12GB.

---

### Post by Seq on 2011-11-18
> **Lars Noodén said:**
> Make the partitions for /home and /usr on the HDD, if that is what you want.  /home is where the data goes and /usr is where most of the programs go.  You can get a full overview of what goes where by looking at [hier](http://manpages.ubuntu.com/manpages/precise/en/man7/hier.7.html).  Myself, I'd put all the programs on the SSD, too, and just leave only the data on the HDD  The whole system is unlikely to go over 12GB.

A large portion of the OS boot sequence is from /usr, so there would be extremely little advantage to having the root, but not /usr on an SSD.

In my laptop, my primary drive is a 60G SSD, and my secondary drive is a large HDD. I have root and /home on the SSD, and made a /mnt/storage and swap on the larger drive. Have not had any trouble.

My root partition sits at about 6G at most, and I've allocated 10 for it.

---

### Post by natpat on 2011-11-18
Would setting up the dual boot on the SSD be the same as doing it on an HDD? I've never really used an SSD before.

---

### Post by LowSky on 2011-11-18
> **natpat said:**
> Would setting up the dual boot on the SSD be the same as doing it on an HDD? I've never really used an SSD before.

yes. Source = my SSD.

---

