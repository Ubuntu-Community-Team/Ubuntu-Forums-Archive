---
title: "How do i add windows 7 to grub"
date: 2011-03-30
forum: General Help
---

### Post by oleink on 2011-03-30
Hey,
I had a successful windows and ubuntu setup earlier.  I have 2 hard drives.  1 with ubuntu and the other with windows.  The windows drive started failing so I had to return it.  It screwed grub up (as would be expected) and I then had just the ubuntu drive.  Got the windows drive back and installed.  Everything works, I can boot to either drive but I cannot access windows from grub.  If i change the boot order I can pick ubuntu or windows drive and boot that way but I'd rather have windows in grub

---

### Post by realzippy on 2011-03-30
Have you run
```
sudo update-grub
```  
?

---

### Post by Nickjpost on 2011-03-30
I found this was the closest to editing grub. Hope it helps or gives you a direction! Cheers
[http://boff.wordpress.com/2007/01/17/editing-bootgrubmenulst-to-change-the-grub-boot-menu/](http://boff.wordpress.com/2007/01/17/editing-bootgrubmenulst-to-change-the-grub-boot-menu/)

---

### Post by oleink on 2011-03-30
> **realzippy said:**
> Have you run
```
sudo update-grub
```  
?

Wow I feel stupid for not trying it.  I'm installing drivers for my windows machine right now so asap I will try this thanks

---

### Post by oleink on 2011-03-30
> **Nickjpost said:**
> I found this was the closest to editing grub. Hope it helps or gives you a direction! Cheers
[http://boff.wordpress.com/2007/01/17/editing-bootgrubmenulst-to-change-the-grub-boot-menu/](http://boff.wordpress.com/2007/01/17/editing-bootgrubmenulst-to-change-the-grub-boot-menu/)

This looks promising I'll give this a try too.  I'll definitely post before like 5 on whether this worked or not.  Thanks guys

---

### Post by drs305 on 2011-03-30
That link refers to the Grub legacy menu file, which is no longer used. 

If the update-grub command doesn't add Windows to your menu, it would probably be best to go to the following site and download the boot info script. Run it from the LiveCD and paste the contents of RESULTS.txt into a post. Once you have it pasted, highlight it and then press the # icon to place it within 'code' tags (for formatting).
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by oleink on 2011-03-30
> **drs305 said:**
> That link refers to the Grub legacy menu file, which is no longer used. 

If the update-grub command doesn't add Windows to your menu, it would probably be best to go to the following site and download the boot info script. Run it from the LiveCD and paste the contents of RESULTS.txt into a post. Once you have it pasted, highlight it and then press the # icon to place it within 'code' tags (for formatting).
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

Alright.  sudo update-grub worked and it recognized that windows exists but it does not show in the menu (I could fix it if there was menu.ls like there used to be)

---

### Post by oleink on 2011-03-30
Output of the update:

```
jordan@Heleo:~$ sudo update-grub
[sudo] password for jordan: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-28-generic
Found initrd image: /boot/initrd.img-2.6.35-28-generic
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Found Ubuntu 10.10 (10.10) on /dev/sdb6
done

```

---

### Post by drs305 on 2011-03-30
There are several reasons why it may not appear. If you post the RESULTS.txt we won't have to guess. If you can boot into Ubuntu normally, you don't have to use the LiveCD.

Added: I saw the previous post after I posted this. Most likely the Grub2 menu you are seeing is from the other Ubuntu installation. You can ensure the default Grub menu is from your currently running installation by running the following:
```
sudo grub-install /dev/sd**X**
```
with X being your drive letter (sd**a**, sd**b**, etc)

---

### Post by oleink on 2011-03-30
> **drs305 said:**
> That link refers to the Grub legacy menu file, which is no longer used. 

If the update-grub command doesn't add Windows to your menu, it would probably be best to go to the following site and download the boot info script. Run it from the LiveCD and paste the contents of RESULTS.txt into a post. Once you have it pasted, highlight it and then press the # icon to place it within 'code' tags (for formatting).
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848 1,953,521,663 1,953,314,816   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

```

---

### Post by drs305 on 2011-03-30
It appears not all of the RESULTS.txt got posted. But take a look at my previous post, which I edited to include the possibility of you having two Ubuntus. Boot into the one you normally use and whose Grub you want to use, then use the grub-install command (sudo grub-install /dev/sdb). 

As long as the computer boots your sdb drive first, you should be set. Running "update-grub" once more and watching the terminal to ensure it is found won't hurt anything.

---

### Post by oleink on 2011-03-30
> **drs305 said:**
> It appears not all of the RESULTS.txt got posted. But take a look at my previous post, which I edited to include the possibility of you having two Ubuntus. Boot into the one you normally use and whose Grub you want to use, then use the grub-install command (sudo grub-install /dev/sdb). 

As long as the computer boots your sdb drive first, you should be set. Running "update-grub" once more and watching the terminal to ensure it is found won't hurt anything.

Yeah I hd tried that but it told me it failed for some reason.  After I looked around a bit i found 

[http://erickoo.wordpress.com/tag/grub-2/]("http://erickoo.wordpress.com/tag/grub-2/")

I followed this and used the comment that had to do with a separate hd.  I then updated and it said "adding windows 7 loader."  It proceeded to say it finished.  I rebooted and found that it still did not appear.  After removing my Windows_11 file, I decided to take a break.  I rebooted an accidently booted to grub2 instead of to windows drive.  Somehow windows was there.  I can't explain it since the file was removed, but it is working fine now.  Thanks very much for your help

---

