---
title: "Infinite boot cycle loop"
date: 2011-01-26
forum: General Help
---

### Post by garethfoxwilliams on 2011-01-26
When I boot one of my machines, it gets as far as GRUB, then proceeds to a blank screen for a second, and then repeats the cycle all over again - ad infinitum.

I have tried previous kernels on the list with the same results

Also, I cant boot into recovery mode either.

I have run Memtest successfully from the GRUB options and no errors appear in the results.

I have tried booting from a Live CD and here I get as far as the "OS choosing screen". When I then select one and hit Enter, the screen goes blank and the machine reboots as before.


Any ideas on how to proceed?

---

### Post by Rubi1200 on 2011-01-26
Hi,
what graphics card do you have installed?

Are there other operating systems on the computer?

Are you able to get hold of another live distro and burn it to CD? (my choices would be Knoppix and/or Slax).

---

### Post by garethfoxwilliams on 2011-01-26
Graphics card is a PNY 128MB Nvidia which I'll whip out to see if that's the problem.

No other OS although once there was a second HDD with W....XP  which still appears in the Grub menu, although that was removed about 9 months ago with no problems ensuing.

---

### Post by garethfoxwilliams on 2011-01-26
OK changing G/card makes no difference, BUT disconnecting the HDD allows the LiveCD to boot fully into Ubuntu.

So the problem must lie somehow with the HDD / Grub ?

I could connect the offending HDD via a USB dock to explore it and change config? If only I knew where to start!!

---

### Post by IWantFroyo on 2011-01-26
Try mounting the drive after booting.

---

### Post by garethfoxwilliams on 2011-01-26
Put HDD back in after booting - it dutifully appeared in Nautilus.

Wondered if I could log out as guest and log in as normal user

Failed miserably at that and couldn't even log back in as guest!

Restarted............. and now the box works normally again - boots repeatedly without a problem.

I re-installed GRUB via Synaptic - just in case.
I removed old kernels via Ubuntu Tweak

Can't think of anything more to do now.....

Problem seems to have sorted itself out now, but in a slightly unsatisfying way, as I'm not really sure what I did that cured it!!

Thanks for the suggestions.

---

### Post by venik212 on 2011-11-07
I had the same problem u 64 bit 11.10).  I rebooted to the terminal, and typed:
sudo rm .Xauthority
sudo reboot now

and all is well now

---

