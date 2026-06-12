---
title: "Installed Ubuntu, Now need help making it primary os"
date: 2012-07-20
forum: General Help
---

### Post by macishayne on 2012-07-20
I installed Ubuntu for the first time today. I LOVE it. My problem is, I don't have another os installed, but I installed ubuntu to a separate partion anyway because all of my file and pictures are saved on a separate partition and I was afraid it would erase it. My hard drive is C and the separate partition I created I named M. Is there a way to install Ubuntu to the C drive without erasing M?

---

### Post by mikewhatever on 2012-07-20
No, there is not. Ubuntu can't be installed on a FAT32 or NTFS partition, you'll need to format it first. Besides, installing on one partition rather then another doesn't make an OS primary or secondary.

---

### Post by lrcaballero on 2012-07-20
Have you consider transferring all your media/photos into a DVD? or better yet if you have an external HDD just transfer it all to the external HDD, you can do this using any distribution Live DVD/CD in your case Ubuntu 12.04.

Good Luck

---

### Post by oldfred on 2012-07-20
If you are still referring the 'drives' (really partitions in most cases) as letters, then you are still in Windows.

So is this a wubi install? Wubi is just a file root.disk that is inside the NTFS Windows partitions. It uses the Windows boot loader and then is like a full install but is really for an extended test of Ubuntu for those who are primarily Windows users and do not want to re-partition.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

If you went to the effort of creating new partition(s) then you could do a full install in a separate partition. That would be true dual boot.

---

### Post by macishayne on 2012-07-22
The partition was created while I had windows, but the windows was removed. When I installed Ubuntu, I used a usb drive to boot from. There was no OS installed when I installed it. But I wasn't sure I'd like Ubuntu so I didn't give it much space. That's what I'd like to do. I can't enter my bios because it's password protected, and I never set a password. As for moving the files to dvd, There are 80gb's worth of files (I'm a photographer) and all my dvd's were 4gb & used. The /root file is on my c drive if that helps. (c is where windows was before.)

---

### Post by oscarivera9 on 2012-07-22
Like oldfred said, if you are still referring to a partition as a C:\ drive, then you are still using Windows.

  Use GParted (if you don't have it installed, then get it from the Ubuntu Software Center) and post a screenshot of what GParted shows you.  If we have an idea of what your hard drive looks like as far as what partitions you have, what they're formatted to, and how big they are, we'll be better able to help you.

You can also try what lrcaballero suggested, which is to transfer everything to an external hard drive, then reinstall Ubuntu but this time use the entire disk if that's what you wish.  Better yet, use a separate partition for your root folder ( **/ **) and a separate partition for your /home folder, that way all of your data will be stored in your **/home** and the operating system will be installed in  **/**   so that if you later decide to install a different OS, you can do so without being in the same predicament in which you find yourself right now.

---

### Post by macishayne on 2012-07-22
[IMG]http://i1067.photobucket.com/albums/u430/Maci_Everwood/Screenshotfrom2012-07-22041810.png[/IMG]

---

### Post by mikewhatever on 2012-07-22
First, already Ubuntu is your primary OS (whatever that means for you), because there aren't any others to claim the title. With that out of the way, if you want Ubuntu installed on /dev/sda1, I'd say that reinstalling would be the most reasonable approach. There is no need to delete other partition in the process, but if you keep /dev/sda6, you'll end up with two installations.

---

### Post by nothingspecial on 2012-07-22
There is absolutely no problem with what you have already. I wouldn't worry about it.

---

