---
title: "Additional drivers are there without installing them..."
date: 2011-02-09
forum: General Help
---

### Post by victor-be on 2011-02-09
Hello

I have a question regarding "additional drivers" that we can find in System > Preferences.

I have recently make a fresh install of Ubuntu 10.10 64 bits on my Asus laptop after  having erased the former Ubuntu that was there. To be precise i have booted on a live USB stick, deleted the 2 old Ubuntu partitions (swap and home) and made a fresh install at the same place on the hard disk.

As I make music with my PC, i want a preemt kernel; so I have downloaded the latest stable kernel on [http://www.kernel.org]("http://www.kernel.org") (the 2.6.37 kernel), changed a few parameters (to meet the preemt kernel characteristics), and i didn't make any **make oldconfig** (i just took it as it is), then I compiled and installed the new kernel. Everything went fine, and I could boot on it without problem.

So I didn't install **ANY** additional drivers, *nothing* else than the recommended updates of Ubuntu and the new compiled kernel, and when I go to **System > Preferences > additional drivers**, the top of the window says : "**No proprietary drivers are in use on this system**", which is consistent with what i said. However, in the list downstairs I have several drivers that seem activated! (such as Raw serio driver, driver for PCI OHCI IEEE 1394 controllers, Atheros 1000M Ethernet Network driver...) (see attached picture); in total there 15 of them without i asked anything...

2 questions : 

1) are they really proprietary drivers or not?

2) I had installed a meta package of proprietary drivers on the preceding version of Ubuntu (the Ubuntu that I have erased to install the new one); is it possible that "traces" of it remain on the hard drive and then "come back" on the new Ubuntu? I have seen something similar : on another PC, i have erased and reinstalled a new Ubuntu. Right after reinstall, i have found, in the network manager, the trace of wireless network i was connected to... 3 days before that... So somehow there was a trace of it that was kept on the laptop...

I know it possible to recover information that were deleted from the hard drive; so it could make sense, but i don't know at all to what extent... on the other hand it is important for me to know if i'm running proprietary drivers or not...

Thank you for your help

---

