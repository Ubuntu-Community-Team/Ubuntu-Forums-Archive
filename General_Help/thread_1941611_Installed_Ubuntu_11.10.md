---
title: "Installed Ubuntu 11.10"
date: 2012-03-16
forum: General Help
---

### Post by GenoDesigns on 2012-03-16
I installed Ubuntu 11.10 recently. And I fully installed it. It is my OS now. Sadly I don't like it, and you cannot open .exe files easily. ( I know it was my fault for installing Ubuntu.) 

So I was wondering, if you guys knew how to restore back to factory settings. From ubuntu 11.10 to Factory Settings.

I tried BIOS booting. But it won't work. 

Please help me.

---

### Post by sp-1070 on 2012-03-16
Dont give up so fast try whine for a bit loads of programs are easy runable using it.

[http://www.winehq.org/](http://www.winehq.org/)

If you need help with it leave me a message

---

### Post by varunendra on 2012-03-16
GenoDesigns,

Looks like you have already struggled enough with wine and don't find gimp acceptable: [http://ubuntuforums.org/showthread.php?t=1929782](http://ubuntuforums.org/showthread.php?t=1929782)
I must admit that wine is not as promising as it might seem at first glance.

Anyway, as for the factory-reset question, I'm afraid we have only two valid options these days:

[LIST=1]
[*]Restore the OS from recovery partition.
[*]Order recovery discs from the manufacturer's site.
[/LIST]
When you say you 'tried BIOS booting' do you mean pressing the 'shortcut key' that was assigned for recovery? Isn't it working as expected? If so it may be because of some change in partition layout during installation of Ubuntu, or the recovery partition might have been deleted altogether.

If the recovery partition still exists, but doesn't work anymore, there is still hope. But how to proceed will depend on other details like the laptop manufacturer, the original OS, and how it has been backed up for recovery. A quick google search with laptop model may give you helpful results.

However, if the partition has been deleted, then ordering recovery disc(s) may be the only legal option left.

If unsure about the existence of recovery partition, please install and run gparted (it already exists on the live cd), and post its screenshot, along with other details like laptop model and the original OS/version it came with. Also, it would be even more helpful if you can tell us how exactly you installed Ubuntu (which partitioning options you chose, how did you partition if you chose to do it manually.. etc.)

---

### Post by GenoDesigns on 2012-03-16
> **sp-1070 said:**
> Dont give up so fast try whine for a bit loads of programs are easy runable using it.

[http://www.winehq.org/](http://www.winehq.org/)

If you need help with it leave me a message
Yeah, i'll keep on trying Wine. But there's a 0% chance it will work with Photoshop CS5 nor visual basic 2008.
> **varunendra said:**
> GenoDesigns,

Looks like you have already struggled enough with wine and don't find gimp acceptable: [http://ubuntuforums.org/showthread.php?t=1929782](http://ubuntuforums.org/showthread.php?t=1929782)
I must admit that wine is not as promising as it might seem at first glance.

Anyway, as for the factory-reset question, I'm afraid we have only two valid options these days:

[LIST=1]
[*]Restore the OS from recovery partition.
[*]Order recovery discs from the manufacturer's site.
[/LIST]
When you say you 'tried BIOS booting' do you mean pressing the 'shortcut key' that was assigned for recovery? Isn't it working as expected? If so it may be because of some change in partition layout during installation of Ubuntu, or the recovery partition might have been deleted altogether.

If the recovery partition still exists, but doesn't work anymore, there is still hope. But how to proceed will depend on other details like the laptop manufacturer, the original OS, and how it has been backed up for recovery. A quick google search with laptop model may give you helpful results.

However, if the partition has been deleted, then ordering recovery disc(s) may be the only legal option left.

If unsure about the existence of recovery partition, please install and run gparted (it already exists on the live cd), and post its screenshot, along with other details like laptop model and the original OS/version it came with. Also, it would be even more helpful if you can tell us how exactly you installed Ubuntu (which partitioning options you chose, how did you partition if you chose to do it manually.. etc.)
Thanks for your reply. 
If I order the recovery disks. Is it 100% sure that it will work?

---

### Post by varunendra on 2012-03-16
> **GenoDesigns said:**
> If I order the recovery disks. Is it 100% sure that it will work?
It 'should', but I can't say it 'must' unless you tell us the model and other details I asked for. Only the manufacturer can say that.

Having said that, there is no point in having a 'recovery disc' if it can't restore a system from scratch. All the OS recovery discs I have ever witnessed are bootable and contain a full system image, which is restored by an automated application included in the booting program on the disc.

But you should confirm this with the manufacturer before ordering, if you wish to go that way.

---

### Post by squilookle on 2012-03-16
No such thing as a guarantee, but I would assume recovery media should be able to recover your system from any state, including situations where you have replaced the hard drive because the original failed. 

I would therefore assume that wiping the hard drive should not prevent the recovery media from working, but checking with the manufacturer first is always a good idea.

---

### Post by GenoDesigns on 2012-03-16
> **varunendra said:**
> It 'should', but I can't say it 'must' unless you tell us the model and other details I asked for. Only the manufacturer can say that.

Having said that, there is no point in having a 'recovery disc' if it can't restore a system from scratch. All the OS recovery discs I have ever witnessed are bootable and contain a full system image, which is restored by an automated application included in the booting program on the disc.

But you should confirm this with the manufacturer before ordering, if you wish to go that way.

Process - AMD Athlon(tm) II Dual-Core M300 × 2
64-bit
Disk - 312.1 GB
Memory - 2.7 GiB

---

### Post by wildmanne39 on 2012-03-16
Hi, so you did not make a set of recovery dics before you installed ubuntu?

Did a windows disc come with your computer?

Copy and paste this command into the terminal and then paste the output here so we can see if you have a recovery partition.
```
sudo fdisk -lu
```
Thanks

---

### Post by GenoDesigns on 2012-03-16
> **wildmanne39 said:**
> Hi, so you did not make a set of recovery dics before you installed ubuntu?

Did a windows disc come with your computer?

Copy and paste this command into the terminal and then paste the output here so we can see if you have a recovery partition.
```
sudo fdisk -lu
```
Thanks

I checked in the box, but there was no disc.

I pasted it into the terminal and got this.
```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00091fb2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   619376639   309687296   83  Linux
/dev/sda2       619378686   625141759     2881537    5  Extended
/dev/sda5       619378688   625141759     2881536   82  Linux swap / Solaris

```

---

### Post by wildmanne39 on 2012-03-16
I am afraid you do not have a recovery partition so I guess you will have to order them.

---

### Post by GenoDesigns on 2012-03-16
> **wildmanne39 said:**
> I am afraid you do not have a recovery partition so I guess you will have to order them.

Is this a good one?
[http://systemdiscs.com/?utm_source=neosmart&utm_medium=article&utm_campaign=Win7_Recovery](http://systemdiscs.com/?utm_source=neosmart&utm_medium=article&utm_campaign=Win7_Recovery)

---

### Post by wildmanne39 on 2012-03-16
Hi, no not for what you need.

You need to order a set of recovery dics or a windows install disc from your computers manufacturer.
Thanks

---

### Post by GenoDesigns on 2012-03-16
> **wildmanne39 said:**
> Hi, no not for what you need.

You need to order a set of recovery dics or a windows install disc from your computers manufacturer.
Thanks
By any chance, do you know where I could get it? 
Thanks

---

### Post by wildmanne39 on 2012-03-16
Look on your computer and see who makes it then  go to there website and get a phone number and call and order the dics from them.
Thanks

---

### Post by varunendra on 2012-03-16
> **wildmanne39 said:**
> Look on your computer and see who makes it then  go to there website and get a phone number and call and order the dics from them.
Thanks
^^this.., and you didn't tell us the brand and model of the computer. The specs you gave are irrelevant in this context. If we know the exact brand and model no. of your computer, we may try to look up the suitable place for you to order the discs.

Another alternate (I guess) is to borrow or anyhow get an installation disk (from a reliable source) of the same version you had originally installed, then install it with _your serial key_, if you have it.

But in any case, contacting the manufacturer should be the best way to proceed.

---

