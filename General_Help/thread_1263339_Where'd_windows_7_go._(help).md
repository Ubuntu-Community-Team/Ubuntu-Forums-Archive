---
title: "Where'd windows 7 go. (help)"
date: 2009-09-10
forum: General Help
---

### Post by twavisdegwet on 2009-09-10
So i installed ubuntu on a seperate partition. I already had windows 7 rc1 installed at the time. Everything worked good and i could boot through grub. However later i had to reinstall ubuntu and now windows7 no longer appears in grub. i do know it is there though as the drive is mounted at the files are still in tact.  
My fdisk-l or w/e
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
240 heads, 63 sectors/track, 20673 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *          14       19633   148316446+   7  HPFS/NTFS
/dev/sda3           19634       20673     7862400    5  Extended
/dev/sda5           19634       20643     7635568+  83  Linux
/dev/sda6           20644       20673      226768+  82  Linux swap / Solaris

```So with this information can someone tell me what i need to add to my 
/boot/grub/menu.lst because i'm at a loss here. 
my ubuntu version is 9.04 (januty)
MY windows 7 version is rc1 if at all relevent.

---

### Post by k956411 on 2009-09-10
when you re-installed did it ask if you wanted to keep your menu.lst file at any time?

if it did, next time choose yes. this time it appears you have got rid of the old one that had your windows reference in it. hopefully adding it back into the file will solve the problem

this is what is in mine at the moment:

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

my windows is on sda1 which in windows is the first disk and first partition hence the hd0,0 above (in this notation numbering begins at zero)

yours appears to be sda2 so it would be hd0,1 (you don't have an sda1 listed for some reason,i just hope you haven't damaged something there)

i kept all the stuff around it too so you can just copy and paste, then just update the hd0,0 to 1 and change the name of the windows.

hope it fixes your problem

---

### Post by twavisdegwet on 2009-09-11
After Following your guide it finally booted to the prooper thing. from there i got a bootmgr error fixed it with the windws7 repair disk. Now i am properly dual booted and good to go THANKS

---

