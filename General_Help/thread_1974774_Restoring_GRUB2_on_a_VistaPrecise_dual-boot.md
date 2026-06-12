---
title: "Restoring GRUB2 on a Vista/Precise dual-boot"
date: 2012-05-06
forum: General Help
---

### Post by yttriuszzerbus on 2012-05-06
A few days ago, I installed Precise Pangolin with the installer CD, it chose 12GB of free space next to my Vista partition. Today, I decided to expand that partition and reduce the size of my windows partition. The result was that now, instead of the GrUB boot menu, I get:
error: no such partition.
grub rescue>

I have booted into a Precise live CD and tried the following:
sudo grub
find /boot/grub/stage1

as many threads on various forums instruct, but it says:
Error 15: file not found

Any ideas how I can fix this? I don't mind wiping the Ubuntu partition, but I don't have the Vista installation media, so I really need to keep that.

Thanks in advance,
yttriuszzerbus

---

### Post by kc1di on 2012-05-06
Try Boot Repair found here:

[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

---

### Post by oldfred on 2012-05-06
+1 on Boot-Repair.

The instructions you found must be old. Ubuntu has used grub2 since 9.10 and finding stage1 is part of grub legacy (0.97).

---

### Post by spideryada on 2012-05-07
I like the Boot Repair from Source Forge,
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)

You can write the image to a cd or flash drive and boot to that.

Real easy to use. Just click on the recommended repair choice. 

Advanced option is real powerful for more complex problems.

spider

---

### Post by AlexOnVinyl on 2012-05-07
To be honest, your best bet would be to use the Windows Bootloader instead of GRUB2 because of how Windows reacts to it when you load from GRUB.

Here's an article on how to do just that using the program [EasyBCD]("http://neosmart.net/download.php?id=1") its a free program, all you need to do is put in some fake email address or use one from Mailinator.com and then your name and they give you the personal licensed version for free.

Here's how to set it up for dual booting: and will save you a lot of grief - [EasyBCD Windows Bootloader for Dualbooting Ubuntu and Windows]("http://www.ubuntugeek.com/use-the-windows-bootloader-to-dual-boot-windows-vista-and-ubuntu.html")

---

### Post by yttriuszzerbus on 2012-05-07
On the third attempt, Boot Repair fixed it. Many thanks to everyone who posted here.
yttriuszzerbus

---

### Post by kc1di on 2012-05-07
> **yttriuszzerbus said:**
> On the third attempt, Boot Repair fixed it. Many thanks to everyone who posted here.
yttriuszzerbus

Glad you got it going. enjoy ;)

---

