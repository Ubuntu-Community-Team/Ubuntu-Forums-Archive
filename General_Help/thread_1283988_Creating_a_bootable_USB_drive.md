---
title: "Creating a bootable USB drive"
date: 2009-10-06
forum: General Help
---

### Post by rmcellig on 2009-10-06
On my Mac, I am able to create a bootable clone of my hard drive using an application called Superduper. Same goes for my PC as well. I use Norton Ghost to clone my PC drive without having to boot from a CD to do it.

Is there a way to do this in Ubuntu so that if anything happens to my main drive, I can quickly boot up from an external cloned USB drive? Right now I am cloning my drive using a Clonezilla CD which I find kind of cumbersome after using the above methods for Mac and PC.

I understand also that I might be able to use the USB startup disk creator tool to create a bootable USB drive of my main HD? If so, is there a video explaining how to do this?

I am running Ubuntu 9.04.

---

### Post by Lars Noodén on 2009-10-06
This isn't a video, but maybe it might be what you are after anyway:

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

If you search around there are many ways to put live CDs on USB sticks.  
If the purpose is recovery, then you might consider a distro like Finnix, which has system administration tools packed onto the CD.  Or you can roll your own live CD
[http://www.linuxjournal.com/article/7246](http://www.linuxjournal.com/article/7246)
[http://www.howtoforge.com/ubuntu-linux-mint-livecd-with-remastersys](http://www.howtoforge.com/ubuntu-linux-mint-livecd-with-remastersys)

---

### Post by rmcellig on 2009-10-06
Thanks. I will take a look at that. In the meantime, I booted from the Clonezilla CD and tried to clone my Ubuntu drive to my external USB partition. I was successful but I can't seem to mount the USB partition or even boot from it. What should I do. Here is a screenshot. SDB2 is the one I am trying to mount on my desktop and also the partition I would like to be able to boot from in case I ever need to. Is it because the mount point is the same as my Ubuntu main drive? If so, what should I set the mount point to?

---

### Post by Lars Noodén on 2009-10-06
What does dolphin or thunar do when you plug the usb drive in?   (Exit the other programs first.)

---

### Post by ushernut on 2009-10-06
I got same issue here.

---

### Post by rmcellig on 2009-10-06
I will try Dolphin and Thunar and post back.

---

