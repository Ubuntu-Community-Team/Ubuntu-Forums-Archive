---
title: "Won't boot - please help!"
date: 2010-03-18
forum: General Help
---

### Post by Chaos_Spear on 2010-03-18
So I'm running Kubuntu Karmic on my Dell Inspiron laptop - about 200 bug fixes behind because my only available internet is a cellular connection on a crappy wi-fi router - and last night, I suspended it, but it shut down instead.  Not a problem, it does this fairly often, figure the RAM gets jostled or something.

But when I go to boot it up, it gets stuck at the pre-loading screen before getting garbled and dropping to the shell, where it says "mount: mounting /dev/disk/by-uuid/[insert hex code here] failed: invalid argument".  Of course, mounting /root/sys, /root/dev and /root/proc fails, (directory does not exist) and it gives me the busybox initramfs prompt.

I have no idea what to do, please help!

---

### Post by Chaos_Spear on 2010-03-18
ALSO: My NTFS partition seems to work fine, as I can run my Vista system.

---

### Post by linden940 on 2010-03-18
get an up-to-date disk put it on and go to a coffee shop and get the updates....


you will have to go 2 the coffee shops ever so often to get the updates...other than i cant help you...one big problem...we dont know what your system has and what it dos not have...becuz its not updated....so ur kinda on ur own on this one bro

like i said best thing for you is to start over and just make sure you get the updates from time to time

---

### Post by Chaos_Spear on 2010-03-18
I tried booting off a live CD and it said something about being unable to mount /dev/sda1.  I don't recall seeing that the last time I tried.

---

### Post by Chaos_Spear on 2010-03-18
Anyone?  Please?  I don't know what would cause this, aside from my filesystem being corrupted... someone please tell me it's not!

---

### Post by ApEkV2 on 2010-03-18
Could be your filesystem bottomed up, ext4 has a sore spot for harddrive interruptions.

Try burning a copy of super grub disk and try booting your linux partition from that. 
But be careful, SGD is a powerful tool. I haven't used it enough to get acquainted yet.
If that doesn't work make sure your first boot device (in the bios) is set for the cdrom drive and try the live cd.
If all else fails, boot the live cd and backup what you can, it's reinstall tiem.

EDIT: this really should be under "Installation & Upgrades", more people who focus on this sort of problem.

---

### Post by Chaos_Spear on 2010-04-01
Good news!  So after doing more research, figured out my ext4 journal had an error.  Took me awhile to figure out how to run fsck on the partition, seeing as it's not built into the boot shell and my Karmic Live CD doesn't want to go live... tried to burn a copy of SGD but had problems with the CD-Rs I had available to me, so FINALLY gave up, decided to re-install Karmic, was looking for the Live CD and came across... my old Jaunty CD!  I decided to try that, and hey, whaddya know, it worked.  Two passes with fsck and my system was back.  I'm incredibly overjoyed.

Thank you people of the Internet!

---

