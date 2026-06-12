---
title: "GRUB error: no such partition grub rescue&gt;"
date: 2010-09-28
forum: General Help
---

### Post by JohnElway on 2010-09-28
FYI: I know this is a common error, but my situation is a little different than previous threads on this issue and I just want to make sure I get the correct solution.

Basically, I had Ubuntu 10.04 and Windows 7 on my netbook and wanted to try a more lightweight version of Ubuntu. After settling on LXDE for a desktop, I decided to install Lubuntu 10.04. I chose not to install LXDE over regular Ubuntu because I wanted to eventually end up with an Ubuntu distro with either GNOME or LXDE, but not both. So rather than put myself through the hassle of uninstalling all the GNOME or LXDE packages, I decided to keep them each on separate partitions.

In the end I decided to just stick with regular Ubuntu and deleted the Lubuntu partitions. Now I get the GRUB error written in the title of this thread. Any ideas on how to fix this?

---

### Post by Quackers on 2010-09-28
I think you may need to purge/re-install grub2. Have a look at this thread. It involves different circumstances, but I think it decribes what you need to do.
[http://ubuntuforums.org/showpost.php?p=9836539&postcount=5](http://ubuntuforums.org/showpost.php?p=9836539&postcount=5)

Maybe somebody else could confirm that this is the correct action.

---

### Post by oldfred on 2010-09-28
The link Quackers posted will work. It is the full chroot method. But you should be able to use the  short method.

Install MBR from LiveCD, Ubuntu install on sda5 and want grub2 in drive sda's MBR:
Find linux partition, change sda5 if not correct, and/or even sda if sdb wanted:
sudo fdisk -l
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda

Short version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by Quackers on 2010-09-28
Thanks for that oldfred. I thought there was a shorter method, but due to my Ubuntu inadequacies I usually have to use the full monty :-)

---

### Post by JohnElway on 2010-09-30
> **Quackers said:**
> I think you may need to purge/re-install grub2. Have a look at this thread. It involves different circumstances, but I think it decribes what you need to do.
[http://ubuntuforums.org/showpost.php?p=9836539&postcount=5](http://ubuntuforums.org/showpost.php?p=9836539&postcount=5)

Maybe somebody else could confirm that this is the correct action.

I tried using the method in the post you linked but I got an error from the first command stating that "/etc/resolv.conf" did not exist. I ended up just reinstalling Ubuntu and now everything works fine, so I'll mark this as solved.

---

