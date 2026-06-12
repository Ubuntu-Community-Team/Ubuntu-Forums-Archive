---
title: "Install ubuntu on SSD..."
date: 2012-05-01
forum: General Help
---

### Post by ivanox1972 on 2012-05-01
Hi, I have notebook with ssd 64gb and hard disc 250gb... Now, xp is on hd (it will stay and win 7 on ssd- I want to put ubuntu 12.04 there...
Generally, installing is not problem for me, I done it many times...
I am in doubt about trim and alignment of partitions...
I see many things about this on net, but nothing seems authoritative enough for me...
Also to go with 64bit or 32bit (I have, of course, 4GB ram)...
Thanks

---

### Post by SlugSlug on 2012-05-01
installing 12.04?

trim is supported, you just need to add discard to your fstab
eg
```
UUID=xxx-xxx-xxx-xxx  /               ext4    discard,errors=remount-ro 0       1

```You can add other stuff there to prolong the life but this is not really needed with newer SSD's  (they now last as long as HDD's)

for partition alignment you can use this guide

[http://lifehacker.com/5837769/make-sure-your-partitions-are-correctly-aligned-for-optimal-solid-state-drive-performance](http://lifehacker.com/5837769/make-sure-your-partitions-are-correctly-aligned-for-optimal-solid-state-drive-performance)

but I've only seen it make a few MB/s difference on each install I've done to SSD's 

(not really worth it tbh) 

Ensuring you have AHCI enabled in BIOS will help performance.

---

### Post by oldfred on 2012-05-01
I enabled AHCI for use with my SSD and I knew my XP would not work. I did find some work arounds to install the drivers with XP, but they really have to be added when you install XP. But for me it was one more reason to finally get away from Windows as I had promised for years.:)

If using Windows 7 you can install the AHCI drivers before changing settings in BIOS.

I also used gpt partitioning for the SSD, but then you can not boot with Windows from a gpt drive unless you have UEFI not BIOS. And XP will not read a NTFS partition in gpt, but Windows 7 will.

BIOS settings (SSD but also most systems)
[http://www.ocztechnologyforum.com/forum/showthread.php?79848-THE-BASIC-GUIDE-amp-FAQ-ABC-for-OCZ-SSD&p=567561&viewfull=1#post567561](http://www.ocztechnologyforum.com/forum/showthread.php?79848-THE-BASIC-GUIDE-amp-FAQ-ABC-for-OCZ-SSD&p=567561&viewfull=1#post567561)

[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives) - SSD

---

### Post by ivanox1972 on 2012-05-01
I have divided, as said in this manual, result is 256 it seems it is correctly aligned. But, this is under win7. Will i DESTROY THIS WHEN FORMAT IN EXT4 for ubuntu. Also I have 4gb ram- do I need swap partition? ... Also AHCI must me set to have ssd work, also already... XP is on other hard disc and runs normally all the time...
thanks

---

### Post by ivanox1972 on 2012-06-03
Hi, again...
I have installed it on SSD witout any problem.
Now, I just have one small thing to set.
I installed Ubuntu on SSD and set ssd as first boot device in bios.
Before, I installed win xp on hard disc, which was in this moment first boot device, now it is second. Problem is thant not ubuntu starts normally, I still have windowds boot option, but when choose it it can not start. Can I fix loader on some way to get xp without reinstalling it (may be this is windows item, but somebody can help).
Thanks

---

