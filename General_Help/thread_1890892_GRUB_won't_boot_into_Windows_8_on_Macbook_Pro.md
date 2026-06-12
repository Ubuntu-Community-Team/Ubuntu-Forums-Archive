---
title: "GRUB won't boot into Windows 8 on Macbook Pro"
date: 2011-12-04
forum: General Help
---

### Post by zgrimshaw on 2011-12-04
Hello,
I had a Macbook Pro that was running OSX and Windows 8 DP. That worked fine.
Then I wanted to be able to boot from a linux live CD, so I installed rEFIt ([http://refit.sourceforge.net/]("http://refit.sourceforge.net/")).

This worked perfectly and I was able to boot into Windows, OSX and a Live CD of linux.
I then decided to install Backtrack 5.

Now I am triple-booting Windows 8, OSX and Backtrack 5. I am able to boot into OSX fine, and when I select BT5 in rEFIt it brings up GRUB and I can select BT5 from there and it boots fine.

Now here’s the problem, since I installed BT5 I can no longer boot into Windows 8 DP. When I try and boot Windows from both Bootcamp and rEFIt, it brings me to the GRUB menu.

In GRUB I can see my windows partition, but it's called "Windows Recovery Environment" but when I select it the screen goes black and after a minute or so it restarts the computer.

Does anyone have a solution to this problem?

Thanks!

---

### Post by 2F4U on 2011-12-04
Did you verify that Windows is still there and not accidentally overwritten by BackTrack. I don't use Windows, but as far Windows needs more than just a recovery partition. From what I know any Windows install has this recovery partition and a partition for the actual install.

---

### Post by zgrimshaw on 2011-12-04
Thanks for the quick reply!

Yes, Windows is still there. I can see the drive and all my files when I boot into both Backtrack and OSX.

---

