---
title: "Installing 10.04 and seems to hang at 95%"
date: 2010-05-05
forum: General Help
---

### Post by Paddy Landau on 2010-05-05
I had Xubuntu 9.10 on a fairly old computer, which I had installed without any hassle. It ran well, very much faster than the Windows XP that it used to have.

I downloaded Xubuntu 10.04 (checking the MD5 sum), and put it onto CD (and ran the CD check). The Live CD ran perfectly fine on the computer.

After doing a full backup, I completely wiped the drive and started to install Xubuntu 10.04. The installation is s-l-o-w. It's been three hours already!

About an hour ago, the installation hit 95% ("Running dpkg"). It seems to have stopped. The computer does respond, but so slow that it takes a few seconds for the mouse to respond. The hard drive is running continuously. Once, I noticed the CD being accessed briefly, but otherwise the CD seems to be unused.

Any ideas? Should I just wait a few more hours for it to progress past 95%, or has something gone wrong? I don't remember 9.10 taking so long to install, and it doesn't seem likely that it needs over three hours to do a fresh installation -- unless the dpkg is uploading and installing lots of upgrades.

---

### Post by Paddy Landau on 2010-05-05
Hmm, I just realised that I started over five hours ago. It's still sitting on 95%. So, I'm going to cancel the installation and try again.

---

### Post by Seal Daemon on 2010-05-05
If it doesn't go through, switch to the second tty window and see why it does so.

---

### Post by Paddy Landau on 2010-05-05
Thanks, I wouldn't have thought of that.

I've restarted, and this time it seems (so far) to be running way faster; only 7 minutes, and already at 46%.

If it gets stuck again, I'll post again to ask you how to find out why it does so.

---

### Post by Paddy Landau on 2010-05-05
Well, only 27 minutes later and it's installed.

I changed two things:

The first time (which hung), I booted into "Try Xubuntu", connected to the wireless (to test), and then clicked the "Install Xubuntu" icon.

The second time (which worked), I disconnected the wireless (it's a USB dongle) and booted straight into "Install Xubuntu".

I hope that helps anyone else with this problem.

---

### Post by weematt on 2010-05-14
I had this bug (95% done installing "running dpkg" and it seeming to not be getting anywhere for 15+ mins.  I started googling the problem, but while reading this post it sorted itself out.  The answer here might just be patience (at least in some cases)...the "ubuntu is almost done installing" message made me think it was having a hard time installing for some reason...

FYI

---

### Post by Rich930 on 2010-05-15
i'm having this problem atm.
going to reboot and "try ubuntu", then install it

---

