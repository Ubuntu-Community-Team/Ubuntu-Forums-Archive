---
title: "Uninstalling Lucid Lynx"
date: 2010-08-14
forum: General Help
---

### Post by KarmicKlot on 2010-08-14
After spending a week battling a whole raft of problems with Lucid Lynx not the least of which was inability to get a stable wireless connection, and deciding that the only way forward was to uninstall it and do a clean install of Karmic Koala, which had worked faultlessly, I was left with the problem of how to uninstall it from an Acer Laptop which was running dual boot with Windows Vista.
 
Here is how I did it.  Firstly I tried and failed to find any "uninstall" procedure within Ubuntu.
 
I booted the laptop into Vista, and downloaded Easy BCD from NeoSmart Technologies website [http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)  Running this free program gives the option to overwrite the MBR (Master Boot Record).  This effectively either removes or bypasses GRUB so that the computer will boot straight into Windows.
 
I then used EASEUS Partition Manager (also a free download) to delete both of the non NTFS partitions that Linux had created, and wipe all data from them.  This is a slow process but gives thorough removal and ensures that the resultant "unallocated space" on the hard disk is free from data that could interfere with any new installation.
 
After this the laptop boots straight into Windows, and is ready for a clean install of Karmic Koala.

---

### Post by blazemore on 2010-08-14
Thanks for this information; I'm sure this will be useful for people in your situation.

Really, you can't "Uninstall" Ubuntu or any operating system because that's just not the way these things work. If you want to try out Ubuntu in a safe manner in the future, and you use Windows, I'd recommend the "Wubi" tool that comes on the CD.

Just put the CD in the drive while you're in Windows and follow the prompts. If you want to uninstall it you can do so through Windows' "Add/Remove Programs" functionality.

---

### Post by NCLI on 2010-08-14
You would probably have saved a lot of time by simply booting the Karmic livecd, firing up gparted to remove Lucid's "/" partition, ahere the operating system is, then installing Karmic side-by-side with Windows.

That way, you'd only have to use one cd, and save a lot of rebboting and research.

Lastly, operating systems don't come with an "uninstall button," since it would basically amount to wiping the partition the OS resides on, and be quite superfluous.

---

### Post by KarmicKlot on 2010-08-18
I just tried that on another laptop (a very old one that I want to use purely for Windows XP.  Deleted the Ubuntu partitions, and ended up with a dead computer which would not boot.  GRUB appeared to be looking for a non existant partition.  To get it going I am having to make a bootable CD with an MBR fix on it.

---

### Post by blazemore on 2010-08-18
> **KarmicKlot said:**
> I just tried that on another laptop (a very old one that I want to use purely for Windows XP.  Deleted the Ubuntu partitions, and ended up with a dead computer which would not boot.  GRUB appeared to be looking for a non existant partition.  To get it going I am having to make a bootable CD with an MBR fix on it.

You can do that, or you can use the Windows CD.

However, you're making it sound like some kind of fault in Ubuntu, whereas actually it's just a fundamental property of operating systems.

---

