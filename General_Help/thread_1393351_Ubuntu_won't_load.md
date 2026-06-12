---
title: "Ubuntu won't load"
date: 2010-01-29
forum: General Help
---

### Post by airwolf on 2010-01-29
Hello,

Recently I reinstalled Ubuntu on my computer and now whenever I shutdown and turn the computer back on in the morning, I cannot load ubuntu.
I get the grub menu and after selecting ubuntu from the list, it starts loading and then all I get is a blank screen. It doesn't matter how many times I reboot, it just won't load. My computer is a dual boot with XP on another partition and if I log into windows first and then restart the computer, I can load ubuntu. It works fine after loading XP first.

I'm thinking there's something wrong with grub but don't know how to fix it. Any help will be really appreciated.

Thanks.

---

### Post by anaconda on 2010-01-29
I think grub2 does indeed have some problems
 
I have almoust the same problem. But I dont have any other os on the machine. Luckily Ubuntu will boot on 1-4 tries, 

I am going to install old version of grub to try to correct this problem. 
Older grub should correct the problem.. the drawback is that I am not sure if old grub can boot from ext4 partition?

---

### Post by Roel Verlaek on 2010-01-30
Hello out there,

I had this problem also yesterday. I couldn't login anymore. I got a terminal like screen at the end but no grub.
I solved the problem by reinstalling GRUB 2 as written in the documentation of ubuntu.
See the link attached, chapter 11:

[https://help.ubuntu.com/community/Grub2#Reinstalling GRUB 2]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202")

I only have two remarks:
1. I used sudo bash to get root rights. You don't have to use sudo for each command you give
2. I got the questen which filesystem sda1 uses.
So to solve this I changed the command in:
mount -t ext4 /dev/sdXY /mntThe rest went perfect for me and after reboot everything was working as before, :)

Hope that this will work for you too.

---

