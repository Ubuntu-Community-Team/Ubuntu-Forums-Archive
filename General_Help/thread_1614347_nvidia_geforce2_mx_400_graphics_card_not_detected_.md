---
title: "nvidia geforce2 mx 400 graphics card not detected in ubuntu"
date: 2010-11-05
forum: General Help
---

### Post by diordz on 2010-11-05
guys..help me with this problem..i have a nvidia graphics card in my computer but not detected by the ubuntu 10.10. when i open the system >>administrator>>additional drivers, it just show that no proprietary drivers installed in the system..i'm newbie to ubuntu, please help me guys.

my computer specs:
board: asrock m266a
512 pc3200 RAM
pentium 4 procesor
40G HD
nvidia geforce2 mx 400 graphics card

---

### Post by 3Miro on 2010-11-05
Try going to System -> Admin -> Synaptic Package Manager and when it open select "Reload". This will refresh the package database with all the software. Hopefully this will solve the problem.

---

### Post by yetiman64 on 2010-11-05
And while in synaptic do a search for nvidia-current-modaliases, I have noted with some installs that if missing or if only other modaliases are installed, newer nvidia cards wont show up in Hardware drivers but do so after installing that package.

Edit: I misread your question and was thinking about the newer GT series of nvidia cards, this may not apply.
You may have to look up the relevant modaliases package that supports your card.

Edit 2: After some searching, it appears you will need to check for the nvidia-96-modaliases see this [--LINK--.]("http://www.nvidia.com/object/IO_32667.html")

Also here is another [--link--]("http://blog.martinsladek.com/2010/07/linux-nvidia-legacy-geforce2-96.html") for using a legacy card (GeForce2 MX400) in 10.04 which may be of some help.

---

