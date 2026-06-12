---
title: "Screen goes black after VGA change"
date: 2010-12-16
forum: General Help
---

### Post by mdrg on 2010-12-16
Hello,

My old GF 8600 went dead some weeks ago. While I waited for my new card, I used an old Trident PCI card to use the desktop. I could use windows but not Ubuntu, but I still removed several nvidia drivers using the command line: [Getting an old Trident Video Accelerator 9440 to work]("http://askubuntu.com/questions/15118/getting-an-old-trident-video-accelerator-9440-to-work")

Two days ago I got my new card, a Radeon HD 5670. I reinstalled Windows, as it crippled itself because of the driver change (I use dual boot). The Windows install killed grub, so I reinstalled it using this: [http://linuxpoison.blogspot.com/2010/10/how-to-restore-grub-2-after.html]("http://askubuntu.com/questions/15118/getting-an-old-trident-video-accelerator-9440-to-work")

After that, my three windows partitions could not be mounted during load time (guess that's because their mount folders are missing), and skipping the mount process lead me to a freezing black screen, so I commented the lines on fstab with nano. Then I restarted Ubuntu, but it keeps locking up at the black screen.

I guess Ubuntu is thinking I still have a GF, or it simply misses the nvidia display drivers. I googled around, but couldn't find any tip to solve my problem. I know ubuntu recognizes the card, as I can use Live CD perfectly.

Any help is welcome!

---

