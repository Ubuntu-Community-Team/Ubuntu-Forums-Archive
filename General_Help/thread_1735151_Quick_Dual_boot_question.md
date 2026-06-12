---
title: "Quick Dual boot question"
date: 2011-04-21
forum: General Help
---

### Post by bryanftw on 2011-04-21
Making sure I have everything correct before I take another try at dual booting.
1. Ill be making another partition on my main HDD ~30 gigs for windows. This should be formated as ntfs right?
2. After I install windows I have to re install grub and what not. I found this [guide ]("http://ubuntuforums.org/showthread.php?t=1014708")

That should be it right? Assuming everything goes correctly. Im running 10.04 if that matters.

---

### Post by ububeginner on 2011-04-21
Hi there

1. yes, Windows partition should be ntfs, you could also leave the partition as unallocated and Windows will format it.
2. Don't know about this guide you link to

Just make sure you got a clean windows DVD/CD
Many of the DVD/CDs that come with preinstalled systems, or the user is required to burn themselvs after buying the system, will run a semi unattended installation giving the user no controll over the partitioning of the drive. These DVD/CDs will wipe your entire drive.

---

### Post by Mark Phelps on 2011-04-21
> **ububeginner said:**
> ... you could also leave the partition as unallocated and Windows will format it.

This is actually the better option -- as Win7 tends to be picky about NTFS formatting details.  Better to let IT do the formatting as part of the OS install.

---

