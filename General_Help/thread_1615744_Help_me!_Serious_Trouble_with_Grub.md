---
title: "Help me! Serious Trouble with Grub"
date: 2010-11-07
forum: General Help
---

### Post by Super Nade on 2010-11-07
Hi everybody,

I am in a serious state of panic right now and hope somebody can help me out. :(:(:(

Last night, I shut down my laptop after surfing the net. This morning, I booted up and I'm now confronted with a grub screen WHISKEY-TANGO-FOXTROT!!!!!! I am locked out of my system! I have very important documents on my laptop that took many hours to compose. I do back up my data, but this happened between my usual backup cycle!!!

I am in panic mode because:
a) The GRUB prompt says Grub 1.xxx something instead of GRUB 2!!!! Something is seriously amiss!
b)Upon typing "root" at the GRUB prompt, I get (hd0,msdos) another W-T-F??? This laptop is 100% Ubuntu!
c)I don't have a 10.10 Live CD, just an 8.04 live CD. I cannot access the HDD because it won't read ext4. :( :(

Laptop and Specs:
----------------
Dell Inspiron 600m
Ubuntu/Kubuntu 10.10 using the entire HDD.

Somebody please help me!

Important Edit####
--------------------
I think this mess was precipitated after the latest update I made (new kernel install via apt).

---

### Post by CyberWasteland on 2010-11-07
I suggest you re-install GRUB. You should be able to to install grub from your live CD.
It'll overwrite the old grub which probably broke somehow. (Make sure you install the latest version)

---

### Post by karthick87 on 2010-11-07
Download  a ubuntu copy from here and reinstall your grub.That may fix your problem

[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

---

### Post by Super Nade on 2010-11-07
How do I do that? Do I need the 10.10 live cd or can I use this 8.04 live CD (typing on it right now).

BTW, I tried this--->[http://john-willis.com/2010/03/ubuntu-stuck-in-grub-command-on-boot/](http://john-willis.com/2010/03/ubuntu-stuck-in-grub-command-on-boot/)

and the results are as follows:

```
     Boot Info Script 0.55    dated February 15th, 2010

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in
    partition #1 for (,msdos1)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:
    Mounting failed:
mount: unknown filesystem type 'ext4'

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0006b35e

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   309,598,207   309,596,160  83 Linux
/dev/sda2         309,600,254   312,580,095     2,979,842   5 Extended
/dev/sda5         309,600,256   312,580,095     2,979,840  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs
/dev/sda1        60947d82-01eb-46dc-984b-f280f8cfea9b   ext4
/dev/sda5        12aa2e07-d183-4529-a3c9-79e86ba6e3e6   swap

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options


=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  69 6e 6b 5f 78 66 72 6d  5f 73 6f 63 6b 65 74 00  |ink_xfrm_socket.|
00000010  6e 65 74 6c 69 6e 6b 5f  73 65 6c 69 6e 75 78 5f  |netlink_selinux_|
00000020  73 6f 63 6b 65 74 00 6e  65 74 6c 69 6e 6b 5f 61  |socket.netlink_a|
00000030  75 64 69 74 5f 73 6f 63  6b 65 74 00 6e 65 74 6c  |udit_socket.netl|
00000040  69 6e 6b 5f 69 70 36 66  77 5f 73 6f 63 6b 65 74  |ink_ip6fw_socket|
00000050  00 6e 65 74 6c 69 6e 6b  5f 64 6e 72 74 5f 73 6f  |.netlink_dnrt_so|
00000060  63 6b 65 74 00 64 62 75  73 00 6e 73 63 64 00 61  |cket.dbus.nscd.a|
00000070  73 73 6f 63 69 61 74 69  6f 6e 00 6e 65 74 6c 69  |ssociation.netli|
Disk identifier: 0x0006b35e

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   309,598,207   309,596,160  83 Linux
/dev/sda2         309,600,254   312,580,095     2,979,842   5 Extended
/dev/sda5         309,600,256   312,580,095     2,979,840  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs
/dev/sda1        60947d82-01eb-46dc-984b-f280f8cfea9b   ext4
/dev/sda5        12aa2e07-d183-4529-a3c9-79e86ba6e3e6   swap

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options


=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  69 6e 6b 5f 78 66 72 6d  5f 73 6f 63 6b 65 74 00  |ink_xfrm_socket.|
00000010  6e 65 74 6c 69 6e 6b 5f  73 65 6c 69 6e 75 78 5f  |netlink_selinux_|
00000020  73 6f 63 6b 65 74 00 6e  65 74 6c 69 6e 6b 5f 61  |socket.netlink_a|
00000030  75 64 69 74 5f 73 6f 63  6b 65 74 00 6e 65 74 6c  |udit_socket.netl|
00000040  69 6e 6b 5f 69 70 36 66  77 5f 73 6f 63 6b 65 74  |ink_ip6fw_socket|
00000050  00 6e 65 74 6c 69 6e 6b  5f 64 6e 72 74 5f 73 6f  |.netlink_dnrt_so|
00000060  63 6b 65 74 00 64 62 75  73 00 6e 73 63 64 00 61  |cket.dbus.nscd.a|
00000070  73 73 6f 63 69 61 74 69  6f 6e 00 6e 65 74 6c 69  |ssociation.netli|
00000020  73 6f 63 6b 65 74 00 6e  65 74 6c 69 6e 6b 5f 61  |socket.netlink_a|
00000030  75 64 69 74 5f 73 6f 63  6b 65 74 00 6e 65 74 6c  |udit_socket.netl|
00000040  69 6e 6b 5f 69 70 36 66  77 5f 73 6f 63 6b 65 74  |ink_ip6fw_socket|
00000050  00 6e 65 74 6c 69 6e 6b  5f 64 6e 72 74 5f 73 6f  |.netlink_dnrt_so|
00000060  63 6b 65 74 00 64 62 75  73 00 6e 73 63 64 00 61  |cket.dbus.nscd.a|
00000070  73 73 6f 63 69 61 74 69  6f 6e 00 6e 65 74 6c 69  |ssociation.netli|
00000080  6e 6b 5f 6b 6f 62 6a 65  63 74 5f 75 65 76 65 6e  |nk_kobject_ueven|
00000090  74 5f 73 6f 63 6b 65 74  00 61 70 70 6c 65 74 61  |t_socket.appleta|
000000a0  6c 6b 5f 73 6f 63 6b 65  74 00 70 61 63 6b 65 74  |lk_socket.packet|
000000b0  00 6b 65 79 00 63 6f 6e  74 65 78 74 00 64 63 63  |.key.context.dcc|
000000c0  70 5f 73 6f 63 6b 65 74  00 6d 65 6d 70 72 6f 74  |p_socket.memprot|
000000d0  65 63 74 00 64 62 5f 64  61 74 61 62 61 73 65 00  |ect.db_database.|
000000e0  64 62 5f 74 61 62 6c 65  00 64 62 5f 70 72 6f 63  |db_table.db_proc|
000000f0  65 64 75 72 65 00 64 62  5f 63 6f 6c 75 6d 6e 00  |edure.db_column.|
00000100  64 62 5f 74 75 70 6c 65  00 64 62 5f 62 6c 6f 62  |db_tuple.db_blob|
00000110  00 70 65 65 72 00 63 61  70 61 62 69 6c 69 74 79  |.peer.capability|
00000120  32 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |2...............|
00000130  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 fe  |................|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 78 2d 00 00 00  |...........x-...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 fe  |................|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 78 2d 00 00 00  |...........x-...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

---

### Post by dino99 on 2010-11-07
here is an example of how to chroot, boot on your 8.04 cd then follow:

[http://ubuntuforums.org/showthread.php?t=1263030&page=2](http://ubuntuforums.org/showthread.php?t=1263030&page=2)

then run: synaptic

and remove/purge then reinstall grub-pc

when done, exit and reboot, you'll be ok

---

### Post by TBerk on 2010-11-07
> **Super Nade said:**
> Hi everybody,

I am in a serious state of panic right now and hope somebody can help me out. :(:(:(

Last night, I shut down my laptop after surfing the net. This morning, I booted up and I'm now confronted with a grub screen WHISKEY-TANGO-FOXTROT!!!!!! I am locked out of my system! I have very important documents on my laptop that took many hours to compose. I do back up my data, but this happened between my usual backup cycle!!!

I am in panic mode because:
a) The GRUB prompt says Grub 1.xxx something instead of GRUB 2!!!! Something is seriously amiss!
b)Upon typing "root" at the GRUB prompt, I get (hd0,msdos) another W-T-F??? This laptop is 100% Ubuntu!
c)I don't have a 10.10 Live CD, just an 8.04 live CD. I cannot access the HDD because it won't read ext4. :( :(

Laptop and Specs:
----------------
Dell Inspiron 600m
Ubuntu/Kubuntu 10.10 using the entire HDD.

Somebody please help me!

Important Edit####
--------------------
I think this mess was precipitated after the latest update I made (new kernel install via apt).



OK, what happens when you boot from the (broken) HD install and once you login try to update not the GRUB 1.x version but the following?:

```

sudo update-grub2 
```

This should have the effect of scanning for kernels and OS versions and rebuilding the startup menu.

[http://www.google.com/search?client=ubuntu&channel=fs&q=sudo+update-grub2+&ie=utf-8&oe=utf-8](http://www.google.com/search?client=ubuntu&channel=fs&q=sudo+update-grub2+&ie=utf-8&oe=utf-8)

hth,
TBerk

---

### Post by Super Nade on 2010-11-07
DAmn...it gets stuck at:

```
ubuntu@ubuntu:~/Desktop$ sudo mkdir /mnt/rescue
ubuntu@ubuntu:~/Desktop$ sudo mount /dev/sda1 /mnt/rescue/
mount: [COLOR="Red"]unknown filesystem type 'ext4dev'[/COLOR]
ubuntu@ubuntu:~/Desktop$ 
```

---

### Post by Super Nade on 2010-11-07
> **TBerk said:**
> OK, what happens when you boot from the (broken) HD install and once you login try to update not the GRUB 1.x version but the following?:

```

sudo update-grub2 
```

This should have the effect of scanning for kernels and OS versions and rebuilding the startup menu.

[http://www.google.com/search?client=ubuntu&channel=fs&q=sudo+update-grub2+&ie=utf-8&oe=utf-8](http://www.google.com/search?client=ubuntu&channel=fs&q=sudo+update-grub2+&ie=utf-8&oe=utf-8)

hth,
TBerk

```
ubuntu@ubuntu:~/Desktop$ sudo update-grub
Searching for GRUB installation directory ... 
No GRUB directory found. To create a template run 'mkdir /boot/grub' first. To install grub, install it manually or try the 'grub-install' command. ### Warning, grub-install is used to change your MBR. ###

ubuntu@ubuntu:~/Desktop$ sudo update-grub2
sudo: update-grub2: command not found
ubuntu@ubuntu:~/Desktop$ 

```

Sorry guys, I am a total noob. :( :(

---

### Post by Super Nade on 2010-11-07
O.k boys, now we are talking!

Saved this to a file (called bash.sh)
```
#!/bin/bash
mount --bind /dev /media/disk/dev
mount --bind /proc /media/disk/proc
mount --bind /sys /media/disk/sys
mount --bind /dev/pts /media/disk/dev/pts
cp /etc/resolv.conf /media/disk/etc/resolv.conf
chroot /media/disk
```

[http://ubuntuforums.org/showthread.php?t=1156240](http://ubuntuforums.org/showthread.php?t=1156240)

Then, I made it executable with:
```
ubuntu@ubuntu:~/Desktop$ sudo chmod u+x bash.sh
```

Ran it and I am in STILL not in my HDD :( :(
```
ubuntu@ubuntu:~/Desktop$ sudo bash
root@ubuntu:~/Desktop# ls
bash.sh   boot_info_script055.sh  RESULTS.txt
bash.sh~  Examples                ubiquity-gtkui.desktop
root@ubuntu:~/Desktop# cd ..
root@ubuntu:~# ls
Desktop  Documents  Music  Pictures  Public  Templates  Videos
root@ubuntu:~# 

```

---

### Post by Super Nade on 2010-11-07
Problem solved! I used method#3 described here--->[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

For some reason you need a liveCD with a kernel that supports ext4 of you are screwed.

Problem is now solved!

---

