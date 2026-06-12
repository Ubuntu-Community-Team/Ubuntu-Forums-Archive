---
title: "I Need Major Help. Ubuntu Is Gone!!!!!"
date: 2010-07-27
forum: General Help
---

### Post by Joker1134 on 2010-07-27
ok first im gonna describe what im running. 
1. ubuntu 10.04
2. windows xp
i used wubi installer. this morning i think i deleted the dll file thats needed for ubntu to boot. i didnt know that at the time. i tried booting ubutnu but it didnt work. so i tried running wubi again but nothing happened. now when i turn on the computer it boots straight to windows. ubuntu is still in my windows add remove programs so i know its still there. but its like gone when i boot the computer. help me please. my whole life was on my ubutnu. i can think of doing is removing ubuntu and re installing it but would i lose all my files and setting. would my home folder be erased? there has to be a way to get it to boot again. please help me

---

### Post by Joker1134 on 2010-07-28
i hate doing this but
BUMP
i really need help

---

### Post by LegendofTom on 2010-07-28
You could move your home folder to your Windows partition, then reinstall with Wubi.  Your Windows partition can be found in /host and /media.

Legend

---

### Post by Smart Viking on 2010-07-28
I can't really help you with restoring your files, i don't know much about wubi.

But i suggest next time you install that you install Ubuntu on a separate partition. I am sure that your files exist though, they are somewhere on your system.

---

### Post by Joker1134 on 2010-07-28
if i move my home folder and reinstall would i still keep all my settings like compiz and stuff?

---

### Post by Joker1134 on 2010-07-28
also where can i find my home folder while on windows?

---

### Post by jerenept on 2010-07-28
You cant.

---

### Post by bcbc on 2010-07-28
the important file is c:\ubuntu\disks\root.disk - back it up (or change c: to another drive letter depending on where you installed it.)

don't reinstall wubi or it will be deleted.

You can loop mount this file and copy off all your data from a live CD. You can also download some program that will let you view it from windows. I'll look around and post back. [http://ext2read.blogspot.com/](http://ext2read.blogspot.com/) (I haven't tried this myself). I have done everything else in this post.

To loop mount, boot a live CD, mount your windows partition containing the root.disk, then mount the root.disk. e.g. if it's on /dev/sda1:
```
sudo mount /dev/sda1 /mnt
sudo mkdir /wubi
sudo mount -o loop /mnt/ubuntu/disks/root.disk /wubi
gksudo nautilus /wubi
```

If the root.disk is fine, you can actually reinstall wubi, and replace the new root.disk with your backup. Then it will boot into it as before. Just make sure you back it up outside of the \ubuntu directory or it will be deleted when you reinstall.

You can also refer the [wubi guide]("https://wiki.ubuntu.com/WubiGuide") for more info.

---

### Post by flier01 on 2010-07-28
if you reinstall,compiz and other programs in ubuntu will disappear.
but these programs is easy to reinstall,it won't take much time.

---

### Post by flier01 on 2010-07-28
I strongly recommand you prepare a special partition for ubuntu.
wubi installer is just a way to experience ubuntu

---

### Post by Joker1134 on 2010-07-28
if i hit remove program for ubuntu would i lose all my files too? or just the operating system. i really dont wanna have to redo everything

---

### Post by bcbc on 2010-07-28
> **Joker1134 said:**
> if i hit remove program for ubuntu would i lose all my files too? or just the operating system. i really dont wanna have to redo everything

You will lose everything - don't do it.

---

### Post by Joker1134 on 2010-07-28
ok so how do i move everything then so i can reinstall ubnuntu. i need like a walk through or something

---

### Post by bcbc on 2010-07-28
> **Joker1134 said:**
> ok so how do i move everything then so i can reinstall ubnuntu. i need like a walk through or something

Look back a few posts.

---

### Post by Joker1134 on 2010-07-28
oh...
i did not see that. thank you

---

### Post by Joker1134 on 2010-07-28
what do i do if the root.disk file is like not there. i tried reintalling wubi when it stopped working.i think it got deleted.

---

### Post by bcbc on 2010-07-28
> **Joker1134 said:**
> what do i do if the root.disk file is like not there. i tried reintalling wubi when it stopped working.i think it got deleted.

If you ran wubi.exe again it would have prompted you to uninstall first. If you said "proceed", it's gone. All you can try now is some file recovery software to find and undelete the root.disk. If you are going to attempt this, first thing to do is to stop using your hard drive, because the more you use it the more likely it will be overwritten.

---

### Post by bcbc on 2010-07-28
Try testdisk: [http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

First - stop using your hard drive. Shutdown and reboot only to a live CD. The follow the guide above.

You can install and run testdisk on a live CD by running:
```
sudo apt-get install testdisk
sudo testdisk
```

---

### Post by Joker1134 on 2010-07-28
do you have any suggestions on what file recovery software i should use? it must be free since i have no money

---

### Post by bcbc on 2010-07-28
> **Joker1134 said:**
> do you have any suggestions on what file recovery software i should use? it must be free since i have no money
Yes see my previous post.

---

### Post by Joker1134 on 2010-07-28
i deleted it almost 24 hours ago and ive been on the computer ever since. its most likley gone but im gonna try and ways. thank you so much for the help

---

### Post by bcbc on 2010-07-28
> **Joker1134 said:**
> i deleted it almost 24 hours ago and ive been on the computer ever since. its most likley gone but im gonna try and ways. thank you so much for the help

You're welcome :) Good luck!

---

### Post by Joker1134 on 2010-07-28
it didnt work. the file is gone. i think the only thing left to do is go to add/remove programs in windows and remove ubuntu. i guess ill just reinstall it. i lost so much work. thanks for help. when i reinstall ubnutu im not gonna use wubi. i still say the ubuntu forums are the best tech support in the world. thank you so much.

---

### Post by varunendra on 2010-07-29
> **Joker1134 said:**
> it didnt work. the file is gone. i think the only thing left to do is go to add/remove programs in windows and remove ubuntu. i guess ill just reinstall it. i lost so much work. thanks for help. when i reinstall ubnutu im not gonna use wubi. i still say the ubuntu forums are the best tech support in the world. thank you so much.

Maybe it's late already, but if you haven't already overwritten it yet then you may try downloading Hiren's Boot CD from [here]("http://www.9down.com/Hiren-s-BootCD-10-6-352820/").
(it contains some very nice GUI recovery tools like GetDataBack for FAT/NTFS. Many such working tools on it are commercial, but the CD itself is- I don't know how- free!!)


For your plan to reinstall Ubuntu on its own partition, here's a suggestion if it isn't too late for that too!!:
Before starting the installation, use GParted from the liveCD to Shrink existing partitions to create empty space for Ubuntu. Then, while installing, choose manual partition option and create 3 partitions in the emptied-up space as follows:

[LIST=1]
[*]one ext3/4 partition of 4-6 GB, with mount-point being '/'
[*]one swap partition (anything between 200MB-2GB, as suits you)
[*]one ext3/4 partition occupying rest of the space with mount-point being '/home'. This is where your data would be stored.
[/LIST]
Benefit of this plan is that if you ever needed to reinstall Ubuntu, your data would be safe as the OS is installed in '/'.

---

