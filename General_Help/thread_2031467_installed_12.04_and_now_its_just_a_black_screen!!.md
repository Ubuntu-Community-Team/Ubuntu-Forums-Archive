---
title: "installed 12.04 and now its just a black screen!!"
date: 2012-07-22
forum: General Help
---

### Post by cindy1990 on 2012-07-22
i just  freshly installed ubuntu 12.04 and now i get a back screen when i turn my computer on. however i installed it via usb and somehow the grub is on there! everything else seemsto be on the hard drive. so in order to start ubuntu i have to plug in my usb. hit f12 have it boot from the usb. (i then can remove the usb) i dont want to have to do it that way every time  i start my pc. how can i fix it?  oh and while doing the updates. it said grub was missing (i had the usb unpluged) and it try to fix it but failed.

---

### Post by jonnyboysmithy on 2012-07-22
So grub is missing. 
Run the following, with X being the your Ubuntu drive:
     ```
sudo grub-install /dev/sd[COLOR=DarkRed]**X**[/COLOR] 
```
For me that would be ```
sudo grub-install /dev/sda
```I think the first hard disk is always /dev/sda and if you have a second disk then that would be /dev/sdb and so forth.

---

### Post by cindy1990 on 2012-07-22
sweet! work perfectly thank you!! :popcorn:

---

### Post by jonnyboysmithy on 2012-07-22
:D:D Good!!:popcorn: Pass the popcorn! :P

---

