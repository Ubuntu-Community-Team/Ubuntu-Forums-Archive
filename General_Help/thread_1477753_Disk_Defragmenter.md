---
title: "Disk Defragmenter"
date: 2010-05-09
forum: General Help
---

### Post by 0918127 on 2010-05-09
Hi 
 
How can do i  Defragmenter Disk on ubuntu?

---

### Post by finlost on 2010-05-09
Unpossible!

Not needed

Psst...trying searching the forums before starting all these threads.  :)

---

### Post by unplugged23 on 2010-05-09
You'll never need to defragment your harddrive while using linux. Although if you wanted to just for fun, I'm sure you could find one browsing through the ubuntu repo's.

---

### Post by Zireth ZH on 2010-05-09
Hi pal .. theres no need to defrag ur disks on linux.. u dun have to worry...

---

### Post by LoneWolfJack on 2010-05-09
just to expand. due to the different concept of the filesystem, you don't need to defrag your drive. ext3/4 can get fragmented if your disk is almost full, however.

if you still feel the need to defrag your drive, simply move all your data to another drive and back again (make sure, the data really gets deleted from the source drive), linux will take care of the rest.

---

### Post by CryptoPaul on 2010-05-09
"Linux filesystems don't need defragmenting" - Is, I'm afraid, perhaps one of the most repeated myths about Linux...

What Linux does do, is to try to avoid fragmenting the inode tables, the actual data can, and does, get fragmented across the disk.

Good Linux defrag utilities are very few and far between, in fact if anyone knows of one that can handle ext3/4 journaling filesystems I would be quite interested.


Paul

---

### Post by Pjotr123 on 2010-05-09
> **CryptoPaul said:**
> "Linux filesystems don't need defragmenting" - Is, I'm afraid, perhaps one of the most repeated myths about Linux...

What Linux does do, is to try to avoid fragmenting the inode tables, the actual data can, and does, get fragmented across the disk.

Good Linux defrag utilities are very few and far between, in fact if anyone knows of one that can handle ext3/4 journaling filesystems I would be quite interested.


Paul

Untrue. This is the technical explanation why Linux doesn't need defragmenting (yes, yes, yes, really!):
[http://sites.google.com/site/easylinuxtipsproject/faq#TOC-How-can-I-defragment-the-hard-drive](http://sites.google.com/site/easylinuxtipsproject/faq#TOC-How-can-I-defragment-the-hard-drive)

And some more:
[http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting)

It's all a matter of good design, people.... :-)

---

### Post by dino99 on 2010-05-09
some usefull info about fsck may answer most of your questions

force it on next reboot:

sudo shutdown -F -r now

---

### Post by howefield on 2010-05-09
> **Pjotr123 said:**
> This is the technical explanation...

Thanks for the first laugh of this otherwise boring Sunday morning. :)

I can't tell you why I find it amusing.

---

### Post by 0918127 on 2010-05-09
please i want more information

---

