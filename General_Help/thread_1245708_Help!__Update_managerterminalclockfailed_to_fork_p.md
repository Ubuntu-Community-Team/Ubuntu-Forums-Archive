---
title: "Help!  Update manager/terminal/clock/failed to fork pty"
date: 2009-08-20
forum: General Help
---

### Post by svtdragon on 2009-08-20
Ladies and gentlemen,

I've got an issue:  if I try to open a terminal or run update manager, I get an "error failed to fork pty" popup.  I haven't made any changes to my /etc/init.d/mountdevsubfs.sh and I do have a symlink at /etc/rcS.d/S11mountdevsubfs.sh.  

What I did make changes to is /etc/default/rcS.  I changed utc=yes to utc=no, since I just installed the Win7 RTM and am now dual-booting.  

I rebooted and it loaded up as a read-only partition.  There were some errors about ": not foundt/rcS 9:" This was all caused by... me using ext2fsd from within windows to get at my main drive.  This is where I changed rcS from.  I rebooted to find that fstab and mtab had options for my main disk "errors=remount-ro", so I removed those, ran "init 1" and from there, fsck. 

Rebooted, and it was fine, and now I have this error again.  Further complicating things, I just installed the latest kernel rev last night, so I'm not sure if that has anything to do with this.

Help?

---

### Post by svtdragon on 2009-08-20
Turns out, even though modifying rcS was involved in my minor modifications, that the source of the problem was the upgrade from kernel 2.6.28-14 to -15.  I picked kernel 14 from the grub menu and it booted up just fine.

Hooray for unnecessary convolution.

---

