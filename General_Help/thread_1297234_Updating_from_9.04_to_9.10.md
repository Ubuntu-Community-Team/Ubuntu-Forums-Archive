---
title: "Updating from 9.04 to 9.10"
date: 2009-10-21
forum: General Help
---

### Post by galaga4991 on 2009-10-21
I've been a fan of Ubuntu for a while now using Wubi, but now that I have a 1TB Hard drive, I figured I should Dual Boot XP and Ubuntu instead of using Wubi. I wanted to install Ubuntu 9.04 today, but I know that 9.10 is being released in a week. If I install 9.04 now, will I be be able to update to 9.10 using the built-in update manager instead of having to reinstall the entire OS again? Or will I have to go through the process of burning a 9.10 disc, deleting my Ubuntu partition, and then installing 9.10?

---

### Post by Niko Johnson on 2009-10-21
bump... im listing too

---

### Post by The Thug on 2009-10-21
You'll be able to upgrade through update manager.

---

### Post by QIII on 2009-10-21
If you haven't installed Ubuntu yet and are in no burning hurry to do so, I'd wait and do a clean installation of Karmic.

The RC should come out tomorrow, and the Final on the 29th.

If you absolutely MUST install Jaunty now, create a separate /home partition when you do it.

When Karmic comes out, back up anything important (like your /home folder stuff) and install clean.  Having your /home folder separate will keep you from having to recreate all of your nifty settings and such.

If you just want to muck around and don't care to save anything in 9.04, just install it and goof around.  Break stuff -- which is the best way to learn.  You have nothing to lose.

Then, do a clean installation of Karmic in a week or so.

---

### Post by galaga4991 on 2009-10-21
> **QIII said:**
> If you haven't installed Ubuntu yet and are in no burning hurry to do so, I'd wait and do a clean installation of Karmic.

The RC should come out tomorrow, and the Final on the 29th.

If you absolutely MUST install Jaunty now, create a separate /home partition when you do it.

When Karmic comes out, back up anything important (like your /home folder stuff) and install clean.  Having your /home folder separate will keep you from having to recreate all of your nifty settings and such.

If you just want to muck around and don't care to save anything in 9.04, just install it and goof around.  Break stuff -- which is the best way to learn.  You have nothing to lose.

Then, do a clean installation of Karmic in a week or so.

What are the downsides to just updating through the update manager instead of doing a clean install? I'd like to start using Ubuntu now and get all my stuff setup before 9.10 is released.

---

### Post by Bonster on 2009-10-21
U should wait for 9.10 final or atleast get the 9.10 beta,  dont use 9.04 no more. 9.10 beta u can update to final. 9.10 got ext4 by default 9.04 u have to configure it manually to get ext4. So like i said if u do it today get 9.10 Beta.

---

### Post by OpenGuard on 2009-10-21
> **Bonster said:**
> U should wait for 9.10 final or atleast get the 9.10 beta,  **dont use 9.04 no more. **9.10 beta u can update to final. 9.10 got ext4 by default 9.04 u have to configure it manually to get ext4. So like i said if u do it today get 9.10 Beta.

Why ? :-s

---

### Post by QIII on 2009-10-21
> **galaga4991 said:**
> What are the downsides to just updating through the update manager instead of doing a clean install? I'd like to start using Ubuntu now and get all my stuff setup before 9.10 is released.

Jaunty installs with GRUB and ext3.

If you want to take advantage of GRUB2 (that is, not be running GRUB in "legacy" mode) and use ext4 (which is the default in Karmic, but not changed via the upgrade method), you would have to update at least those two things in Jaunty before you upgraded.  That can be done.  I have both on all of my Jaunty machines.

A clean install gives you both by default at installation.  Those are two of the biggest reasons I suggest a clean install, although the two are not necessarily prohibitive.  They might be beyond the comfort zone of inexperienced users and are as much a risk as upgrading in terms of leaving yourself with a borked system.

There is also the fact that many people have found updates to be somewhat more troublesome than clean installations.  I've not idea what percentage of people that may be, so I can't give you an empirical answer on that.

---

