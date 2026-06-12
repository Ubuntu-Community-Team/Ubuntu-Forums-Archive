---
title: "Help with windows/ubuntu"
date: 2009-10-27
forum: General Help
---

### Post by sticks360 on 2009-10-27
I need to know if it is possible to restore/repair windows on a laptop without a cd/dvd rom? IF so how? My laptops dvd drive stoped working a few days before, and needs replaced. I was running ubuntu, with the windows folder opened, and left the house for a while. When I got home I found a friends 2 year old messing with it, and windows hasn't booted sence.

If its not possible, how could I reformat the windows dirve, and reformat it so ubuntu can use it? Can I combine the 2 partitions? How?

Thanks a ton.

---

### Post by XDevHald on 2009-10-27
Hmm, if you're needing help with Windows then you will need to speak with them as this is for Ubuntu. Second question about combining two partitions is possible, I am running Ubuntu with dual boot on Windows XP for my wife.

Here's a guide on dual booting Ubuntu and Windows XP: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by fluffman86 on 2009-10-27
I haven't tried this, but perhaps unetbootin (available for Ubuntu) could create a bootable USB drive from a Windows ISO.  Otherwise, you'd need either a new CD drive for your laptop, or an external USB CD Drive.

As for wiping your windows partition, use gparted (available in synaptic).  Just delete your old windows partition, move the slider for your /home or / partition to expand over it, and hit OK.  :)

---

