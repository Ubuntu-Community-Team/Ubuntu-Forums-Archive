---
title: "Grub bootloading and two distros"
date: 2010-07-16
forum: General Help
---

### Post by Axolotl9250 on 2010-07-16
[LEFT]Hi I want to make a laptop have three distro's Arch Fedora and Ubuntu on dual boot, or in this case you could say tri-boot. Anyway I want to do this using Grub Legacy that came with Arch Linux. But with Ubuntu installing with Grub 2 and the whole automated process I'm not really sure how I go about installing Ubuntu without wiping grub legacy and my current setup.  Does anybody else have Ubuntu with Grub legacy or has it booting with other distros and Grub legacy or could tell me how it's done?

Cheers.
[/LEFT]

---

### Post by WorMzy on 2010-07-16
Pay attention while you're installing Ubuntu; towards the end of the installation process you should have the option of installing the boot loader or not. The option is hidden and ticked by default, so you need to look for it and untick it. After you've finished the installation you'll need to boot into your Arch or Fedora installation and update your menu.lst to get the ubuntu installation to have a boot option.

---

### Post by oldfred on 2010-07-16
Look for the advanced button to choose where to install grub. One choice should be to not install.

[http://members.iinet.net/~herman546/p28/032_install-now.png]("http://members.iinet.net/%7Eherman546/p28/032_install-now.png")

An entry like this will use the linked files  in root to boot the most current kernel, so you do not have to edit on every update.

title    Most Current Ubuntu on sdc5
root    (hd2,4)
linux   /vmlinuz root=/dev/sdc5 ro quiet splash
initrd  /initrd.img

[COLOR=Red]Correction[/COLOR] see post #15 linux should be kernel.

---

### Post by Axolotl9250 on 2010-07-16
Ok thanks, which files in Ubuntu to I need to point to for the "kernel" and "initrd" fields in menu.lst?

---

### Post by WorMzy on 2010-07-16
You could try oldfred's suggestion of a linux line, rather than a kernel and initrd line; I've never used that myself though, and I don't know if it works without an initrd file.

Or you can use kernel and initrd lines like these:

```
kernel       /vmlinuz root=UUID=<UUID HERE> ro quiet splash
initrd       /initrd.img
```

---

### Post by oldfred on 2010-07-16
If you look in your Ubuntu root you will see the linked files are automatically created. You do not have to do anything to maintain. Part of a new Ubuntu kernel backs up the link and creates a new link.

---

### Post by Axolotl9250 on 2010-07-16
I tried it:

```
# (2) Ubuntu 10.04 Lucid
title Ubuntu 10.04 Lucid
root   (hd0,2)
linux /vmlinuz root=/dev/sda3 ro quiet splash
initrd /initrd.img
```


 and I can see the two links but when I try to start grub I get an error saying a kernel needs loading before an initrd file.

---

### Post by oldfred on 2010-07-16
Are you booting from a drive that is not sda? I found on my system if I boot sdc, I have to change the hd0 to hd1 etc as it automatically makes the boot drive hd0 (sdc in my case). So you may have to change the root to hd1,2 or hd2,2 to get it to work. The /dev/sda3 should be correct even if the root refers to hd1.

---

### Post by Axolotl9250 on 2010-07-16
I've just double checked, my drive is definately sda

---

### Post by oldfred on 2010-07-16
Just to see if we can see anything unusual.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.

---

### Post by Axolotl9250 on 2010-07-17
Here it is:
```
           Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  [H[2J Arch Linux () ()
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    58,589,054    58,588,992  83 Linux
/dev/sda2          58,589,116   285,149,183   226,560,068   5 Extended
/dev/sda5          58,589,118   117,178,109    58,588,992  83 Linux
/dev/sda6         117,178,173   214,837,244    97,659,072  83 Linux
/dev/sda7         214,837,248   226,555,903    11,718,656  82 Linux swap / Solaris
/dev/sda8         226,557,952   285,149,183    58,591,232  83 Linux
/dev/sda3         285,149,184   324,210,687    39,061,504  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        ae58baec-0509-4989-b123-521ce8868612   ext4       Archroot                      
/dev/sda2: PTTYPE="dos" PART_ENTRY_SCHEME="dos" PART_ENTRY_TYPE="0x5" PART_ENTRY_NUMBER="2" 
/dev/sda3        f9809aa5-0950-46e5-bf43-3467ac47fead   ext4                                     
/dev/sda5        b398fbee-5d75-43cd-97da-7e20851ec9b3   ext4       Archvar                       
/dev/sda6        34a7eb6b-43f8-469b-9323-75cf746b28ed   ext4       Archome                       
/dev/sda7        4aa9dfcc-53f0-4034-8314-86c19024b162   swap                                     
/dev/sda8        843d95a2-22f7-446f-9bdf-bdfbc61a5b91   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,commit=0)
/dev/sda5        /var                     ext4       (rw,commit=0)
/dev/sda6        /home                    ext4       (rw,commit=0)


=========================== sda1/boot/grub/menu.lst: ===========================

# Config file for GRUB - The GNU GRand Unified Bootloader
# /boot/grub/menu.lst

# DEVICE NAME CONVERSIONS 
#
#  Linux           Grub
# -------------------------
#  /dev/fd0        (fd0)
#  /dev/sda        (hd0)
#  /dev/sdb2       (hd1,1)
#  /dev/sda3       (hd0,2)
#

#  FRAMEBUFFER RESOLUTION SETTINGS
#     +-------------------------------------------------+
#          | 640x480    800x600    1024x768   1280x1024
#      ----+--------------------------------------------
#      256 | 0x301=769  0x303=771  0x305=773   0x307=775
#      32K | 0x310=784  0x313=787  0x316=790   0x319=793
#      64K | 0x311=785  0x314=788  0x317=791   0x31A=794
#      16M | 0x312=786  0x315=789  0x318=792   0x31B=795
#     +-------------------------------------------------+
#  for more details and different resolutions see
#  http://wiki.archlinux.org/index.php/GRUB#Framebuffer_Resolution 

# general configuration:
timeout   5
default   0
color light-blue/black light-cyan/blue

# boot sections follow
# each is implicitly numbered from 0 in the order of appearance below
#
# TIP: If you want a 1024x768 framebuffer, add "vga=773" to your kernel line.
#
#-*

# (0) Arch Linux
title  Arch Linux
root   (hd0,0)
kernel /boot/vmlinuz26 root=/dev/sda1 ro
initrd /boot/kernel26.img

# (1) Arch Linux
title  Arch Linux Fallback
root   (hd0,0)
kernel /boot/vmlinuz26 root=/dev/sda1 ro
initrd /boot/kernel26-fallback.img

# (2) Ubuntu 10.04 Lucid
title Ubuntu 10.04 Lucid
root   (hd0,2)
linux    /vmlinuz root=/dev/sda3 ro quiet splash
initrd    /initrd.img

# (3) Windows
#title Windows
#rootnoverify (hd0,0)
#makeactive
#chainloader +1

=============================== sda1/etc/fstab: ===============================

# 
# /etc/fstab: static file system information
#
# <file system>        <dir>         <type>    <options>          <dump> <pass>
devpts                 /dev/pts      devpts    defaults            0      0
shm                    /dev/shm      tmpfs     nodev,nosuid        0      0

#/dev/cdrom             /media/cd   auto    ro,user,noauto,unhide   0      0
#/dev/dvd               /media/dvd  auto    ro,user,noauto,unhide   0      0
#/dev/fd0               /media/fl   auto    user,noauto             0      0

/dev/sda1 / ext4 defaults 0 1
/dev/sda5 /var ext4 defaults 0 1
/dev/sda6 /home ext4 defaults 0 1
/dev/sda7 swap swap defaults 0 0

=================== sda1: Location of files loaded by Grub: ===================


   2.5GB: boot/grub/menu.lst
    .1GB: boot/grub/stage2
    .1GB: boot/kernel26-fallback.img
    .1GB: boot/kernel26.img
  23.8GB: boot/vmlinuz26

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=f9809aa5-0950-46e5-bf43-3467ac47fead /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda8 during installation
UUID=843d95a2-22f7-446f-9bdf-bdfbc61a5b91 /home           ext4    defaults        0       2
# swap was on /dev/sda7 during installation
UUID=4aa9dfcc-53f0-4034-8314-86c19024b162 none            swap    sw              0       0

=================== sda3: Location of files loaded by Grub: ===================


 155.0GB: boot/initrd.img-2.6.32-21-generic
 154.8GB: boot/vmlinuz-2.6.32-21-generic
 155.0GB: initrd.img
 154.8GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  6f 6e 5f 72 65 63 6f 76  65 72 79 5f 74 69 6d 65  |on_recovery_time|
00000010  64 6f 75 74 00 62 65 69  73 63 73 69 5f 70 72 6f  |dout.beiscsi_pro|
00000020  63 65 73 73 5f 6d 63 63  00 69 6f 77 72 69 74 65  |cess_mcc.iowrite|
00000030  33 32 00 5f 5f 74 68 69  73 5f 6d 6f 64 75 6c 65  |32.__this_module|
00000040  00 62 6c 6b 5f 71 75 65  75 65 5f 6d 61 78 5f 73  |.blk_queue_max_s|
00000050  65 67 6d 65 6e 74 5f 73  69 7a 65 00 62 65 69 73  |egment_size.beis|
00000060  63 73 69 5f 65 70 5f 64  69 73 63 6f 6e 6e 65 63  |csi_ep_disconnec|
00000070  74 00 73 6e 70 72 69 6e  74 66 00 70 63 69 5f 64  |t.snprintf.pci_d|
00000080  65 76 5f 70 75 74 00 62  6c 6b 5f 69 6f 70 6f 6c  |ev_put.blk_iopol|
00000090  6c 5f 65 6e 61 62 6c 65  00 62 65 69 73 63 73 69  |l_enable.beiscsi|
000000a0  5f 70 72 6f 63 65 73 73  5f 61 6c 6c 5f 63 71 73  |_process_all_cqs|
000000b0  00 69 73 63 73 69 5f 74  61 72 67 65 74 5f 61 6c  |.iscsi_target_al|
000000c0  6c 6f 63 00 5f 5f 69 73  63 73 69 5f 63 6f 6d 70  |loc.__iscsi_comp|
000000d0  6c 65 74 65 5f 70 64 75  00 69 73 63 73 69 5f 63  |lete_pdu.iscsi_c|
000000e0  6f 6e 6e 5f 62 69 6e 64  00 69 73 63 73 69 5f 68  |onn_bind.iscsi_h|
000000f0  6f 73 74 5f 67 65 74 5f  70 61 72 61 6d 00 66 69  |ost_get_param.fi|
00000100  6e 69 73 68 5f 77 61 69  74 00 62 65 69 73 63 73  |nish_wait.beiscs|
00000110  69 5f 67 65 74 5f 68 6f  73 74 5f 70 61 72 61 6d  |i_get_host_param|
00000120  00 6d 67 6d 74 5f 67 65  74 5f 66 77 5f 63 6f 6e  |.mgmt_get_fw_con|
00000130  66 69 67 00 69 73 63 73  69 5f 73 65 73 73 69 6f  |fig.iscsi_sessio|
00000140  6e 5f 73 65 74 75 70 00  5f 5f 70 63 69 5f 72 65  |n_setup.__pci_re|
00000150  67 69 73 74 65 72 5f 64  72 69 76 65 72 00 69 6f  |gister_driver.io|
00000160  75 6e 6d 61 70 00 63 6c  65 61 6e 75 70 5f 6d 6f  |unmap.cleanup_mo|
00000170  64 75 6c 65 00 64 6d 61  5f 73 75 70 70 6f 72 74  |dule.dma_support|
00000180  65 64 00 70 61 72 61 6d  5f 73 65 74 5f 75 69 6e  |ed.param_set_uin|
00000190  74 00 70 72 65 70 61 72  65 5f 74 6f 5f 77 61 69  |t.prepare_to_wai|
000001a0  74 00 62 65 5f 63 6d 64  5f 68 64 72 5f 70 72 65  |t.be_cmd_hdr_pre|
000001b0  70 61 72 65 00 6d 65 6d  63 70 79 00 73 63 00 fe  |pare.memcpy.sc..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 40 ff 7d 03 00 fe  |..........@.}...|
000001d0  ff ff 05 fe ff ff 42 ff  7d 03 ff 28 d2 05 00 00  |......B.}..(....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

  No volume groups found
mdadm: No arrays found in config file or automatically
```

---

### Post by WorMzy on 2010-07-17
Looks all right to me. You could try replacing linux with kernel, see if that works.

The only thing that confuses me is why you put Lucid outside of the extended partition, in a primary partition. It makes it a little more confusing because physically, it's the sixth partition, but logically, it's the third. So if the kernel line doesn't make any difference, try using 'root (hd0,5)'

---

### Post by Axolotl9250 on 2010-07-17
I've been under the impression up till now that you had root and boot partitions as primary partitions and then any /home or /var and such as extended partitions.

---

### Post by WorMzy on 2010-07-17
You need to have one non-extended primary partition to contain the MBR, but that's it as far as "you must have"s go. The bios needs to be able to read stage1 grub from the MBR, and from there grub should be able to read stage 1.5 (et al) from any partition, primary or otherwise.

Of course I'm not 100% sure about that. It may differ from HDD to HDD.

---

### Post by oldfred on 2010-07-17
I was editing a grub2 version and left the linux in when it should be kernel. Try this:

title Ubuntu 10.04 Lucid
root   (hd0,2)
[COLOR=Red]kernel [/COLOR]   /vmlinuz root=/dev/sda3 ro quiet splash
initrd    /initrd.img

---

### Post by Axolotl9250 on 2010-07-17
It's working now I've changed it to say kernel. Thank you very much for your help! :-)

---

