---
title: "Can't Install Packages"
date: 2012-09-06
forum: General Help
---

### Post by MckayKnight on 2012-09-06
Howdy all, I'm trying to install Weechat on top of my Ubuntu 12.04.1 LTS release. Prior to this I recently installed Wicd and removed the default network-manager for Ubuntu. As it was giving me trouble.

When I search for Weechat in Ubuntu's Software Center I see that the 'Install' button is grayed out and below the program's description it implies that 'No network connection is available' yet I'm on the Internet and I can browse freely.

I also tried to see if other programs had the same problem and yet to my dismiss they do. Is this a known bug where I am forced to use the 'network-manager' program just to install any program in the existing Software Center?!?

I did also try manually downloading Weechat's package and the button was still grayed out preventing me from installing anything without the 'network-manager' so it seems.

---

### Post by MckayKnight on 2012-09-06
I don't see the point of using sudo apt-get update. I can install Weechat through a Terminal but I can't install it from within Software Center without having to reinstall the 'Network-Manager' program.

Still doesn't solve my problem as I would have to install every program from the Terminal and from then that'll be pretty annoying.

I don't want to reinstall 'network-manager' as it's buggy and continuously disconnects me from my Wireless-N wifi connection.

I'm assuming there's no workaround at this moment I also seen a newer version of 'network-manager' but I'd have to compile it to see if it fixes anything. I tried sudo apt-get update and it just went through it's process.

As you can see Geany is even grayed out. [http://i.imgur.com/nwgL3.jpg](http://i.imgur.com/nwgL3.jpg)

Changing the repository won't fix my problem. I guess I'll have to just use the upgraded Network-manager tool.

---

### Post by Epodx64 on 2012-09-07
[https://launchpad.net/~mathieu-tl/+archive/nm](https://launchpad.net/~mathieu-tl/+archive/nm)

might have the network manager your looking for?

---

### Post by MckayKnight on 2012-09-07
I'll check that out Epodx64 thanks for the PPA been trying to find it on launchpad.

---

### Post by Epodx64 on 2012-09-07
> **MckayKnight said:**
> I'll check that out Epodx64 thanks for the PPA been trying to find it on launchpad.

yep, hope it works for you.

---

