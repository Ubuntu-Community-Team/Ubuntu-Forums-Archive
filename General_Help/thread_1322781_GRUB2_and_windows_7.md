---
title: "GRUB2 and windows 7"
date: 2009-11-11
forum: General Help
---

### Post by psycho5 on 2009-11-11
Hi, I installed Windows 7 32bit on a 320gb disk, and then ubuntu on a separate disk. 

Grub2 didn't have a default entry for windows 7, I had to make one. I try to boot to windows, it says bootmgr missing.

I tried using the windows dvd to go to command prompt and run bootrec /fixboot and /fixmbr. First the setup didn't recognize the freshly installed OS, secondly /fixboot didn't work, only /fixmbr worked.

Still, I can't get into windows, I get the same bootmgr missing error.

My windows is on /dev/sda1

My Ubuntu is on /dev/sdb2

I created the script under /etc/grub.d/ set root = (hd0,1) 

```

oj@oj-desktop:~$ cat /etc/grub.d/11_windows7 
#!/bin/sh -e
echo "Adding Windows 7">&2
cat <<EOF
menuentry "Windows 7" {
insmod ntfs
insmod chain
insmod drivemap
set root=(hd0,1)
drivemap -s (hd0) (hd1)
chainloader +1

}
EOF

```

Still I can't boot into windows, there is a bootmgr file in C:\Windows\Boot\PCAT folder I don't know why windows is unable to load. 

Anyone please suggest what I should do?

---

### Post by Giblet5 on 2009-11-11
Something else is wrong.

9.10 will add Windows 7 partitions without any help from you, assuming that it can find a Windows 7 partition, which it apparently doesn't on your system.

I have Win7 on four systems that have Karmic and all four work just fine after grub2 automatically found and added them.

Here are the 'Other' OS entries from the generated /boot/grub/grub.cfg for this box:
```
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda2)" {
	saved_entry=${chosen}
	save_env saved_entry
	insmod ntfs
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set 8a2e59bf2e59a4cb
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
	saved_entry=${chosen}
	save_env saved_entry
	insmod ntfs
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set e0d4a286d4a25e92
	chainloader +1
}
menuentry "CentOS release 5.3 (Final) (on /dev/sdc1)" {
	saved_entry=${chosen}
	save_env saved_entry
	insmod ext2
	set root=(hd2,1)
	search --no-floppy --fs-uuid --set c6257793-7912-491e-a623-0dc30ad23394
	linux /boot/vmlinuz-2.6.18-128.el5 root=/dev/sdc1
}
menuentry "Microsoft Windows XP Professional (on /dev/sdd1)" {
	saved_entry=${chosen}
	save_env saved_entry
	insmod ntfs
	set root=(hd3,1)
	search --no-floppy --fs-uuid --set 646cc6dc6cc6a85e
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###
```

---

### Post by psycho5 on 2009-11-11
I think so you're right about not being able to see Windows 7 partition.

Even in the windows dvd setup recovery, it could not locate my windows 7 partition.

But I just installed it the same day and rebooted a couple of times because I was installing drivers and everything was fine. 

What can I do? Should I reinstall win7 while ubuntu is on another disk?

---

### Post by Giblet5 on 2009-11-11
It's difficult to diagnose via a forum: there are many things that can go wrong, and only one way for them to go right...

I would look at BIOS setup for the disks. If you have the ability to choose between AHCI and IDE access methods, you should set that to "IDE". If it's already set to IDE, then I have no idea what went wrong.

I suspect that the shortest path is to reinstall Win7 and follow the usual procedure for re-writing the MBR with grub.

I would also remove any changes you made to the grub config, because grub2 knows all about Windows 7.

---

### Post by psycho5 on 2009-11-11
so how do i reinstall grub2 with the live cd?

---

### Post by Giblet5 on 2009-11-11
> **psycho5 said:**
> so how do i reinstall grub2 with the live cd?

Boot into "Try it" mode.

Bring up a terminal window and enter the following commands
```
sudo bash # DANGEROUS! ENTER COMMANDS EXACTLY!
mount /dev/sdb2 /mnt
mount -o bind /proc /mnt/proc
mount -o bind /dev /mnt/dev
chroot /mnt bash
update-grub
grub-install /dev/sda
exit
exit
```

All done.

---

### Post by psycho5 on 2009-11-11
Thanks, I'll try it after I reinstall Win7. Thankfully it was a near-fresh install won't take long to configure it.

---

### Post by extigyro on 2009-11-22
Look at this - [http://erickoo.wordpress.com/2009/06/14/how-to-add-vista-partition-to-grub-2-ubuntu-9-10-karmic-koala/](http://erickoo.wordpress.com/2009/06/14/how-to-add-vista-partition-to-grub-2-ubuntu-9-10-karmic-koala/)

I tried it yesterday and it worked perfectly for me.

---

### Post by nishant.singh28 on 2009-11-22
> **Giblet5 said:**
> Boot into "Try it" mode.

Bring up a terminal window and enter the following commands
```
sudo bash # DANGEROUS! ENTER COMMANDS EXACTLY!
mount /dev/sdb2 /mnt
mount -o bind /proc /mnt/proc
mount -o bind /dev /mnt/dev
chroot /mnt bash
update-grub
grub-install /dev/sda
exit
exit
```All done.

I am thinking of kicking Vista out of my dual boot laptop( with Karmic and Grub2 ). I want to install Win7 on the Vista drive. Will the above commands be sufficient for me to restore the Grub2 menu or is there anything else I need to do as I don't want to reinstall Karmic and I want to use Grub 2.
P.S.: I'll be installing Win7 from a DVD after formatting Vista drive so tell me if I need to do anything special.

---

### Post by krash1220 on 2009-12-10
I have an AMD Phenom II X4, I have two sata hard drives and a sata dvd drive. If I set my drives up in IDE mode in the bios Grub2 installs fine but if I have them set to AHCI mode grub will not install to the mbr. I'm not using my drives for any kind of raid but am confused as to whether running them in ide mode is slower with sata drives or not. Should I be using them in IDE mode? The only way I can use Grub2 is to install it to a USB flash drive or I have to use regular grub. Can someone help me? Oh and I guess I should tell you I have Windows 7 installed to sda1 and ubuntu installed to sdb1.

---

### Post by parthab on 2009-12-19
> **nishant.singh28 said:**
> I am thinking of kicking Vista out of my dual boot laptop( with Karmic and Grub2 ). I want to install Win7 on the Vista drive. Will the above commands be sufficient for me to restore the Grub2 menu or is there anything else I need to do as I don't want to reinstall Karmic and I want to use Grub 2.
P.S.: I'll be installing Win7 from a DVD after formatting Vista drive so tell me if I need to do anything special.
Short answer is yes. As usual, you do this at your own risk.

Partha

---

