---
title: "Is WUBI or actual install better?"
date: 2011-06-26
forum: General Help
---

### Post by Megacack on 2011-06-26
I want the full experience of Ubuntu and i'm using WUBI to use it. Is WUBI slower then an actual install of ubuntu or it's the same? Personally I think it's fast and it's all good. But maybe it can go faster? So do i stay with WUBI or actually install ubuntu.(Keep in mine i constantly switch from ubuntu to windows)

---

### Post by flipper T on 2011-06-26
> Limitations

Compared with a regular installation, a Wubi installation faces some limitations. Hibernation is not supported and the filesystem is more vulnerable to hard reboots[1]. Also, if the Windows drive is unmounted uncleanly (most commonly because of a Windows crash), Ubuntu will not be able to mount the Windows drive and boot until Windows has successfully booted and shut down. If the Windows system cannot be booted after the crash, the user also cannot boot Ubuntu.

Performance related to hard-disk access is also slightly slower, more so if the disk image file is fragmented, on a Wubi install compared to a normal one

from wikipedia.org/wiki/Wubi


if you are happy with your set up, stick with it.

ps google is a wonderful thing

---

### Post by jerrrys on 2011-06-26
wubi is a way to try ubuntu.  however if you want to switch between the two without reboot, then maybe its for you.  i like being able to switch and use virtualbox, a much better solution in my opinion.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

[http://www.virtualbox.org/](http://www.virtualbox.org/)

P.S. googlubuntu is a wonderful thing :D

---

### Post by bcbc on 2011-06-26
If you're trying out Ubuntu, wubi is fine. If you are going to be using Ubuntu on an ongoing basis you should do a regular install. 

The main reason for this is that the virtual disk wubi uses is like having all your eggs in one basket. If the file is corrupted or accidentally deleted you can lose your entire ubuntu install. 

Another benefit of a direct install is that you can hibernate windows and boot ubuntu with a normal install. With wubi you have to completely shutdown windows and it takes forever to restart windows (in my experience).

Running ubuntu in a VM is great for certain things (like having access to it without rebooting windows) but you don't get full access to the hardware resources so unless you have a powerhouse machine (lots of ram), the experience is painful. And even with a fancy machine the graphics will be half-baked. If you're just browsing the web it's fine.

Anyway... this post got a little long, but my advice is: if you like Ubuntu and feel you'll be using it a long time, then you should plan to partition and install direct or [migrate]("http://ubuntuforums.org/showthread.php?t=1519354") Wubi. There's no rush, but that's the best way to use Ubuntu in the long run.

PS backup everything prior to partitioning.

---

### Post by Megacack on 2011-06-28
> **bcbc said:**
> If you're trying out Ubuntu, wubi is fine. If you are going to be using Ubuntu on an ongoing basis you should do a regular install. 

The main reason for this is that the virtual disk wubi uses is like having all your eggs in one basket. If the file is corrupted or accidentally deleted you can lose your entire ubuntu install. 

Another benefit of a direct install is that you can hibernate windows and boot ubuntu with a normal install. With wubi you have to completely shutdown windows and it takes forever to restart windows (in my experience).

Running ubuntu in a VM is great for certain things (like having access to it without rebooting windows) but you don't get full access to the hardware resources so unless you have a powerhouse machine (lots of ram), the experience is painful. And even with a fancy machine the graphics will be half-baked. If you're just browsing the web it's fine.

Anyway... this post got a little long, but my advice is: if you like Ubuntu and feel you'll be using it a long time, then you should plan to partition and install direct or [migrate]("http://ubuntuforums.org/showthread.php?t=1519354") Wubi. There's no rush, but that's the best way to use Ubuntu in the long run.

PS backup everything prior to partitioning.

Im not switching but i like ubuntu. But what i want to know is, is wubi the same speed as having a normal install. Like does it preform as good as a normal install

---

### Post by Mark Phelps on 2011-06-28
> **Megacack said:**
> Im not switching but i like ubuntu. But what i want to know is, is wubi the same speed as having a normal install. Like does it preform as good as a normal install

Go BACK to post #2 -- and this time, read the quoted material.

It clearly answers your question at the end of the quote.

---

### Post by holycow131415 on 2011-06-28
Now Now Mark Phelps, how about you just requote #2 for the good fellow and not be so mean? =P

> **flipper T said:**
> 
Performance related to hard-disk access is also slightly slower, more so  if the disk image file is fragmented, on a Wubi install compared to a  normal one                      

---

### Post by flipper T on 2011-06-28
How Now Holy Cow,

how about i pop around to OP's home and read it to him / her ?

---

### Post by bcbc on 2011-06-28
In my experience, I don't notice a difference. If I boot Wubi and then boot normal, I notice that I use more ram on Wubi and it takes a little longer to boot. But when I just use wubi alone there is no noticeable slowness (like you would get running from a live USB).

Actually phoronix did [a test that quantifies the difference]("http://www.phoronix.com/scan.php?page=article&item=ubuntu_wubi_1010&num=1"). Surprisingly Wubi is faster in some areas (likely due to a bug).

---

