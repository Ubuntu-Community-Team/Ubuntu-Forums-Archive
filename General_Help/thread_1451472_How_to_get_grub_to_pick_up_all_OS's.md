---
title: "How to get grub to pick up all OS's?"
date: 2010-04-10
forum: General Help
---

### Post by candtalan on 2010-04-10
I am using Ubuntu 8.04.4 which is on the first partition. There are other installs of Ubuntu on this hard drive in other partitions, of Ubuntu 8.10 and Ubuntu 9.04. Both grub legacy as I understand it.

I use 8.04.4 LTS for daily use, although the 8.10 and 9.04 were installed subsequently for interest and testing etc and are used regularly but less frequently.

Events have caused me to reconfigure the machine, and I now decided to use the first partition (ubuntu 8.04.4) to boot from. 

I cannot seem to get menu.lst created by grub so as to include not only the 8.04.4 entries, but also the entries for the other two systems. 

I am running triple boot ubuntu on machines with no problems in other circumstnces, usually the last ubuntu installed takes over, and it includes full grub entries of the pre existing installations.

This is what I am doing now, an dfailing to get a 'full' menu.lst

From my running 8.04.4
```

grub> find /boot/grub/stage1
 (hd0,0)
 (hd0,5)
 (hd0,7)

grub> root (hd0,0)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,0)/boot/grub/stage2 /boot/grub/menu.lst"... succeeded
Done.
grub> 

quit


```

I then did
```

sudo update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.24-27-generic
Found kernel: /boot/vmlinuz-2.6.24-26-generic
Found kernel: /boot/vmlinuz-2.6.24-25-generic
Found kernel: /boot/vmlinuz-2.6.24-24-generic
Found kernel: /boot/vmlinuz-2.6.24-23-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

```

Finally, examining menu.lst, all I see is the 8.04.4 stuff. I do *not* see anything for 'Other OS's' or the like.

What am I missing here if I want the other OSs on other partitions on the drive to be picked up?

tia

---

### Post by dcstar on 2010-04-10
> **candtalan said:**
> I am using Ubuntu 8.04.4 which is on the first partition. There are other installs of Ubuntu on this hard drive in other partitions, of Ubuntu 8.10 and Ubuntu 9.04. Both grub legacy as I understand it.
.......
What am I missing here if I want the other OSs on other partitions on the drive to be picked up?


Then install grub2, legacy grub does **not** automatically find OSs post-install.

If you want to retain legacy grub then **you** must manually enter the other OSs.

---

### Post by candtalan on 2010-04-11
> **dcstar said:**
> Then install grub2, legacy grub does **not** automatically find OSs post-install.

If you want to retain legacy grub then **you** must manually enter the other OSs.

Thanks!
If I retain legacy grub for the time being now, will it get upgraded to grub2 when I do an online version upgrade going from LTS 8.04.4 to LTS 10.4 do you know please?

---

