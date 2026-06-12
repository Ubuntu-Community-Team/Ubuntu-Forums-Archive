---
title: "BIOS age fails cutoff"
date: 2009-11-29
forum: General Help
---

### Post by phoenox on 2009-11-29
I tried running ubuntu 9 off of a cd on my computer.  While ubuntu is booting I get the error message-- Bios age fails cutoff(1999) 2000 required(this is from my memory, not the exact text of the message).  It still ran and I was able to have a look around.  I was quite impressed and would like to install ubuntu on my computer.

But then the next time I tried to start my computer it froze in bios.  I had to turn it off and unplug the cd drive before it would boot properly.  No permanent damage, but I need to resolve this issue before I can install.

I dont know if I should update my bios or just find an older version of ubuntu to install.  I am leaning towards finding an older version.  Can anyone recomend a good version of ubuntu for an older computer, or do I have to go out and learn how to update my bios?

---

### Post by zaphod777 on 2009-11-29
If there is an update for your bios I would try that. what model pc do you have? A lot of them have a gui to install the update from inside windows.

---

### Post by oldos2er on 2009-11-29
No version of Ubuntu will work with your older BIOS, AFAIK. What are your computer's specs?

---

### Post by oldfred on 2009-11-29
Older computer BIOS could only see drives of a certain size to boot. Larger drives could not be seen or may not boot. You may be able to install with a separate /boot partition at the front of the drive.

Herman has more info on BIOS and limits with info on separate /boot.
[http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_boot_partition]("http://members.iinet.net.au/%7Eherman546/p15.html#How_to_make_a_separate_boot_partition")

If the computer is that old you may not have enough memory for Ubuntu. It now requires a min of 256mb. Other smaller linux may then be more appropriate.

---

### Post by efflandt on 2009-11-29
I tried out various versions of Ubuntu on an old PIII 550 w/320 MB RAM and got that warning in dmesg.  The computer also would not shut down entirely (except with gparted-live CD).  By trying different options I determined I need to add **acpi=force lapic** (the latter for the shutdown issue).  Those are usually not critical issues and I had no real problem running without them.  During install I think you press F6 (see function keys at bottom of opening menu after selecting language) to add those parameters.  And I believe Ubuntu automatically adds those parameters as defaults for grub on the installed system.

Ubuntu 9.04 ran reasonably well with no issues (flash video had a slow framerate, but sound was smooth).

Ubuntu or Xubuntu 9.10 had issues with my older ATI Radeon video card.  I could inially log into Xubuntu 9.10, but after I did updates, login just looped back the login screen and I could not get into X.  I could not even log into Ubuntu 9.10 unless I selected **Failsafe GNOME** at screen bottom.  So I installed **xorg-driver-fglrx** in Xubuntu before doing any updates on it, or from Failsafe GNOME in Ubuntu to get video to work properly in those.  But that fglrx driver is not needed for all ATI cards, just ones that the new X seems to have a problem with.  My main desktop has ATI Radeon video, and it works fine with default drivers in 9.10.

I eventually installed "Qimo for kids" (based on Ubuntu 8.10) on that old PC and gave it to my niece for her twin 4 year old boys.  The educational games run fine on it, and no great loss if they break it.

---

### Post by phoenox on 2009-11-29
The moterboard is ASUS P2L97
266 MHz processor
262 megs ram

There is a beta update for the bios at [ASUS site]("http://support.asus.com/user_main.aspx?cat=download&product=1&SLanguage=en-us"):

Not very enthusiastic about using a beta version.  
I will try acpi=force lapic, see if that fixes the problem.

---

### Post by oldos2er on 2009-11-29
If I were you, I'd give Puppy Linux a try. Your specs are too low for the 'buntus, in my opinion.

---

### Post by dcstar on 2009-11-29
> **phoenox said:**
> 
........
I dont know if I should update my bios or just find an older version of ubuntu to install.  I am leaning towards finding an older version.  Can anyone recomend a good version of ubuntu for an older computer, or do I have to go out and learn how to update my bios?

6.06 LTS is still available:

[http://releases.ubuntu.com/releases/](http://releases.ubuntu.com/releases/)

---

### Post by phoenox on 2009-12-04
I have installed puppy linux on my computer.  I am quite happy with it.  Still some debugging to do, but I think the OS is a good fit for my computer.

Thanks All.

---

