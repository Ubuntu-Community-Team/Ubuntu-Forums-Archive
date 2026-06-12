---
title: "Kernel update to 2.6.32-26 creates problems"
date: 2010-12-02
forum: General Help
---

### Post by JKyleOKC on 2010-12-02
Is anyone else having problems with the new 2.6.32-26 kernel and Lucid LTS?

I first installed it several days ago on a test system and it immediately killed VirtualBox, since the header files necessary to rebuild the vbox modules were not included in the update. I installed the header files via Synaptic and everything then worked properly, so this morning I allowed my production system to install the updates.

That was a mistake.

Immediately upon the required reboot, my GUI failed to appear. Eventually I got a CLI login on TTY1, and attempted to use "startx" to launch the GUI. It failed with a message that the nvidia driver could not be found.

Rebooting and choosing the older kernel version cured all the problems, but for now the security update provided by the new kernel is unavailable to me. This is NOT the reliability I have come to expect from Ubuntu's long term support and update notifications!

Has anyone installed these recent updates successfully?

---

### Post by TBABill on 2010-12-02
No I installed the kernel and the updates and have no issues, although I do not run VB. All systems go from my hardware, but perhaps you could just remove the kernel in Synaptic and try again? It could have just been an error in the downloaded file(s) that caused the problem rather than something bigger.

---

### Post by JKyleOKC on 2010-12-02
Interesting!

I installed the linux-headers files via Synaptic while running the old kernel, then re-booted into the new kernel, and now all is working properly again. Apparently the required header files were not included in the update; I don't remember this ever happening before and I've been through a number of kernel updates in the past three years.

Anyway I'm happy again.

---

