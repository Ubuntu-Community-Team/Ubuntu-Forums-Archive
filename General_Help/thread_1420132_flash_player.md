---
title: "flash player"
date: 2010-03-02
forum: General Help
---

### Post by cragtom on 2010-03-02
I need the flash player so I can watch videos on you tube please I have it already for vista but need it for ubuntu..........
Many thanks in advance .............

---

### Post by Ozymandias_117 on 2010-03-02
Several options.

1. You can install ubuntu-restricted-extras which contains flash, java, support for mp3 and other common things people use

2. You can install flashplugin-nonfree This will get you just flash

3. Go to adobe's site and download the .deb they offer and install it.

1 and 2 are preferable because if there are updates, they will be installed automatically. If you wish to use 1 or 2, you can either go to System -> Administration -> Synaptic Package Manager and search for them there, or open up a terminal and type "sudo apt-get install *packagename*" Package name is either ubuntu-restricted-extras or flashplugin-nonfree depending on your choice. To install the .deb, just open up your downloads folder and double click on it.

---

### Post by Ghost|BTFH on 2010-03-02
> **cragtom said:**
> I need the flash player so I can watch videos on you tube please I have it already for vista but need it for ubuntu..........
Many thanks in advance .............

So...
[I]
sudo apt-get update
sudo apt-get install flashplugin-installer[/I]

Or go into System -> Administration -> Synaptic Package Manger and search for flash player, find it and install it.

If you can't find this package...then you need to add Multiverse and Universe to your repositories, but I believe they're on by default now, so...no excuses - go find it and install.

Cheers,
Ghost|BTFH

---

