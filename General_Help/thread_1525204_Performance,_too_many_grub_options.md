---
title: "Performance, too many grub options"
date: 2010-07-06
forum: General Help
---

### Post by Lunami on 2010-07-06
Hello everyone. Haven't posted in a while, so my memory of Ubuntu is rather slim at the moment.

I had an old disk laying about of 9.10, and then when I finished, it asked me to run an update, so I did so, andnow I'm running 10.04. I was curious if I'd see a vast improvement of my performance if I just wiped it off, then made a disk of 10.04 and ran it.

I also have about 8 options in my grub menu. Let's see... 3 kernels and their safe mode, the mem tests, and windows XP. Would this be slowing the computer down?

Lastly, overall, it just seems sluggish. I'm running a computer with a 2.0 ghz processor, and 768 MB of RAM. WOuld this be adequate to running 10.04?

I only really have need to run two programs on this. Both are games, and are apparently documented and people seem to have it work for them.

Thanks for your help.

PS. Would any of this affect my flash player performance? Youtube is simple awful on this side of the computer.

---

### Post by mikewhatever on 2010-07-06
> **Lunami said:**
> Hello everyone. Haven't posted in a while, so my memory of Ubuntu is rather slim at the moment.

I had an old disk laying about of 9.10, and then when I finished, it asked me to run an update, so I did so, andnow I'm running 10.04. I was curious if I'd see a vast improvement of my performance if I just wiped it off, then made a disk of 10.04 and ran it.
You might, but it depends on what causes the sluggishness.

> I also have about 8 options in my grub menu. Let's see... 3 kernels and their safe mode, the mem tests, and windows XP. Would this be slowing the computer down?
These are old Linux kernels, all but the latest ones can be safely uninstalled from Synaptic. Regardless, the number of kernels shouldn't affect performance.

> Lastly, overall, it just seems sluggish. I'm running a computer with a 2.0 ghz processor, and 768 MB of RAM. WOuld this be adequate to running 10.04?

I only really have need to run two programs on this. Both are games, and are apparently documented and people seem to have it work for them.

Thanks for your help.

PS. Would any of this affect my flash player performance? Youtube is simple awful on this side of the computer.

What's your graphics card? Both games and flash would benefit from a decent graphics card, that said, flash for Linux is greatly inferior to flash on Windows.

---

### Post by Lunami on 2010-07-06
> **mikewhatever said:**
> You might, but it depends on what causes the sluggishness.
Any way I can check to see what may be causing it to slow down?

> These are old Linu kernels, all but the latest ones can be safely uninstalled from Synaptic. Regardless, the number of kernels shouldn't affect performance.
I'll attempt to remove them then, and report back later.


> What's your graphics card? Both games and flash would benefit from a decent graphics card, that said, flash for Linux is greatly inferior to flash on Windows.
My graphics card is an NVidia GeForce FX 5200. If I recall correctly, it has 128 memory, or whatever it's called. I can't recall the term atm.

---

### Post by mikewhatever on 2010-07-06
What kind of sluggishness are you talking about? Is it the general interface related delais, mouse clicks delais, etc, or is it restricted to the two games you mentioned.
Try running htop (may need to install it first) and identify the most taxing processes. Disable desktop effects. Installing the proprietary nvidia driver might help.
Quite frankly, however, if all you need Ubuntu for is to run two Windows games, I don't see any benefits of using Ubuntu.

---

### Post by Lunami on 2010-07-06
Well, after clearing up the kernel's it improved a bit in the performance. Suppose I need better hard drives, perhaps. The one with Ubuntu on it is rather old.

Desktop effects have already been disabled.

I do more than use Ubuntu for two games (in fact, I'm only doing a test now to see if I can get them to run in the first place, no luck yet, however). I have personal reasons for getting this particular machine on Ubuntu. The only issues I'm having now is the webcam / mic and a messenger to go with it (that will allow access to friends who use AIM, MSN, YIM, etc...), and these two games to work.

---

### Post by mikewhatever on 2010-07-06
What makes you think Ubuntu 10.04 has old hardware drivers?
Be as it may, I don't think that is an issue, since, judging by NVidia GeForce FX 5200, your computer is all but brand new.

---

