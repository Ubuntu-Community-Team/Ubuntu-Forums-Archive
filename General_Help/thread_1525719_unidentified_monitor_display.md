---
title: "unidentified monitor display?"
date: 2010-07-07
forum: General Help
---

### Post by Da CalebMan on 2010-07-07
Hello fellow linux geeks;)

I'm having some strange problems with my monitor. It's an LG Flatron L1730S and the graphics card is a Nvidia Geforce 5600FX. The monitor is listed as unknown in monitor settings and is going at 51 HZ with performance and out of range issues in some game. How can I get ubuntu to recognise it, or better yet change the driver?

I did some googling and discovered a tool called displayconfig-gtk, but I can't install it in Ubuntu 10.04! Anyone know which way to go? Thanks, The Steel Banana

---

### Post by dcstar on 2010-07-07
> **Da CalebMan said:**
> Hello fellow linux geeks;)

I'm having some strange problems with my monitor. It's an LG Flatron L1730S and the graphics card is a Nvidia Geforce 5600FX. The monitor is listed as unknown in monitor settings and is going at 51 HZ with performance and out of range issues in some game. How can I get ubuntu to recognise it, or better yet change the driver?

I did some googling and discovered a tool called displayconfig-gtk, but I can't install it in Ubuntu 10.04! Anyone know which way to go? Thanks, The Steel Banana

Have you installed the Hardware Drivers for it?

Actually, on second thoughts is that card still supported in Ubuntu?

---

### Post by dino99 on 2010-07-07
try without xorg.conf

maybe add x-swatt ppa: [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

---

### Post by Da CalebMan on 2010-07-07
Yes, I have version 173 of the Nvidia graphics driver installed. It runs alright, believe it or not. It's the monitor driver I'm concerned about. Since it's not recognised by ubuntu, it's probably using some default plug-and-play... plugin. 

@dino99: yes, I do have the x update ppa. What did you mean about not using xorg.conf? Delete it? I'll make me a backup first ;)

Thanks for the replies :)

---

### Post by Da CalebMan on 2010-07-11
bump

---

