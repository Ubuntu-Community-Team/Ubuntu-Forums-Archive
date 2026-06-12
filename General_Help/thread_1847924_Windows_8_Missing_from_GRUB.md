---
title: "Windows 8 Missing from GRUB"
date: 2011-09-21
forum: General Help
---

### Post by hiever1 on 2011-09-21
I just installed Windows 8 DP. I dual boot Windows 7 and Windows 8. Now I just install Ubuntu 11.04 and it's missing from the GRUB menu.

I tried this > udo update-grub2
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done

Am I able to add it in manual?

---

### Post by oldfred on 2011-09-21
Do not know about Windows 8, but all previous versions of Windows can only boot thru the active (boot flag) primary NTFS partition. But there are work arounds when you install, bit more difficult afterwards.

To see where everything is at:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by hiever1 on 2011-09-21
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 7 for /boot/burg.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   191,740,551   191,533,704   7 NTFS / exFAT / HPFS
/dev/sda3         191,741,952   265,107,455    73,365,504   7 NTFS / exFAT / HPFS
/dev/sda4         265,109,502   312,580,095    47,470,594   f W95 Extended (LBA)
/dev/sda5         307,054,592   309,123,071     2,068,480  82 Linux swap / Solaris
/dev/sda6         309,129,216   312,580,095     3,450,880  82 Linux swap / Solaris
/dev/sda7         265,109,504   307,052,543    41,943,040  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        9488F66B88F64B6E                       ntfs       System Reserved
/dev/sda2        1A2AFAF42AFACBAF                       ntfs       Windows 7
/dev/sda3        26681BC9681B96A1                       ntfs       Windows 8
/dev/sda5        3f0be784-2e3e-45a4-85a0-582420651790   swap       
/dev/sda6        b38b2f93-1b0a-446d-8b14-63ac5f20d527   swsuspend  
/dev/sda7        b3bc7269-6a16-49bc-b109-a71015ca5bab   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /tmp/BootInfo0/sda1      fuseblk    (ro,nosuid,nodev,allow_other,blksize=4096)
/dev/sda2        /media/Windows 7         fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda3        /media/Windows 8         fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda7        /                        ext4       (rw,errors=remount-ro,commit=0)


========================== sda1/grldr embedded menu: ===========================

--------------------------------------------------------------------------------

=============================== StdErr Messages: ===============================

/home/tristan/Desktop/boot_info_script.sh: line 1888: (  / 2 ) + 16 : syntax error: operand expected (error token is "/ 2 ) + 16 ")

```

---

### Post by hiever1 on 2011-09-21
I noticed that if I select Windows 7 from GRUB it will redirect me to Windows 8 and Windows 7 dual boot menu. How can I make Windows 8 have it's own entry?

---

### Post by oldfred on 2011-09-21
Is the boot script error why major portitions of the script are missing. From what is posted I do not see anything wrong, but it is missing almost all the partition detail information.

Do you have a grub4dos (grldr/grub.exe) as that is part of what line 1888 is trying to calculate?

---

### Post by Gremlinzzz on 2011-09-21
From what i been reading windows 8 will not dual boot with Linux.

[http://www.broadbandreports.com/forum/r26341356-Windows-8-Secure-Boot-Would-Exclude-Linux](http://www.broadbandreports.com/forum/r26341356-Windows-8-Secure-Boot-Would-Exclude-Linux)

[http://www.zdnet.com.au/windows-8-secure-boot-to-block-linux-339322781.htm](http://www.zdnet.com.au/windows-8-secure-boot-to-block-linux-339322781.htm)

---

### Post by oldfred on 2011-09-21
@Gremlinzzz
That is SecureBoot with UEFI which is still just a Microsoft proposal, OP is using standard BIOS to boot. It should be the same as two Win7 installs as far as booting goes, but I would like to see full boot script to confirm.

Second install of Windows litterally moves boot files to first install. Grub then cannot find any boot files in the second installs partition.

This primarily shows Vista, but Windows 7 boots like Vista except it usually has an additional hidden 100MB boot/recovery partition.
To get each MS to have its own boot loader make a primary partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

---

### Post by PRC09 on 2011-09-22
Just a little point of curiosity on Win8.I have installed the 64bit version on 2 different machines now,clean hard drives just so as not to mess with the current software on the machines.When I remove the Win8 drive and re-plugin the existing hard drive they will not boot,no errors or anything at all,the machine just sits there with the fans running,and the monitor is active but no bios post screen.The only way I have found to make it boot properly again is to reset the bios back to factory defaults(power down,remove the battery,use the reset jumper) and then the machine reboots as normal. 2 different desktops 1 intel and 1 amd both dual core 4gb ram. I havent tried dual boot yet but I think there is already something going on with the bios....maybe......

---

### Post by Mark Phelps on 2011-09-22
> **hiever1 said:**
> I noticed that if I select Windows 7 from GRUB it will redirect me to Windows 8 and Windows 7 dual boot menu. How can I make Windows 8 have it's own entry?

You would need to modify the Win7 BCD to remove the Win8 entry, and then, you would have to install the Win8 boot loader to the Win8 OS partition.  Once that was done, you would be able to run "sudo update-grub" and it should find BOTH Windows boot loaders, adding entries for both to the menu.

---

### Post by dcstar on 2011-09-22
> **PRC09 said:**
> Just a little point of curiosity on Win8.I have installed the 64bit version on 2 different machines now,clean hard drives just so as not to mess with the current software on the machines.When I remove the Win8 drive and re-plugin the existing hard drive they will not boot,no errors or anything at all,the machine just sits there with the fans running,and the monitor is active but no bios post screen.The only way I have found to make it boot properly again is to reset the bios back to factory defaults(power down,remove the battery,use the reset jumper) and then the machine reboots as normal. 2 different desktops 1 intel and 1 amd both dual core 4gb ram. I havent tried dual boot yet but I think there is already something going on with the bios....maybe......

I would suspect that Windows 8 is playing with the TPM/UEFI setup in the BIOS locking it to only boot itself. You may want to disable UEFI and see if it still occurs.

Also: [http://www.theregister.co.uk/2011/09/21/secure_boot_firmware_linux_exclusion_fears/](http://www.theregister.co.uk/2011/09/21/secure_boot_firmware_linux_exclusion_fears/)

---

### Post by hariks0 on 2011-10-09
> **Gremlinzzz said:**
> From what i been reading windows 8 will not dual boot with Linux.

[http://www.broadbandreports.com/forum/r26341356-Windows-8-Secure-Boot-Would-Exclude-Linux](http://www.broadbandreports.com/forum/r26341356-Windows-8-Secure-Boot-Would-Exclude-Linux)

[http://www.zdnet.com.au/windows-8-secure-boot-to-block-linux-339322781.htm](http://www.zdnet.com.au/windows-8-secure-boot-to-block-linux-339322781.htm)

Not true. It was there in the Grub after first installation. After a reinstallation, it is not appearing directly in Grub...

---

