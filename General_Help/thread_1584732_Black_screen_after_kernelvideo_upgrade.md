---
title: "Black screen after kernel/video upgrade"
date: 2010-09-29
forum: General Help
---

### Post by SharkWipf on 2010-09-29
Well, unfortunately my first post on the forums is one heck of a problem...

I recently bought an HP pavillion dv7 4040ed, and immediately regretted it. I've tried several Linux distro's, under which Puppy and Debian, and they only ran when I passed the acpi=off parameter. Because of this, Debian failed partitioning my disk, and left me with an half partitioned disk. I decided to give Ubuntu a try, especially since I accidentally ruined my winblows 7 install. To my suprise, Ubuntu just booted, and I successfully managed to install it. It ran flawlessly, at first. Then I installed the latest updates (including the kernel update), and installed the suggested ATI video drivers. Both of these told me to reboot (!! ;-)), and so I did.
Unfortunately, Ubuntu didn't boot through anymore. After grub, I see the bootsplash, and after that, the screen goes completely black. Sometimes, seemingly at random, the backlights turns off as well. Ubuntu doesn't respond to anything (ctrl+alt+F1, ctrl+alt+del, etc.) except the power button, which shows the bootsplash again, and then shuts down the pc.
Things I tried so far:
I tried switching to vesa drivers, without success.
I copied the Xorg.conf.failsafe (?) to Xorg.conf. No success.
I tried booting in recovery mode. Same problem. (!!)
I tried to un/reinstall several ATI drivers, including from the ATI website. No luck.
I read my logs through grub/ubuntu live, which I will attach later on, as soon as I boot back to Ubuntu. These said the following: "EGA/VGA planes are not yet supported by the fbdriver."
I tried to boot with the following flags:
vga=normal (no notable effect)
nofb (no notable effect)
vga=ask (deprecated, not longer supported)
nomodeset (see below)

Of the above, only nomodeset worked up to a certain level. I got into the safe mode failed graphics menu thingy. There were some interesting new entries in the logs, which I will post later (winblows atm). As long as I pass the 'nomodeset' parameter, i can boot in safe graphics mode, which works fine, except for the fact that I'm not using any reasonable video driver, so no compiz (noooo!). Also, it's quite annoying to have to click through the error messages in the 'fail menu', before being able to to boot through.

I'm no Linux newbie, so fire away! :) I'll include my logs as soon as I boot to Ubuntu, which won't be to long, I guess :p
On the bright (meh...) side, I got my winblows back online :)

Hardware:
HP dv7 4040ed
ATI Mobility Radeon HD 5650 1GB
Intel Core i5 M 450 (onboard GPU)
2x2GB DDR3 RAM

Software:
Ubuntu 10.04 x86
Kernel: Newest :) (pae, apparently)

---

### Post by SharkWipf on 2010-09-29
So, here are the logfiles. The one named *noATI is without ATI drivers installed, and the *ATI one is with ATI drivers installed (doh).

By the way, my problem seems to be very much alike [this one]("http://ubuntuforums.org/showthread.php?t=1584734"), exept that I can't even switch to an terminal by pressing ctrl+alt+F1. Also I have tried to use "aticonfig --initial" and "aticonfig --initial=dualhead", to no avail. I also tried to attach an external (vga) monitor, which only showed the bootsplash while shutting down. If you need more details, just ask, as long as you don't ask for passwords etc ;)

ps.
uname -a output:
Linux Taplop 2.6.32-25-generic-pae #44-Ubuntu SMP Fri Sep 17 21:57:48 UTC 2010 i686 GNU/Linux

---

### Post by SharkWipf on 2010-09-30
Well, at least I got a little progress... I noticed the fglrx driver was still being loaded and used, even though I set my xorg.conf to vesa. This caused the 'fail menu' to pop up every boot. I did a 'sudo modprobe -b fglrx', and now I can boot with vesa drivers, without having to click through all the error messages every boot. Unfortunately, I still can't boot without the 'nomodeset' flag, which makes me think it's partially a kernel problem as well. Any ideas yet?

---

### Post by SharkWipf on 2010-10-01
Hmm, well, maybe I didn't update the kernel at all, since there's only one kernel available in my /boot/ folder... Anyway, I upgraded *something* which requested a reboot, and the only thing I could think about, apart from the video drivers, was the kernel. Maybe I just 'double upgraded' my videodrivers... Still, I also uninstalled them, so I still don't know what's the problem.

Hmm, kinda feels like I'm just blogging here. Anyone got any ideas yet? Anything?

EDIT:
Turns out I didn't remove all drivers. Now I did, and I managed to boot in 'normal' mode, using vesa drivers, without the 'nomodeset' tag. Not perfect yet, but it's something. At least I managed to pinpoint the problem.
EDIT2: Ignore above edit. Somehow I had 'nomodeset' twice in my grub.conf. Only removed one, so I still booted with 'nomodeset'...

---

### Post by SharkWipf on 2010-11-17
Final update.
As soon as 10.10 was released, I did an upgrade, which didn't help. I also started to get problems in windoze, like graphics adapters disappearing from the system. I decided to bring back the laptop, and fortunately they agreed that it was a hp problem, and, after a week, I got back my money. I got myself an Asus X77JQ (on the Asus site supported as N71JQ), and it still works like a charm. The specs are better in every way, exept for the hard disk size (500GB). Only problems I had so far, is that the touchpad is a little cheap, and that I can't remap my powerbutton to the eject command :)

For everyone looking to buy a laptop: DON'T buy HP. For around the same price, you get a better laptop, which actually works.

Also, yesterday someone had the same problem, with a different laptop (also HP with ATI). So this is not only limited to the dv7 branch. 

End of blog ;)

---

