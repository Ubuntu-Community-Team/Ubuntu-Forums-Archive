---
title: "How to enable Hibernation"
date: 2011-05-20
forum: General Help
---

### Post by erotavlas on 2011-05-20
Hi,

I have installed Ubuntu 11.04 with a swap space about half of my system RAM (3 GB). So the hibernate command doesn't work. With LiveCD and gparted I have resized the swap space to cover all the RAM (about 4 GB). Now the command hibernate from panel menu is not present. How can I enable it?

Thank you

PS I have tried sudo gconf-editor apps/gnome_power_management but I could find can_hibernation value.

---

### Post by An Sanct on 2011-05-20
To enable hibernation, you should have at lease 1.5 as much swap as ram (some say 2x as much).

Hibernation dumps all the memory into swap and shuts down the machine, so if swap is used before, there has to be more than ram.

I hope I'm making sense here :)

---

### Post by psusi on 2011-05-20
Make sure your swap space is actually mounted:

cat /proc/swaps

---

### Post by An Sanct on 2011-05-20
+1 that has to be done, yes...

```

free
```
should also provide swap info
also look at ```
/etc/fstab
```
there you should find something like:
```

...
UUID=59f2... *your guid here* ...5c39 none            **swap    sw**              0       0
...

```

And note, that the swap partition has to be in one piece, to be good enough for hibernation. I don't recall where I found that info, but it seems logical ...

---

### Post by erotavlas on 2011-05-20
> **psusi said:**
> Make sure your swap space is actually mounted:

cat /proc/swaps

The swap partition is not mounted 

```

cat /proc/swaps
Filename                Type        Size    Used    Priority

```

Now I have reactive the swap partition from Gparted but the hibernate function is not available.

---

### Post by erotavlas on 2011-05-20
> 
```

free
```should also provide swap info
also look at ```
/etc/fstab
```there you should find something like:
```

...
UUID=59f2... *your guid here* ...5c39 none            **swap    sw**              0       0
...

```And note, that the swap partition has to be in one piece, to be good enough for hibernation. I don't recall where I found that info, but it seems logical ...


The command ```
 sudo /etc/fstab 
``` does not work. > sudo: /etc/fstab: command not found


If I'm not wrong for a correct hibernation procedure is necessary to store the content of the RAM in the disk, the swap space is not necessary...so where is the mistake?

---

### Post by psusi on 2011-05-20
> **erotavlas said:**
> The command ```
 sudo /etc/fstab 
``` does not work. 

He said to look at the file /etc/fstab, not run the command sudo /etc/fstab.

> **erotavlas said:**
> If I'm not wrong for a correct hibernation procedure is necessary to store the content of the RAM in the disk, the swap space is not necessary...so where is the mistake?

The swap partition is the part of the disk where the ram is written to, so you need to get it mounted.

---

### Post by Slim Odds on 2011-05-20
> **erotavlas said:**
> The command ```
 sudo /etc/fstab 
``` does not work. 

If I'm not wrong for a correct hibernation procedure is necessary to store the content of the RAM in the disk, the swap space is not necessary...so where is the mistake?

```
sudo vi /etc/fstab
```/etc/fstab is a file not a command.

Hibernation uses the swap space as the disk space. Therefore, you need swap space (maybe not for swapping but at least for hibernation).

---

### Post by An Sanct on 2011-05-20
fstab is a file .... I apologize for not being clear about that before.

so the command ```

sudo gedit /etc/fstab

```should open a file like this (my copy looks like this, don't mind the '#' comments, they are part generated, part mine ...)
> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=f66f4cf1-1e93-4b57-9acc-66845f7810f2 /               ext4    errors=remount-ro 0       1

#swap after
**UUID=59f2578d-350e-482a-b998-c361fcfe5c39 none            swap    sw              0       0**
#warehouse
UUID=dc1356bf-6675-4a6f-b07a-eb4979b378e2  /media/warehouse  ext4  defaults,noatime  0  0


I have "bolded" the part, that is responsible that swap gets mounted at startup, you can find you UUID/GUID in gparted if you right click on swap and select 'information'.

---

### Post by mbeierl on 2011-05-20
The "/etc/fstab" is a configuration file, not a command.  Try:
```
cat /etc/fstab
```

Edit: An Sanct beat me to it.  Ignore me!

---

### Post by erotavlas on 2011-05-20
Ok, thank to all for the answers.
This is my fstab file
```

[B]# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc        proc  nodev,noexec,nosuid      0  0  
# / was on /dev/sda3 during installation
UUID=463157af-230a-4262-a09d-e0bbee7256ee  /            ext4  errors=remount-ro        0  1  
# swap was on /dev/sda4 during installation
UUID=11603ad6-96fd-481a-9473-90269506c43b  none         swap  sw                       0  0  
/dev/sda1                                  /media/sda1  ntfs  nls=iso8859-1,umask=000  0  0  
/dev/sda2                                  /media/sda2  ntfs  nls=iso8859-1,umask=000  0  0  [/B]

```

If I launch gparted then I can enable the swap by swap on but after a restart it return to off state.

---

### Post by psusi on 2011-05-20
And the UUID?  Is it correct?

---

### Post by QLee on 2011-05-20
> **erotavlas said:**
> ...
I have installed Ubuntu 11.04 with a swap space about half of my system RAM (3 GB). So the hibernate command doesn't work. With LiveCD and gparted I have resized the swap space to cover all the RAM (about 4 GB). Now the command hibernate from panel menu is not present. How can I enable it?
...

There is considerable misinformation in this thread, the swap partition does not have to be in "one piece" and it is sufficient to set swap=RAM for hibernation. (Hibernation uses some compression and will only store contents of RAM, thus it is actually possible to hibernate with somewhat less than RAM some times, that doesn't negate the recommendation of equal to RAM to ensure operation).

Your problem is with the initial ramdisk, that is what has the hook for resuming from hibernation. You changed your swap partition but you did not mention updating the initrd.img. After verifying the UUID in fstab, amend the /etc/initramfs-tools/conf.d/resume file to reflect the new swap and then run update-initramfs as root.

---

### Post by An Sanct on 2011-05-20
I apologize for any inconviences I have made ... I see, That people are saying:
> There is considerable misinformation in this thread, the swap partition  does not have to be in "one piece" and it is sufficient to set swap=RAM  for hibernation. (Hibernation uses some compression and will only store  contents of RAM, thus it is actually possible to hibernate with somewhat  less than RAM some times, that doesn't negate the recommendation of  equal to RAM to ensure operation).
I would like to say, I have 8Gb of ram and will not accept any OS to take as much to store information unless needed. 

Okay, I am being rude here,..... sorry ...........

well, this said ... I back off from this issue ...

edit: a quick "sorry" ... I apologize, QLee ... I apologize psusi...

---

### Post by azupan on 2011-05-22
Got similar problems. I had Ubuntu installed besides Windows 7, now it's also Mint, triple boot so to speak. When I upgraded from 10.10 to 11.4, Hibernate option vanished. I figured out, that partition devices were renamed during upgrade. Fixed that in /etc/fstab, but resume from hibernation still didn't work. System went into login mode instead. About half an hour ago, I did this:

$sudo apt-get install   hibernate
Hibernation now works- occasionally. I'm not sure whether it hibernates on Mint's swap space or something, I don't know. Anyway, try it out, maybe it'll work for you.

What are Canonical's plans for hibernation anyway? I heard some rumors that it intends to scrap it alltogether.

---

### Post by An Sanct on 2011-05-22
Hibernation is something great! they should not "scrap" it ...but they should not scrap gnome either (IMHO) ...

well, 0% and that is **zero** percent of the developers give a care about this forum, so choose other paths of contacting them....

---

### Post by azupan on 2011-05-22
> **An Sanct said:**
> Hibernation is something great! they should not "scrap" it ...but they should not scrap gnome either (IMHO) ...

well, 0% and that is **zero** percent of the developers give a care about this forum, so choose other paths of contacting them....I'm not aware of any other paths. I don't think developers determine priorities and strategy anyway.

As for me- I was a bit too enthusiastic about Natty, installed it a bit too early, and stumbled upon a bug, which effectively prevented me from doing my work. I had no other option but to install Mint alongside Ubuntu & Windows 7 Here's the whole story if you're interested: [http://ubuntuforums.org/showthread.php?t=1753566](http://ubuntuforums.org/showthread.php?t=1753566). Currently I'm using Mint, but I'll keep Ubuntu until the next release or two. Once I see where the whole thing is heading, I'll make up my mind. Generally, I like Ubuntu, I still think Unity is a good idea, but if Canonical decides to dumb down Ubuntu for the people's masses, I'll keep Mint, and use the newly emptied partition to try other distros or new versions.

---

### Post by erotavlas on 2011-05-23
> **QLee said:**
> There is considerable misinformation in this thread, the swap partition does not have to be in "one piece" and it is sufficient to set swap=RAM for hibernation. (Hibernation uses some compression and will only store contents of RAM, thus it is actually possible to hibernate with somewhat less than RAM some times, that doesn't negate the recommendation of equal to RAM to ensure operation).

Your problem is with the initial ramdisk, that is what has the hook for resuming from hibernation. You changed your swap partition but you did not mention updating the initrd.img. After verifying the UUID in fstab, amend the /etc/initramfs-tools/conf.d/resume file to reflect the new swap and then run update-initramfs as root.


Hi, 

I have followed the your suggestions... I have copied from fstab the UUID into the resume file and after I have update the initramfs. Now If I try with cat /proc/swaps I get 

```

Filename                Type        Size    Used    Priority

```
The option hibernate from main mane is not present.

---

### Post by psusi on 2011-05-23
> **QLee said:**
> 
Your problem is with the initial ramdisk, that is what has the hook for resuming from hibernation. You changed your swap partition but you did not mention updating the initrd.img. After verifying the UUID in fstab, amend the /etc/initramfs-tools/conf.d/resume file to reflect the new swap and then run update-initramfs as root.

No, the location of the swap partition is not built into the initramfs, it is passed on the kernel command line by grub.

You need to get the swap partition mounted correctly in /etc/fstab, make sure it shows up in /proc/swaps after either a reboot or running sudo swapon -a, and finally, run sudo update-grub.

---

### Post by An Sanct on 2011-05-23
> **azupan said:**
> I'm not aware of any other paths. I don't think developers determine priorities and strategy anyway.

As for me- I was a bit too enthusiastic about Natty, installed it a bit too early, and stumbled upon a bug, which effectively prevented me from doing my work. I had no other option but to install Mint alongside Ubuntu & Windows 7 Here's the whole story if you're interested: [http://ubuntuforums.org/showthread.php?t=1753566](http://ubuntuforums.org/showthread.php?t=1753566). Currently I'm using Mint, but I'll keep Ubuntu until the next release or two. Once I see where the whole thing is heading, I'll make up my mind. Generally, I like Ubuntu, I still think Unity is a good idea, but if Canonical decides to dumb down Ubuntu for the people's masses, I'll keep Mint, and use the newly emptied partition to try other distros or new versions.

Ubuntu went into a strange way .... Unity IMHO is not bad, but under-developed and mostly usable for netbooks and other portable appliances with mini screens.

I read (most) of the stuff you wrote in the link ... and would like to know where you work :)

Its just a dumb-*** question from my side, but really ... do people employ Linux users.... please tell :)

Ow .. and yes, Canonical developers (and I might get banned for this) are really working on a "Hello Kitty" OS, I don't like it ... and am not the only one ... they just do it...

azupan - a zoki? :)

stari moj, vse poti vodijo v Ljubljano...

---

### Post by azupan on 2011-05-23
> **An Sanct said:**
> Ubuntu went into a strange wayIt went the way every widespread OS has to go. Nothing new about that. That's what I've meant by "dumbing down for the people's masses".

One of the reasons I like Linux is that I can configure it whatever way I like. Development machine for myself, teenage version for my daughter, geriatric version for my 80+ father (Cairo with BIG icons, home folder on desktop), no problem. Canonical currently insists on teenage version, or so it seems.

> **An Sanct said:**
> I read (most) of the stuff you wrote in the link ... and would like to know where you work :)I've been working in finance for the last 15 years. On Windows.

> **An Sanct said:**
> Its just a dumb-*** question from my side, but really ... do people employ Linux users.... please tell :)I installed Ubuntu out of curiosity, and for the old time's sake. Namely, I started my career 25+ years ago on Unix and Unix-like systems. I wanted to find out how theese things look nowadays, and ended up using Linux almost full time at home. I started doing an afternoon PHP project. Linux is the most suitable environment for this.

The bosses of the company I work for also started playing with the idea of switching to Linux. Microsoft's support is becoming kinda shaky lately.

> **An Sanct said:**
>  Ow .. and yes, Canonical developers (and I might get banned for this) are really working on a "Hello Kitty" OS, I don't like it ... and am not the only one ... they just do it...As far as financial IT is concerned... Stuff must work, that's the only thing that's important. If it doesn't, somebody must be at hand immediately, with the right answers, because every minute of downtime costs $$$. If Canonical can do that better than Microsoft it wins the corporate IT. Otherwise it loses, as simple as that. Hello Kitty or no Hello Kitty.

---

### Post by erotavlas on 2011-05-24
> **psusi said:**
> No, the location of the swap partition is not built into the initramfs, it is passed on the kernel command line by grub.

You need to get the swap partition mounted correctly in /etc/fstab, make sure it shows up in /proc/swaps after either a reboot or running sudo swapon -a, and finally, run sudo update-grub.


Ok, I have done :).
The UUID was uncorrect (if I typed sudo swapon -a the terminal told me cannot find the device for UUID=11603ad6-96fd-481a-9473-90269506c43b), after I have found the correct UUID from gparted on swap property. Now with swapon -a and sudo update-initramfs -u the hibernate option appears again, but it doesn't work. The PC can't go in hibernation, it only goes to black screen and after to login screen.
Thank you very much at all.

---

### Post by linuxinstalledfromhdd on 2011-05-24
Good job

---

### Post by azupan on 2011-05-28
Very helpful, thanxx everyone!

Following your advices, I've managed to fix hibernation issues in my Mint **and** Ubuntu installations. All that remains is Windows 7 hibernation, but that can wait. I'll fix it, when and if I'm ever going to use it a bit more than I do. I haven't booted it for weeks now.

Some additional details, which could be helpful.

It all started when 10.10 to 11.4 upgrade renamed /dev/mapper/isw_dehfcahgdd_Volume0*#* to 
/dev/mapper/isw_dehfcahgdd_Volume0p#. I fixed that. After a while, I installed Mint 10, and hibernation kinda got the will of its own again. After much frustration and experimentation I found out, that /dev/dm-# are not assigned to the same partitions every time, numbers were always different. Consequently, the system attempted to restore from the wrong partition. Worse still, Ubuntu and Mint were trashing each other's session stored in swap partition. Replacing /dev/ with UUID= in fstab, and fixing the /etc/initramfs-tools/conf.d/resume solved the problem. While doing this, I've stumbled upon the following bug:

[https://bugs.launchpad.net/ubuntu/+source/cryptsetup/+bug/497110](https://bugs.launchpad.net/ubuntu/+source/cryptsetup/+bug/497110)

In my case, the solution was to uninstall uswsusp package. It caused problems during restore anyway, so I just threw it out. If you can't live without uswsusp, however, you must fix the /etc/uswsusp.conf file. The "resume device =" entry must be in the exact same format as /etc/initramfs-tools/conf.d/resume. Namely, update-initramfs considers /dev/disk/by-uuid/6d62893d-25bd-4a00-b91f-64d0f60839d7 and UUID="6d62893d-25bd-4a00-b91f-64d0f60839d7" two different devices.

While experimenting, I also uninstalled hibernate package. I don't know whether it causes any problems and I don't intend to find out. In any case, it's not necessary.

---

### Post by Savio2010 on 2011-06-23
Hi I too have the same problem hibernation does not work in natty'

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   314,574,847   314,572,800  83 Linux
/dev/sda2         314,574,848   943,720,447   629,145,600  83 Linux
/dev/sda3         943,720,448 1,572,866,047   629,145,600  83 Linux
/dev/sda4       1,572,868,094 1,953,523,711   380,655,618   5 Extended
/dev/sda5       1,572,868,096 1,951,424,511   378,556,416  83 Linux
/dev/sda6       1,951,426,560 1,953,523,711     2,097,152  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/mapper/cryptswap1 3619deff-c2ff-4fca-859a-a2443c1fb915   swap       
/dev/sda1        6d1f4a1b-74d2-413d-96b9-e594996d7402   ext4       System
/dev/sda2        ca8ee211-656f-4a31-b6d2-e1ea6271b883   ext3       DataDrive1
/dev/sda3        9683b8e6-6767-4aae-bb5d-ab792b1f2d28   ext3       DataDrive2
/dev/sda5        d294d160-207b-47ff-a463-e026760ad1bc   ext3       DataRecovery

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
cryptswap1

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sda1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 6d1f4a1b-74d2-413d-96b9-e594996d7402
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 6d1f4a1b-74d2-413d-96b9-e594996d7402
set locale_dir=($root)/boot/grub/locale
set lang=en_IN
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 6d1f4a1b-74d2-413d-96b9-e594996d7402
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=6d1f4a1b-74d2-413d-96b9-e594996d7402 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 6d1f4a1b-74d2-413d-96b9-e594996d7402
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=6d1f4a1b-74d2-413d-96b9-e594996d7402 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 6d1f4a1b-74d2-413d-96b9-e594996d7402
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 6d1f4a1b-74d2-413d-96b9-e594996d7402
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
proc            /proc           proc    nodev,noexec,nosuid 0       0
UUID=6d1f4a1b-74d2-413d-96b9-e594996d7402 /               ext4    errors=remount-ro 0       1
/dev/mapper/cryptswap1 none swap sw 0 0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  16.135009766 = 17.324834816   boot/grub/core.img                             1
  16.135017395 = 17.324843008   boot/grub/grub.cfg                             1
   4.166946411 = 4.474224640    boot/initrd.img-2.6.38-8-generic               3
  16.133281708 = 17.322979328   boot/vmlinuz-2.6.38-8-generic                  1
   4.166946411 = 4.474224640    initrd.img                                     3
  16.133281708 = 17.322979328   vmlinuz                                        1

=============================== StdErr Messages: ===============================

unlzma: Decoder error

```Some other terminal outputs:

```
**cat /proc/swaps**
Filename                Type        Size    Used    Priority
/dev/dm-0                               partition    1048572    0    -1

**free**
             total       used       free     shared    buffers     cached
Mem:       1534584    1367684     166900          0      62320     853632
-/+ buffers/cache:     451732    1082852
Swap:      1048572          0    1048572

**cat /etc/fstab**
proc            /proc           proc    nodev,noexec,nosuid 0       0
UUID=6d1f4a1b-74d2-413d-96b9-e594996d7402 /               ext4    errors=remount-ro 0       1
/dev/mapper/cryptswap1 none swap sw 0 0


```I think my swap works, hibernation doesn't work. I don't resume from the same point I hibernated it starts all over again.:(

Help!!

---

### Post by psusi on 2011-06-23
I don't know if cryptswap works with hibernation...

---

### Post by wilsonB on 2012-03-10
I have the same problem with simular history.
Using SSD, 2GB Ram in Asus 1015pem Netbook.
Resinstalled Ubuntu (Dual boot w/ Win 7), resized Swap file now at 3800+

Swap file shows mounted and Swap is on. UUID is same in Gparted.

The option to Hibernate is not there. Once I get this working...

Also would like to make Swap file used only for hibernation not actual swapping. How would I do this? I'm using a SSD drive.

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=24159a3c-8e6e-4801-a9e5-ad54800f9676 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=c4efd754-7214-4437-9cdc-28de0315fa20 none            swap    sw              0       0
~                                                                               
"/etc/fstab" 12L, 664C                                        1,1           All

---

