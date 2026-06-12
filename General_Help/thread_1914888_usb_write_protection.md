---
title: "usb write protection"
date: 2012-01-25
forum: General Help
---

### Post by maverick555 on 2012-01-25
I have a sandisk cruzer blade pen drive with some data inside it.
But,i cannot able to delete it.It says write protected.
I have done some command like dmsg which says write protection is on.
how to remove this ?:confused::confused:
please help.

---

### Post by ajgreeny on 2012-01-25
In what filesystem is it formatted?

With it attached and mounted, which it should be by default when you plug it in, run the command ```
sudo fdisk -l
```lower case L at the end, not 1, and report back the output from that command.

---

### Post by ElliotS on 2012-01-30
I'm having a similar problem, just started today, with an 8 GB Sandisk Cruzer Blade.

I removed the silly encryption software that came with it, and re-formatted to FAT32.
In the middle of copying files to it, it suddenly decided that it was write-protected.  I've done a little searching, and it seems problems with this drive and “sudden write-protection syndrome” are pretty common.  (I don't think you will find that term  online until now, but I'm going to popularize it until Sandisk pays attention.)  I've used the regular Cruzers with no trouble, including the ones with that nasty U3 system, which I've always managed to delete.
    
    Here's the output from sudo fdisk -l :     
    Disk /dev/sdg: 8004 MB, 8004304896 bytes      35 heads, 21 sectors/track, 21269 cylinders, total 15633408 sectors      Units = sectors of 1 * 512 = 512 bytes      Sector size (logical/physical): 512 bytes / 512 bytes      I/O size (minimum/optimal): 512 bytes / 512 bytes      Disk identifier: 0x00000000       
       Device Boot      Start         End      Blocks   Id  System      /dev/sdg1              32    15633407     7816688    b  W95 FAT32    
  
    I tried gparted, with no luck, as it reports the device as     mounted read-only, and refuses to touch it. 
    
    I cannot reformat in Windows 7 either, it reports the drive is write-protected.  
   
    I also tried some sort of HP low level format utility, no luck either. 
    
    I'll post a reply if I figure out or find something.  Otherwise, good advice would be appreciated.

Sorry if the formatting is a bit mangled, having some problems with the message editor.

---

