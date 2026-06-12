---
title: "Windows dissapeared in grub."
date: 2009-08-20
forum: General Help
---

### Post by Johndo1 on 2009-08-20
I setup webmin on a desktop that I put a server on through ssh on my laptop. I shutdown my laptop and when I restarted it it seems that the grub has "erased" the windows section. 
Some info:
I have "cleaned the grub" before due to a clutter of boot options through the menu.lst file. Here is the kernal list at the end of the menu.lst file.

## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		befd5b44-91a8-4896-81e9-7efe635894b4
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=befd5b44-91a8-4896-81e9-7efe635894b4 ro splash quiet 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		befd5b44-91a8-4896-81e9-7efe635894b4
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=befd5b44-91a8-4896-81e9-7efe635894b4 ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, kernel 2.6.28-14-generic
uuid		befd5b44-91a8-4896-81e9-7efe635894b4
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=befd5b44-91a8-4896-81e9-7efe635894b4 ro splash quiet 
initrd		/boot/initrd.img-2.6.28-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid		befd5b44-91a8-4896-81e9-7efe635894b4
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=befd5b44-91a8-4896-81e9-7efe635894b4 ro  single
initrd		/boot/initrd.img-2.6.28-14-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		befd5b44-91a8-4896-81e9-7efe635894b4
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=befd5b44-91a8-4896-81e9-7efe635894b4 ro splash quiet 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		befd5b44-91a8-4896-81e9-7efe635894b4
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=befd5b44-91a8-4896-81e9-7efe635894b4 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

### END DEBIAN AUTOMAGIC KERNELS LIST



======Output to sudo fdisk -l==================================

doug@doug-laptop:~$ sudo fdisk -l
[sudo] password for doug: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x149f149f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12823   103000716    7  HPFS/NTFS
/dev/sda2           17962       19457    12016620    7  HPFS/NTFS
/dev/sda3           13086       17961    39166470   83  Linux
/dev/sda4           12824       13085     2104515    5  Extended

Partition table entries are not in disk order
doug@doug-laptop:~$ 


=========================================================
The NTFS system makes me suspicious that windows merged with the  ubuntu boot selection? 

Thanks and any help is appreciated...

---

### Post by egalvan on 2009-08-20
> **Johndo1 said:**
> I shutdown my laptop and when I restarted it it seems that the** grub has "erased" the windows section.** 
Some info:
I have **"cleaned the grub" through the menu.lst file.**


Under normal, day-to-day operations, GRUB does not write to or update the menu.lst.

menu.lst is updated when grub is updated,
or when a kernel update triggers a grub update.

It's more likely your having "cleaned the grub" ended up erasing the XP section.

Changing the "how many" option is any easy, safe way to limit the "clutter" in menu.lst

here is mine, set to value of 2:

```

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
#[COLOR="Red"] howmany=2[/COLOR]
```

> 
Here is the kernal list at the end of the menu.lst file.

## ## End Default Options ##
.
.
.
### END DEBIAN AUTOMAGIC KERNELS LIST


Indeed, there is no XP stanza.

> 
======Output to sudo fdisk -l==================================

doug@doug-laptop:~$ sudo fdisk -l
[sudo] password for doug: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x149f149f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12823   103000716    7  HPFS/NTFS
/dev/sda2           17962       19457    12016620    7  HPFS/NTFS
/dev/sda3           13086       17961    39166470   83  Linux
/dev/sda4           12824       13085     2104515    5  Extended

Partition table entries are not in disk order
doug@doug-laptop:~$ 


=========================================================
The NTFS system makes me suspicious that windows merged with the  ubuntu boot selection? 



Other than the partitions being in reverse order (not fatal),
the partition table looks OK.


you can try my XP stanza (the text headings been modified)
It SHOULD work for you as-is.

```

#--------------------------------------------------------------------------
# This entry automatically added by the Debian installer for a non-*nix OS
# on /dev/sda1

title		Other non-*nix OS's:
root

title		WinXP Pro
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

---

### Post by Johndo1 on 2009-08-20
Thank you very much. I have the option of selecting windows back (if thats a good thing)... I changed xp pro to vista and now it looks and works fine. 

When I changed this: 
## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# [COLOR="Red"]howmany=2[/COLOR]

The grub loader was still cluttered... Did I do something wrong or should I just delete the excess ubuntu options?


Anyways, I believe this occurred because I executed this command witch may have changed the grub because of a kernel update.  

sudo apt-get update

---

### Post by mcduck on 2009-08-20
Did you perhaps move your Windows entry inside the section marked as "debian automagic kernels list"?

If you do that, you will loose it on every kernel update. That section is re-created automatically based on default options and available kernels, and any extra entries will disappear. It actually even tells that in the menu.lst file itself, if you  read the comments.

Any extra entries should be put either above this line:
```

### BEGIN DEBIAN AUTOMAGIC KERNELS LIST
```

..or after this line:
```
### END DEBIAN AUTOMAGIC KERNELS LIST
```

What comes to entries for old kernels, my recommendation is to simply uninstall the old kernels with Synaptic. That will automatically remove their entries from the menu.lst as well. And of course free you some disk space (about 100MB per every kernel version, not much but I still have better use for it than storing old kernels I'm not using)

---

### Post by Johndo1 on 2009-08-20
I got it all fixed thanks to the forums... 
Here is a summery of what I did.


In order to add the windows option back I added this to the end of the menu.lst:
To find the menu.lst run this in the terminal:   [COLOR="Red"]gksu gedit /boot/grub/menu.lst [/COLOR]


#--------------------------------------------------------------------------
# This entry automatically added by the Debian installer for a non-*nix OS
# on /dev/sda1

title		Other Operating Systems:
root

title		Vista
root		(hd0,0)
savedefault
makeactive
chainloader	+1



Alright in order to fix clutter I did this and it worked great:

#1 Run this: 
gksu gedit /boot/grub/menu.lst

#2 Ctrl+find -  howmany

#3 Change howmany=all  to   howmany=1
This will change it so there is only
1 ubuntu and 1 ubuntu repair.

#4 save

#5 Run this command:
sudo update-grub

That should clear everything up...


Thank you for all of the help.
Now everything is back to normal.

---

