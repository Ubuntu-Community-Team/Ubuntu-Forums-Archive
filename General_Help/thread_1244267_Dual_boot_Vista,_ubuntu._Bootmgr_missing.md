---
title: "Dual boot Vista, ubuntu. Bootmgr missing"
date: 2009-08-19
forum: General Help
---

### Post by jedispork on 2009-08-19
I have vista loaded first onto my ide drive which is hd1 on my system. I then install ubuntu to my secondary sata hard drive. I make a new partition on it and install ubuntu at hd0,4. Vista loaded and no sign of grub. So I use super grub disc so I can boot my new ubuntu install. I follow these steps

sudo grub
find /boot/grub/stage1
root (hd?,?)
setup (hd?)
quit

I've tried to setup on both hd0 and hd1. Grub loads but I get bootmgr missing when I try to load vista. The only way I could fix is to use bootrec on my vista install disc. After some reading I discover another program called easybcd. I configured it so ubuntu shows up in the windows boot manager which in turns loads grub so I can load ubuntu. 

This seems to be working for now but what was I doing wrong? This has been a major deterrent for me to get started in linux. What can I do to get grub working the proper way? I don't understand why I'm having this issue and others aren't? Does it have anything to do with me using the eide drive as my primary windows install? My reason for that is because the sata drive is only 5400 rpm and originally intended as a backup.

thanks for any suggestions you can give

---

