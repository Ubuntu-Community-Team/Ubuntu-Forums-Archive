---
title: "Enabling nVidia driver makes file browsing very slow in 10.04"
date: 2011-05-16
forum: General Help
---

### Post by DawieS on 2011-05-16
My two youngest daughters each got a new video card from their elder brother last Christmas. I installed the two new cards in their computers, and up till now have problems to get it working properly in Ubuntu 10.04. They previously ran fine on on-board video, given the limitations thereof.

The specs are as follows:

Machine A:
Intel Quad Core 9300 @ 2.00 GHz
4 GB DDR2 RAM @ 800Mz
NVidia GF 210 (PCIE) 512MB DDR3 64Bit

Machine B:
AMD Single Core 3500+
2 GB DDR2 RAM @ 800Mz
NVidia GF 210 (PCIE) 512MB DDR3 64Bit

I did the following test on both machines:
On the left side of the screen, I opened a terminal with "top" displayed. On the right, I opened a nautilus file browser in "list" view, clicked on "File System", and then clicked (from the bottom upwards) on the "+" sign in front of the sub-folders, in order to open them.

On machine B:
With the driver (version current) installed and enabled, it takes several seconds for each of the folders to open and the contents displayed. Clicking ahead causes the clicks to be buffered, and it can take more than 30 seconds to open a folder if it contains many files/folders. "Top" shows that xorg consumes 94% cpu, and nautilus 6% during this time. The hard drive LED flickers slowly every now and then.

With the driver removed, the response is almost instantly. "Top" shows that nautilus consumes 40% cpu, and xorg 15%, leaving ample processing power still available. The hard drive LED flickers fast.

On machine A:
With the driver installed and enabled, the delay is noticeable and xorg consumes about 70% cpu, however the brute force computing power of the machine almost keeps up with the clicking during the test. I thus kept the driver enabled, with the advantage that compiz effects can be enabled.

Both machines are dual boot with XP, and the video cards perform well in XP, especially with the latest games that makes use of the features of the new generation video cards.

On machine B I have tried the following to no avail:
- Completely fresh install and update of Ubuntu 10.04.
- Downloaded and manually installed the latest proprietary driver from the NVidia website.
- Searched for possible solutions on the forums and tried a few, such as reconfiguring the graphics with "sudo dpkg-reconfigure -phigh xserver-xorg" in a terminal, and a few reboots and driver re-installs.

I have come to the conclusion that I may as well remove the video card and utilize machine B with on-board graphics only, and still get the same performance in Ubuntu.

Any advice will be greatly appreciated.:razz:

---

