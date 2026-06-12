---
title: "Wise to use Ubuntu CD to delete &amp; resize partitions?"
date: 2006-02-12
forum: General Help
---

### Post by happyponcho42 on 2006-02-12
I currently have Ubuntu Breezy and Kubuntu Breezy installed on the same hard drive (2 different partitions).  It just came to mind that I can save the wasted hd space by just installing the kubuntu-desktop on my Ubuntu setup and remove Kubuntu from my system all together.

Is it wise for me to boot from the Ubuntu cd so I can enter the setup process just to use it's partitioner?  I was planning on getting to the partition setup stage, deleting the partition with Kubuntu on it, then resizing my Ubuntu partition to include the rest of the hard drive space, then reboot right after (exiting before the Ubuntu setup process continues).

Would that method work, or would it interfere with the GRUB boot loader and start giving me errors about not being able to find Kubuntu?  Kubuntu is on hda1 and Ubuntu is on hda2.  All my data and customization is on hda2 (Ubuntu) so I'm wishing to remove Kubuntu.  Being that Kubuntu is the first partition, and perhaps where the mbr is located on, would following the methods i just outline interfere with GRUB and result in me having to redo everything?

\\:D/

---

### Post by happyponcho42 on 2006-02-12
I have decided to resort to gparted and just delete the Kubuntu partition and format it as ext3.  I'll just mount it to my current Ubuntu installation rather then try to make one large partition.

I may even follow the tip someone suggested and move my /home to the new partition so I can be free to fool around with my OS without fear of loosing data.

---

