---
title: "2nd Distro Ideas?"
date: 2009-12-11
forum: General Help
---

### Post by black28 on 2009-12-11
hey guys, so i'm running Xubuntu 9.1 on a HP Vectra VL400 800 something MHz 60 GB HDD, 256mb+128mb Ram, 

i have a extra 10bg HDD that i can install into my desktop tower and was wondering what a good 2nd distro would be for me to install on to that HDD, and what i could use it for? programming (have no clue but willing to learn) or maybe music or something. what do y'all think? thanks.

---

### Post by 3rag0n on 2009-12-11
Looks like you have a somewhat low-end machine. Well, if you choose suse or mandriva or some other such distro, IMHO you'll not learn much apart from what you know from your ubuntu experience ( they tend to hide the guts of the system ). I recommend Arch Linux. Because it is a minimalist distro which comes barebones initially, you have to build your system from scratch. Since you choose to install exactly what programs you want, It wont be a memory hog. And most important of all, you'll get to know how a unix/linux system works.

Music and programming? You can do that in (almost) any distro.

Check it out, if you really want to learn, you wont regret it : [http://www.archlinux.org/]("http://www.archlinux.org/")

---

### Post by black28 on 2009-12-11
yah, well i was thinking of using my Xubuntu 9.1 as a "Main" system to save all important files, and what ever to. and then use this second one to play around with and stuff. for the low end part it doesnt bother me. as long as i can get good internet access, and use it for everyday PC uses i'm good. main thing is i got my desired resolution working. i play PS3 games. not too much of a fan of PC Games. kinda wanted to learn linux and get into the programming. (for fun) but who knows...i might start making a living off program making. lol.

---

### Post by MisfitI38 on 2009-12-11
Slackware would also be a fun choice.

---

### Post by ST3ALTHPSYCH0 on 2009-12-11
What about alpha testing 10.04. You'll be able to provide feedback about what does and doesn't work on low end hardware, and give back to the community.
I plan on alpha testing on my legacy machine, as soon as I get some money together for another HDD.

---

### Post by waynep on 2009-12-11
Another hard drive? Run a virtual machine!

---

### Post by 4Orbs on 2009-12-11
Assuming you plan to dual boot: It would be prudent to first get a good idea of what happens to the boot loader when you install a second os. The new distro will overwrite the boot loader on the mbr (if that is what you tell it to do), and it probably won't detect your Xubuntu system (because Xubu uses grub2), and so you will be left without access to the Xubuntu system from your newly installed boot loader. You'll need to learn to manually add other boot options to the boot loader, which is another can of worms.

---

### Post by Ylon on 2009-12-11
Puppylinux.

---

### Post by andrew.46 on 2009-12-13
Hi black,

> **black28 said:**
> i have a extra 10bg HDD that i can install into my desktop tower and was wondering what a good 2nd distro would be for me to install on to that HDD, and what i could use it for? 

I second Slackware as an interesting distro to install and since it is a superlative compiling environment you could perhaps experiment with some of the many media applications that respond really well to compilation + tweaking such as MPlayer, FFmpeg, vlc and transcode.

All the best,

Andrew

---

### Post by Bigtime_Scrub on 2009-12-13
I would use Fedora, xfce or lxde spin.

---

