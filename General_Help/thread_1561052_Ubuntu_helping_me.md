---
title: "Ubuntu helping me"
date: 2010-08-25
forum: General Help
---

### Post by chapacha on 2010-08-25
So I am switching to Ubuntu for the first time. I wish to dual boot with Windows 7. It just so happens that my Windows 7 Ultimate 64-bit edition develops a problem. Let me explain the problem then how this relates to Ubuntu.

When I start my computer since it is dual boot and I can use the keyboard to choose Windows 7 or Ubuntu. Well if I choose Windows 7 then suddenly my keyboard and mouse will not work. This just happened randomly. I have been using just Windows 7 for about 4 months then about a month ago I installed Ubuntu. Keyboard and mouse have worked flawlessly until 2 days ago. Now for Windows 7 when I boot with it they keyboard and mouse won't work.

Here is what has to do with Ubuntu. Is it possible to use Ubuntu to recover the pictures and files that I want on Windows 7? After I recover them then wipe the Windows partition and just reinstall Windows on the partition again.

Basically I am asking if I could use Ubuntu to recover files that I want on Windows then reinstall Windows. Thanks in advance and if you need more information I would be happy to tell you what I can!

Thanks,
chapacha

---

### Post by silverglade00 on 2010-08-25
You can boot into Ubuntu and copy your files from your Windows partition to an external drive. Then you can reinstall Windows, but that will wipe out your ability to dual boot. You need to then reinstall grub from a live Ubuntu CD. Also, you need to be careful because Windows 7 will create two partitions, one of them 100MB boot partition and then the main Windows partition.

---

### Post by Smart Viking on 2010-08-25
Yes you can!

Most likely the windows partition will be available in the file browser when using ubuntu, you can copy the files(or directories) from the windows partition, and paste them somwhere on the ubuntu partition.

If you install windows it will screw up grub replacing it with MBR, you will need to install grub again afterwords if you want to boot from ubuntu again.

---

### Post by chapacha on 2010-08-25
Wow fast response! Well thanks for all that information! I will do that. Also is there some virtualization software for Ubuntu that I could use to have Windows 7 within Ubuntu for all my Windows only apps?

Thanks,
chapacha

---

### Post by silverglade00 on 2010-08-25
Virtualbox is the easiest to use, in my opinion. You can get the Ubuntu supported version by typing:

```
sudo apt-get install virtualbox-ose
```

If you need to use your USB devices within Windows, then you need to go download the Personal Use version at the [Virtualbox website]("http://www.virtualbox.org").

---

### Post by chapacha on 2010-08-25
Wow thank you all! I hope Ubuntu becomes more universal so I can stop using Windows :P!

Thanks,
chapacha

---

