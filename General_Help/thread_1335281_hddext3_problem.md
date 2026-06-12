---
title: "hdd/ext3 problem"
date: 2009-11-23
forum: General Help
---

### Post by balkanji on 2009-11-23
Hi,everybody! -
I'm really stuck:( My kubuntu 8.04 is not booting from the hdd. I see my hdd, grub starts, brings the menu, starts a few services but then it gets to fsck and gets stuck with block read errors. I boot from liveCD, see my hdd and partitions in gparted (but NOT in testdisk) and can mount the partitions. I can list the directories but most/all files are corrupted/unreadable :( e2fsck reports:

e2fsck: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda1

my /home partition is on this hdd with all my data from the last year, some of it copied over from 20+ years:(..
What shall I do, any ideas?
Please..

---

### Post by ptn107 on 2009-11-23
So when you boot the live CD to the desktop, open a terminal (Applications -> Accessories -> Terminal), and type:
```
sudo fsck /dev/sda1
```
Nothing happens?

---

### Post by balkanji on 2009-11-23
> **ptn107 said:**
> So when you boot the live CD to the desktop, open a terminal (Applications -> Accessories -> Terminal), and type:
```
sudo fsck /dev/sda1
```
Nothing happens?

What happens is EXACTLY what I told above:

fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda1
Could this be a zero-length partition?


:(

---

### Post by ptn107 on 2009-11-24
Many who encountered this problem [from what I read] were told their disks were beginning to fail.  Most of them also said they had improper shutdowns that started the problem.  They had to physically remove the drive from the machine and put it in as a slave drive in another computer so they could backup the data.  After the data was backed up, the drives were reformatted ext3/4 and a thorough 'fsck' and 'badblocks' were run to keep future data from being written to the bad areas.  The drives were then returned to the original machine.

---

### Post by balkanji on 2009-11-24
> **ptn107 said:**
> Many who encountered this problem [from what I read] were told their disks were beginning to fail.  Most of them also said they had improper shutdowns that started the problem.  They had to physically remove the drive from the machine and put it in as a slave drive in another computer so they could backup the data.  After the data was backed up, the drives were reformatted ext3/4 and a thorough 'fsck' and 'badblocks' were run to keep future data from being written to the bad areas.  The drives were then returned to the original machine.

Well, I wouldn't mind losing the hdd if I could save my data!..I'm afraid of doing that could cause (greater or complete)loss of the data. It seems like the journal is corrupt but I don't think there was much going on on the drive as the break down happened, so in the journal won't be an awful lot to replay...ould it be possible to mount it as ext2, i.e. without the journal so I could read out my data?..then I could think about rformtting/thrashing it?..
thanx!

---

### Post by ptn107 on 2009-11-24
You can use tune2fs to disable the journal on an ext3 file system effectively converting it to ext2[1].  From the live CD you can try:

```
sudo tune2fs -O ^has_journal /dev/sda1
sudo fsck.ext2 -f /dev/sda1
```

You can then mount the drive as ext2 (manually or change /etc/fstab and reboot) and then try to recover the data on the pc or on another pc.

[1]http://batleth.sapienti-sat.org/projects/FAQs/ext3-faq.html

---

### Post by balkanji on 2009-11-27
> **ptn107 said:**
> You can use tune2fs to disable the journal on an ext3 file system effectively converting it to ext2[1].  From the live CD you can try:

```
sudo tune2fs -O ^has_journal /dev/sda1
sudo fsck.ext2 -f /dev/sda1
```

You can then mount the drive as ext2 (manually or change /etc/fstab and reboot) and then try to recover the data on the pc or on another pc.

[1]http://batleth.sapienti-sat.org/projects/FAQs/ext3-faq.html


Thank you very much for bothering to answer me! You're the only one and I am really grateful! Being fighting for a week with the problem I achieved the following:

Booted Kubutu 9.10 LiveCD, installed gparted, it sees my hdd and the partitions on it, but marks them with an "atention" sign, probably that's why udev is not mounting them and PySDM doesn't see them either.

Booted Kubuntu 9.04 from LiveCD. Installed gparted. Sees partitions. Can mount them as statically created devices /dev/sda1, /dev/sda2, etc.. Did fsck.ext3 on them, reported all partitions clean but ONE- the boot partition sda1 :( tune2fs -O &#293;as_journal reports: 

ubuntu@ubuntu:~$ sudo tune2fs -f -O ^has_journal /dev/sda1
tune2fs 1.41.4 (27-Jan-2009)
The needs_recovery flag is set.  Please run e2fsck before clearing
the has_journal flag.

Although I'm forcing it!

trying:

ubuntu@ubuntu:~$ sudo tune2fs -f -O ^needs_recovery /dev/sda1
tune2fs 1.41.4 (27-Jan-2009)
Clearing filesystem feature 'needs_recovery' not supported.

so I'm stuck again:(...

Booted win Live-CD!!! total commander sees and reeds ALL partitions thru its "ext2plugin" without problems!...And note that's WINDOZE!!!...:(((

So, what now?? I don't know:( Seems like I'll have to reformat my hdd..but HOW can I know that it's physically ok and not generating eratical erors and going to die on me in an inappropriate moment???...

Thank you again for all your answers!

---

### Post by ptn107 on 2009-12-01
If you have all your data off of the drive, just reformat it ext3 or ext4 and use as normal.  All ext2/3/4 partitions are set up to be automatically checked by fsck at boot after so many mounts anyway.  That should keep things healthy (until the disk physically doesn't want to read or write anymore that is).

---

