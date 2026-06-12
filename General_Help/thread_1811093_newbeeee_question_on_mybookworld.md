---
title: "newbeeee question on mybookworld"
date: 2011-07-24
forum: General Help
---

### Post by starfirey2k on 2011-07-24
p { margin-bottom: 0.08in; }  Any help on this would be great, I am trying to recover data from a 1tb mybookworld, these are the commands I am using to mount the drive
 sudo modprob md
 sudo mknod /dev/md4 b 9 4
 sudo apt-get install mdadm
 sudo mdadm –assembel /dev/md4 /dev/sdb4
 sudo mkdir /media/xyz
 sudo mount /dev/md4 /media/xyz
 sudo chmod -r 777 /media/xyz
 

 the error I am getting is with the modprobe line
 modprobe: command not found
 

 I just started using ubuntu for this recovery project, a real newbeeeeeee
using ubuntu 10.04 lts
 

 HELP.................

---

