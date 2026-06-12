---
title: "Cloning hard drive"
date: 2010-03-01
forum: General Help
---

### Post by agkq62 on 2010-03-01
Knew it couldn't be that easy. I have an ubuntu installation which has taken a long time to set up and I would like to clone it to another hard drive. I have a usb lead for connecting to the hard drive and I hoped I could copy the files to a spare computer and then copy to a new hard drive. The files as showing on the spare computer but when I try and copy the files I get the message

The folder " Private" cannot be handled because you do not have permissions to read it

Any way I can copy or is it mission impossible?

Thanks

---

### Post by switch10 on 2010-03-01
It is best to use a Live cd like clonezilla.  it will actually clone the entire partition.

---

### Post by agkq62 on 2010-03-04
Thanks, I am just about to try Clonezilla. The HD I want to move the image to already has XP loaded. Will I have to remove that?

---

### Post by switch10 on 2010-03-04
Hmm.  I'm not sure.  I found this tutorial though, it may tell say in there...[http://www.dedoimedo.com/computers/free_imaging_software.html](http://www.dedoimedo.com/computers/free_imaging_software.html)

---

### Post by agkq62 on 2010-03-04
Wow, that was quick. Thanks for the link.

---

### Post by ZeldeR on 2010-03-04
Step1. Take liveCD - for example ubuntu 
Step2. dd if=/dev/sda of=/dev/sdc
copy everything from sda to sdc (best solution)


Solution 2:
mkdir /mnt/test/
mount /dev/sdc /mnn/test

rsync -azv / /mnt/test


/dev/sdc = your second HDD ;)

---

