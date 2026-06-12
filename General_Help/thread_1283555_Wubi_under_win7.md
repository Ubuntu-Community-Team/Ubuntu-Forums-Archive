---
title: "Wubi under win7"
date: 2009-10-05
forum: General Help
---

### Post by Gonz_91 on 2009-10-05
Hi everyone!

I've used Ubuntu for a few months last year, and loved it, but... well, there were a lot of things I needed in windows (namely world of warcraft, and office '07, which never ran well on my ubuntu install). So, a few days ago I read about the first 9.10 beta coming out, and I thought I'd give it a spin through Wubi.

Well, long story short, I pop the disc in the drive, run Wubi, install the thing, boot into it, wait for that "Checking Installation" thingy to end, it reboots on itself, I choose "Ubuntu", and then I get to some GRUB-related menu, and never get to see a desktop...

So... Any ideas?

[Prefixed as 'all variants' because I tried both Ubuntu and Kubuntu, and I really don't think I'll have more luck with the others...]

---

### Post by bigboy_pdb on 2009-10-05
I've never used Wubi so I won't be able to help you with getting it to work. However, if you want the benefits of both, you could try installing Ubuntu in a virtual machine within Windows.

---

### Post by Gonz_91 on 2009-10-05
> **bigboy_pdb said:**
> I've never used Wubi so I won't be able to help you with getting it to work. However, if you want the benefits of both, you could try installing Ubuntu in a virtual machine within Windows.

That's a no-go for me. My computer's fairly weak, so, running ubuntu on top of 7 would be... well, bad. And pointless.

I can either go with wubi or the partition-your-drive way.

By the way, I know a disc can't have more than 4 partitions, or all hell breaks loose, but I can have 2 partitions, then an extended one with 3 under it, right?

Thx a lot :D

---

### Post by louieb on 2009-10-05
4 primary or 3 primary + 1 extended. The extended partition allows you have an additional 15 logical partitions on a SATA drive (more than that if the drive is IDE/PATA) [Nuts n Boldt: Partitions 101]("http://louboldt.com/ilinuxpart.htm")

---

### Post by Gonz_91 on 2009-10-06
> **louieb said:**
> 4 primary or 3 primary + 1 extended. The extended partition allows you have an additional 15 logical partitions on a SATA drive (more than that if the drive is IDE/PATA) [Nuts n Boldt: Partitions 101]("http://louboldt.com/ilinuxpart.htm")

Well, in that case, I think I'll be going with the partitioning way, again. I'll put a home, install and swap partitions inside an extended one, and leave it at that...

Thanks a lot for your help :D

---

### Post by bigboy_pdb on 2009-10-06
Installing Linux on a partition after Windows has been installed isn't too hard. All you need is a [live CD with gParted]("http://gparted.sourceforge.net/livecd.php") and your Ubuntu installation disk. You can boot with the live CD that has gParted on it to resize the Windows partition. Following that you'd install Ubuntu (being careful not to overwrite the Windows partition).

Also, don't forget to backup your files before you start. External hard drives and CD/DVD-RWs are good for this.

Although, if you've tried that before, you should be fine.

**EDIT**: You mentioned World of Warcraft and I noticed it's on the platinum list for Wine, meaning you might be able to get it to work. Mind you, if your video card or any other important hardware isn't well supported by Ubuntu then it could be problematic.

---

### Post by praveenthivari on 2009-10-12
Well friend I too had the same problem but it was not at the beginning of installation. It was after all the installation was over; it would ask for reboot to continue using the system and when it rebooted there was dual boot option and on selecting ubuntu there was some sort of error with grub.

So, I posted on this forum and was told that may it is a bug. So, I have uninstalled 9.10 and installed 9.04 from outside( that is in separate drive.)

---

