---
title: "How to make faster and lighter Ubuntu"
date: 2010-04-25
forum: General Help
---

### Post by Kangarooo on 2010-04-25
I wanted to make fastest possible boot with lightest Ubuntu distro
What needs to be taken in mind to do that.

1.)X window system desktop enwironment (KDE, GNOME, XFCE, Openbox, etc)
KDE is very big (KUbuntu)
Gnome is big (Ubuntu)
Xfce is small (XUbuntu) my favorite
Openbox is very small (Crunchbang)

2.)File system (EXT4, XFS)
Many are using latest and safest EXT4 (if not then in new installations putting it)
But i found that faster mounts and works XFS then EXT4 witch im as using with Xubuntu
Statistics made from [http://www.debian-administration.org/articles/388](http://www.debian-administration.org/articles/388) (maybe a little old)
Somewhere i read that EXT4 is faster then XFS after kernel 2.6.30 but where i read that was no proof of that and when i asked in #ubuntu no one can confirm that

3.)Partitioning (Use whole disk, Manual partitioning)
To ilustrate ill use theese legends P=programs, D=data files, B=Boot files, S=Swap file, []=partition.
a.)Using whole disk files with time will be stored like this.
[BBPPDDPDBPDBDPBDPBDBDPPBDBPDBBDP][SSSSS]
swap file will be at end of disk and physicaly on disk it means it will be on outer side so reading writing is slower. But since Swap will be used more then any of P and D it needs to be more to begining (inner side of disk) therefore better solution
b.)Manual partitioning.
Boot file if is first it will be very fast executed. I think can even be at end since booting is only once a day but i havent tryd yet making it at end.
Swap at first. Then programms and data as they are not beeing used all at same time then all left till end.
Also as i see my boot/ is just 43 mb enough will be 100mb. Becouse im using sudo aptitude on install and on remove it removes old kernels (but somehow some of removed kernel files still stay in boot) So if computer is set for user who just uses programms and dont use aptitude then maybe for boot 200mb will be better so it doesnt run out of disk after 5y.
So solution
Swap is needed to be the same as ram size to hibernation be working also maybe possible ram upgrade can happen and if small ram (less then 512) then make bigger then ramsize. But if u know u wont upgrade ram then make same size.
[S=ramsize or bigger][P=5gb is enough if not installing anything then default programms][D=all the rest][B=min 100mb]

So what i did for one friend just now is Crunchbang on 40gb drive
/boot/ 100mb
/swap  512mb
/      5gb
/home  all the rest drive space ~32gb
all drives are XFS exept swap (couse for swap its not configurable at least on istallation)
After all updates && sudo aptitude remove firefox old kernels were removed boot has 55mb free space and / has 3gb free space and since he will only use chrome and maybe music i could even make / just 3gb

Computer counting from grub to usefull/active system takes 23seconds to boot

Any comments/ideas/suggestions?

---

### Post by overdrank on 2010-04-25
Moved to General Help :)

---

### Post by Kangarooo on 2010-04-30
only one strage thing. grub is not showing up but system is starting so it works but somehow different then if using EXT4

---

