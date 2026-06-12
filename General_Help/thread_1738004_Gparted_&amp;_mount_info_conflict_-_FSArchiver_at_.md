---
title: "Gparted &amp; mount info conflict - FSArchiver at fault?"
date: 2011-04-24
forum: General Help
---

### Post by LewRockwellFAN on 2011-04-24
Gparted tells me sdb1, which is another ubuntu installation, is mounted as /tmp/fsa/20110424-still-more-numbers-I-can't-copy-n-paste while bash gives me this information:

f@f-U64:~$ sudo umount /dev/sdb1
umount: /dev/sdb1: not mounted
f@f-U64:~$ 

I closed gparted, ran umount again and reopened gparted and nothing had changed. The name of the mount point, including the date like part somewhat like the name I just gave a FSArchiver backup of sdb1 make me think FSArchiver is at fault. At least in the sense it should have let go of that partition. I don't see a process in System Manager with a name that suggests FSArchiver. Anyway, regardless of how FSArchiver is involved why should these programs see the mount status differently?  Am I being dumb or is this a bug, or at least a malfunction? And who should I report it to? Gparted people? Bash people?

I am running the 64 bit version of 10.04. The mounted/not-partition is a 32 bit installation of the same. Pentium D, 2 G of RAM.

---

### Post by Paddy Landau on 2011-04-24
I have not seen this type of discrepancy before.

Try opening System > Administration > Disk Utility to see what that says.

It may be that FSA is using some kind of loop mount, which GParted and mount are seeing differently. That's just a guess on my part, though.

---

### Post by LewRockwellFAN on 2011-04-24
I'm sorry. By the time I read your reply I had rebooted which eliminated the weirdness. I just spent a few hours carefully documenting my every step trying to reproduce this but all seems to work as expected now. If it happens again I won't reboot until I look at that, at least. Thanks, anyway.

---

### Post by LewRockwellFAN on 2011-04-24
AHAAAA! For what it's worth if anyone has similar issue I did gather one additional datum after I had given up. In the process of trying to reproduce the error, I created another FSArchive backup. Now I just noticed something I should have then. The second backup (and it is only the second time I've run FSArchive so I didn't know what file size to expect) was three times the size of the first even though this time I had remembered to run bleachbit (which empties trash cans, cleans up behind apt, deletes unneeded caches, etc.), move a few things off the desktop to a data partition, and generally clean up the installation before backing it up, so it should have been smaller, not larger. Evidently FSArchive (which the developers caution not to depend on being perfect yet) terminated abnormally and had NOT made a complete backup the first time even though I would have sworn the the output in the terminal made it look like it completed successfully. I bet there is terminal log somewhere if I haven't bleachbited it out. Anyway, thanks, Paddy.

---

### Post by Paddy Landau on 2011-04-25
Well, glad you found that.

If you require a full backup of your entire partitions, look at [CloneZilla]("http://www.clonezilla.org/"). It's a bit confusing to understand at first, but once you've "got it", it's very easy to use. I back up to an external hard drive. It works on Windows as well, so once you have a virus-free working version of Windows, back it up with CloneZilla.

---

### Post by LewRockwellFAN on 2011-04-25
Thanks. I love Clonezilla. I've used it for years.  I've also tried to get Clonezilla to boot from its own partition on a hard drive but never succeeded. But I'm an unfaithful lover and I'm flirting with Partimage, FSArchiver, and DD. I looked at KDE Partition manager in this context also but we won't have a second date cause as far as I can tell it won't compress worth a hoot. So far FSArchiver looks the best, but I haven't tried a restore yet. What I want is to make it so much easier than Clonezilla I do it more often. The best procedure I've worked out so far is to clean up, reboot in another partition and use FSArchiver. That way I can use the high compression setting, give it only one core, and continue to do other stuff while it runs. Might not be worth the drive space to most people if is the only thing you install another boot partition for but I like to experiment with different setups anyway.

---

