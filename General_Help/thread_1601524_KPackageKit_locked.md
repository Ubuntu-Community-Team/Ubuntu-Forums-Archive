---
title: "KPackageKit locked"
date: 2010-10-20
forum: General Help
---

### Post by G. Rodrigues on 2010-10-20
When running KPackageKit to fetch the latest updates, for some reason (I was surfing the web at the same time KPackageKit was running, but other than that and the usual background services, nothing else was running) it went awry and locked. This was a few hours ago. In the meantime I had to leave, so I shutdown as is my practice whenever I am AFK for more than a couple of hours. Upon returning and getting online, I get the usual automatic notice of available updates. Do the usual thing... and KPAckageKit is locked: there is a small dialog window "Waiting for package manager lock" and no visible progress.

Anyone know what this is about and a way to solve it and resume the ability to update / install new software?

Running Kubuntu 10.04 updated (well, updated until yesterday). Feel free to ask for any needed additional information.

TIA, regards,
G. Rodrigues

---

### Post by joshthechamp14 on 2010-10-20
Try this

sudo apt-get install -f

---

### Post by G. Rodrigues on 2010-10-21
> **joshthechamp14 said:**
> Try this

sudo apt-get install -f

It seems to work. Running it, apt-get instructs me to run

sudo dpkg --configure -a

and then running it, KPackageKit is indeed unlocked. Unfortunately, when trying to update the packages, it chokes again in the same way when trying to install the linux kernel package. Grrrr.

Anyway, I am flagging this as solved and will open a new thread asking about this problem.

Thanks for the help, regards,
G. Rodrigues

---

