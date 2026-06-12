---
title: "Ubuntu 10.10 monitor resolution"
date: 2011-01-09
forum: General Help
---

### Post by zamadatix on 2011-01-09
I have an AMD Radeon HD 6950 and I know that no driver will be released for a while that works (current one causes xorg to crash and creates a reboot loop). Until then I have a 1920x1080 monitor running at 1280x1024 bc there are no higher settings...

Is there any way to increase the resolution until the driver support comes? I tried a method involving xandr but that didnt work.

---

### Post by dopeking on 2011-04-15
Hy There

I've encountered the same problem.
I'm running Ubuntu 10.10 amd64 Desktop on a AMD Quadcore CPU with an Intel Board and a Sapphire HD 6950.

What i've tried so far:

- installing the proprietary driver from the amd page... it is complete CRAP!!! neither the resolution is correctly detected nor is the 3D Accel working, plus i've encountered many crashes and after i messed around with glx, i broke X completly :-(
After a quick

> aptitude reinstall xserver-xorg

my system was working again and i could pursuit my work... 

- I've tried out the [edgers ppa]("https://launchpad.net/~xorg-edgers") for X and found no big improvement. At least the System is working fast and with no crashes (still wrong resolution and no 3D)

- i've tried to [add the correct resolution with xrandr]("http://ubuntuforums.org/showthread.php?t=1112186"). It did not work. System said something about an unfound Video Device... short, i could not add the resolution to the right display device. And this while using the output of xrandr which told me the devices named "default".

- i've cursed ADM / ATI with some [swissstyle voodoo]("http://www.youtube.com/watch?v=NvrNZ4nOXwc") for there false promise to make the fglrx driver and ALL of the important interfaces open-source and encourage the community to get good drivers :twisted:

... so far, no improvement :-(

Anyway, if somebody now's more about the issue, let me know.
And for those lol-ing ... i now, its a bold move to buy a new ati card and expect it to work on linux. but what should i say... never give up dreaming :D

---

### Post by linuxmaniack on 2011-04-15
Are you using virtualbox? If you are, mount the guest editons .iso file. Then browse for the one that is a x86 or x64, depending on your operating system. If you not, and you are running a x64 os, see if there is a x86 one*. Try that. There may be a non-ATI one from elsewhere, that may work.

hope this helps

linuxmaniack

*, however, the x86 one may not work with a x64 one.

---

### Post by dopeking on 2011-04-19
Hy Linuxmaniack

No, i'm using the standart os, not inside a virt. machine.

But thanx for the intrest ):P

---

### Post by dopeking on 2011-04-19
It seems i found a solution:

There is fglrx driver for linux which is supposed to work with my new sapphire hd6950... its called the catalyst 11.4b Package and is available [here]("http://www.ati-forum.de/files/Downloads/Driver/Catalyst_11-4a_11-4b/amd_catalyst_8.84_linux_radeon_hd_6700_6600_6500_6400_apr5.run") Just click "save_as" and save it as a file.
To run this driver you'll need the new 2.6.39 kernel freshly released from linus and available as unpached ppa [here]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.39-rc1-natty/"). Since the 2.6.39 kernel is not supposed to work under ubuntu 10.10, i've downloaded myself the [ubuntu 11.4 beta]("http://cdimage.ubuntu.com/daily-live/current/") and gave it a try.
Here's my little howto:

1. makeup space on your disk for another partition... safety first!
2. install natty on the recently created partition
3. update and upgrade natty
4. Give it a try without the fglrx-driver

Right from the first second, natty is very nice... highres-grub and upstart and full resolution for my wuxga monitor. The System was running fast and stable. The only Problem that i encounterd in an hour of testing was that mplayer had some strange black scenes every now and then.

5. Trying to install fglrx....  as expected, the driver did NOT work well! In fact it broke my system to the point, that the kernel could not load the ram disk and froze imediatly on boot.

My Conclusion... fglrx drivers still are less functional as os drivers from the community. Natty is a fast System and i'm eagerly awaiting the release date :-\"

If somebody finds a way to make wuxga work on Maverick, please let me know.

---

### Post by linuxmaniack on 2011-06-01
Ok, have you tried going on AMD's Website and finding the drivers for linux (nearly all GPUs drivers from AMD have a linux version.

---

