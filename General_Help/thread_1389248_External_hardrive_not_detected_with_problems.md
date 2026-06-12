---
title: "External hardrive not detected with problems"
date: 2010-01-24
forum: General Help
---

### Post by MultiThug12 on 2010-01-24
Hi can someone please help me here ive got ubuntu 9.10 i was having trouble detecting my external harddrive. I found a thread which surgested i do it manually in terminal with this;

sudo mkdir /media/myHD
sudo mount /dev/sdc/ /media/myHD
Now that didn't work instead ive now got an extra drive called myHD which is an exact duplicate of my Filesystem.

Can anyone explain how i can undo this without a reinstall.
Thanks

---

### Post by rbc on 2010-01-24
> sudo mount /dev/sdc/ /media/myHD

It may have just been a typo on your part, but that command probably should have been:
sudo mount /dev/sdc1 /media/myHD

When you say that the external HD isn't being detected, what do you mean? It's not showing up at all, it won't mount?......

With the external plugged in, reboot, then open terminal and type these consecutive commands:
mount
sudo fdisk -l (that is a lower case L, not the number 1)

Post back with the results

---

### Post by MultiThug12 on 2010-01-24
Thanks but i managed to sort it, i had to connect the external hard drive to a windows os and reformat the drive. now its working again.

As for the exta drive (my HD) with the system files. I did like a system restore and that restored the system to the last update or thats what i think it was.

---

