---
title: "Stripped down Ubuntu"
date: 2011-08-27
forum: General Help
---

### Post by ixusubunt on 2011-08-27
Hope this hasn't been covered before ... but how much software can I remove from Ubuntu 11.04 before I do any damage and stop it working?
I originally loaded Ubuntu 9.10 on an old IBM Thinkpad R30 just for browsing the Internet on my home WiFi network. I was really impressed with the speed ... I could be Googling 55 secs after pressing the 'on' button !
Since then I have upgrading twice and each time the computer has got slower. 11.04 seems to be the worst so I have been browsing for solutions. I noticed that I had over a hundred pieces of software installed; many that I do not use. I have reduced it to less than 80 but I'm a bit worried about removing such things as Network Tools, Network Manager, and so on.
Also, I read that 'swapping' should be as low as possible to make the computer faster ... not sure what this means but System Monitor tells me that my swap history is 6.5%. Is this ok?
For info: i have a Pentium 3 processor, 488Mb memory, and an 80Gb hard drive.
Any tips (easy ones please!)
Thanks
Paul

---

### Post by sanderd17 on 2011-08-27
What do you define as working?

I suppose you still need a graphical environment (you can work on your computer without one), and probably also sound management and ...

As you see, it's a matter of choices. If you don't want to make choices, you can use others' peoples choices and use a lighter distro. I would advise Lubuntu.

About swapping: Swapping is extending your main memory by using your hard disk. But your hard disk is typically about 100 times slower than your memory. That means if you are swapping a lot of files, than your computer is unusable. So files are only swapped when really needed, and the oldest ones are swapped first.

---

### Post by jerrrys on 2011-08-27
other options would be [xubuntu]("https://wiki.ubuntu.com/Xubuntu") and [lubuntu]("https://wiki.ubuntu.com/Lubuntu")

---

### Post by snowpine on 2011-08-27
Your computer is slow because it does not meet the [hardware requirements]("https://help.ubuntu.com/community/Installation/SystemRequirements") for Ubuntu 11.04:

> Ubuntu Desktop Edition

    1 GHz x86 processor (Pentium 4 or better)

    512 MiB of system memory (RAM)
    5 GB of hard-drive space
    Graphics card and monitor capable of 800x600
    Either a CD/DVD drive or a USB port (or both)
    Internet access is helpful 

What I would recommend is going to the Software Center and installing "xubuntu-desktop" or "lubuntu-desktop" then log out and, from the login screen, select the Xfce or LXDE desktop. This should be a little lighter on resources than Unity/Gnome.

It is a myth that "removing software I don't use will make my computer run faster" because applications don't use CPU/RAM unless you use them. The main benefit of removing applications would be a little bit more free space on your hard drive.

If you want the lightest/fastest possible Ubuntu install, you can use the Minimal CD as described here: [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal) You could also try a distro like Puppy, SliTaz, Antix, CrunchBang, etc. that is designed specifically for older hardware. (CrunchBang is what I personally run on my Pentium 3). Good luck! :)

---

### Post by ixusubunt on 2011-08-27
Thanks for the replies ... looks like Lubuntu is a good option so I might give it a try. I should really get rid of this old machine ... I've been on the way to the wheelie bin with it once but I just couldn't do it!! It doesn't even have a separate graphics card, no wonder movies don't run too well! I should have known that uninstalling software wouldn't make any difference, as there is loads of room on the hard-drive. Cheers.
Paul

---

### Post by ixusubunt on 2011-08-28
Just for info ... Lubuntu is much better!
Wasted too much time messing around with the 'panels' and wondering why there was no audio when I had 'mute' pressed on the keyboard! After that, everything is good ... even (most) videos play ok! Thanks again. Paul

---

### Post by sanderd17 on 2011-08-28
> **ixusubunt said:**
> Just for info ... Lubuntu is much better!
Wasted too much time messing around with the 'panels' and wondering why there was no audio when I had 'mute' pressed on the keyboard! After that, everything is good ... even (most) videos play ok! Thanks again. Paul

This is all because of the war between Gnome and Canonical. That war is also the reason why I went to another distro (Arch in my case, not for beginners, but a great experience to set up).

---

### Post by jerrrys on 2011-08-28
its not a war, its change and change is enviable to happen to all distros

---

### Post by Thewhistlingwind on 2011-08-28
mini.iso

I'm pretty sure thats the name of the Ubuntu iso that comes with bash and apt-get.

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by jerrrys on 2011-08-28
[http://ubuntuforums.org/showthread.php?p=11196230#post11196230](http://ubuntuforums.org/showthread.php?p=11196230#post11196230)

---

### Post by jerrrys on 2011-08-28
[http://ubuntuforums.org/showthread.php?p=11196230#post11196230](http://ubuntuforums.org/showthread.php?p=11196230#post11196230)

---

