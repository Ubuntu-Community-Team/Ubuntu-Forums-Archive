---
title: "Windows 7 MBR help!!"
date: 2011-11-14
forum: General Help
---

### Post by DivineMancy on 2011-11-14
Hey, guys...I'm totally new to Ubuntu and I tried to uninstall it I did it wrong I know but, that's what I did.


First of all, I was on Windows and I uninstalled it using the wubi.exe and un-installed it like any other application....I rebooted and Ubuntu was still there. -.- and I was on GRUB. So, I found this guide on the internet and I followed it to uninstall ubuntu "safely" as it said, I got screwed. So, first of all I had to use this software called EasyBCD which is supposed to be used in order to remove GRUB and use MBR...So, I picked my choices carefully and I chose the "Windows Vista/7 MBR" and I clicked Write MBR...GRUB was removed but, I couldn't boot into Windows. I re-installed Ubuntu and of course GRUB came along...I noticed something...It used to say at the bottom "Windows 7 loader/sda" Now, it says "Windows Vista loader" So, I guess that means that I got the Windows Vista MBR not the Windows 7 one....I don't have a Windows disk or anything..Right now, all what I have is Ubuntu 11.10 installed and Ubuntu 11.10 Live disk on a USB flash drive and please help! I want to get the Windows 7 MBR back and I tried many stuff to restore the MBR but, it restores Windows Vista MBR...I used lilo and the boot-repair thing..it's just not working. :(

Please, help!

---

### Post by DivineMancy on 2011-11-14
Anyone??

---

### Post by Quackers on 2011-11-14
So you're getting a grub menu on startup which gives you the choice of Ubuntu or Windows Vista (don't worry about the Vista thing for the moment)?

If you choose Ubuntu does it boot up?
Presumably there are a couple of Windows vista entries? Is one for the recovery loader?

---

### Post by DivineMancy on 2011-11-14
> **Quackers said:**
> So you're getting a grub menu on startup which gives you the choice of Ubuntu or Windows Vista (don't worry about the Vista thing for the moment)?

If you choose Ubuntu does it boot up?
Presumably there are a couple of Windows vista entries? Is one for the recovery loader?


Yeah, if I choose Ubuntu it boots up Ubuntu. And no, nothing is recovery for Vista. There's a recovery but it says Ubuntu.

---

### Post by Quackers on 2011-11-14
How many Windows entries appear in the grub menu?
If you choose the Vista entry what happens?
Have you tried the Windows Recovery Loader entry, if there is one?

---

### Post by DivineMancy on 2011-11-14
> **Quackers said:**
> How many Windows entries appear in the grub menu?
If you choose the Vista entry what happens?
Have you tried the Windows Recovery Loader entry, if there is one?


Just 1. Only 1 Windows entry appears.

If I choose Vista, it takes me to the failed-boot in Windows that gives me instructions on using a recovery disk and nope, there's no Windows Recovery Loader at all.

---

### Post by Quackers on 2011-11-14
It seems from your first post that you had Ubuntu installed via wubi and then uninstalled it.
I presume your present Ubuntu installation is not via wubi. In other words Ubuntu has its own partition now.
When you installed Ubuntu this last time did you resize the Windows C: drive or allow the Ubuntu installer to do that?

---

### Post by DivineMancy on 2011-11-14
> **Quackers said:**
> It seems from your first post that you had Ubuntu installed via wubi and then uninstalled it.
I presume your present Ubuntu installation is not via wubi. In other words Ubuntu has its own partition now.
When you installed Ubuntu this last time did you resize the Windows C: drive or allow the Ubuntu installer to do that?

Yeah, at first I had the wubi thing then I removed it. Then, after I couldn't get into Windows again, I downloaded the Ubuntu for a CD or USB stick from the website and installed it...and yeah, it asked about resizing a partition and it took some capacity from the D. And just to let u know, I have full access to the HDD. Like, I can access the Windows partition and stuff.

---

### Post by Quackers on 2011-11-14
Unfortunately it is better to make any changes to Windows partitions with Windows software before installing Ubuntu.
You also should have made a Windows repair disc from within Windows before doing anything else. They can come in very handy, especially for repairing the MBR.

Please go to the site below and download the boot script. This will give you a zip file which should be extracted in the same directory as it was downloaded. This produces a folder which contains the script and a changelog file.
You then need to cd to that directory in the terminal (for example ```
 cd Downloads/boot_info_script060
``` if you downloaded it to your Downloads folder). You don't need to do that if you downloaded it to your home folder.
Then enter
```
sudo bash boot_info_script.sh
```

This will produce a results.txt file in the same directory as the downloaded boot script. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply) and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Or alternatively, have a look here

[http://ubuntuforums.org/showthread.php?t=1821980](http://ubuntuforums.org/showthread.php?t=1821980)

---

### Post by DivineMancy on 2011-11-14
I followed the instructions on the website at the bottom using the boot-repair thing.

```
     [COLOR=#000]                                   **Download as text**

    1   2   3   4   5   6   7   8   9  10  11  12  13  14  15  16  17  18  19  20  21  22  23  24  25  26  27  28  29  30  31  32  33  34  35  36  37  38  39  40  41  42  43  44  45  46  47  48  49  50  51  52  53  54  55  56  57  58  59  60  61  62  63  64  65  66  67  68  69  70  71  72  73  74  75  76  77  78  79  80  81  82  83  84  85  86  87  88  89  90  91  92  93  94  95  96  97  98  99 100 101 102 103 104 105 106 107 108 109 110 111 112 113 114 115 116 117 118 119 120 121 122 123 124 125 126 127 128 129 130 131 132 133 134 135 136 137 138 139 140 141 142 143 144 145 146 147 148 149 150 151 152 153 154 155 156 157 158 159 160 161 162 163 164 165 166 167 168 169 170 171 172 173 174 175 176 177 178 179 180 181 182 183 184 185 186 187 188 189 190 191 192 193 194 195 196 197 198 199 200 201 202 203 204 205 206 207 208 209 210 211 212 213 214 215 216 217 218 219 220 221 222 223 224 225 226 227 228 229 230 231 232 233 234 235 236 237 238 239 240 241 242 243 244 245 246 247 248 249 250 251 252 253 254 255 256 257 258 259 260 261 262 263 264 265 266 267 268 269 270 271 272 273 274 275 276 277 278 279 280 281 282 283 284 285 286 287 288 289 290 291 292 293 294 295 296 297 298 299 300 301 302 303 304 305 306 307 308 309 310 311 312 313 314 315 316 317 318 319 320 321 322 323 324 325 326 327 328 329 330 331 332 333 334 335 336 337 338 339 340 341 342 343 344 345 346 347 348 349 350 351 352 353 354 355 356 357 358 359 360 361 362 363 364 365 366 367 368 369 370 371 372 373 374 375 376 377 378 379 380 381 382 383 384 385 386 387 388 389 390 391 392 393 394 395 396 397 398 399 400 401 402 403 404 405 406 407 408 409 410 411 412 413 414 415 416 417 418 419 420 421 422 423 424 425 426 427 428 429 430 431 432 433 434 435 436 437 438 439 440 441 442 443 444 445 446 447 448 449 450 451 452 453 454 455 456 457 458 459 460 461 462 463 464 465 466 467 468 469 470 471 472 473 474 475 476 477 478 479 480 481 482 483                  Boot Info Script 0.60    from 17 May 2011   ============================= Boot Info Summary: ===============================   => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of      the same hard drive for core.img. core.img is at this location and looks      for  on this drive.  sda1: __________________________________________________________________________      File system:       ntfs     Boot sector type:  Windows Vista/7     Boot sector info:   No errors found in the Boot Parameter Block.     Operating System:  Windows 7     Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe  sda2: __________________________________________________________________________      File system:       Extended Partition     Boot sector type:  Unknown     Boot sector info:    sda5: __________________________________________________________________________      File system:       ntfs     Boot sector type:  Windows Vista/7     Boot sector info:   According to the info in the boot sector, sda5 starts                         at sector 63.     Operating System:       Boot files:          sda6: __________________________________________________________________________      File system:       ntfs     Boot sector type:  Windows Vista/7     Boot sector info:   According to the info in the boot sector, sda6 starts                         at sector 63.     Operating System:       Boot files:          sda7: __________________________________________________________________________      File system:       ntfs     Boot sector type:  Windows Vista/7     Boot sector info:   According to the info in the boot sector, sda7 starts                         at sector 63.     Operating System:       Boot files:          sda8: __________________________________________________________________________      File system:       ext4     Boot sector type:  -     Boot sector info:       Operating System:  Ubuntu 11.10     Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img  sda9: __________________________________________________________________________      File system:       swap     Boot sector type:  -     Boot sector info:    ============================ Drive/Partition Info: =============================  Drive: sda _____________________________________________________________________  Disk /dev/sda: 500.1 GB, 500107862016 bytes 255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors Units = sectors of 1 * 512 = 512 bytes Sector size (logical/physical): 512 bytes / 512 bytes  Partition  Boot  Start Sector    End Sector  # of Sectors  Id System  /dev/sda1    *             63   286,712,054   286,711,992   7 NTFS / exFAT / HPFS /dev/sda2         286,712,116   976,768,064   690,055,949   f W95 Extended (LBA) /dev/sda5         286,712,118   393,171,518   106,459,401   7 NTFS / exFAT / HPFS /dev/sda6         491,508,738   696,305,294   204,796,557   7 NTFS / exFAT / HPFS /dev/sda7         696,305,358   976,768,064   280,462,707   7 NTFS / exFAT / HPFS /dev/sda8         393,172,992   483,532,799    90,359,808  83 Linux /dev/sda9         483,534,848   491,507,711     7,972,864  82 Linux swap / Solaris   "blkid" output: ________________________________________________________________  Device           UUID                                   TYPE       LABEL  /dev/sda1        D8924DD8924DBBAE                       ntfs        /dev/sda5        5852EF7652EF5772                       ntfs       Music /dev/sda6        A648D25E48D22CB5                       ntfs       Movies /dev/sda7        3224DD1024DCD7C5                       ntfs       Games /dev/sda8        96bc4301-cdde-46cd-a38a-66356cfa6a2e   ext4        /dev/sda9        b98f4d4b-ae76-4f72-bfc0-b14924891195   swap         ================================ Mount points: =================================  Device           Mount_Point              Type       Options  /dev/sda1        /media/D8924DD8924DBBAE  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions) /dev/sda6        /media/Movies            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions) /dev/sda7        /media/Games             fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions) /dev/sda8        /                        ext4       (rw,errors=remount-ro,commit=600)   =========================== sda8/boot/grub/grub.cfg: ===========================  -------------------------------------------------------------------------------- # # DO NOT EDIT THIS FILE # # It is automatically generated by grub-mkconfig using templates # from /etc/grub.d and settings from /etc/default/grub #  ### BEGIN /etc/grub.d/00_header ### if [ -s $prefix/grubenv ]; then   set have_grubenv=true   load_env fi set default="0" if [ "${prev_saved_entry}" ]; then   set saved_entry="${prev_saved_entry}"   save_env saved_entry   set prev_saved_entry=   save_env prev_saved_entry   set boot_once=true fi  function savedefault {   if [ -z "${boot_once}" ]; then     saved_entry="${chosen}"     save_env saved_entry   fi }  function recordfail {   set recordfail=1   if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi }  function load_video {   insmod vbe   insmod vga   insmod video_bochs   insmod video_cirrus }  insmod part_msdos insmod ext2 set root='(hd0,msdos8)' search --no-floppy --fs-uuid --set=root 96bc4301-cdde-46cd-a38a-66356cfa6a2e if loadfont /usr/share/grub/unicode.pf2 ; then   set gfxmode=auto   load_video   insmod gfxterm   insmod part_msdos   insmod ext2   set root='(hd0,msdos8)'   search --no-floppy --fs-uuid --set=root 96bc4301-cdde-46cd-a38a-66356cfa6a2e   set locale_dir=($root)/boot/grub/locale   set lang=en_US   insmod gettext fi terminal_output gfxterm if [ "${recordfail}" = 1 ]; then   set timeout=10 else   set timeout=10 fi ### END /etc/grub.d/00_header ###  ### BEGIN /etc/grub.d/05_debian_theme ### set menu_color_normal=white/black set menu_color_highlight=black/light-gray if background_color 44,0,30; then   clear fi ### END /etc/grub.d/05_debian_theme ###  ### BEGIN /etc/grub.d/10_linux ### if [ ${recordfail} != 1 ]; then   if [ -e ${prefix}/gfxblacklist.txt ]; then     if hwmatch ${prefix}/gfxblacklist.txt 3; then       if [ ${match} = 0 ]; then         set linux_gfx_mode=keep       else         set linux_gfx_mode=text       fi     else       set linux_gfx_mode=text     fi   else     set linux_gfx_mode=keep   fi else   set linux_gfx_mode=text fi export linux_gfx_mode if [ "$linux_gfx_mode" != "text" ]; then load_video; fi menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {     recordfail     set gfxpayload=$linux_gfx_mode     insmod gzio     insmod part_msdos     insmod ext2     set root='(hd0,msdos8)'     search --no-floppy --fs-uuid --set=root 96bc4301-cdde-46cd-a38a-66356cfa6a2e     linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=96bc4301-cdde-46cd-a38a-66356cfa6a2e ro   quiet splash vt.handoff=7     initrd    /boot/initrd.img-3.0.0-12-generic } menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {     recordfail     insmod gzio     insmod part_msdos     insmod ext2     set root='(hd0,msdos8)'     search --no-floppy --fs-uuid --set=root 96bc4301-cdde-46cd-a38a-66356cfa6a2e     echo    'Loading Linux 3.0.0-12-generic ...'     linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=96bc4301-cdde-46cd-a38a-66356cfa6a2e ro recovery nomodeset      echo    'Loading initial ramdisk ...'     initrd    /boot/initrd.img-3.0.0-12-generic } ### END /etc/grub.d/10_linux ###  ### BEGIN /etc/grub.d/20_linux_xen ### ### END /etc/grub.d/20_linux_xen ###  ### BEGIN /etc/grub.d/20_memtest86+ ### menuentry "Memory test (memtest86+)" {     insmod part_msdos     insmod ext2     set root='(hd0,msdos8)'     search --no-floppy --fs-uuid --set=root 96bc4301-cdde-46cd-a38a-66356cfa6a2e     linux16    /boot/memtest86+.bin } menuentry "Memory test (memtest86+, serial console 115200)" {     insmod part_msdos     insmod ext2     set root='(hd0,msdos8)'     search --no-floppy --fs-uuid --set=root 96bc4301-cdde-46cd-a38a-66356cfa6a2e     linux16    /boot/memtest86+.bin console=ttyS0,115200n8 } ### END /etc/grub.d/20_memtest86+ ###  ### BEGIN /etc/grub.d/30_os-prober ### menuentry "Windows Vista (loader) (on /dev/sda1)" --class windows --class os {     insmod part_msdos     insmod ntfs     set root='(hd0,msdos1)'     search --no-floppy --fs-uuid --set=root D8924DD8924DBBAE     chainloader +1 } ### END /etc/grub.d/30_os-prober ###  ### BEGIN /etc/grub.d/40_custom ### # This file provides an easy way to add custom menu entries.  Simply type the # menu entries you want to add after this comment.  Be careful not to change # the 'exec tail' line above. ### END /etc/grub.d/40_custom ###  ### BEGIN /etc/grub.d/41_custom ### if [ -f  $prefix/custom.cfg ]; then   source $prefix/custom.cfg; fi ### END /etc/grub.d/41_custom ### --------------------------------------------------------------------------------  =============================== sda8/etc/fstab: ================================  -------------------------------------------------------------------------------- # /etc/fstab: static file system information. # # Use 'blkid' to print the universally unique identifier for a # device; this may be used with UUID= as a more robust way to name devices # that works even if disks are added and removed. See fstab(5). # # <file system> <mount point>   <type>  <options>       <dump>  <pass> proc            /proc           proc    nodev,noexec,nosuid 0       0 # / was on /dev/sda8 during installation UUID=96bc4301-cdde-46cd-a38a-66356cfa6a2e /               ext4    errors=remount-ro 0       1 # swap was on /dev/sda9 during installation UUID=b98f4d4b-ae76-4f72-bfc0-b14924891195 none            swap    sw              0       0 --------------------------------------------------------------------------------  =================== sda8: Location of files loaded by Grub: ====================             GiB - GB             File                                 Fragment(s)   219.678741455 = 235.878252544  boot/grub/core.img                             1  219.638267517 = 235.834793984  boot/grub/grub.cfg                             1  226.167964935 = 242.846003200  boot/initrd.img-3.0.0-12-generic               1  219.677463531 = 235.876880384  boot/vmlinuz-3.0.0-12-generic                  1  226.167964935 = 242.846003200  initrd.img                                     1  219.677463531 = 235.876880384  vmlinuz                                        1  ======================== Unknown MBRs/Boot Sectors/etc: ========================  Unknown BootLoader on sda2  00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................| * 000001b0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff 00 fe  |................| 000001c0  ff ff 07 fe ff ff 02 00  00 00 09 71 58 06 00 fe  |...........qX...| 000001d0  ff ff 05 fe ff ff 8f f2  34 0c cc f2 34 0c 00 00  |........4...4...| 000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................| 000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.| 00000200   =============================== StdErr Messages: ===============================  unlzma: Decoder error  ADDITIONAL INFORMATION : **************** log of boot-repair 2011-11-13__16h21 **************** boot-repair version : 3-0ppa21~oneiric clean-ubiquity-common version : 3-0ppa8~oneiric internet: connected boot-repair-common version : 3.0-0ppa37~oneiric /usr/share/clean/cleancommon-gui.sh: line 151:  3197 Terminated              while true; do done LIVESESSION is : no BYTES_BEFORE_PART[1] (sda) = 63 sectors * 512 bytes = 32256 bytes. OSPROBER: /dev/sda8:The OS now in use - Ubuntu 11.10 CurrentSession:linux /dev/sda1:Windows Vista (loader):Windows:chain BLKID: /dev/sda1: UUID="D8924DD8924DBBAE" TYPE="ntfs" /dev/sda5: LABEL="Music" UUID="5852EF7652EF5772" TYPE="ntfs" /dev/sda6: LABEL="Movies" UUID="A648D25E48D22CB5" TYPE="ntfs" /dev/sda7: LABEL="Games" UUID="3224DD1024DCD7C5" TYPE="ntfs" /dev/sda8: UUID="96bc4301-cdde-46cd-a38a-66356cfa6a2e" TYPE="ext4" /dev/sda9: UUID="b98f4d4b-ae76-4f72-bfc0-b14924891195" TYPE="swap" sda8 contains The OS now in use - Ubuntu 11.10 (linux) sda1 contains Windows Vista (windows) 1 disks with OS, 2 OS : 1 Linux, 0 MacOS, 1 Windows, 0 unknown type OS. Total of 2 OS detected on sda disk. sda contains minimum one OS FDISK Disk /dev/sda: 500.1 GB, 500107862016 bytes 255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors Units = sectors of 1 * 512 = 512 bytes Sector size (logical/physical): 512 bytes / 512 bytes I/O size (minimum/optimal): 512 bytes / 512 bytes Disk identifier: 0x13181318  Device Boot      Start         End      Blocks   Id  System /dev/sda1   *          63   286712054   143355996    7  HPFS/NTFS/exFAT /dev/sda2       286712116   976768064   345027974+   f  W95 Ext'd (LBA) /dev/sda5       286712118   393171518    53229700+   7  HPFS/NTFS/exFAT /dev/sda6       491508738   696305294   102398278+   7  HPFS/NTFS/exFAT /dev/sda7       696305358   976768064   140231353+   7  HPFS/NTFS/exFAT /dev/sda8       393172992   483532799    45179904   83  Linux /dev/sda9       483534848   491507711     3986432   82  Linux swap / Solaris  Partition table entries are not in disk order  Disk /dev/sda: 500.1 GB, 500107862016 bytes 255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors Units = sectors of 1 * 512 = 512 bytes Sector size (logical/physical): 512 bytes / 512 bytes I/O size (minimum/optimal): 512 bytes / 512 bytes Disk identifier: 0x13181318  Device Boot      Start         End      Blocks   Id  System /dev/sda1   *          63   286712054   143355996    7  HPFS/NTFS/exFAT /dev/sda2       286712116   976768064   345027974+   f  W95 Ext'd (LBA) /dev/sda5       286712118   393171518    53229700+   7  HPFS/NTFS/exFAT /dev/sda6       491508738   696305294   102398278+   7  HPFS/NTFS/exFAT /dev/sda7       696305358   976768064   140231353+   7  HPFS/NTFS/exFAT /dev/sda8       393172992   483532799    45179904   83  Linux /dev/sda9       483534848   491507711     3986432   82  Linux swap / Solaris  Partition table entries are not in disk order sda8 : sda, not-sepboot, grub, aptget, 32, with boot, , with-os, no-gpt, fstab-without-efi. sda1 : sda, not-sepboot, no-grub, no-aptget, 32, no boot, /media/D8924DD8924DBBAE, with-os, no-gpt, no-fstab. sda5 : sda, is-maybe-sepboot, no-grub, no-aptget, 32, no boot, /mnt/clean/sda5, no-os, no-gpt, no-fstab. sda6 : sda, is-maybe-sepboot, no-grub, no-aptget, 32, no boot, /media/Movies, no-os, no-gpt, no-fstab. sda7 : sda, is-maybe-sepboot, no-grub, no-aptget, 32, no boot, /media/Games, no-os, no-gpt, no-fstab. PARTED: Model: ATA TOSHIBA MK5065GS (scsi) Disk /dev/sda: 500GB Sector size (logical/physical): 512B/512B Partition Table: msdos  Number  Start   End    Size    Type      File system     Flags 1      32.3kB  147GB  147GB   primary   ntfs            boot 2      147GB   500GB  353GB   extended                  lba 5      147GB   201GB  54.5GB  logical   ntfs 8      201GB   248GB  46.3GB  logical   ext4 9      248GB   252GB  4082MB  logical   linux-swap(v1) 6      252GB   357GB  105GB   logical   ntfs 7      357GB   500GB  144GB   logical   ntfs MOUNT /dev/sda8 on / type ext4 (rw,errors=remount-ro,commit=0) proc on /proc type proc (rw,noexec,nosuid,nodev) sysfs on /sys type sysfs (rw,noexec,nosuid,nodev) fusectl on /sys/fs/fuse/connections type fusectl (rw) none on /sys/kernel/debug type debugfs (rw) none on /sys/kernel/security type securityfs (rw) udev on /dev type devtmpfs (rw,mode=0755) devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620) tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755) none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880) none on /run/shm type tmpfs (rw,nosuid,nodev) binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev) gvfs-fuse-daemon on /home/omak/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=omak) /dev/sda6 on /media/Movies type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions) /dev/sda7 on /media/Games type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions) /dev/sda1 on /media/D8924DD8924DBBAE type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions) /dev/sda5 on /mnt/clean/sda5 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096) /sys/block/sda:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 sda5 sda6 sda7 sda8 sda9 size slaves stat subsystem trace uevent /sys/block/sr0:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent /dev:  agpgart autofs block bsg btrfs-control bus cdrom cdrw char console core cpu cpu_dma_latency disk dri dvd dvdrw ecryptfs fb0 fb1 fd freefall full fuse hpet input kmsg log mapper mcelog mei mem net network_latency network_throughput null oldmem port ppp psaux ptmx pts random rfkill rtc rtc0 scd0 sda sda1 sda2 sda5 sda6 sda7 sda8 sda9 sg0 sg1 shm snapshot snd sr0 stderr stdin stdout uinput urandom usbmon0 usbmon1 usbmon2 v4l vga_arbiter video0 zero /dev/mapper:  control DF Filesystem    Type    Size  Used Avail Use% Mounted on /dev/sda8     ext4     43G  2.5G   38G   7% / udev      devtmpfs    1.2G   12K  1.2G   1% /dev tmpfs        tmpfs    490M  860K  489M   1% /run none         tmpfs    5.0M     0  5.0M   0% /run/lock none         tmpfs    1.2G  100K  1.2G   1% /run/shm /dev/sda6  fuseblk     98G   53G   46G  54% /media/Movies /dev/sda7  fuseblk    134G   58G   77G  44% /media/Games /dev/sda1  fuseblk    137G   71G   67G  52% /media/D8924DD8924DBBAE /dev/sda5  fuseblk     51G  6.6G   45G  13% /mnt/clean/sda5 FDISK Disk /dev/sda: 500.1 GB, 500107862016 bytes 255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors Units = sectors of 1 * 512 = 512 bytes Sector size (logical/physical): 512 bytes / 512 bytes I/O size (minimum/optimal): 512 bytes / 512 bytes Disk identifier: 0x13181318  Device Boot      Start         End      Blocks   Id  System /dev/sda1   *          63   286712054   143355996    7  HPFS/NTFS/exFAT /dev/sda2       286712116   976768064   345027974+   f  W95 Ext'd (LBA) /dev/sda5       286712118   393171518    53229700+   7  HPFS/NTFS/exFAT /dev/sda6       491508738   696305294   102398278+   7  HPFS/NTFS/exFAT /dev/sda7       696305358   976768064   140231353+   7  HPFS/NTFS/exFAT /dev/sda8       393172992   483532799    45179904   83  Linux /dev/sda9       483534848   491507711     3986432   82  Linux swap / Solaris  Partition table entries are not in disk order Logs saved into /var/log/clean/log/2011-11-13__16h21boot-repair24 Logs saved into /media/D8924DD8924DBBAE/clean/log/2011-11-13__16h21boot-repair24 combobox_ostoboot_bydefault_fillin combobox_efi_fillin sda8 combobox_separateboot_fillin set_checkbutton_reinstall_grub set_radiobutton_ostoboot_bydefault separate_bootpart and efi show_hide sda8 efi_show_hide 1 (no-gpt) set_radiobutton_place_grub separate_bootpart and efi show_hide sda8 efi_show_hide 1 (no-gpt) ************************Before mainwindow appear PURGE_POSSIBLE yes PART_TO_REINSTALL_GRUB_PURGE 1 (sda8) FSCK_ACTION no PASTEBIN_ACTION yes REINSTALL_POSSIBLE yes MBR_ACTION reinstall UNHIDEBOOT_ACTION yes (10.s) PART_TO_REINSTALL_GRUB 1 (sda8) FORCE_GRUB no NOFORCE_DISK sda REMOVABLEDISK no UNCOMMENT_GFXMODE no ATA no-ata ADD_KERNEL_OPTION no (acpi=off) MBR_TO_RESTORE sda (mbr) (sda) USE_SEPARATEBOOTPART no (sda5) grub-pc () /usr/share/clean/cleancommon-gui.sh: line 672:  3803 Terminated              while true; do done RETOURCOMBO_purge_grub : sda8 (The OS now in use - Ubuntu 11.10) RETOURCOMBO_ostoboot_bydefault : sda8 (The OS now in use - Ubuntu 11.10) separate_bootpart and efi show_hide sda8 efi_show_hide 1 (no-gpt) RETOURCOMBO_place_grub (NOFORCE_DISK) : sda RETOURCOMBO_separateboot (BOOTPART_TO_USE) : sda5 set_checkbutton_reinstall_grub set_radiobutton_ostoboot_bydefault separate_bootpart and efi show_hide sda8 efi_show_hide 1 (no-gpt) set_radiobutton_place_grub separate_bootpart and efi show_hide sda8 efi_show_hide 1 (no-gpt) RETOURCOMBO_place_grub (NOFORCE_DISK) : sda internet: connected ************************Before Repairing PURGE_POSSIBLE yes PART_TO_REINSTALL_GRUB_PURGE 1 (sda8) FSCK_ACTION no PASTEBIN_ACTION yes REINSTALL_POSSIBLE yes MBR_ACTION nombraction UNHIDEBOOT_ACTION no (10.s) PART_TO_REINSTALL_GRUB 1 (sda8) FORCE_GRUB no NOFORCE_DISK sda REMOVABLEDISK no UNCOMMENT_GFXMODE no ATA no-ata ADD_KERNEL_OPTION no (acpi=off) MBR_TO_RESTORE sda (mbr) (sda) USE_SEPARATEBOOTPART no (sda5) grub-pc () internet: connected /usr/share/clean/bootrepair-actions.sh: line 88:  7314 Terminated              while true; do done dpkg-preconfigure: unable to re-open stdin: 
  
  
                 
         
     [/COLOR]
    
```I hope that's what u were looking for.

That's the link as well... [http://paste.ubuntu.com/738010/](http://paste.ubuntu.com/738010/)

---

### Post by Quackers on 2011-11-14
It's too difficult to read in that format. Plese copy/paste the URL in your next post.

---

### Post by DivineMancy on 2011-11-14
[http://paste.ubuntu.com/738010/](http://paste.ubuntu.com/738010/)


Here is it again.

---

### Post by Quackers on 2011-11-14
Here is the output in code tags to preserve proper formatting.
Let me look at it and I'll get back to you.

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda9: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   286,712,054   286,711,992   7 NTFS / exFAT / HPFS
/dev/sda2         286,712,116   976,768,064   690,055,949   f W95 Extended (LBA)
/dev/sda5         286,712,118   393,171,518   106,459,401   7 NTFS / exFAT / HPFS
/dev/sda6         491,508,738   696,305,294   204,796,557   7 NTFS / exFAT / HPFS
/dev/sda7         696,305,358   976,768,064   280,462,707   7 NTFS / exFAT / HPFS
/dev/sda8         393,172,992   483,532,799    90,359,808  83 Linux
/dev/sda9         483,534,848   491,507,711     7,972,864  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        D8924DD8924DBBAE                       ntfs       
/dev/sda5        5852EF7652EF5772                       ntfs       Music
/dev/sda6        A648D25E48D22CB5                       ntfs       Movies
/dev/sda7        3224DD1024DCD7C5                       ntfs       Games
/dev/sda8        96bc4301-cdde-46cd-a38a-66356cfa6a2e   ext4       
/dev/sda9        b98f4d4b-ae76-4f72-bfc0-b14924891195   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /media/D8924DD8924DBBAE  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda6        /media/Movies            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda7        /media/Games             fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda8        /                        ext4       (rw,errors=remount-ro,commit=600)


=========================== sda8/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos8)'
search --no-floppy --fs-uuid --set=root 96bc4301-cdde-46cd-a38a-66356cfa6a2e
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos8)'
  search --no-floppy --fs-uuid --set=root 96bc4301-cdde-46cd-a38a-66356cfa6a2e
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=10
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
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set=root 96bc4301-cdde-46cd-a38a-66356cfa6a2e
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=96bc4301-cdde-46cd-a38a-66356cfa6a2e ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set=root 96bc4301-cdde-46cd-a38a-66356cfa6a2e
	echo	'Loading Linux 3.0.0-12-generic ...'
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=96bc4301-cdde-46cd-a38a-66356cfa6a2e ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-12-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set=root 96bc4301-cdde-46cd-a38a-66356cfa6a2e
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos8)'
	search --no-floppy --fs-uuid --set=root 96bc4301-cdde-46cd-a38a-66356cfa6a2e
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root D8924DD8924DBBAE
	chainloader +1
}
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

=============================== sda8/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda8 during installation
UUID=96bc4301-cdde-46cd-a38a-66356cfa6a2e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda9 during installation
UUID=b98f4d4b-ae76-4f72-bfc0-b14924891195 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda8: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 219.678741455 = 235.878252544  boot/grub/core.img                             1
 219.638267517 = 235.834793984  boot/grub/grub.cfg                             1
 226.167964935 = 242.846003200  boot/initrd.img-3.0.0-12-generic               1
 219.677463531 = 235.876880384  boot/vmlinuz-3.0.0-12-generic                  1
 226.167964935 = 242.846003200  initrd.img                                     1
 219.677463531 = 235.876880384  vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001b0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff 00 fe  |................|
000001c0  ff ff 07 fe ff ff 02 00  00 00 09 71 58 06 00 fe  |...........qX...|
000001d0  ff ff 05 fe ff ff 8f f2  34 0c cc f2 34 0c 00 00  |........4...4...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error

ADDITIONAL INFORMATION :
**************** log of boot-repair 2011-11-13__16h21 ****************
boot-repair version : 3-0ppa21~oneiric
clean-ubiquity-common version : 3-0ppa8~oneiric
internet: connected
boot-repair-common version : 3.0-0ppa37~oneiric
/usr/share/clean/cleancommon-gui.sh: line 151:  3197 Terminated              while true; do
done
LIVESESSION is : no
BYTES_BEFORE_PART[1] (sda) = 63 sectors * 512 bytes = 32256 bytes.
OSPROBER: /dev/sda8:The OS now in use - Ubuntu 11.10 CurrentSession:linux
/dev/sda1:Windows Vista (loader):Windows:chain
BLKID: /dev/sda1: UUID="D8924DD8924DBBAE" TYPE="ntfs"
/dev/sda5: LABEL="Music" UUID="5852EF7652EF5772" TYPE="ntfs"
/dev/sda6: LABEL="Movies" UUID="A648D25E48D22CB5" TYPE="ntfs"
/dev/sda7: LABEL="Games" UUID="3224DD1024DCD7C5" TYPE="ntfs"
/dev/sda8: UUID="96bc4301-cdde-46cd-a38a-66356cfa6a2e" TYPE="ext4"
/dev/sda9: UUID="b98f4d4b-ae76-4f72-bfc0-b14924891195" TYPE="swap"
sda8 contains The OS now in use - Ubuntu 11.10 (linux)
sda1 contains Windows Vista (windows)
1 disks with OS, 2 OS : 1 Linux, 0 MacOS, 1 Windows, 0 unknown type OS.
Total of 2 OS detected on sda disk.
sda contains minimum one OS
FDISK
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x13181318

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   286712054   143355996    7  HPFS/NTFS/exFAT
/dev/sda2       286712116   976768064   345027974+   f  W95 Ext'd (LBA)
/dev/sda5       286712118   393171518    53229700+   7  HPFS/NTFS/exFAT
/dev/sda6       491508738   696305294   102398278+   7  HPFS/NTFS/exFAT
/dev/sda7       696305358   976768064   140231353+   7  HPFS/NTFS/exFAT
/dev/sda8       393172992   483532799    45179904   83  Linux
/dev/sda9       483534848   491507711     3986432   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x13181318

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   286712054   143355996    7  HPFS/NTFS/exFAT
/dev/sda2       286712116   976768064   345027974+   f  W95 Ext'd (LBA)
/dev/sda5       286712118   393171518    53229700+   7  HPFS/NTFS/exFAT
/dev/sda6       491508738   696305294   102398278+   7  HPFS/NTFS/exFAT
/dev/sda7       696305358   976768064   140231353+   7  HPFS/NTFS/exFAT
/dev/sda8       393172992   483532799    45179904   83  Linux
/dev/sda9       483534848   491507711     3986432   82  Linux swap / Solaris

Partition table entries are not in disk order
sda8 : sda, not-sepboot, grub, aptget, 32, with boot, , with-os, no-gpt, fstab-without-efi.
sda1 : sda, not-sepboot, no-grub, no-aptget, 32, no boot, /media/D8924DD8924DBBAE, with-os, no-gpt, no-fstab.
sda5 : sda, is-maybe-sepboot, no-grub, no-aptget, 32, no boot, /mnt/clean/sda5, no-os, no-gpt, no-fstab.
sda6 : sda, is-maybe-sepboot, no-grub, no-aptget, 32, no boot, /media/Movies, no-os, no-gpt, no-fstab.
sda7 : sda, is-maybe-sepboot, no-grub, no-aptget, 32, no boot, /media/Games, no-os, no-gpt, no-fstab.
PARTED: Model: ATA TOSHIBA MK5065GS (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
1      32.3kB  147GB  147GB   primary   ntfs            boot
2      147GB   500GB  353GB   extended                  lba
5      147GB   201GB  54.5GB  logical   ntfs
8      201GB   248GB  46.3GB  logical   ext4
9      248GB   252GB  4082MB  logical   linux-swap(v1)
6      252GB   357GB  105GB   logical   ntfs
7      357GB   500GB  144GB   logical   ntfs
MOUNT /dev/sda8 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/omak/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=omak)
/dev/sda6 on /media/Movies type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda7 on /media/Games type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda1 on /media/D8924DD8924DBBAE type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda5 on /mnt/clean/sda5 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/sys/block/sda:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 sda5 sda6 sda7 sda8 sda9 size slaves stat subsystem trace uevent
/sys/block/sr0:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev:  agpgart autofs block bsg btrfs-control bus cdrom cdrw char console core cpu cpu_dma_latency disk dri dvd dvdrw ecryptfs fb0 fb1 fd freefall full fuse hpet input kmsg log mapper mcelog mei mem net network_latency network_throughput null oldmem port ppp psaux ptmx pts random rfkill rtc rtc0 scd0 sda sda1 sda2 sda5 sda6 sda7 sda8 sda9 sg0 sg1 shm snapshot snd sr0 stderr stdin stdout uinput urandom usbmon0 usbmon1 usbmon2 v4l vga_arbiter video0 zero
/dev/mapper:  control
DF Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda8     ext4     43G  2.5G   38G   7% /
udev      devtmpfs    1.2G   12K  1.2G   1% /dev
tmpfs        tmpfs    490M  860K  489M   1% /run
none         tmpfs    5.0M     0  5.0M   0% /run/lock
none         tmpfs    1.2G  100K  1.2G   1% /run/shm
/dev/sda6  fuseblk     98G   53G   46G  54% /media/Movies
/dev/sda7  fuseblk    134G   58G   77G  44% /media/Games
/dev/sda1  fuseblk    137G   71G   67G  52% /media/D8924DD8924DBBAE
/dev/sda5  fuseblk     51G  6.6G   45G  13% /mnt/clean/sda5
FDISK
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x13181318

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   286712054   143355996    7  HPFS/NTFS/exFAT
/dev/sda2       286712116   976768064   345027974+   f  W95 Ext'd (LBA)
/dev/sda5       286712118   393171518    53229700+   7  HPFS/NTFS/exFAT
/dev/sda6       491508738   696305294   102398278+   7  HPFS/NTFS/exFAT
/dev/sda7       696305358   976768064   140231353+   7  HPFS/NTFS/exFAT
/dev/sda8       393172992   483532799    45179904   83  Linux
/dev/sda9       483534848   491507711     3986432   82  Linux swap / Solaris

Partition table entries are not in disk order
Logs saved into /var/log/clean/log/2011-11-13__16h21boot-repair24
Logs saved into /media/D8924DD8924DBBAE/clean/log/2011-11-13__16h21boot-repair24
combobox_ostoboot_bydefault_fillin
combobox_efi_fillin sda8
combobox_separateboot_fillin
set_checkbutton_reinstall_grub
set_radiobutton_ostoboot_bydefault
separate_bootpart and efi show_hide sda8
efi_show_hide 1 (no-gpt)
set_radiobutton_place_grub
separate_bootpart and efi show_hide sda8
efi_show_hide 1 (no-gpt)
************************Before mainwindow appear
PURGE_POSSIBLE yes PART_TO_REINSTALL_GRUB_PURGE 1 (sda8)
FSCK_ACTION no PASTEBIN_ACTION yes
REINSTALL_POSSIBLE yes MBR_ACTION reinstall UNHIDEBOOT_ACTION yes (10.s)
PART_TO_REINSTALL_GRUB 1 (sda8) FORCE_GRUB no NOFORCE_DISK sda REMOVABLEDISK no UNCOMMENT_GFXMODE no ATA no-ata ADD_KERNEL_OPTION no (acpi=off) MBR_TO_RESTORE sda (mbr) (sda) USE_SEPARATEBOOTPART no (sda5) grub-pc ()
/usr/share/clean/cleancommon-gui.sh: line 672:  3803 Terminated              while true; do
done
RETOURCOMBO_purge_grub : sda8 (The OS now in use - Ubuntu 11.10)
RETOURCOMBO_ostoboot_bydefault : sda8 (The OS now in use - Ubuntu 11.10)
separate_bootpart and efi show_hide sda8
efi_show_hide 1 (no-gpt)
RETOURCOMBO_place_grub (NOFORCE_DISK) : sda
RETOURCOMBO_separateboot (BOOTPART_TO_USE) : sda5
set_checkbutton_reinstall_grub
set_radiobutton_ostoboot_bydefault
separate_bootpart and efi show_hide sda8
efi_show_hide 1 (no-gpt)
set_radiobutton_place_grub
separate_bootpart and efi show_hide sda8
efi_show_hide 1 (no-gpt)
RETOURCOMBO_place_grub (NOFORCE_DISK) : sda
internet: connected
************************Before Repairing
PURGE_POSSIBLE yes PART_TO_REINSTALL_GRUB_PURGE 1 (sda8)
FSCK_ACTION no PASTEBIN_ACTION yes
REINSTALL_POSSIBLE yes MBR_ACTION nombraction UNHIDEBOOT_ACTION no (10.s)
PART_TO_REINSTALL_GRUB 1 (sda8) FORCE_GRUB no NOFORCE_DISK sda REMOVABLEDISK no UNCOMMENT_GFXMODE no ATA no-ata ADD_KERNEL_OPTION no (acpi=off) MBR_TO_RESTORE sda (mbr) (sda) USE_SEPARATEBOOTPART no (sda5) grub-pc ()
internet: connected
/usr/share/clean/bootrepair-actions.sh: line 88:  7314 Terminated              while true; do
done
dpkg-preconfigure: unable to re-open stdin:
```

---

### Post by DivineMancy on 2011-11-14
Alright, thanks! =)

I'll be waiting.

---

### Post by Quackers on 2011-11-14
Do you know how many primary partitions were in use before you installed Ubuntu?
You appear to have 4 Windows type partitions (NTFS). What is in those partitions?

---

### Post by DivineMancy on 2011-11-14
> **Quackers said:**
> Do you know how many primary partitions were in use before you installed Ubuntu?
You appear to have 4 Windows type partitions (NTFS). What is in those partitions?


Yeah, I had 4 partitions. One for System and the other 3 r for Music, Movies and Games.

---

### Post by Quackers on 2011-11-14
Were they all primary partitions or were some logical partitions?
The maximum number of primary partitions on an MBR partitioned disc is 4.
If you had 4 already then installed Ubuntu it's a miracle that Windows still shows as the correct file type. It often gets changed from NTFS to SFS, which is bad!
Do you have backups of your Windows data and music/movies etc? If not I would suggest that you make them now if you can access those partitions through Ubuntu.

As to what to do about it, I'm not sure what to suggest. As Windows 7 is installed to just one partition I see no reason why it will not boot, unless Windows just didn't enjoy its D: drive being adapted by the Ubuntu installer.
It may be that Windows just needs a chkdsk to be run, but that's easier said than done now.
I will contact a couple of other members to see what they suggest.

---

### Post by DivineMancy on 2011-11-14
> **Quackers said:**
> Were they all primary partitions or were some logical partitions?
The maximum number of primary partitions on an MBR partitioned disc is 4.
If you had 4 already then installed Ubuntu it's a miracle that Windows still shows as the correct file type. It often gets changed from NTFS to SFS, which is bad!
Do you have backups of your Windows data and music/movies etc? If not I would suggest that you make them now if you can access those partitions through Ubuntu.

As to what to do about it, I'm not sure what to suggest. As Windows 7 is installed to just one partition I see no reason why it will not boot, unless Windows just didn't enjoy its D: drive being adapted by the Ubuntu installer.
It may be that Windows just needs a chkdsk to be run, but that's easier said than done now.
I will contact a couple of other members to see what they suggest.

I have no idea if they were primary or logical. I've had Ubuntu for like 2 months on my computer and never encountered any problems when I used Ubuntu or Windows. Everything was fine till I used this software and it made my MBR Windows Vista. That's when stuff got bad, I think if the MBR can go back to Windows 7 everything would be back to normal. After all, u're the one who knows about that kind of stuff so, it's ur call. =D

---

### Post by Quackers on 2011-11-14
I don't think the MBR is the problem at the moment.
The Ubuntu that was booting ok with Windows was wubi wasn't it?
Did Windows stop booting when you installed Ubuntu on its own partition - after uninstalling wubi?

Don't worry about the Vista thing for the moment. Vista and Windows 7 bootloaders are the same.

---

### Post by DivineMancy on 2011-11-14
> **Quackers said:**
> I don't think the MBR is the problem at the moment.
The Ubuntu that was booting ok with Windows was wubi wasn't it?
Did Windows stop booting when you installed Ubuntu on its own partition - after uninstalling wubi?

Yeah, Ubuntu was just find along Windows when it was Wubi.

After uninstalling Wubi Windows was still working fine...but, I had to boot through GRUB. Then, when I attempted to replace GRUB with MBR that's when this all crap happened. It used to say Windows 7 loader on GRUB now it says Windows Vista loader. So, basically, everything was just perfect until I tried to replace GRUB with MBR.

---

### Post by Quackers on 2011-11-14
Interesting.
I have contacted a few other people on here to offer advice. I would like their input before offering any advice. They are not online at the moment unfortunately, but I would recommend that we wait.
It may be worthwhile googling for a Windows 7 repair disc download - you may need one. NOTE it must be the same architecture as your installation - ie 32 bit/64 bit.

Sadly, as I have been up all night I need to sleep. Hopefully the others will be along shortly to offer advice on what to do.
I'll look in later to check everything's ok. Good luck :-)

---

### Post by Rubi1200 on 2011-11-14
Hi,
I am one of those Quackers asked to take a look at things.

What you will need to do is work from the LiveCD/USB.

First, boot the computer with the live environment and open a terminal with Ctrl+Alt+T.

Then post the output of the following commands:

```
sudo fdisk -lu
sudo sfdisk -V
```

Once you have done that, please do this:

```
sudo apt-get update
sudo apt-get install gawk
```

Once gawk is installed, run the boot info script again and post the results as before.

After all that, we can take this to the next level.

Thanks.

---

### Post by coffeecat on 2011-11-14
> **DivineMancy said:**
> If I choose Vista, it takes me to the failed-boot in Windows that gives me instructions on using a recovery disk and nope, there's no Windows Recovery Loader at all.

@DivineMancy, this "failed boot" that you get. Is it anything like the screenshot in the thumbnail below? That's a screenshot from Vista, but I think the Windows 7 one would be similar. If that's what you are seeing, this is because winload.exe has moved its absolute (not relative) location and Windows can't deal with this (as far as I understand the situation). If this is what you are seeing, it is fixable.

---

### Post by oldfred on 2011-11-14
Vista & Windows7 almost always start at sector 2048, yours starts at sector 63 which was the standard for XP. Old versions of gparted would move a Windows partition to 63 and cause issues. The Windows NTFS partition boot sector has info that has to match the partition table. So if it is moved it will not work.

The repairs are usually a combination of fixboot and chkdsk from a Windows repair console. Do you have a full Windows install, not vendor recovery or a Vista repair Disk?

---

### Post by DivineMancy on 2011-11-14
> **coffeecat said:**
> @DivineMancy, this "failed boot" that you get. Is it anything like the screenshot in the thumbnail below? That's a screenshot from Vista, but I think the Windows 7 one would be similar. If that's what you are seeing, this is because winload.exe has moved its absolute (not relative) location and Windows can't deal with this (as far as I understand the situation). If this is what you are seeing, it is fixable.

Yeah, that's exactly what I get...but,1 difference....It doesn't say winload.exe it says bcd.

---

### Post by DivineMancy on 2011-11-14
> **oldfred said:**
> Vista & Windows7 almost always start at sector 2048, yours starts at sector 63 which was the standard for XP. Old versions of gparted would move a Windows partition to 63 and cause issues. The Windows NTFS partition boot sector has info that has to match the partition table. So if it is moved it will not work.

The repairs are usually a combination of fixboot and chkdsk from a Windows repair console. Do you have a full Windows install, not vendor recovery or a Vista repair Disk?
I'm sorry but, I don't have any Windows CD..it's a laptop and I didn't get any recovery disks with it.

---

### Post by coffeecat on 2011-11-14
> **DivineMancy said:**
> I'm sorry but, I don't have any Windows CD..it's a laptop and I didn't get any recovery disks with it.

You have Windows 7, correct? You need a Windows 7 repair CD which is only about 270MB in size. It's quite different from the manufacturer's recovery discs, which would have to be DVDs for Windows 7.

Do you have access to another Windows 7 system? You can use any Windows 7 system to create a repair CD so long as you use 64-bit for 64-bit and 32-bit for 32-bit. Just click on the start button and type "repair" in the search box. If you don't have access to another Windows 7 system, have a look here:

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

There's a charge for those, so you will probably want to prevail on the goodwill of a friend or relative with Windows 7.

---

### Post by DivineMancy on 2011-11-14
> **Rubi1200 said:**
> Hi,
I am one of those Quackers asked to take a look at things.

What you will need to do is work from the LiveCD/USB.

First, boot the computer with the live environment and open a terminal with Ctrl+Alt+T.

Then post the output of the following commands:

```
sudo fdisk -lu
sudo sfdisk -V
```Once you have done that, please do this:

```
sudo apt-get update
sudo apt-get install gawk
```Once gawk is installed, run the boot info script again and post the results as before.

After all that, we can take this to the next level.

Thanks.

Hi, thanks for trying to help. =)

I've did as u said and logged in from the Live USB and typed in the commands and installed gawk. Please, visit the link below for the info since I'm not well with the CODE thing since last time I did it, it was difficult to read.

[http://paste.ubuntu.com/738621/](http://paste.ubuntu.com/738621/)

Thanks in advance. =)

---

### Post by DivineMancy on 2011-11-14
I'm sorry guys I wasn't here when you replied, I had to go. I'm a college student and I was with Quackers at night so, I had 3 hours left to sleep before class. I hope u understand. =)

---

### Post by DivineMancy on 2011-11-14
> **coffeecat said:**
> You have Windows 7, correct? You need a Windows 7 repair CD which is only about 270MB in size. It's quite different from the manufacturer's recovery discs, which would have to be DVDs for Windows 7.

Do you have access to another Windows 7 system? You can use any Windows 7 system to create a repair CD so long as you use 64-bit for 64-bit and 32-bit for 32-bit. Just click on the start button and type "repair" in the search box. If you don't have access to another Windows 7 system, have a look here:

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

There's a charge for those, so you will probably want to prevail on the goodwill of a friend or relative with Windows 7.

Yeah, I have Windows 7 Home Premium x64. And I'll be looking for someone who has Windows 7 and try this. I would ask my roommate but he uses Linux Mint.

EDIT: Is there a way to do this with a USB flash drive?? I have a Flash drive with Ubuntu in it but, I think I can just remove Ubuntu from the flash drive and put the recovery thing since I already have Ubuntu 11.10 installed on my computer and it boots just fine. Do u think I can do that?

---

### Post by oldfred on 2011-11-14
I really recommend that you have a liveCD, repairCD or USB for every system you have installed. 
Make your own Windows recoveryCD/repair:
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

I did manage to get a Win7 repair installed on a 2GB flash and it took  so little space I installed grub and loopmounted several small repair  ISOs, so I have an all in one repair flash drive. I was surprised that  grub could boot the Windows repair and that was more the reason it did  it, just to see if it would work.

---

### Post by DivineMancy on 2011-11-14
> **oldfred said:**
> I really recommend that you have a liveCD, repairCD or USB for every system you have installed. 
Make your own Windows recoveryCD/repair:
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

I did manage to get a Win7 repair installed on a 2GB flash and it took  so little space I installed grub and loopmounted several small repair  ISOs, so I have an all in one repair flash drive. I was surprised that  grub could boot the Windows repair and that was more the reason it did  it, just to see if it would work.

I got to work on that one, I downloaded an ISO recovery disk for Windows 7, I also made sure it's for 64*bit. I'm following the article and I'll reply back with the results.

---

### Post by DivineMancy on 2011-11-14
It worked!!! Thanks so much everyone!! Windows ran the CHKDSK then it restarted and it worked! But, here r a few things I've noticed...It still says Windows Vista on GRUB...but it loads normally...another thing, when the computer used to boot, it used to go to GRUB then I'd have to pick Windows or Ubuntu...when I would pick Windows it would ask me again but on MBR if I want to boot into Ubuntu or Windows. Now, I boot into Windows it doesn't show Ubuntu at all at the MBR...it just boots in. So now, my computer boots to GRUB...Right now, I would like to un-install Ubuntu safely. There's no Ubuntu folder in my C: drive cuz this time it's not the Wubi...I wanna un-install it without having to go through all this hassle again, any help??

Thank you everyone who helped me along the way, I truly appreciate it. =)

---

### Post by oldfred on 2011-11-14
If you have wubi, it boots with Windows and in Windows you choose Ubuntu or Windows.

If you have a full install of Ubuntu then you boot with grub2's boot loader and you choose Ubuntu or Windows.

If you want to directly boot Windows then you have to reinstall the Windows boot loader. From the Windows repair it is the fixMBR command or run the repair 3 times and that should automatically rewrite the MBR. But then you cannot boot Ubuntu that is in a separate partition.

---

### Post by DivineMancy on 2011-11-14
> **oldfred said:**
> If you have wubi, it boots with Windows and in Windows you choose Ubuntu or Windows.

If you have a full install of Ubuntu then you boot with grub2's boot loader and you choose Ubuntu or Windows.

If you want to directly boot Windows then you have to reinstall the Windows boot loader. From the Windows repair it is the fixMBR command or run the repair 3 times and that should automatically rewrite the MBR. But then you cannot boot Ubuntu that is in a separate partition.

Yeah, but..right now, I'm trying to uninstall Ubuntu completely and leave the live version on my flash drive just in case I wanted to use Ubuntu some day in the future. So, can u help me with that? Uninstalling Ubuntu?

---

### Post by oldfred on 2011-11-14
Reinstall the Windows boot loader to the MBR first. Then from the liveCD/USB with gparted, you can delete the Ubuntu partitions. I would suggest using the space for a d: drive as it is better to separate system from data as much as you can.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

The windows repair disk will also restore the Windows boot loader to the MBR.

If you want to remove wubi.

HOW TO Avoid Wubi & Install Ubuntu on USB Drive -amjjawad
[http://ubuntuforums.org/showthread.php?t=1650699](http://ubuntuforums.org/showthread.php?t=1650699)

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)
The Windows-based Ubuntu Installer (Wubi) allows you to install and uninstall Ubuntu from within Microsoft Windows. It lets a Microsoft Windows user try Ubuntu without risking any data loss due to disk formatting or partitioning.

---

### Post by DivineMancy on 2011-11-14
Done! I deleted the Ubuntu partition on Windows then restarted the computer; after that I chose to boot from the Windows 7 Recovery USB, went to command prompt and typed those...

```
bootrec.exe/fixboot
```

Then,

```
bootrec.exe/fixmbr
```

I restarted again and it booted normally as if nothing ever happened.

Thanks Quackers, Rubi1200, coffeecat and oldfred!! U guys rock! =)

Solved!

---

### Post by Rubi1200 on 2011-11-14
Great news! Glad you got things sorted out :)

Bookmark all those links and other things we provided you with; you never know when you may need them again.

---

### Post by Quackers on 2011-11-15
I'm very glad to hear that you got things sorted out :-)
It is important to have the means to recover your system BEFORE installing other operating systems or changing partitions - as you have seen.
A good result I think.

---

