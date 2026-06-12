---
title: "Problem with update to 2.6.28-17-generic"
date: 2009-12-19
forum: General Help
---

### Post by mediax on 2009-12-19
The update from 2.6.28-16-generic to 2.6.28-17-generic (on 9.04 Jaunty) left me with a system that wouldn't even boot into a command line. I've been running off the previous version with no problems, but I'm now wondering how this will affect future updates, and whether it's worth trying to rerun the update.

If I were to have another crack at installing 2.6.28-17,presumably I'd need to uninstall the existing version of 2.6.28-17 to get the update to run again?  Is there an uninstall utility somewhere, or would it be a case of deleting files manually?

Thanks in advance.

---

### Post by coffeecat on 2009-12-19
> **mediax said:**
> 
If I were to have another crack at installing 2.6.28-17,presumably I'd need to uninstall the existing version of 2.6.28-17 to get the update to run again?  Is there an uninstall utility somewhere, or would it be a case of deleting files manually?

Thanks in advance.

Simply go to Synaptic and mark all the 2.6.28-17 files for reinstallation. Alternatively, mark them for 'complete removal' which will delete the downloaded packages that are stored in /var/cache/apt/archives as well as all the installed files. Then, when you do the update again, the packages will be re-downloaded.

A question. I haven't used Jaunty for some time, so I'm not familiar with where the kernel has got to in 9.04. Was 2.6.28-17 a regular update, or have you enabled the proposed repository? The reason I ask is that I haven't seen a snowstorm of threads about a Jaunty kernel update, and updates from the proposed repository are a common cause of breakages.

---

### Post by mediax on 2009-12-19
> **coffeecat said:**
> A question. I haven't used Jaunty for some time, so I'm not familiar with where the kernel has got to in 9.04. Was 2.6.28-17 a regular update, or have you enabled the proposed repository? The reason I ask is that I haven't seen a snowstorm of threads about a Jaunty kernel update, and updates from the proposed repository are a common cause of breakages.

Thanks for that.  I don't have the proposed repository enabled (bit too adventurous for me :lolflag:) - 2.6.28-17 was a regular update.

---

### Post by coffeecat on 2009-12-19
> **mediax said:**
>   I don't have the proposed repository enabled

Good for you! :)

Good luck with the re-install.

---

