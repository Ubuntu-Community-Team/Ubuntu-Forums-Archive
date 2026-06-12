---
title: "Tried a variety of things, still can't shrink NFTS Partition"
date: 2009-08-17
forum: General Help
---

### Post by Slaskie on 2009-08-17
I have been trying for a long time now to make a dual boot between windows xp and kubuntu, except that on whatever partitioner program I am using the "shrink" option for the big 99 GB NTFS Partition is greyed out. I have tried cleaning up the hard drive, disabling paging, using various Live CD partitioners such as Gparted and PartedMagic, and last but not least, defragging 6-10 times. None of these have allowed me to shrink the XP partition (which I have ample free space on of course) and therefore create a ext4 / 3 partition on which I can then install kubuntu. Am I hopeless or is there more work to be done? Thank you.

---

### Post by michy99 on 2009-08-17
Can you post a screenshot from gparted?

---

### Post by Slaskie on 2009-08-17
Here is the screenshot.

---

### Post by ppirilla on 2009-08-17
I've run into problems in the past where the OEM Windows install intentionally puts system files in some of the last sectors on the drive, making it impossible to resize the partition.

---

### Post by Slaskie on 2009-08-18
:( I guess this means I'll have to keep using wubi and replacing it every few months when it starts to break down

---

### Post by HiImTye on 2009-08-18
have you tried it on the live CD? there's a screen where you choose how to do the drives and one of them is just a slider with something like 'auto-resize drive /drive/location' and you drag the slider left and right to resize it

might be worth checking out if nothing else is working. also make sure you're not using a swap partition on the same drive. also the live CD has Gparted (option: custom) so you can manually set your partitions

GParted should resize the partition regardless of what data is at the end of the drive. ntfsresize (the tool used by both qtparted and gparted to resize ntfs partitions) resized the drive regardless of whether files that the file system would not let you move are present at the ends of the partition. best bet is boot from a live CD, disable the swap partition if you have one on the drive

---

### Post by HiImTye on 2009-08-18
also make sure you can mount it. sometimes NTFS partitions get 'locked out' and need to be force mounted

---

