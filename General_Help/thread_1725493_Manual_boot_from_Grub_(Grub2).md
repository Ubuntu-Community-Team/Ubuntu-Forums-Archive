---
title: "Manual boot from Grub (Grub2?)"
date: 2011-04-09
forum: General Help
---

### Post by jruh64 on 2011-04-09
Hi,
After resizing/moving some partitions using Gparted I am unable to boot into Ubuntu.
I first got error saying "unknown filesystem" and it went to "Grub rescue" mode.
 
I did search and found some tutorials to fix this. From instructions [here]("http://www.dedoimedo.com/computers/grub-2.html#mozTocId842078") I was able to install Grub and now when I start the system it goes to a grub> prompt.
 
I have been trying to manually boot my Ubuntu 10.10 from grub menu by following instructions at [help.ubuntu.com ]("https://help.ubuntu.com/community/Grub2#Command%20Line%20Mode")but I keep getting 'file not found'.
 
Have run a Ubuntu Live session from thumb drive to access and verify locations of my partitions. 
 
My boot partition is sda5 and my ubuntu install is in sda7. sda6 is swap, sda8 is where /home is mounted, sda9 is an NTFS partition. All of these are contained in the extended partition sda4.
sda1, sda2 and sda3 are my Windows7 installation.
 
When i do an 'ls' command from grub it returns:
(hd0) (hd0.msdos9) (hd0,msdos8  ) (hd0,msdos7) (hd0,msdos6) (hd0,msdos5) (hd0.msdos3) (hd0,msdos2) (hd0,msdos1)
 
When I do an ```
ls (hd0,5)/
``` command, it does show that the file (kernel?) is there. "vmlinuz-2.6.35-28-generic-pae" as well as "-27-" and "-25-" versions.
 
When I try:
```
 
set root=(hd0,7)
linux /vmlinuz root=/dev/sda5 ro

```
it returns 'file not found'
I am a little (a lot) unclear as to which partitions to specify in these commands. sda5 is my boot partition, sda7 is my ubuntu root partition.
I have tried every combination i could think of but still get 'file not found'.
I have also tried:
```
 
linux /vmlinuz-2.6.35-28-generic-pae root=/dev/sda5 ro

```
and still get 'file not found'
 
I am sure this is all due to my own ignorance and really hoping someone can enlighten me. Hoping I won't have to wipe and re-install everything on this HDD.
 
Thanks in advance, John

---

### Post by techunit on 2011-04-09
When you installed GRUB you didn't tell Grub where to findYyour partitions and what to do with them. 

You may just need to reboot into a live cd chroot into the Harddisk and run a ```
sudo update-grub
```

---

### Post by jruh64 on 2011-04-09
Thank you techunit.
 
This is probably a dumb question but how do i 'chroot' into the HDD?
 
Thanks, John

---

### Post by oldfred on 2011-04-09
Example with separate /boot:

Separate /boot on sda1, / on sda2:
grub> set prefix=(hd0,1)/grub
grub> insmod linux
grub> set root=(hd0,2)
grub> linux (hd0,1)/vmlinuz-2.6.32-30-generic root=/dev/sda2 ro
grub> initrd (hd0,1)/initrd.img-2.6.32-30-generic
grub> boot

---

### Post by jruh64 on 2011-04-10
OK,
 
Following instructions from [this site,]("http://www.dedoimedo.com/computers/grub-2.html#mozTocId842078") I did the following:
 
```
 
##sda5 is my boot partition, sda7 is my ubuntu install (root)
 
sudo mount /dev/sda7 /mnt
 
sudo mount /dev/sda5 /mnt/boot
 
sudo mount --bind /dev /mnt/dev
 
sudo chroot /mnt
 
dpkg-reconfigure grub-pc 

```
 
This opened up a somewhat graphical grub reconfiguring program that seemed to hang up at one point until i hit 'esc' key. then it listed all partitions and i selected sda5 as my boot partition (at least i think that's what i did).
 
after that i tried to unmount all the drives per instructons but it would not let me, said they were busy.
 
I rebooted and now it does boot into Ubuntu!! :D but there is no option to boot into windows now :(.
 
Still was curious how to boot manually from grub command line so i rebooted and hit 'c' to get back to command line and i tried it using the help from **oldfred.**
it did find the kernel this time and it did boot!
 
So now i am able to boot into Ubuntu but not windows yet. How can I properly configure Grub now that i am booted into Ubuntu.  Before messing this all up i actually had BURG as my bootloader and it was very nice.  How can I get that working again?
 
Thanks again, John

---

### Post by oldfred on 2011-04-10
Do not know about burg.

To get grub's os-prober to scan system for windows.

sudo update-grub

---

### Post by jruh64 on 2011-04-10
thanks again oldfred,
 
That is excactly what techunit had told me to do previously but for some reason I never did try it in my confusion.  i will try that as soon as i get home this afternoon.
 
Thanks, John

---

### Post by jruh64 on 2011-04-10
Well that did the trick.
Grub is fully functional and i can boot to Ubuntu or Windows again.
I will look into restoring BURG again sometime in future, at least my system is running again.

Thanks a bunch to techunit and oldfred!!!

---

