---
title: "Here's one... fstab issues I think"
date: 2010-01-21
forum: General Help
---

### Post by JiuJitsu500 on 2010-01-21
Well I ran face first into another wall for the moment...

I deleted the extended partition and the swap.... turned swappiness to 0 in the fstab instead of the 5 I had it on, but then had a serious issue.... I obviously couldn't boot the computer. The error under the GRUB splash was soemthing like "one or more of these could not be mounted" and gave me the finger with "line 14 of the fstab" which is where I put vm.swappiness=0.....

But I solved the issue by recreating the Extended partition and formatting the unallocated space to Linux-Swap, and gave it 1GB just because it would boot that way.

Then, running "gksu nautilus" I deleted the vm.swappiness=0 from the fstab and from the backup it makes.

And now I can use my computer fine.... BUT..... the question now is it never brings up the initial splash screen, instead it brings up the boot splash and gives me "press ESC to run in recovery shell"

It works fine when I press esc and log in (though seemingly a little choppy), but does anyone know how to get rid of this?

---

### Post by john newbuntu on 2010-01-21
Can you post the output of:
sudo blkid
cat /etc/fstab
free
sudo fdisk -l

---

### Post by JiuJitsu500 on 2010-01-21
[COLOR=Blue]&#8220;sudo blkid&#8221; yields:[/COLOR]
 

 /dev/sda1: UUID="f0e4be75-4e21-41ab-99ad-a7ca899c1cd5" TYPE="ext4"  
 /dev/sda5: UUID="ac6ee9bf-986e-4c7a-a1fb-ebdcbdcdd142" TYPE="swap"  
 /dev/sdb1: LABEL="" UUID="0085-E23F" TYPE="vfat"  
 

 [COLOR=Blue]&#8220;cat /etc/fstab&#8221; yields:[/COLOR]
 
 # /etc/fstab: static file system information. 
 # 
 # Use 'blkid -o value -s UUID' to print the universally unique identifier 
 # for a device; this may be used with UUID= as a more robust way to name 
 # devices that works even if disks are added and removed. See fstab(5). 
 # 
 # <file system> <mount point>   <type>  <options>       <dump>  <pass> 
 proc            /proc           proc    defaults        0       0 
 # / was on /dev/sda1 during installation 
 UUID=f0e4be75-4e21-41ab-99ad-a7ca899c1cd5 /               ext4    errors=remount-ro 0       1 
 # swap was on /dev/sda5 during installation 
 UUID=5fa991b7-2fb8-4998-9e66-6d335413572b none            swap    sw              0       0 
 none /proc/bus/usb usbfs devgid=121,devmode=664 0 0  
 

 [COLOR=Blue]The last line right here is where I put the Swappiness setting, now I see it's gone completely though, and as a matter of fact when I was changing it to &#8220;0&#8221; I don't remember it actually having the &#8220;5&#8221; I put on there..... strange, no?[/COLOR]
 

 [COLOR=Blue]&#8220;free&#8221; yields:[/COLOR]
 

              total       used       free     shared    buffers     cached 
 Mem:       3797236    1007008    2790228          0      51980     422332 
 -/+ buffers/cache:     532696    3264540 
 Swap:            0          0          0 
 [COLOR=Blue]
[/COLOR] 
 [COLOR=Blue]I also notice here, nothing for swap... which may be the problem because I did create the point in gparted, but I never mounted it perhaps?[/COLOR]
 

 [COLOR=Blue]&#8220;sudo fdisk -l&#8221; yields:[/COLOR]
 

 Disk /dev/sda: 160.0 GB, 160041885696 bytes 
 255 heads, 63 sectors/track, 19457 cylinders 
 Units = cylinders of 16065 * 512 = 8225280 bytes 
 Disk identifier: 0x596a6dbc 
  
    Device Boot      Start         End      Blocks   Id  System 
 /dev/sda1   *           1       19329   155260161   83  Linux 
 /dev/sda2           19330       19457     1028160    5  Extended 
 /dev/sda5           19330       19457     1028128+  82  Linux swap / Solaris 
  
 Disk /dev/sdb: 500.1 GB, 500107862016 bytes 
 255 heads, 63 sectors/track, 60801 cylinders 
 Units = cylinders of 16065 * 512 = 8225280 bytes 
 Disk identifier: 0x000e4cce 
  
    Device Boot      Start         End      Blocks   Id  System 
 /dev/sdb1   *           1       60801   488384001    c  W95 FAT32 (LBA) 
 

 [COLOR=Blue]So I'm curious if I just simply didn't mount the Swap partition.... Or if I just plain forgot something else along the way....

*EDIT: It's also showing my external Hard Drive too, as I'm sure anyone can notice :)
[/COLOR]

---

### Post by blackened on 2010-01-21
The vm.swappiness value belongs in /etc/sysctl.conf, not fstab.

Was the extended partition listed in fstab and, if so, did you remove the entry for it after you deleted it? 

Altering the partition table on a working install is dodgy business to just start mucking around in. But breaking things is the fun way to learn I suppose. Make backups.:D

---

### Post by JiuJitsu500 on 2010-01-21
Okay... update because I do realize a total mistake :) oops!!!! I checked sysctl.conf and the swappiness is there :) holy crap I can't believe I was making that screw up!!! HA!!!!

And the extended one was listed, and I didn't delete anything from the file.... but it did write the Swap partitions in all the same places (sda2, sda5)...

And dodgy business... what's the point of linux without making serious mistakes and learning? :) And I am learning that's for sure.... simple mistakes can go a long way, and I've made plenty... obviously :D

---

### Post by JiuJitsu500 on 2010-01-21
I still do have that crazy press esc problem though.... any ideas on that weird thing?

---

### Post by Elfy on 2010-01-21
swap uuid is wrong in fstab

> UUID=5fa991b7-2fb8-4998-9e66-6d335413572b none swap sw 0 0 

blkid shows > ac6ee9bf-986e-4c7a-a1fb-ebdcbdcdd142 for swap - change that 

```
gksudo gedit /etc/fstab
```
save close and then 

```
sudo swapon -a
```

check that swap is recognised with

```
free -m
```

---

### Post by JiuJitsu500 on 2010-01-21
Spledid! I got Swap recognized.... let me reboot real fast before I treat this as Solved :)

Yup! did the trick! Thanks!

---

