---
title: "Ubuntu after 1.5 year is slower than the beginning"
date: 2012-07-08
forum: General Help
---

### Post by esbrinartot on 2012-07-08
As I said lately Ubuntu is getting slower. At the beginning was so fast but as more you use it is getting slower. (Just like windows)

Y try to do some maintenance:
Delete old Kernel.
Clean Cache.
Clean unnecessary packets.
I also used bleach bit.
Control start-up applications and demons.

I would like to know the  reason. Can anyone help me? I also thought about the fragmentation and here are the fragmentation results of my system:

_**SYSTEM PARTITION**_
xubuntu@xubuntu:~$ sudo fsck.ext4 -vpf /dev/sda2

292258 inodes used (15.75%)
271 non-contiguous files (0.1%)
517 non-contiguous directories (0.2%)
# de nodos-i con bloques ind/dind/tind: 0/0/0
Extent depth histogram: 245522/114
4768499 blocks used (64.33%)
0 bad blocks
2 large files

203517 regular files
29254 directories
59 character device files
26 block device files
2 fifos
948 links
59355 symbolic links (46489 fast symbolic links)
36 sockets
--------
293197 files

**_HOME PARTITION_**
xubuntu@xubuntu:~$ sudo fsck.ext4 -vpf /dev/sda5

44636 inodes used (2.74%)
1654 non-contiguous files (3.7%)
34 non-contiguous directories (0.1%)
# de nodos-i con bloques ind/dind/tind: 0/0/0
Extent depth histogram: 43627/211/1
4692769 blocks used (71.99%)
0 bad blocks
2 large files

37335 regular files
6437 directories
0 character device files
0 block device files
0 fifos
0 links
855 symbolic links (787 fast symbolic links)
0 sockets
--------
44627 files

Is the fragmentation that I have a problem? "I think it's low". Anyway if it's a problem how I could solve it? I've heard it's not easy in Linux to defrag.

For further information I have a double core Pentium D 2.0 Ghz (1200 Mhz)
3 Gb RAM  DDR2 667
512Mb Nvidia video card

Well if anyone can help me to find out why now is slow I would say thanks :)

---

### Post by dino99 on 2012-07-08
Well your cpu also has "low" specs, and the latest kernels needs more capabilities, specially if you use opengl/compiz/unity. So its up to you to make the choices that are best for your hardware. Maybe you should drop compiz/unity and use gnome-fallback (gnome-classic); you should see your pc going faster again  :)

---

### Post by Laiquendi on 2012-07-08
I don't think it's the fragmentation problem either. Try monitoring CPU use, maybe some applications are doing that, or it may be hardware problem - have you ever in this 1,5 year time cleaned fans/grids in your computer? :P

---

### Post by kimda on 2012-07-08
Are you running the same Ubuntu version as 1.5 years ago? Fragmentation isn't a big problem like with Windows. Also you do not have to do this manually since it will automatically after a certain amount of days or boots. And what exactly is slower? Booting Ubuntu or starting programs? Have you measured boot time with bootchart?

---

### Post by esbrinartot on 2012-07-08
Dear all

I don't use Unity. I use Gnome classical and opengl. I don't like unity.

My computer is mainly slower when you boot the system. I should take a clock and measure but I think needs 40 seconds to boot. In the past was faster.

I've already check and disabled most the option that I don't need in the start-up menu.

When you want to open a widnows also is a little bit slow but this is because of the compiz effects. 

Kernel explanation sounds reasonable. Is there a minimum required specifications for each kernel? I would like to compare the specifications of the initial kernel of Ubunutu 11.04 and the latest which is 2.6.38.15.

CPU is slower. But I think it's good enough to run properly the last linux Distro. However I always coould instal XFCE or LXDE. With a live Xubuntu USB Stick the computer fly.... It's so fast

thks to everyone

---

### Post by Megaptera on 2012-07-08
> **esbrinartot said:**
> ... My computer is mainly slower when you boot the system. I should take a clock and measure but I think needs 40 seconds to boot....

How many times a day do you need to boot? 
40 seconds is pretty fast I think ! :D

---

### Post by esbrinartot on 2012-07-08
> **Megaptera said:**
> How many times a day do you need to boot? 
40 seconds is pretty fast I think ! :D

Hi The average is approximately once per day.

Anyway I have precise data:

From grub exit to gdm the computer last 54 seconds.

If I do the same with windows 7 only 37 seconds.

I know the comparation is not equivalent because after introducing your user password windows 7 needs more time than ubuntu. However you can clearly see that the time you need to boot ubuntu 64 bits is nearly the same as Windows 7 32bis.

In a lot of blogs people say that linux boot faster than windows... Well the answer is not with Ubuntu. However Comparisons are awful because both system should be both with the same proceses on the start-up. 

Of course that 54 seconds is not a disaster. I just complain that at the beginning was faster and actually nowadays the results that I obtained are equivalent to windows

---

### Post by GreatDanton on 2012-07-08
My question:
How much data you have for Ubuntu, and how much for Windows?

---

### Post by esbrinartot on 2012-07-08
> **GreatDanton said:**
> My question:
How much data you have for Ubuntu, and how much for Windows?

Windows have all the necessary software to work. Microsoft office, chrome, Firefox, explorer, photoshop and so on.

Windows is in a partition of approximate 50gb and I just have 10 gb free or even less.

Ubuntu also have all the partitions quite full. Just check at the beginning and you will see that both system and home are at the 70or 80% of its capacity. Both os mounts a common partition ntfs called data and I use it to exchange information.

In conclusion windows I have the software that allow me to do the same as I do in Ubuntu.

If you require I can give more precise information but later because I don't have the counter in front of me

---

### Post by Rexilion on 2012-07-08
Stuff that slows down boot are:

- programs that are being started
- kernel detecting devices

Programs are started using roughly two methods, these are used interchangebly since not every package has been ported to support upstart in Ubuntu.

- Old style SysVInit: [update-rc.d]("http://www.tin.org/bin/man.cgi?section=8&topic=update-rc.d")

- New style Upstart: the 'start' lines in the /etc/init/*.conf files

For example, I disable:

Old Style SysVinit:
- grub-common
- ondemand
- smartmontools
- winbind
- dns-clean
- pppd-dns
- rsync
- ipsec
- setkey

New Style Upstart:
- /etc/init/atd.conf \
- /etc/init/binfmt-support.conf \
- /etc/init/flush-early-job-log.conf \
- /etc/init/module-init-tools.conf \
- /etc/init/mounted-debugfs.conf \
- /etc/init/mounted-proc.conf \
- /etc/init/plymouth.conf \
- /etc/init/plymouth-log.conf \
- /etc/init/plymouth-splash.conf \
- /etc/init/plymouth-stop.conf \
- /etc/init/plymouth-upstart-bridge.conf \
- /etc/init/setvtrgb.conf \
- /etc/init/tty2.conf \
- /etc/init/tty3.conf \
- /etc/init/tty4.conf \
- /etc/init/tty5.conf \
- /etc/init/tty6.conf \
- /etc/init/udevmonitor.conf \
- /etc/init/ufw.conf \
- /etc/init/ureadahead.conf \
- /etc/init/ureadahead-other.conf

As for the kernel, compile it with only build in modules of stuff you use. This gives the kernel some speed, since it doesn't have to check every boot which module is required for each piece of hardware.

Also, firmware can slow things down quite a bit. I have a laptop which uses firmware for it's wireless. That means that the kernel has to wait before your disk is ready so it can read the firmware files. Compiling these individial files into your kernel could also give a huge boost.

Also note, when you mess with this make back-ups. Above settings will almost definitly wreck your box. For me, this works since it's a computer which starts directly into X(FCE) and has no NetworkManager or any of that stuff.

---

### Post by esbrinartot on 2012-07-08
> **Rexilion said:**
> Stuff that slows down boot are:

- programs that are being started
- kernel detecting devices

Programs are started using roughly two methods, these are used interchangebly since not every package has been ported to support upstart in Ubuntu.

- Old style SysVInit: [update-rc.d]("http://www.tin.org/bin/man.cgi?section=8&topic=update-rc.d")

- New style Upstart: the 'start' lines in the /etc/init/*.conf files

For example, I disable:

Old Style SysVinit:
- grub-common
- ondemand
- smartmontools
- winbind
- dns-clean
- pppd-dns
- rsync
- ipsec
- setkey

New Style Upstart:
- /etc/init/atd.conf \
- /etc/init/binfmt-support.conf \
- /etc/init/flush-early-job-log.conf \
- /etc/init/module-init-tools.conf \
- /etc/init/mounted-debugfs.conf \
- /etc/init/mounted-proc.conf \
- /etc/init/plymouth.conf \
- /etc/init/plymouth-log.conf \
- /etc/init/plymouth-splash.conf \
- /etc/init/plymouth-stop.conf \
- /etc/init/plymouth-upstart-bridge.conf \
- /etc/init/setvtrgb.conf \
- /etc/init/tty2.conf \
- /etc/init/tty3.conf \
- /etc/init/tty4.conf \
- /etc/init/tty5.conf \
- /etc/init/tty6.conf \
- /etc/init/udevmonitor.conf \
- /etc/init/ufw.conf \
- /etc/init/ureadahead.conf \
- /etc/init/ureadahead-other.conf

As for the kernel, compile it with only build in modules of stuff you use. This gives the kernel some speed, since it doesn't have to check every boot which module is required for each piece of hardware.

Also, firmware can slow things down quite a bit. I have a laptop which uses firmware for it's wireless. That means that the kernel has to wait before your disk is ready so it can read the firmware files. Compiling these individial files into your kernel could also give a huge boost.

Also note, when you mess with this make back-ups. Above settings will almost definitly wreck your box. For me, this works since it's a computer which starts directly into X(FCE) and has no NetworkManager or any of that stuff.

Thks for your good Answer. I've already reduced reduced the terminal numbers. I will try to find out the function of all the process that you describe and then if I don't need them I will proceed to disable.

My question is how to disable ?

Do I have to go inside the conf file and comment all the lines?
I've tried to chance all the extension of the Plymouth files. From conf to conf.disabled but the Plymouth is still there.

Thks to help me. One good think of Linux is that allow you to control de computer

---

### Post by Rexilion on 2012-08-25
Yes, you have to comment our the 'start' lines for upstart. Which is pretty nasty to my opinion too :P .

---

### Post by oldfred on 2012-08-25
I found just mounting my NTFS shared data partitions slows boot. And if the NTFS needs chkdsk or could use it, then it is even slower. 

On my new SSD it took 20 sec total time and when to 25 sec when  I added NTFS mount (and some other additions, so I cannot totall blame NTFS). From grub to working system is 10 sec, but BIOS & grub add 12 to 15 sec. And my SSD is an inexpensive (for SSDs that is) slower one.

---

### Post by Rexilion on 2012-08-25
> **oldfred said:**
> I found just mounting my NTFS shared data partitions slows boot. And if the NTFS needs chkdsk or could use it, then it is even slower. 

On my new SSD it took 20 sec total time and when to 25 sec when  I added NTFS mount (and some other additions, so I cannot totall blame NTFS). From grub to working system is 10 sec, but BIOS & grub add 12 to 15 sec. And my SSD is an inexpensive (for SSDs that is) slower one.


Why not use autofs for mounting then?

---

### Post by oldfred on 2012-08-25
I need the partition mounted as I link to folders & files and do not want that slowed down even if it does work with my link. My Firefox & Thunderbird profiles are in  the NTFS partition for sharing with my old XP which I now do not use. I use the profile.ini to create a share.

---

### Post by Rexilion on 2012-08-25
> **oldfred said:**
> I need the partition mounted as I link to folders & files and do not want that slowed down even if it does work with my link. My Firefox & Thunderbird profiles are in  the NTFS partition for sharing with my old XP which I now do not use. I use the profile.ini to create a share.

Then autofs is the program for you.

---

### Post by sgage on 2012-08-25
> **oldfred said:**
> I found just mounting my NTFS shared data partitions slows boot. And if the NTFS needs chkdsk or could use it, then it is even slower. 

On my new SSD it took 20 sec total time and when to 25 sec when  I added NTFS mount (and some other additions, so I cannot totall blame NTFS). From grub to working system is 10 sec, but BIOS & grub add 12 to 15 sec. And my SSD is an inexpensive (for SSDs that is) slower one.

Hmmm... I don't notice any such effect - when I comment out my NTFS partition in fstab, my boot time is exactly the same (24 seconds from grub to working desktop - I auto-logon) as with it uncommented and mounting my NTFS partition.

---

