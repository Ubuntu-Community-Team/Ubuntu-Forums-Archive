---
title: "nVIDIA boot agent?"
date: 2012-03-19
forum: General Help
---

### Post by kumoshk on 2012-03-19
Somehow, I have an nvidia boot agent that tries to boot something (for a long time, and fails) before grub will speedily and successfully boot. Any ideas on how to get rid of this?

(I'm using Debian instead of Ubuntu, this time, though. I just did a clean install. Maybe it left something on the MBR instead of replacing it, since I seem to remember seeing that boot agent before, once.)

Would installing Ubuntu on my other partition fix this? (And, can Debian and Ubuntu run side-by-side? I seem to remember that multiple Ubuntu installations caused issues, at least.)

---

### Post by 2F4U on 2012-03-19
Are you saying that this agent appears before the grub boot screen? Then it may be something belonging to the BIOS. I would check the BIOS settings if it can be turned off.

Debian and Ubuntu can run side by side, as much other Linux distributions can. The distributions are running on separate partitions and therefore shouldn't influence each other. It may be something different if you want to have a common home partition.

---

### Post by kumoshk on 2012-03-19
Ah, 2F4U, you were quite correct. Thank you. It seems to have been because of some network boot thing being enabled (which was also listed in the boot order). I think the boot agent was trying to boot Vista (which has been absent for years, backup partition and all).

I'll have to try out the dual-boot. I'm not sure if I was using the same home directory when I tried to install multiple Ubuntus, but I guess there's a strong possibility. I generally like to have them on multiple partitions. This time, however, I'm having it all on root with a separate (non-home) partition for storage, and I plan to use symbolic links to it for the folders of my media and stuff (then I can get it all on one partition, still, and save memory).

Off-topic:
Just a plug for Debian here (as a first-time user, after years of primarily Ubuntu and secondarily other stuff): suspend and my microphone work out of the box (plus, it's faster than I thought possible with Gnome, and it uses the pre-Unity version, which I prefer, and have missed). Suspend working is a first for me, and I'm quite excited to use it regularly (and I've tried a lot of Linux distributions, which have all failed there). I used the business card install where everything is downloaded during installation.

I figure since Ubuntu is Debian-based, plugs for Debian shouldn't be too off-color. Are they?

---

