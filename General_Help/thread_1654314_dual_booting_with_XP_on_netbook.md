---
title: "dual booting with XP on netbook"
date: 2010-12-28
forum: General Help
---

### Post by Ron W on 2010-12-28
Hello

I would be grateful for any advice on the above. For example, what's the minimum size required for RAM and HD.

Thanks

Ron

---

### Post by amsterdamharu on 2010-12-28
For Ubuntu you need about 8GB, then about the same size as your memory (about 2G diskspace for 1GB mem works fine for me). The minimum specs are lower but you might get a slow running system.

If you download the Ubuntu iso (I recommend Lucid because it's long term support and all the problems that you might run into are already posted and solved on this forum) you can use Unetbootin to put it on a USB (about 1GB) then when you boot off it you can select the try Ubuntu without installing option and see what happens.

Best thing to do when you're in the live cd (try Ubuntu) mode is execute the following command, and post the output here to see if you could run into any deal breakers because of incompatible hardware:
```
sudo lshw
```To execute the command you can press alt + F1, type gnome-terminal and click run. Then copy one command and paste it in the terminal (black screen that showed up after you clicked run). Use the mouse to paste commands in the terminal.
Then you can select all the text in the terminal, right click and select copy. When pasting it here please wrap it in ```
 
``` tags.

---

### Post by dandnsmith on 2010-12-28
If you don't already have the netbook,
go for at least 1G RAM, and whatever HD size you can get (allowing for at least 5G for each of XP and Ubuntu - these are min sizes, and you should get a lot more to allow for updates and added software).

---

