---
title: "Going from ext2 to ext3"
date: 2006-03-09
forum: General Help
---

### Post by Danni on 2006-03-09
I made a mistake during installation, and used ext2 as the filing system instead of ext3. I would like to change this, as I suffer a lot of powercuts and it takes forever to reboot.

Is there an easy way to do this without reinstalling everything?

---

### Post by John.Michael.Kane on 2006-03-09
[http://www.troubleshooters.com/linux/ext2toext3.htm](http://www.troubleshooters.com/linux/ext2toext3.htm)

---

### Post by retsaw on 2006-03-09
Yeah, you can use tune2fs to add the journal, which converts it from ext2 to ext3.  Just type in a terminal```
sudo tune2fs -j /dev/hda1
```This assumes you have installed Kubuntu on hda1 if you have installed it on a different partition, you'll have to change that to reflect the partition you installed it on.

After that, you'll need to edit your /etc/fstab and change the filesystem for your root partition from ext2 to ext3.  If you don't want to do it from the terminal you can do it from Disk & Filesystems in System Settings.

---

### Post by Danni on 2006-03-09
Thank you so much :)

I'll do it straight away :)

---

### Post by John.Michael.Kane on 2006-03-09
Your very welcome Danni... And take your time doing it... if you have any more problems please post..

---

