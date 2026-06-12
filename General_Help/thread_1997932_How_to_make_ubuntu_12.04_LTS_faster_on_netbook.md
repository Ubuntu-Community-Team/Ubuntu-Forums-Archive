---
title: "How to make ubuntu 12.04 LTS faster on netbook"
date: 2012-06-05
forum: General Help
---

### Post by ndonio on 2012-06-05
Hi all!

I looked around a lot for an advice as in the title but without any success.

I'd like to have some advices on how to make lighter and faster ubuntu 12.04 LTS on a netbook.
I have a samsung netbook (N150) with an Intel(R) Atom(TM) CPU N450   @ 1.66GHz (32 bit), 1 GB RAM and an Intel GMA graphic processor as graphic card.

I upgraded from ubuntu 10.04 LTS (netbook version) to 12.04 LTS some week ago. The 10.04 LTS version was very very faster than the one I have now.
I don't need any graphical effect (I use the 2D desktop environment), just I'd like to return to the speed of ubuntu 10.04 LTS.

Thanks for your help!

---

### Post by Megaptera on 2012-06-06
Six suggestions here [http://www.howtogeek.com/115797/6-ways-to-speed-up-ubuntu/](http://www.howtogeek.com/115797/6-ways-to-speed-up-ubuntu/)

---

### Post by Bucky Ball on 2012-06-06
1/ Use something more lightweight like Xubuntu or Lubuntu; better still, do a minimal install and use only the packages you need with xfce4 or lxde as your desktop environment (used by Xubuntu and Lubuntu, respectively);

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

2/ Install more RAM.

;)

---

### Post by zombifier25 on 2012-06-06
Installing [Jupiter Applet](http://www.jupiterapplet.org/downloads.html), which minimizes power usage on netbooks is also a good idea.

---

### Post by leopoldbirkholm on 2012-06-06
Found a video on how to upgrade RAM on your device.

[http://www.youtube.com/watch?v=JrJgvHZnHqY](http://www.youtube.com/watch?v=JrJgvHZnHqY)

1 GB of RAM is quite small. I would say at least 2 GB for a small netbook or 4 GB for a regular laptop.

---

### Post by temporos on 2012-06-06
> **leopoldbirkholm said:**
> 1 GB of RAM is quite small. I would say at least 2 GB for a small netbook...

Yeah, about that...  :-?  My netbook's maxed-out at 1 GB RAM.  I'm going to try installing Lubuntu later this week once my SDHC cards arrive so I can properly back-up my Home directory.

---

### Post by wheeze on 2012-06-06
You can increase your disk performance by adding the **noatime** option to the ext4 partitions listed in **/etc/fstab**.

Explained more here, along with some other more adventurous options. I do this for my installs and the improvement in disk I/O is noticeable!
[http://blog.smartlogicsolutions.com/2009/06/04/mount-options-to-improve-ext4-file-system-performance/](http://blog.smartlogicsolutions.com/2009/06/04/mount-options-to-improve-ext4-file-system-performance/)

---

### Post by holycow131415 on 2012-06-06
install lxde or xfce desktop enivorments instead of using unity

---

### Post by ndonio on 2012-06-08
OK! I'll try all of this! I'll keep this post updated with the results so that, hopefully, we can write a short guide for those with my same problems.

Thanks!

---

### Post by ndonio on 2012-06-13
By now the only thing that made my computer faster is using lxde, all the modifications on the fstab file didn't give appreciable improvements. But I have a problem with the dual monitor in lxde: when I connect an external monitor it is cloned and I can set them separately. I installed ARandR but it doesn't work.

Any suggestion?

Thanks

---

### Post by Bucky Ball on 2012-06-13
> **ndonio said:**
> ... I have a problem with the dual monitor in lxde: when I connect an external monitor it is cloned and I can set them separately. I installed ARandR but it doesn't work.

Any suggestion?

Thanks

Yes. Please post a new thread regarding this new issue with a descriptive thread title and as much explanation as you can give. You will get more help that way. Post a link to it back here if you like and mark this thread as solved. 

Good luck. ;)

---

### Post by ndonio on 2012-06-15
Ok, thanks!

---

### Post by spartan7 on 2012-06-24
I am running a eeepc 1005ha and what made the most difference was a ssd drive. It was a 100% improvement.

---

