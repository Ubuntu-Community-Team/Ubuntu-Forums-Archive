---
title: "How to triple boot????"
date: 2009-11-18
forum: General Help
---

### Post by McMichael96 on 2009-11-18
How can I triple boot Windows Vista, Ubuntu (My main OS) and Windows 7? I already am dual booting Vista and Ubuntu (Vista was installed first then Ubuntu) I want to add Windows 7 to my dual boot to make it a triple boot. Thanks!:D

---

### Post by oldfred on 2009-11-18
With Windows it is difficult to triple boot. You can only double, double boot. Windows will combine its bootloaders with another previous install of windows making the new install unbootable on its own. Windows uses the boot flag to know which partition to boot and loads everything from that partition then lets you choose.

I did see somewhere that if you turned off the boot flag before installing, the new install did not see the old install and did not combine boots. You then, from windows, could only boot one windows, but could then set grub up to boot both separately. I do not know for sure if that works or not.

Windows still needs to be on a primary partition. I have seen where the second install of windows is in an extended partiton but because of the combined boot the boot is still from the version in a primary partition. The extended version would never be bootable on its own.

Of course you will still have to plan on reinstalling grub to the MBR as windows will overwrite that.

Vista and Win7 copies boot manager to one 
[http://members.iinet.net/~herman546/p15.html#BOOTMGR_is_missing](http://members.iinet.net/~herman546/p15.html#BOOTMGR_is_missing)
Moral of the story - look on other NTFS partitions for the missing bootmgr and Boot directory.

[http://ubuntuforums.org/showthread.php?t=1279218&highlight=booting+MS+products](http://ubuntuforums.org/showthread.php?t=1279218&highlight=booting+MS+products)
louieb's suggestion:
Just a note about dual booting 2 MS products. When you install the 2nd one - the installer will put its boot loader in the partition with the boot flag on (usually the partition holding the 1st MS product). And the 2nd product can only be booted thru the boot loader in the 1st product.

---

