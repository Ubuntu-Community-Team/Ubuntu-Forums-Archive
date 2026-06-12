---
title: "Grub 1.5 Error 15"
date: 2012-05-06
forum: General Help
---

### Post by bchin on 2012-05-06
Hi,

I searched google and this forum for help on this issue, and none of the solutions I read worked, so I'm starting this new thread.

Anyways, I have an old athlon 3800+ x2 computer with one ide hard drive (windows xp) and one sata hard drive (ubuntu). My recently upgraded to 12.04 with an old kernel (3.0) because the 3.2 kernel panics when I try to start up. And I finally decided to upgrade to grub2 because I couldn't help myself, I was in some upgrading mood. 

I did all the "update-grub2" and "upgrade-from-grub-legacy", and I made sure to select my /dev/sdb1 drive because that's where my /boot partition was located. Anyways, after I rebooted, I got the

Grub Loading stage 1.5.
GRUB loading, please wait...
Error 15

So I tried to fix it by following instructions from places like [here]("http://linuxers.org/howto/how-fix-grub2-error-15-ubuntu"). I spent so much time trying to fix it, that I decided to format and re-install my /boot and / partitions using Ubuntu 11.10.

That didn't work either. I still got the Error 15. Then I decided to unplug my sata cable and boot up from my windows hard drive only, so I could get some work done. I could not boot up windows xp. I got the Grub Error 15 message. 

I reinstalled my windows C: partition, and now I can boot up to windows. 

What should I do next? Right now I'm thinking of re-install grub 1.5. Thanks for any help anyone can provide.

---

### Post by bchin on 2012-05-06
It appears, if I disable my ide ports (windows partition), I get a Grub error 18 instead when I try to boot up my Ubuntu or sata drive.

---

### Post by oldfred on 2012-05-06
It sounds like your grub was installed to the Windows drive. Does your system let you boot either drive?

You install the grub2 boot loader to the MBR of the drive you want to boot from. Some older computers could only boot from sda, most newer can boot from any drive that you set in BIOS. If you can boot from sdb,  then install grub2's boot loader to sdb.

If you have a separate /boot partition, you have to also mount that with a grub2 reinstall.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or Create BootInfo report & post the link to a run of boot info script so we can see your exact configuration. If you use this to reinstall, be sure to tick the extra /boot partitioin.

Most instructions only mention the /boot as a footnote, so be sure to see those extra instructions.
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 and later with grub2) by talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)
Grub2 info & full chroot version - also see METHOD 3 - CHROOT:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

---

### Post by bchin on 2012-05-06
after reading [this]("http://forums.techguy.org/linux-unix/1010466-solved-grub-error-18-selected.html"). I got the idea that my root partition was too big: 256GB. Before all these problems started, my computer had /, /usr, /var, and /home partitions. So I just re-install ubuntu 11.10 with a smaller root (/) partition: 128GB. My computer can now boot up to windows and ubuntu.

also, thank you oldfred for the reply. I just saw your reply when I was going to write this update.

---

