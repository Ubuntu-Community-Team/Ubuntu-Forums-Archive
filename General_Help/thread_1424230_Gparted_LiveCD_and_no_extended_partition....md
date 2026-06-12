---
title: "Gparted LiveCD and no extended partition..."
date: 2010-03-07
forum: General Help
---

### Post by Barriehie on 2010-03-07
Hey all,
So I've got hda2 that I would like to create an extended partition out of so I can add 3 more sub partitions for /tmp, /var, and /opt.  Below is a a pic, from my phone, of gparted after booting with the LiveCD.  How/why can't I create an extended partition with the unallocated space???

TIA,
Barrie

---

### Post by wilee-nilee on 2010-03-07
Your partition on the right end looks like it is set as a extended already. It is hard to tell what exactly the first one is. 

did you build the one on the right intending a swap?

---

### Post by Barriehie on 2010-03-07
> **wilee-nilee said:**
> Your partition on the right end looks like it is set as a extended already. It is hard to tell what exactly the first one is. 

did you build the one on the right intending a swap?

The one on the far right, red/blue, is the /swap that was made at install.  The one on the left is hda1, boot. Hmm, just looking in gparted again and yes, that IS an extended partition.  So I should be able to resize it and create partitions within it for my needs?

Thank you wilee-nilee!

---

### Post by uRock on 2010-03-07
> **Barriehie said:**
> The one on the far right, red/blue, is the /swap that was made at install.  The one on the left is hda1, boot. Hmm, just looking in gparted again and yes, that IS an extended partition.  So I should be able to resize it and create partitions within it for my needs?

Thank you wilee-nilee!

You can resize it or delete it then create a large extended partition, then recreate the swap within it.

---

### Post by Barriehie on 2010-03-07
> **iRock said:**
> You can resize it or delete it then create a large extended partition, then recreate the swap within it.

Cool!  Going to give it a go now. Thanks!

---

### Post by Barriehie on 2010-03-07
Thanks guys!  That worked out well.  Sometimes I need a blinking pointer... 8)

Barrie

---

### Post by uRock on 2010-03-07
Lol, I am glad it worked.:)

---

