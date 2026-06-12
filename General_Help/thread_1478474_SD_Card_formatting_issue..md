---
title: "SD Card formatting issue."
date: 2010-05-09
forum: General Help
---

### Post by awtodd89 on 2010-05-09
So here is the problem: I have this SanDisk SDHC 8 GB that I have been using for my Wii for games and such.

So, earlier today I plugged it into my Windows 7 machine and it said that it needed to be formatted. I thought that to be a little odd, so I plugged it into my linux machine and it popped up just fine. So I made a quick copy to be safe and procceded to plug it back into the Windows 7 machine. It said that it needed to be formatted, so I choose the option to format. Well, I ended up with an error message, so I went back to my linux machine.

Nothing happened when I plugged it in, so I went hunting on the internet for a bit of answers.

So I happened upon web page that had some instructions on formatting in linux and what not. So I ran fdisk and a brought up the partitions, but I had none. So, I created a partition, using the defaults options available, then after that I ran mkfs -t vfat /dev/sdb1 for my drive. Shortly afterwards the drive was mounted and I thought that I had successfully completed my task.

Well, I was wrong. I put the drive in the Windows 7 machine but it said it needed to be formatted. So...I clicked ok. Failed. No suprise, I put the drive back in the linux machine and ran fdisk again and noticed that I had no partitions again.

Now I'm not really sure whats going on. When I format the drive in linux, it works -- but only with the linux machine I have. When I take it to any other computer or device (I've tried it on my wii and dsi as well) it says either the drive needs to be formatted or the sd card cannot be used. So I'm thinking maybe I just have a bad SD card, but I'm hoping that's not the case.

I'm using Ubuntu 10.04, FYI.

Thanks for any help in advanced!

---

