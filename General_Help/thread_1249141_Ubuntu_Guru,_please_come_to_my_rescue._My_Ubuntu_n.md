---
title: "Ubuntu Guru, please come to my rescue. My Ubuntu not boot."
date: 2009-08-25
forum: General Help
---

### Post by tal007 on 2009-08-25
Hello to Ubuntu World. I am stuck, and need some help. I am losing a lot of hair and sleep over Ubuntu. I have already lost enough hair and about to lose what remains standing. I installed Ubuntu on my my Desktop PC. Installation goes smoothly without any problem, but the problem comes up when I boot the system. Ubuntu kernel won't load into memory. It gets stuck and goes into a loop displaying a message "boot from ( hd0,4 ) ext2 + an enormous number(kernel Id of sore sort )". I can not get the system past that point. I am at a loss now and don't know what would make it boot. I have read a lot on the internet and tried everything conceivable suggested by others on the internet. If you have faced the same problem, please let me know how you brought it up.


I partitioned my Hard Drive into 3 segments. One for root file system and the other for boot and swap.

Thanks.

---

### Post by sanderj on 2009-08-25
I would start by doing a fresh install of Ubuntu to see if that helps.

And: which version of Ubuntu are you using?

---

### Post by tal007 on 2009-08-25
This is not the first installation. I have installed several times afresh, to speak probably 5 or 6 times without any exaggeration. Each time I try to bring up the system after installation, I see the very same problem. By the way, I am using the latest Ubuntu for Desktop(AMD & X64 ). I am not sure what is causing it. I don't have any option in my BIOS where I can fiddle with it. The only option I have is auto or none. So, I set it to auto detect for my Hard Drive. The other thing that I noticed is the amount of delay. It takes about 10 minutes to get to there.

---

### Post by P4man on 2009-08-25
Maybe this is just a typo by you, and I dont see why it wouldnt boot because of it anyhow, but:
> 
boot from ( hd0,4 ) ext**2** 

did you format the root as Ext2 ? Default is Ext3 or 4.

---

### Post by tal007 on 2009-08-25
I cleaned up my hard drive with a utility called zap, because I noticed that in some cases some OS can not delete partitions even if you use utility like raw write.It happened to me many times with Windows XP. I verified that the drive is clean. As for other question. I created 3 partitions:  root, boot and swap.

I created the root file system with type ext3 and mounted it on /.

Then I created the boot file system with type ext2 and mounted it on /boot.

The remaining partition allocated for swap 

I followed all the conventions that calls for. Where can I go wrong?

---

### Post by jesuisbenjamin on 2009-08-25
An important part to a proper installation is your Installation CD. I onced broke many neurones trying to install Ubuntu, only to find out something wrong had occured when downloading/burning image. A new Installation disk did the trick.

---

### Post by P4man on 2009-08-25
> **tal007 said:**
> I cleaned up my hard drive with a utility called zap, because I noticed that in some cases some OS can not delete partitions even if you use utility like raw write.It happened to me many times with Windows XP. I verified that the drive is clean. As for other question. I created 3 partitions:  root, boot and swap.

I created the root file system with type ext3 and mounted it on /.

Then I created the boot file system with type ext2 and mounted it on /boot.

The remaining partition allocated for swap 

I followed all the conventions that calls for. Where can I go wrong?

everywhere lol.

Can you boot a live cd ?
If you please post the output of:

```
sudo fdisk -l
```

then run:

```
sudo grub

```
at the grub prompt type:

```
find /boot/grub/stage1

```

Post the out put here. Type "quit" to quit grub.

Id also like to see your menu.lst if you know where it is. Somewhere /media/yourbootpartition/boot/grub/menu.list.

---

### Post by mechanic on 2009-08-25
If it's the latest Ubuntu it uses Grub2 so no stage1 etc. On the other hand you can edit the booting lines in place when Grub starts to test variations on (hd0,4). If there are three partitions that seems wrong, try (hd0,3) (hd0,2) and so on. Watch the error messages carefully, the clue is usually there! Also partition numbers start at 1 not 0 in Grub2.

---

### Post by P4man on 2009-08-25
> **mechanic said:**
> If it's the latest Ubuntu it uses Grub2 

Thats only for 9.10 Karmic, which is still in alpha. Im assuming he's using the release version (jaunty). If he's using karmic then god help him. I made the mistake of trying out grub 2 and while it worked initially, lets just say I dont look forward to it being the new standard :shudder:.

---

