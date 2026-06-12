---
title: "Some Help Would Be Appreciated"
date: 2011-07-18
forum: General Help
---

### Post by Godsrycht on 2011-07-18
When I installed ubuntu I had no intentions of returning to windows. Later I found out the my one and only favorite game ever is unplayable in ubuntu so now I'm ready to dual-boot. The only issue is I cant I partition some space! Can someone tell me how to take my partition and free up some of the free space I have? Attached is an SS of my partition manager.

---

### Post by wildmanne39 on 2011-07-18
> **Godsrycht said:**
> When I installed ubuntu I had no intentions of returning to windows. Later I found out the my one and only favorite game ever is unplayable in ubuntu so now I'm ready to dual-boot. The only issue is I cant I partition some space! Can someone tell me how to take my partition and free up some of the free space I have? Attached is an SS of my partition manager.Hi, you have to boot from the livecd you can not do it while booted into ubuntu. Here is a link for partitioning and one for installing windows after ubuntu.

Please be very careful working with partitions you can make your system unbootable or wipe it out completely.

[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)
[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=1](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=1)

---

### Post by akand074 on 2011-07-19
Yeah just pop in your Ubuntu disc and run the partition manager from a live session. On a related note, once you install Windows it will likely overwrite Grub and thus it'll boot right into Windows without knowing Ubuntu is there. Here is instructions on [reinstalling Grub.]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2")

---

### Post by Godsrycht on 2011-07-23
Okay so I did what was directed and cleared 100gig of my free space for my windows section. I installed windows but now it doesnt give me to option of dual-boot. Just loads windows =/. Is there some software or something I need. I know my ubuntu is still there I can see it with partition magic just dont know how to boot with it. SOme help would be great.

---

### Post by wildmanne39 on 2011-07-23
Hi, you have to use the livecd and reinstall grub.
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[http://opensource-sidh.blogspot.com/2011/06/recover-grub-live-ubuntu-cd.html](http://opensource-sidh.blogspot.com/2011/06/recover-grub-live-ubuntu-cd.html)

---

### Post by Godsrycht on 2011-07-24
LOL I did that and now ubuntu loads without asking me if I want to load windows. How do I make this work so that when I reset the PC I'm given a choice of what to run.

---

### Post by plucky on 2011-07-24
> **Godsrycht said:**
> LOL I did that and now ubuntu loads without asking me if I want to load windows. How do I make this work so that when I reset the PC I'm given a choice of what to run.

What happens if you open a terminal and run ```
sudo update-grub
```

---

### Post by Godsrycht on 2011-07-24
Thank you so much dude I wish I knew it was just that easy!

---

### Post by wildmanne39 on 2011-07-24
Hi, glad you got it working, please mark thread solved.

---

