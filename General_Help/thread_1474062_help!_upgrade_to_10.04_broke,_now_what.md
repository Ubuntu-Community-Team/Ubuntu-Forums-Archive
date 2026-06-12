---
title: "help! upgrade to 10.04 broke, now what?"
date: 2010-05-05
forum: General Help
---

### Post by chumley1970 on 2010-05-05
help! calling all linux nerds/gurus...

i upgraded ubuntu 9.10 to 10.04... and not only did it take 2 days to download and install, it died at the end after a bunch of bug reports generated (i didnt take time to look them over). now its 3/4 of the way installed, and not working (obviously!) what now? i burned a cd of 10.04, but if i install it from the cdrom will it nuke my home file? that would be really bad. bad. bad. 

how can i get lucid lynx install and save my home folder?

---

### Post by Soul Circuit on 2010-05-05
I had similar trouble. The only way I got it to work was to completely format the partition and reinstall Ubuntu. If someone else has a better idea go for it, but just in case if you can access all the files you want to keep you should back them up.

---

### Post by wwwil on 2010-05-05
Is your Home folder located on a separate partition?

If so you can use the CD to install, choose manual setup of partitions and format your old root partition for your new one. Then find your Home partition and just set the mount point.

Otherwise use the CD to boot into Ubuntu live and mount your Ubuntu partition, navigate to your home and copy your data onto a memory stick or other backup device.

This is my first post on the Ubuntu forums though I've been using Ubuntu for a while now so I hope I can help.

---

### Post by Vaphell on 2010-05-05
what wwwil says - if you have single partition you need to mount it and back up using some other device because it will be wiped during the installation
if you have separate home then you can leave it alone/select as home during install and skip formatting.

---

### Post by chumley1970 on 2010-05-06
my home folder isnt in a separate partition. i'm going to try to copy my home folder after booting from the live cd. is there anything else i should copy?

---

### Post by finlost on 2010-05-06
[Do this]("http://www.psychocats.net/ubuntu/separatehome") and then do a fresh install.

---

### Post by finlost on 2010-05-06
Dp

---

