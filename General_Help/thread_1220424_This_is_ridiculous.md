---
title: "This is ridiculous"
date: 2009-07-22
forum: General Help
---

### Post by Theory5 on 2009-07-22
1- I dont know why but if I try to boot Ubuntu from anything other than a harddrive it doesnt work. the boot fails. 
2- I need to have a flashdrive with ubuntu 9.04 on it made by unetbootin and I need to have unetbootin put ubuntu on a partition, then the ubuntu installation uses that partition. 
3- AND I cant install ubuntu because when I try to, it has conflicts with other partitions. 
4- {FIXED} And now it just fragmented my hdd partitions so there are multiple partitions scattered around of linux-swap and ext3. 
5- {FIXED} And my bootable copy of Gparted wont put them back the way they should be!!! 
Could somebody help me?

---

### Post by hansdown on 2009-07-22
Hi Theory5.

Just need to ask a couple questions.

Do you have 9.04 installed on a hard drive already? The reason I ask, is that 9.04 comes with a bootable usb creator. It works very well.
Click system> administration> usb startup disk creator.

Is the usb for installing to a netbook?

---

### Post by Theory5 on 2009-07-22
its not a netbook. and I did try that. It gave me the same exact error I got with anything other than unetbootin used to install ubuntu on the partition and then use it to install it on the USB device, which it then boot off but uses the partition ubuntu live cd feature. It might just be using the USB device to boot from because there is not a boot entry yet for ubuntu, but the fact is that it uses the partition and nothing else. Its a HP Touchsmart tx2 laptop

---

### Post by hansdown on 2009-07-22
If you plug the usb into your computer,(don't boot from usb), can you double click to open it?

There should be a syslinux file inside.

---

### Post by pawnrocket on 2009-07-22
I have found that with unetbooting if you don't format the drive often times installation with fail. 

If I format the drive I boot off usb no problem.

---

### Post by hansdown on 2009-07-22
Good point pawnrocket. Might be good to look at.

Another thing that troubles me, is the part about installing to the hard drive first.

Softpedia has a tutorial that seems a little more straight forward.

[http://news.softpedia.com/news/How-to-Run-Linux-from-an-USB-Flash-Drive-93316.shtml](http://news.softpedia.com/news/How-to-Run-Linux-from-an-USB-Flash-Drive-93316.shtml)

I'd just like to point out the warning in step 2. Please don't take it wrong, I'm just trying to help.

---

### Post by Theory5 on 2009-07-23
I think you guys are missing the point.I am sorry if I am not being clear enough. My computer refuses too boot from anything other than the partition I use unetbootin on. No matter how I make the usb drive, or burn it to a cd, it wont boot. And this is a problem because ubuntu needs to unmount the entire disk to make changes to certain partitions in the installation. I even tried booting from my external drive partition, that did not work. even when I used gparted to format the drive in ext3 then I went into the Ubuntu installer and it still wanted to make changes to the harddrive. 
    This would seem like a huge problem, but apperently I am the only one who is getting it, even though other people have installed ubuntu 9.04 on their HP Touchsmart tx2. I would just pay the 3-5 bucks and have an official cd sent to me, but Im not sure if it will work either. I know my Ubuntu 7.10 disk works and I was going to upgrade it with that, but my network adapters are too new, and it wont recognize either of them.  
   However i did hear of an alternate installer, how does that work and where can I get it?

---

### Post by credobyte on 2009-07-23
Alternate CD: [http://www.ubuntu.com/GetUbuntu/downloadmirrors#alternate](http://www.ubuntu.com/GetUbuntu/downloadmirrors#alternate)

---

### Post by Theory5 on 2009-07-23
is this a totally new base, or is it based off of the ubuntu live cd? which might cause problems for me.

---

### Post by credobyte on 2009-07-23
> **Theory5 said:**
> is this a totally new base, or is it based off of the ubuntu live cd? which might cause problems for me.

Wouldn't it be easier to open that link and read it's description ? :roll: Alternate CD is the same as LiveCD, exept, it does not have a graphical interface.

---

### Post by Theory5 on 2009-07-23
> **credobyte said:**
> Wouldn't it be easier to open that link and read it's description ? :roll: Alternate CD is the same as LiveCD, exept, it does not have a graphical interface.

Oh, then it probably wouldnt work because I dont need a text based interface. That is not my problem becuase I would have trouble booting the live cd.

---

### Post by Theory5 on 2009-07-23
Does anybody have any other ideas for booting?

---

### Post by Theory5 on 2009-07-23
> **hansdown said:**
> If you plug the usb into your computer,(don't boot from usb), can you double click to open it?

There should be a syslinux file inside.

yes I can open it. Why? Is there a way to fix this problem?

---

### Post by kerry_s on 2009-07-23
is your bios set to boot from usb?
your saying it will only boot from a partion on the harddrive, which leaves me to believe your bios is not set to boot from usb.

---

### Post by Theory5 on 2009-07-23
Im not saying it wont boot, I am saying booting from anything but the usb drive, which triggers the partition, results in ubuntu crashing to busybox. 
This is the exact error I get:
[   2.120056] ata1: Softreset Failed (Device not ready)
[   2.772051] ata2: Softreset Failed (Device not ready)
modprobe: FATAL: could not load /lib/modules/2.6.28-11generic/modules.dep: No Such file or directory
modprobe: FATAL: could not load /lib/modules/2.6.28-11generic/modules.dep: No Such file or directory

Loading. please wait...

BusyBox v1.10.2 (Ubuntu 1:1.10.2-2ubuntu7) Built in shell (ash)
Enter 'help' for list of built in commands.
(initramfs)

---

### Post by Theory5 on 2009-07-23
[http://ubuntuforums.org/showthread.php?t=1165715](http://ubuntuforums.org/showthread.php?t=1165715) 

YES! the method works from this thread. You do need to have the installation made by unetbootin though.

---

### Post by kerry_s on 2009-07-23
ooh, i've seen that before. i think your screwed.
i don't think theres a fix but you can look:
[http://www.google.com/search?q=Softreset+Failed+(Device+not+ready)&ie=utf-8&oe=utf-8&aq=t&rls=org.debian:en-US:unofficial&client=iceweasel-a](http://www.google.com/search?q=Softreset+Failed+(Device+not+ready)&ie=utf-8&oe=utf-8&aq=t&rls=org.debian:en-US:unofficial&client=iceweasel-a)

---

### Post by Theory5 on 2009-07-24
they say a fix is to add 'all_generic_ide' in the kernal part of the grub bootup, but when I enter that and then I hit tab it says its unknown.

---

