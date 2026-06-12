---
title: "Ubuntu 9.10 and Dual Monitor problems!"
date: 2009-11-02
forum: General Help
---

### Post by Gp. on 2009-11-02
Hi all,
I've got a Samsung SyncMaster 226BW 22" LCD, and a Dell 15" LCD.

I'm trying to set them up to work with Ubuntu and it's just not going well. I've set the resolutions appropriately for each screen, and I do NOT want mirroring.

The login screen does not fit the screen for the 22" and even after logged in there are still problems.

I can't move any windows to the second screen (Dell), it just gets stuck half way and won't let me move it any further. If I try to maximize the window it doesn't fill the whole window (22"). I can't even try to maximize it in the 15" dell because I can't move anything over there! Some kind of strange boundary.

Basically, it seems Ubuntu is getting the boundaries of the screens wrong, and all that jazz. Sometimes I can't even move my cursor past half of the 22" until I open another window. It's really bizarre everything is just messed up!

Really need some assistance, because I just fixed 9.10's audio issue, and the Ubuntu team have fixed the soft reset error so Ubuntu 9.10 finally works on my system and I'd like to get into using it again. Just need to iron out these issues!

Thanks all!

---

### Post by Gp. on 2009-11-03
If this wasn't an issue I'd be using more Ubuntu than Win7 atm.
Sigh.

---

### Post by P4man on 2009-11-03
Which videocard and drivers are you using?

---

### Post by scouser73 on 2009-11-03
The following instructions are for an nVidia card only, so if you don't have one then please don't follow my instructions.

Please follow these instructions for setting up dual monitors.

**1** - Paste this command into terminal: **gksudo nvidia-settings**

**2** - Then go to **X Server Display Configuration** then set up your monitors to your liking

**3** - Once you have done so click **Apply** then click **Save To X Configuration File**

You will now have dual monitors working.

---

### Post by jermac3 on 2009-12-05
> **scouser73 said:**
> The following instructions are for an nVidia card only, so if you don't have one then please don't follow my instructions.

Please follow these instructions for setting up dual monitors.

**1** - Paste this command into terminal: **gksudo nvidia-settings**

**2** - Then go to **X Server Display Configuration** then set up your monitors to your liking

**3** - Once you have done so click **Apply** then click **Save To X Configuration File**

You will now have dual monitors working.


Except when I try that I get the error: "failed to parse existing xconfig file '/etc/X11/xorg.conf'!

Any help with that... please.

Thanks,

Jeremy

---

### Post by schmolch on 2009-12-05
I get the same ******* error!

---

### Post by Gp. on 2009-12-06
I'm back on windows. I need something that works, I don't have the time to **** around fixing things.

---

### Post by schmolch on 2009-12-06
I can tell you how to fix it if you want.

---

### Post by Gp. on 2009-12-07
??

---

### Post by schmolch on 2009-12-07
I stumbled across a fix on another thread.
Before you run "sudo nvidia-settings" you have to execute "sudo nvidia-xconfig", this will create a xorg.conf that nvidia-settings is able to read.

---

### Post by Mr. Spoon on 2009-12-07
Thanks schmolch. I just bought a second monitor, and this fixed the issue I had with getting it to work.

---

### Post by Picky88 on 2010-01-09
Hi there,

I am having some issues with dual monitors, I wonder if anyone can assist. I have set them up as twin view, but I cannot access half of the righthand screen, the mouse cursor will initially not go onto the second display,except when I drag a window across, then the mouse will go onto the second screen, but the windows will not go past about a third of the screen.  Im in ubuntu 9.10, the graphics card is a nvidia 8400 gs, I am not using the proprietry drivers (they would not set up dual monitors at all)

Thanks,

Picky88

---

