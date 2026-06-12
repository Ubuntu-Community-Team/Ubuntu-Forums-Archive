---
title: "disappearing cursor in karmic 9.10"
date: 2010-02-02
forum: General Help
---

### Post by charonred on 2010-02-02
This is driving me up the wall; my mouse cursor disappears whenever I cross from monitor 1 to monitor 2, but returns after moving the mouse around. I've been reading to other posts and tried changing themes etc, but now I have slightly messed up desktop as well - my minimise/restore/close buttons have gone, they only appear when I mouse over where they should be.

There are several things I like about Karmic, but I only migrated to it from Hardy so that the ATI drivers would work correctly for my new HD5770 graphics card, otherwise I would have stayed with Hardy.

Any idea how I can get the mouse cursor to stay visible all the time?

---

### Post by cliff_s on 2010-02-17
I had the same problem. Try installing the drivers from the ati website I'm pretty sure that's what fixed it for me.

---

### Post by charonred on 2010-02-17
thanks, I've downloaded the ATI driver file. I think I used Terminal the last time I installed a .run file, but I can't remember the exact script/method used.

It's ok, I found it on the driver download page; open terminal and CD to where the download is located, then enter the following command (using the version of driver downloaded)```
sudo sh ./ati-driver-installer-10-1-x86.x86_64.run
``` this'll fire up a graphical interface; just follow the prompts for 'Automatic' install, then reboot PC (which I'm about to do ... hope it works)

My PC rebooted and I'm back - the cursor seems to be visible all the time now, no disappearing act. I'll see how it goes and report back.

Thanks cliff_s

UPDATE - been using PC for few hours yesterday, and last night, and again this morning; latest ATI drivers seem to have fixed the disappearing cursor problem ... excellent.

---

