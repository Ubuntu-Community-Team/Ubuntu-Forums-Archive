---
title: "can't boot my lvm partition(ubuntu 9.04)"
date: 2011-07-01
forum: General Help
---

### Post by jamil.farooq@hotmail.com on 2011-07-01
Hi,

i can't boot from my lvm partition.


it gives  ALERT /dev/mapper/lmspv1-lmslv1 not found error
before this it also give error of not finding physical volume with given uuid. 

1. as i have swap some disks here n there so i m not sure if uuid changes due to this.
2. exit again and again intrifms does not work so i think its not rootdelay problem.
3. how come i can't see my lvm partition uuid by calling ls -l /dev/disk/by-uuid.
4. I tried lvdisplay but it gives me same physical device missing error with uuid as it were on boot.



please help its urguent

regards

---

### Post by jamil.farooq@hotmail.com on 2011-07-01
when i run vgchange -a y
 i got this messasge
 
Couldn't find device with uuid 'ivb13Y-Ul95-8Ash-BRkf-FxEY-Hb7X-KUsmZj'.
  Couldn't find all physical volumes for volume group lmsVG1.
  Couldn't find device with uuid 'ivb13Y-Ul95-8Ash-BRkf-FxEY-Hb7X-KUsmZj'.
  Couldn't find all physical volumes for volume group lmsVG1.
  Volume group "lmsVG1" not found

i can see my lvm partition in GParted as /dev/sda2 with information sign

[IMG]file:///tmp/moz-screenshot.jpg[/IMG][IMG]file:///tmp/moz-screenshot-1.jpg[/IMG]

---

