---
title: "How to move  &quot;/boot&quot;  folder to another partition?"
date: 2012-01-24
forum: General Help
---

### Post by iX9 on 2012-01-24
Hi!;)
I need to encrypt whole system partition with Natty Kubuntu (on /dev/sdb3, ext4).
So, I created new small partition (/dev/sdb2, ext4) for /boot folder.
Then I just copy folder /boot to this partition.
Next I ran LiveCD, and:
  mount /dev/sdb3 /mnt
  grub-install --root-directory=/mnt/ /dev/sdb2 --force
Partition /dev/sdb2 is marked "active" - so I can install grub loader to this partition (instead to MBR), and boot from it.

This works, BUT:

If I will need to run "sudo update-grub", what /boot folder will be actualised? Old one (on sdb3), or the new (on sdb2)??
And how to alter or force system to update the right one? (What exactly edit?)

ThanX.
:D

---

### Post by raja.genupula on 2012-01-24
It will move to new /boot . i mean to sdb2.

---

### Post by Lampi on 2012-01-24
> **raja.genupula said:**
> It will move to new /boot . i mean to sdb2.
possibly, but to be sure he can mount sdb2 to /boot using /etc/fstab

---

### Post by oldfred on 2012-01-24
You do not install grub2's boot loader to the /boot partition, although it should not hurt. That installs grub to the PBR or partition boot sector and you have to have another boot loader to chain to the PBR.

It is somewhat like a move home. You also have to edit fstab to mount the new /boot. I think after editing fstab and a mount -a command a reinstall of grub to the MBR will recognize the new location of /boot. 
I did it with grub legacy years ago but never with grub2. I then decided I did not want /boot and reconfigured to a grub only boot parition as grub legacy worked well with chainloads.

#edit fstab to add /boot entry
sudo mount -a
sudo grub-install /dev/sda


From a liveCD you have to mount the /boot as well as / (root) to install grub to the MBR so it knows /boot is not in /.

#If separate /boot
$ sudo mount /dev/sda2 /mnt
$ sudo mount /dev/sda1 /mnt/boot
$ grub-install --root-directory=/mnt /dev/sda

#If separate /boot & Natty or later
$ sudo mount /dev/sda7 /mnt
$ sudo mount /dev/sda5 /mnt/boot
$ sudo grub-install --boot-directory=/mnt/boot /dev/sda

---

### Post by iX9 on 2012-01-24
> **oldfred said:**
> 
#edit fstab to add /boot entry


OK, please, what line exactly should be in fstab? I'm not sure:

```

# /dev/sdb2
UUID=9711c560-2ed2-4eef-baf5-eda014509f6e /boot ext4 0 0

```
(I am using UUID more likely than /dev/sd??, for higher reliability.)
And, if I mount it like this, then should I copy (move?) to boot partition only the content of /boot folder or the folder itself? (To not have /boot/boot/ instead of /boot ?
And, after copying, should I delete original /boot folder or not?


> **oldfred said:**
> 
You do not install grub2's boot loader to the /boot partition, although it should not hurt. That installs grub to the PBR or partition boot sector and you have to have another boot loader to chain to the PBR.


  I am using YUMI MultiBoot loader on this disk (for booting some others ISOs directly from hardrive); it installs loader to MBR and is using first partition (/dev/sdb1, FAT32). If I will install Natty's GRUB2 to MBR, I'am not sure if this will work any more... This is the purpose of using grub2 installed to boot sector of partition instead of MBR.

---

### Post by oldfred on 2012-01-24
I am sure you do not want /boot/boot. You do need all of /boot and /boot/grub in the new partition. I think your fstab entry looks ok.

You also need to run a sudo update-grub as the grub menu has to have the set root and search lines looking at the /boot partition but the kernel line still looks for the / partition.

You can delete the /boot in your install, but I might not until I was sure it was booting correctly with the new partition. perhaps rename the /boot in / to /bootold so it will not work and see if it then only boots with new /boot partition. Be prepared to boot from a repairCD if necessary.

If you have to have grub in the PBR you may need to run this so it reinstalls to the PBR on updates. It remembers where to reinstall.

I think this is only by drive not partition but it will not hurt.

#to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

I do not know yummi but use grub2 to loopmount isos directly from harddrive.

ISO Booting with Grub 2 from Hard drive - drs305
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
Boot ISO from harddrive. To install it would have to be different partition
[SOLVED] Using grub 2 to boot an iso off hard drive
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)

---

### Post by iX9 on 2012-01-24
Thank You very much!
Tomorrow I will reconfigure /boot and try to iso-boot.
If succes, I will not need to have three partitions, probable one will be enough for /boot and isofiles together...

And then, I can finally encrypt system partition. I was planned to do it by truecrypt, becouse I use it in M$ OS, but it dont support whole linux system. What tool to use You recommend? LUKS? Is there any good tutorial for encrypt installed system? I mean, with alternate CD I can do it by installation, but after...?

---

### Post by oldfred on 2012-01-24
May be best to start a new thread. I thought full encryption required LVM.

I avoid encryption as I see too many who have not backed up and then have issues and want to recover from an encrypted partition.

---

### Post by iX9 on 2012-01-25
It works! With special partition just for /boot I am familiar now.

Next step: For reduction of numbers of partitions now I trying to make one for /boot together with YUMI's multiboot files. It must be FAT32, and I would like to have my linux /boot/* files in /dev/sdb1/MultiBoot/Boot/ folder. Is some-how possible to mount /dev/sdb1/MultiBoot/Boot/ to /boot ? Otherwise, maybe I can live with /boot/* files in the root of /dev/sdb1, but it will be a mess...
So, how to have /dev/sdb1 mounted in /media/M, but folder dev/sdb1/MultiBoot/Boot have mounted as /boot?

---

### Post by oldfred on 2012-01-25
Once booted you can link, but that I think is part of Ubuntu not the grub boot loader. 
So I do not think grub or most boot loaders would support a linking to another location.

Back to original question. Why YUMI? I find I can do just about everything with grub2. But then I now know grub2 best.

---

### Post by iX9 on 2012-01-25
> 
Once booted you can link, but that I think is part of Ubuntu not the grub boot loader.
So I do not think grub or most boot loaders would support a linking to another location.

Link will not work, I agree. To have a little mess on boot partition, it is smaller trauma than to have two boot partitions.. ;)

> 
Back to original question. Why YUMI? I find I can do just about everything with grub2. But then I now know grub2 best. 

[YUMI]("http://pendrivelinux.com/yumi-multiboot-usb-creator/") I use because it can boot C/DVD such as W7 installer or W7-repair CD or Hiren's BootCD or others. I cant find (yet?) to be it bootable by GRUB2. (Til now I saw only linux-based isos bootable by it). But, I know, YUMI uses win version of GRUB(1), so teoreticaly, if progress go forward, GRUB2 should be able the same, maybe more? :shock:

Now I found, YUMI dont need to be in MBR, it installs only to PBR and only PBR it updates. So, now I have GRUB2 in MBR and dont need to have any partitions marked "active"! That's progress!  :-)

---

### Post by oldfred on 2012-01-25
I use grub2 to boot my Windows 7 repair USB.

I could not find a way to directly install the repairCD to the flash drive from Ubuntu, so I made the CD and used it to create & copy to a flash drive. It was FAT32 and booted with a Windows boot loader and some sort of custom FAT32 PBR as usually newer Windows want NTFS. But repair install was tiny and I had lots of room on flash so I wanted to install other repair ISO and boot with grub. I then just installed grub and manually created a grub.cfg with a chainload to the PBR that Windows/grub was in. I frankly was suprised it worked.:)  The issue with Windows is that it has a /Boot and grub is in a /boot which then confuses Windows. I just made sure the grub was really in /Boot next to the BCD not a separate folder.

---

### Post by iX9 on 2012-01-25
Nice! Can You post some of your grub.cfg menuentry? Everything done by GRUB2 sounds good!

---

### Post by oldfred on 2012-01-25
The boot drive for grub is always hd0 which can lead to confusion if chainloading to another drive.

I guess I cannot upload grub.cfg, so I will just post it. It is now older for the other ISOs as I have newer ISO on another flash drive. 

```
menuentry "Microsoft Windows Recovery" {
      set root=(hd0,1)
      chainloader --force +1
}

menuentry " " {
set root= 
}

menuentry "ubuntu-9.10-desktop-i386.iso" {
    set isofile="/ISO/ubuntu-9.10-desktop-i386.iso"
    insmod ext2
    loopback loop (hd0,2)$isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile quiet splash noprompt --
    initrd (loop)/casper/initrd.gz
}

# iso_filename=$isofile boot=live load_ramdisk=1 prompt_ramdisk=0 noeject noprompt 
menuentry "Parted Magic 6.1" {
    set isofile="/boot/iso/pmagic-6.1.iso"
    loopback loop $isofile 
    linux (loop)/pmagic/bzImage iso_filename=$isofile edd=off noapic load_ramdisk=1 prompt_ramdisk=0 rw loglevel=0 max_loop=256
    initrd (loop)/pmagic/initramfs
}

menuentry " " {
set root= 
}

menuentry "systemrescuecd-x86-1.6.3.iso" {
 set isofile="/ISO/systemrescuecd-x86-1.6.3.iso"
 loopback loop (hd0,2)$isofile  
 linux (loop)/isolinux/rescuecd isoloop=$isofile  
 initrd (loop)/isolinux/initram.igz
}

# boot=live config  noswap noprompt  toram=filesystem.squashfs ip=frommedia  nosplash
menuentry "Gparted Live ISO" {
set isofile="/boot/iso/gparted-live-0.8.0-5.iso"
loopback loop $isofile
linux (loop)/live/vmlinuz boot=live config union=aufs noswap noprompt ip=frommedia findiso=$isofile toram=filesystem.squashfs nomodeset
initrd (loop)/live/initrd.img
}

menuentry "gparted-live-0.8.0-5.iso" {
  insmod loopback
  insmod iso9660
  set gfxpayload=800x600x16, 800x600
  set isofile="/ISO/gparted-live-0.8.0-5.iso"
  loopback loop (hd0,2)$isofile 
  linux (loop)/live/vmlinuz boot=live union=aufs noswap noprompt ip=frommedia toram=filesystem.squashfs findiso=$isofile
  initrd (loop)/live/initrd.img
}

menuentry " " {
set root= 
}

menuentry "Reboot" {
    reboot
}

menuentry "Halt" {
    halt
}

menuentry "Memory test (memtest86+)" {
 linux /boot/memtest86+.bin
}

Boot most up2date Lucid kernel on sdc7
menuentry "Lucid on sdc7" {
    set root=(hd2,7)
        linux /vmlinuz root=/dev/sdc7 ro quiet splash
        initrd /initrd.img
}
```

One of my other grub.cfgs I added some header info:

set default=0 
set menu_color_normal=cyan/blue
set menu_color_highlight=white/blue
set gfxpayload=800x600

---

