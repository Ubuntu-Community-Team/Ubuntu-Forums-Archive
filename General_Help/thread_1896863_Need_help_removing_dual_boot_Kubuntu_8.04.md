---
title: "Need help removing dual boot Kubuntu 8.04"
date: 2011-12-17
forum: General Help
---

### Post by grandpabear on 2011-12-17
I have a problem in that I need to remove a dual boot installation on an IBM G41 Laptop so I can give the laptop to my church to use (they are happy with the XP (SP3) also loaded on it). The problem is that the logon that worked for the first two weeks I played with the install (Kubuntu 8.04 disk) has changed either in my iPhone or on the computer. I can say that I know which partition needs to remain intact; it is just the rest of the partitions I would like to dispose of. 

I need to know how to get rid of the Kubuntu installation, especially the boot manager, so I can reconfigure the HDD for the church.:confused:

Any help, other than telling me how stupid I am (I take heavy pain pills for ankylosing spondylitis), will be greatly appreciated.:)

I will try to check this every day so please be patient if I miss a day or two, lots of things happening right now and this is but one small fire.:redface:

---

### Post by 2F4U on 2011-12-18
If you have the Windows XP installation disk that has an option to repair the boot loader. This would restore the Windows boot loader to MBR and overwrite Grub. From that moment on, the Kubuntu partition is just like any other partition, meaning you can format it and use it the way you like.

---

### Post by grandpabear on 2011-12-19
Thanks. I'm sure it is around here somewhere (I have two or three XP discs, and I'm down to 4 computers running XP, two running Linux, and a new Apple that I'm working on learning how to use).
Just in case I can't find it, what is the next choice?

One thing I need to own up to, I installed a second version of Linux so right now the computer has the following (gleaned when running the second installation--loaded so I could work from within Linux, if needed):
Partition  Size      Mount Point   Type   Device       Enabled      my notes
1.           34.9GB                              /dev/sda1                    This is the XP partition
2.           8.9GB                                /dev/sda2
3.           3.9GB                                /dev/sda3
4.           1.0KB    /proc                     proc           enabled     Obviously the 2d install
5.           17.2GB                              /dev/sda5
6.           807.9MB                            /dev/sda6
7.           8.5GB                                /dev/sda7  enabled     Obviously the 2d install?
8.           439.2MB                            /dev/sda8   enabled     Obviously the 2d install?
System...
Burner...

Yup, I like to be difficult with my problems. I was hoping that I could dump the first Linux install, change the Boot Manager to run Windows XP if nothing is done during boot, and hiding the 2nd Linux installation onboard so I can operate in that mode if needed while restricting what can be done in XP by the people who would try to use this for the wrong things.

Thanks,
Art  :redface:

---

