---
title: "Nautilus stuck as zombie"
date: 2011-05-20
forum: General Help
---

### Post by harricklomax on 2011-05-20
Hey.  This problem started a few days ago and so far only occurs when I'm moving files between my computer and my external hard drive.  The "File Operations" window will stop and stay frozen, then my CPU usage goes up to 100%.  I can't open new folders, the file transfer never completes, and often I can't open Terminal or System Monitor, although sometimes they work.  Firefox, Banshee, and other programs still run.  CPU stays at 100% although it says nautilus is using 0 and acts normally, not as if it's straining or slowed down, just as if nautilus is dead.

In System Monitor, when it will open, it shows nautilus as Zombie.  I cannot stop, end, or kill it from there.  Cannot access my external drive either, and when I try to shutdown or restart the computer, it just goes to the purple Ubuntu screen and sits there.  I have to cut off the power to shut the machine down.  This has happened about six times in the last three days.  Seems to only happen when I'm moving over a GB of material, but I'm not positive.

Running 10.04, up to date to the best of my knowledge
Computer is a HP Pavilion laptop, dv6000

Appreciate any help, thanks.

---

### Post by tgalati4 on 2011-05-20
Open a terminal in another workspace.  When it happens:

dmesg | tail -50

Post any details that seem related.

---

### Post by linuxinstalledfromhdd on 2011-05-20
I get that sometimes when i am dealing with an external drive that is formatted for windows partitioning. 

Common sense dictates if you are going to be doing a considerable amount of file transfers to an external hard drive device, to make sure it is partitions and formatted with linux structure.  Not fat32 Not Ntfs.

---

### Post by harricklomax on 2011-05-21
Thanks for the replies.

tgalati4:  I will do this if and when it happens again.

linuxinstalledfromhdd:  You're right, and I now know this is an option, but I'm still learning to work with Linux and since the drive worked out of the box when I got it a few months ago, I never thought to change the formatting.  Now, the drive has more material on it than I can fit on my internal hard drive, so reformatting would be difficult at the moment, since I assume it would erase my data.  None the less I intend to do this at some point.

---

### Post by tgalati4 on 2011-05-21
It could be that the USB port is worn out or the external disk is drawing more power.  Do you have an external power supply for this external disk?  Is it putting out full voltage?

When Nautilus gets stuck, it's usually an I/O wait because a mounted disk stopped responding.  It will remain stuck until the disk comes back on line.  Dmesg will show I/O wait or other errors.  Try a different USB port, a different cable, a different disk power supply.

---

### Post by harricklomax on 2011-05-24
tgalati4, I tried this.  I moved the external, which does have it's own power supply, to a different USB port.  It was running through an extension device, a multi-pronged USB strip like a power strip, which had not been a problem before.  I plugged it directly into the computer and since then I moved a large number of files and there hasn't been a crash, so that may have been the problem.  I will keep testing this out for a while, since it had been on that strip a long time and there had never been a problem before, but it looks like that may have been what was causing the freeze.
thanks for the idea

---

### Post by RivetingScholar on 2011-05-24
I know that many Linux applications have config files stored in hidden (".*") directories within the user's home. Have you considered deleting any user-specific configurations for Nautilus? Also, have you considered the dpkg reconfigure command?

---

### Post by linuxinstalledfromhdd on 2011-05-24
Try formatting your external hard drive like this:

[http://www.mattcutts.com/blog/format-external-drive-for-linux/](http://www.mattcutts.com/blog/format-external-drive-for-linux/)

---

