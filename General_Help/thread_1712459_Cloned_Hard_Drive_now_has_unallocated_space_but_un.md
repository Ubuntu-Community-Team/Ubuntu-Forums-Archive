---
title: "Cloned Hard Drive now has unallocated space but unable to expand partition"
date: 2011-03-22
forum: General Help
---

### Post by Reikiboy on 2011-03-22
Hi, 

I'm looking for someone who can help me before I find the nearest bridge and jump off it.

I installed Ubuntu a few days ago (after going back to windows for a moth or so then realizing it was stupid thing to have done) The disk utility showed that my hard disk was had an imminent failure warning so I took the drive out (80gb) and found a spare that I had (40gb) and reinstalled. I realized to day that I had a 160gb drive sitting on a shelf doing nothing but not wanting to reinstall , I decided to have a go at cloning the drive. I used the following command  [I]"dd if=/dev/sda of=/dev/sdb bs=64k" this took around 30 mins and when it was done I shut down the PC unplugged my old drive and rebooted with the newer cloned 160gb drive.

The only problem now is that GParted is showing that I have a lot of unallocated space but I cannot for the life of me expand the partition. I have tried using the live cd but nothing will allow me to resize. I have take a screen shot in the hope that someone out there can help. I would rather have one single partition over two and I would rather not reinstall Ubuntu. I have been playing around quite a bit and managed to delete the swap partitions. I am pretty much a complete novice so please go easy on me. If anyone can guide me on how to get the screen shot looking like it should I would be most grateful.

Thanks
Adam

Ubuntu Release - 10.10 (maverick)
[/I]

---

### Post by kiyop on 2011-03-22
There is no necessary data in /dev/sda3, is not it?

If there is no necessary data in /dev/sda3, **boot with Ubuntu Live CD** and open Gparted, and delete /dev/sda3, then delete /dev/sda2, too.

Expand /dev/sda1 to backward as you like.
I think Gparted does not change UUID value of the partition even the partition is expanded to backward.

Apply change by clicking green "v" (check icon).

That's all.

If UUID value is changed, you should manually change UUID value in /etc/fstab and execute
```
sudo update-grub
```to make the boot loader (grub2) configuration file /boot/grub/grub.cfg suitable.

---

### Post by Reikiboy on 2011-04-01
HI , thanks soooooooo much for your help. I have only just got round to sorting it out and everything worked as you described. 

Problem solved , thanks again

---

