---
title: "Strange problem with Ubuntu"
date: 2010-02-09
forum: General Help
---

### Post by angelbla on 2010-02-09
Hi everyone.
I'm having a strange problem with Ubuntu and I can't find out what's happening.
I installed Ubuntu 9.10 (32 bits) in an external USB HDD. Everything went fine. It installed correctly, creating a user called "ubuntu".

Well, I boot, and log with "ubuntu". Right, everything fine. I install language support and then all updates. After rebooting I install:

- google earth
- stellarium
- ntfsprogs
- partimage
- gparted
- Drivers for my rt73 wifi adapter.
- Maybe something else I don't remember right now.

And then I start having a strange problem everytime I boot.

- I get to the login screen and log in as "ubuntu"
- I start a xterm window.
- I can barely type 2 or 3 characters... and the keyboard stops working immediately. But only in xterm window. I can launch any application and keyboard works fine. No problem. But I'm unable to type anything else in xterm window.
- Then, I'm unable even to finish the process. If I try to close the window ubuntu comes out with a message saying the process doesn't respond and I have to kill it (the window disappears)... But I'm unable even to kill it. If I try to reboot, shutdown or log out... system just hangs. It warns me again there are processes running (xterm and unknown process), although I had already killed it (or tried to) before. It was still alive.
- Ubuntu seems to get out of the session... and then just hangs. No keyboard response at all (even caps lock or scroll lock lights don't work at all). No Ctrl+Alt+F1,F2,F3... I just have to switch off the machine.
- If I try to open a new xterm window before trying to reebot or shutdown, it doesn't open.

I've reinstalled Ubuntu 9.10 about six times, with identical result in all of them. I've tried it in two different HDDs, one 320 GB and another one 160GB. Two different external cases too.

The problem occurs only with user "ubuntu". If I log in as "root", everything seems to work fine.

I created a second user: "ubuntu2". (useradd -m -s /bin/bash ubuntu2), then rebooted and logged in as ubuntu2. Everything fine too. Although I haven't experimented it for a while, ubuntu2 doesn't seem to suffer this problem.

It only happens in my laptop. If I boot my desktop computer with the same USB HDD, everything works fine, even for user "ubuntu". 

So:

- It's not a HDD problem.
- It's not an external HDD case problem.
- It only happens with user "ubuntu", doesn't seem to be a hardware issue.
- It only happens in my laptop.
- It only happens after two or three reboots, after installing all that I said before and updating the system. It starts suddenly. Before that, everything works fine.

Has anyone had any problem similar to mine?. It's driving me nuts!. Apart from the fact it only happens with a particular user, the laptop has been running Windows XP x64 for several years, and Windows Server 2008 x64 for about two years with absolutely no trouble. No hangs, no strange behaviour... everything perfect. So I would discard a hardware issue.

My hardware:

Acer Travelmate 7514 WSMi
Turion 64 X2 TL-56 processor
2 GB RAM
500 GB HD (not used or mounted, remember I boot with an external USB HDD)
Nvidia Gforge Go7600
Broadcom BCM43xx wifi adapter (internal, haven't ever tried to make it work under Ubuntu).
Ethernet connection (I use this to do all the initial setup and updating, until the problem comes out)

Disk partitioning is (all partitions are primary):
/dev/sdb1 -> ext4, 40 GB
/dev/sdb2 -> swap, 2 GB
/dev/sdb3 -> ntfs, about 260 GB, or FAT32 (tried both)

Any idea?

---

### Post by Tristan Tonks on 2010-02-09
I recon you may have found a genuine bug there ;)
have you tried any other terminals?

---

### Post by angelbla on 2010-02-10
Upsss. Sorry. I don't know how I came to the conclusion that I was using xterm.

I'm using the standard gnome-terminal that comes with Ubuntu. This is different from xterm, or isn't it?. (I'm not an expert in linux, as you can see  ;)).

Answering your question, no, I haven't tried any other terminal. This happens as soon as I finish installing updates, so I didn't go further (I would also have to make my Broadcom wifi work, I had some problems with it in previous versions of Ubuntu). I was just trying to install basic things and make it work. But instead I found myself trying everything I could, trying to find some logic in this behaviour. But I have no idea of what it could be. It's weird. :)

I'll try to change the terminal for another one, and see what happens. But since in other computers it works fine and in my laptop it's so easy as using a different user, I don't know if it's worth the effort of trying to find out. I might even try to delete user "ubuntu" and create it again. And see what happens. Funny anyway (well, funny but you can't imagine how much I swore with this :p)

Thanks for the answer anyway. If I make any progress, I'll let you know.  ;)

Greetings.

---

