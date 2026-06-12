---
title: "Non-EFI System, Want to boot FakeRAID with GPT"
date: 2010-06-19
forum: General Help
---

### Post by megamandos on 2010-06-19
Ok, so, let me explain what I am trying to do:

I have a nVidia FakeRaid setup with 4x 1TB drives. For simplified explanation i will refer to this drive as 'fra'.

fra has several partitions on it with a GPT style partition table:

fra1: ~500GB NTFS, Windows 7 x64, from a MBR style table drive.
fra2: ~260GB ext4, empty
fra3: ~8GB swap space (for my 8GB of DDR3-1600, figured >8GB was over-overkill)
fra4: ~3.2TB NTFS, some storage space (empty)

I also have on the system:

sde: MBR, 2TB drive, currently with ubuntu 10.04 x64 installed, and about 1.3TB of movies
sdf: MBR, 2TB drive, contains a bootable copy of the ~500GB windows installation for backup, and ~500GB of music.

So what I want to do, is use GRUB2 on sde to boot fra1.

The problem I am having is, first, GRUB2 recognizing fra, and second, I don't know if grub2 will recognize the GPT disk.

When I try running 'update-grub' right after boot i get the following readout:

```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sdf1
done
```

NOTE: no faikraid?

then i run gparted, and suddenly ubuntu can recognize fra, then i run 'update-grub' again, and i get:

```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sdf1
Found Windows 7 (loader) on /dev/mapper/nvidia_ceeaecaa1
/usr/sbin/grub-probe: error: cannot find a GRUB drive for /dev/mapper/nvidia_ceeaecaa1.  Check your device.map.
You have a memory leak (not released memory pool):
 [0x7e40f0]
done

```

I noticed the memory leak, and I think its a separate problem. What is of interested to me here is that NOW fra (/dev/mapper/nvidia_ceeaecaa) is recognized and scanned properly, but wtf is this "cannot find a GRUB drive for dev/mapper/nvidia_ceeaecaa1.  Check your device.map."?

So I did as it said, and i couldnt find a device map in /boot/grub

So i made one with the command 'grub-mkdevicemap'

then opened /boot/grub/device.map and this is what it looks like:

```
(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc
(hd3)	/dev/sdd
(hd4)	/dev/sde
(hd5)	/dev/sdf
(hd6)	/dev/mapper/nvidia_ceeaecaa
```

well, I noticed that "/dev/mapper/nvidia_ceeaecaa" doesnt actually exist until after i run gparted, then i realized that is probably why i get that funny error.

And now I am stuck.

How do I get GRUB2 to see 'fra' at boot time, and be able to boot the windows partition on it? I know Windows 7 is compatible with GPT, and the only reason windows 7 wont boot without a bootloader is because normal (non-EFI) BIOS wont recognize and read a GPT disk. So I figured that if I can get GRUB2 to read the GPT disk (fra) then GRUB2 can load the second stage boot code for windows just as easily as if it were on an MBR, since GRUB2 supports GPT.

Thanks a bunch in advance.

---

### Post by megamandos on 2010-06-19
bump...

I know this is an advanced topic, so I am expecting it to take a while for someone to come along who can help, I apologize for bumping.

---

### Post by megamandos on 2010-06-20
bumpy?

---

### Post by megamandos on 2010-06-20
Please help!

---

### Post by megamandos on 2010-06-20
bump again...

---

### Post by NCLI on 2010-06-20
First of all, you're asked not to bump your own threads in the support forums until at least 24h have passed from your last post. Many people use filters to find the posts with only none or one reply, doing this means that they won't see your thread, and most will think that a thread with this many replies is pretty much solved.

Now, it looks like you've setup a RAID0 device with nVidia fakeraid. This is very dangerous, as it means that if one HDD fails, you lose all of your data with it. It is also taking the long way around, because Linux has RAID-functionality built-into the kernel.

If I were you, I'd disable the fakeraid, delete the partitions you've used for it(After taking backups of the appropriate data of course), then come back here, and I'll assist you in setting up a RAID5 array with the built-in mdadm. 

Now, GRUB will not be able to boot from the array. This is because the array(And therefore the data Ubuntu needs to boot, if installed on the array) does not exist until Ubuntu has booted, found the array, and built it. You'll need to have a normal partition which the system can boot from, or get a hardware RAID-controller, which can be quite expensive. The partition shouldn't need to be larger than 20-30 GB.

EDIT: Ok, you're using windows on this as well. Well, it's still dangerous and the long way around, etc, etc, but all I can say is that you need to follow [this guide]("https://help.ubuntu.com/community/FakeRaidHowto").

---

### Post by megamandos on 2010-06-20
first of all, thanks a bunch for your response!

Also, i am greatly considering switching to RAID5, I have a masters in computer science, so I know a thing or two.

So I have kind of given up on the exact idea from before, what I am doing now is installing GRUB2 on a thumbdrive (4GB) and having that as "/boot" and installing the rest of linux on an ext4 partition on fra3 mounted as "/". I was surprised, this time the install worked, but now after reboot, I got into GRUB2 menu and saw a few options:

```
Ubuntu, with linux 2.6.32-21-generic
Ubuntu, with linux 2.6.32-21-generic (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)
Windows 7 (loader) (on /dev/mapper/nvidia_ceeaecaa1)
```

So I was like, oh neato! it worked!, then i selected Windows 7, and hit enter and:

```
error: invalid signature.

press any key to continue..._
```

And I was like, oh thats fine i guess, i will try to boot into linux!, so i pressed space and it displayed the same options from before and i selected "Ubuntu, with linux 2.6.32-21-generic" and then this happened:

blank screen with blinking cursor... (figured it was busy, so i waited)

and then:

```
Gave up waiting for root device. Common Problems:
 - Boot args (cat /proc/cmdline)
   - Check rootdelay = (did the system wait long enough?)
   - Check root= (did the system wait for the right device?)
 - Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/mapper/nvidia_ceeaecaa3 does not exist. Dropping to shell!


Busybox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) _ <blinking cursor>
```

now i am sitting here starting at this wondering what just happened... from what I see, I am guessing that the fakeraid wasnt detected upon boot. although, look that this:

```
(initramfs) ls
dev	lib64	bin	conf	init	sys	tmp
root	lib	scripts	etc	sbin	proc	var
(initramfs) cd /dev/mapper
(initramfs) ls
control		nvidia_ceeaecaa
(initramfs) _
```

so, it sees the fakeraid! and i was like, hells yeah! ...then i relized that none of the partitions were listed, ie nvidia_ceeaecaa1, then i thought, it did mention a missing module... oh snap, the GPT.mod! Since its a GPT partition table, it probably cant read it. but i dont know the commands to get mapper to do its thing.

So, now I am staring at this trying to think of how to get it to try and look at the drive. Since this doesnt have parted, idk what to do... I am thinking about booting into the live CD and the chrooting to the /dev/mapper/nvidia_nvidia_ceeaecaa3 and then doing "grub-install --modules=GPT /dev/sdf", sdf is my thumb drive in this case. but idk what will happen... and i dont wanna mess it up.

Any suggestions?

---

### Post by megamandos on 2010-06-20
ok from some googleing i discovered that apparently linux device mapper doesn't like the "_" in the device name of the dmraid. so... now i need to find a way to rename a nvidia dmraid device...

great...

---

### Post by megamandos on 2010-06-20
ok I was wrong, the case is: *[http://ubuntuforums.org/showthread.php?t=1369224](http://ubuntuforums.org/showthread.php?t=1369224) *

---

