---
title: "Natty on netbook won't boot after crash"
date: 2011-09-23
forum: General Help
---

### Post by hobbit.trap on 2011-09-23
So my netbook crashed today, and since then it will not boot.  I'm  running 11.04.Natty Narwhal.  If I attempt to boot normally, then I see a  cursor blinking in the upperleft for a while (as usual), the screen  flashes to change resolution, and it stays black.  I've let it sit for  up to about 90 minutes and nothing changes.

The first thing I did was boot off a LiveUSB disc and ran 'fsck -fv' on  the / drive (ext4), which claims that no errors were found.  I am able  to mount the drive and 'cd' around the filesystem.

Next, I ran memtest for about an hour; it completed 2 full passes with 0 errors reported.

I've also tried a cold reboot (shut down, let the computer sit for a few minutes, boot back up).

The last thing I've tried was to boot in "Recovery" mode.  When I do  this, the computer begins to boot, flashes to switch resolution, and so  far everything looks fine.  Then the init scripts begin, and it stops at  a seemingly random place in the init scripts - it stops at a different  place each time.  The same happens if I select a previous kernel version  from the Grub menu.

I'm out of ideas and would greatly appreciate any help on this.  Thanks!

---

