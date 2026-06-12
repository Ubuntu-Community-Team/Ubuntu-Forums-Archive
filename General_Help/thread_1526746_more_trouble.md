---
title: "more trouble"
date: 2010-07-08
forum: General Help
---

### Post by unbuntunewb on 2010-07-08
so a few days ago this happened
[http://ubuntuforums.org/showthread.php?t=1523958](http://ubuntuforums.org/showthread.php?t=1523958)

I un-installed and re-installed using a dual boot. Everything was fine. Now when I choose ubuntu 2.6.32-23 on the grub it does not load up my desktop but takes me to a command line terminal where I log in and it says "welcome to ubuntu"

On my grub menu there is another version of ubuntu, Ubuntu 2.6.32-21. When I chose this one it also had problems but had an option where I could restore the factory settings on the video drivers. I did that and now its working although it looks like crap compared to what it was. There is no option to do this on the 2.6.32-23 

Why did my custom settings work for a while then suddenly crap out on me? is it this 2.6.32.23 version of ubuntu? Is it my video card? (nVidia) 

How do I restore the original settings on the latest version of ubuntu on the grub, and then how do I get my custom settings to work again? Ive tried the following on the terminal I get instead of the desktop vbut it does not work.

sudo dpkg - reconfigure xserver - xorg
sudo dpkg - reconfigure -p high xserver - xorg

Please help me!

---

### Post by unbuntunewb on 2010-07-08
This is odd, it randomly started working on the latest version. I noticed one thing though, on the grub when I load an older version of ubuntu the ubuntu opening screen with the name "ubuntu" is full screen and crisp, when I open up the newer version on the grub that same screen is not full screen and the image looks glitchy, almost wobbly but then the desktop is perfect. Any ideas?

---

### Post by Vincentlaborant on 2010-07-08
> **unbuntunewb said:**
> This is odd, it randomly started working on the latest version. I noticed one thing though, on the grub when I load an older version of ubuntu the ubuntu opening screen with the name "ubuntu" is full screen and crisp, when I open up the newer version on the grub that same screen is not full screen and the image looks glitchy, almost wobbly but then the desktop is perfect. Any ideas?

I think the screen resolution during the boot is wrong. You can change it easily with manuals/ guides available on several forums.

---

