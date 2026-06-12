---
title: "Can I set Windows to boot by default?"
date: 2009-11-24
forum: General Help
---

### Post by mongrel boy on 2009-11-24
Hi, its been a while since I had Ubuntu on a system and I just installed Windows XP on my new desktop. Then I installed Karmic on a partition of the hard drive.

When I boot up I get the ubuntu menu where I'm asked to choose what OS to run.

I just wondered if I can change this so that I get the Windows menu with two options: Windows or Ubuntu.
(I use windows more because I run Reason4 in it)

I haven't been able to find anything about this, so I'm sorry if I've been looking in the wrong places any help would be awesome!

---

### Post by Darael on 2009-11-24
You'd be better off changing your Grub default to Windows - which you can do with the instructions at [https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202](https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202) followed by running "sudo update-grub".

It's a better idea, because grub is a whole lot more flexible (to say nothing of more reliable) than the Windows bootloader, no to mention that to switch you'd have to reinstall grub to a partition's boot record instead of that of the drive, then rewrite the MBR of the drive with the Windows bootloader - which I for one haven't the foggiest how to do!

---

### Post by mongrel boy on 2009-11-24
hi, thanks, ive tried changing the grub default to windows but it doesn't seem to have worked. I've removed ubuntu from the boot.ini file in windows so I'm happy now. thanks a lot for the reply!

---

### Post by wilee-nilee on 2009-11-24
Since your running intrepid install startup manager from synaptic it will do the job.

---

### Post by mongrel boy on 2009-11-25
im using karmic, my account info needs updating

---

### Post by mongrel boy on 2009-11-25
O.K, just to clarify whats hapening here: I'm running Karmic, when I boot it says GRUB 1.97~beta4 at the top of the menu screen. These links seem to hold information about editing GRUB2. strangely these GRUB2 files are in my home folder. I edited them and still Ubuntu is the default boot??

I have removed Ubuntu from window's boot.ini file so when I do select Windows I don't get faced with another menu. I'd just like to not have to select Windows, I'd like Windows to be selected by default. Apologies if I'm being stupid here.:oops:

---

### Post by raktarok on 2009-11-25
You can edit the grub config file to achieve that:
```
sudo gedit /etc/default/grub
```

Now change the number in the entry GRUB_DEFAULT. Initially, it should be 0 (the entry at the top of the menu. 1 will correspond to the second entry and so on). Check the order of the Windows entry in the grub menu,and change the GRUB_DEFAULT value accordingly. This should make Windows the default entry.

You may also want to decrease the GRUB_TIMEOUT entry. It reduces the time you have to wait at the grub menu before the entry highlighted by default boots automatically. Personally, I find 3 seconds an ideal time to wait,and I have Ubuntu as my default OS. I would recommend you to go with linux as well, but of course, you must have sound, valid reasons to choose windows. Each man to his own taste..

In the end, don't forget to do this:
```
sudo update-grub
```

Look at the link posted above if you want more details, or if you want to customize further.

There's no reason to apologize, we are all learning here :)
Hope this helped!

---

### Post by egalvan on 2009-11-25
> **mongrel boy said:**
> I'm running Karmic, when I boot it says** GRUB 1.97~beta4 **at the top of the menu screen.
 These links seem to hold information about editing **GRUB2.**
 strangely these GRUB2 files are in my home folder.


Not strange, just version numbering...
GRUB2 is at 1.97-xxx, it has not reached version 2.xxx yet.
Just the name is version 2.

GRUB legacy is at 0.97-xxx, and will probably never advance.

---

### Post by mongrel boy on 2009-11-25
worked a treat, thanks a lot! I would have linux as default I like it a lot but I use propellerheads Reason4 and it doesnt run roperly in wine (last time I checked) so Windows has to be my number 1.

---

