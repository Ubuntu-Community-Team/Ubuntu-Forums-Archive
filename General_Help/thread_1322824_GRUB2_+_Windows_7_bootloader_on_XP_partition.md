---
title: "GRUB2 + Windows 7 bootloader on XP partition"
date: 2009-11-11
forum: General Help
---

### Post by Shne on 2009-11-11
I have Ubuntu Karmic (64bit on ext4), Windows 7 (64bit) and Windows XP (32bit) installed on same disk, using GRUB2 to dualboot.
I want to remove the XP partition but the Windows 7 bootloader is apparently on that partition. GRUB2's entry is "Windows 7 Loader (on /dev/sda3)" and sda3 is the XP partition. 
I'm afraid that if I remove the XP partition I will lose the Windows 7 bootlader and won't be able to boot Windows 7 and from what I can read, reinstalling the Windows 7 bootlader and then GRUB2 is not an easy task.

So my question is: What is the easiest way of removing the XP partition without losing ubuntu or windows 7?
Does the bootloader on the XP partition merely redirect to a bootloader on the windows 7 partition or will windows 7 be left unbootable without the bootloader on the XP partition?
If the bootloader on the XP partition merely redirects, how do I make GRUB2 see the bootloader on the Windows 7 partition?


sidenote: I can't even boot Windows XP, after choosing Windows 7 Loader in GRUB2 and then "Older windows operating system" in the Windows 7 loader, it says it can't boot because of missing or damaged "windows\system32\ntoskrnl.exe".

---

### Post by Giblet5 on 2009-11-11
This is Microsoft's way of telling you where you want to go today. Smile and be glad that no Fanboyz have shown up to beat you for installing Ubuntu on their Windows PC. ;)

This is what happens when you install two Windows versions on the same system: they provide a messed-up way of boot selection...

Where did Windows 7 install? Is it ```
D:\Windows
```

If so, you must either keep XP installed or wipe out XP AND Win7 and reinstall Win7.

--

For future reference, if you want to install multiple copies of Windows, it is best to use linux to hide the other Windows partitions before attempting to install a new one.

You can do this by editing the partition that old windows is installed on, and changing the filesystem type to ext3 (type = 83). That doesn't really change the filesystem - it just makes Windows think it can't read it: Windows is 250,000 volts of dumb.

Install the new Windows.

Reboot and fix your grub MBR after you set that other Windows partition back to type 7 (NTFS).

That yields systems like this which can boot many many OSes w/ no interdependency.

---

### Post by Shne on 2009-11-11
> **giblet5 said:**
> where did windows 7 install? Is it ```
d:\windows
```

if so, you must either keep xp installed or wipe out xp and win7 and reinstall win7.
I'm not completely sure what you mean...
Windows 7 has assigned drive letter C: to the partition it is installed on, and some other letter (can't recall what it is right now and I don't see how it can matter) to the Windows XP partition.
I can't boot Windows XP, so I don't know what letter, if any, it has assigned the Windows 7 partition. It's own drive letter is C:.

I still don't understand what your point exactly is..

I didn't do any sort of upgrade (if that's even possible on Windows), 7 and XP are on different primary partitions.

---

### Post by Giblet5 on 2009-11-11
If Windows 7 thinks it's installed on C, then you should be able to easily test a "pretend" removal of XP:

Boot into linux, open a terminal window and use fdisk to set the XP partition's type to 83 (ext3). That will hide it from update-grub and from Win7.

Let's say XP is installed on /dev/sda1 (don't even try this if you don't understand IDE disk partitioning, btw)

```
sudo fdisk /dev/sda

The number of cylinders for this disk is set to 60801.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): t
Partition number (1-4): 1
Hex code (type L to list codes): 83
Command (m for help): w
```

Now you must rewrite the grub menu.

```
sudo update-grub
sudo grub-install /dev/sda
```

Now reboot and verify that Win7 boots correctly.

If it doesn't, then you either have to remove the XP partition and reinstall Win7, or you 'll just have to live with the dead XP partition.

To set that now hidden XP drive back to XP:
```
sudo fdisk /dev/sda

The number of cylinders for this disk is set to 60801.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): t
Partition number (1-4): 1
Hex code (type L to list codes): 7
Command (m for help): w
```

Now you must rewrite the grub menu.

```
sudo update-grub
sudo grub-install /dev/sda
```

---

### Post by Shne on 2009-11-11
well, I think I understand what you mean now.

But when I try to run update-grub (without sudo, without having done anything else yet, just to check that I have it installed) it says:

```
No command 'update-grup' found, did you mean:
 Command 'update-grub' from package 'grub-efi-amd64' (universe)
 Command 'update-grub' from package 'grub-efi-ia32' (universe)
 Command 'update-grub' from package 'grub-coreboot' (universe)
 Command 'update-grub' from package 'grub-ieee1275' (universe)
 Command 'update-grub' from package 'grub' (main)
 Command 'update-grub' from package 'grub-pc' (main)
update-grup: command not found
```
The only one of those packages I have installed is 'grub-pc'. why doesn't it automatically select that? and how can I make it use it? (if that's what I should do)

---

### Post by Shne on 2009-12-18
Okay, since I didn't get a reply last time, I never got around to actually testing it.
I tried it now and changing the type of the partition apparently didn't hide it from GRUB2. It still found a windows bootloader on /dev/sda3 (which is the XP partition).
So, looking at the Disk Utility in ubuntu, I saw that the XP partition had a "bootable" checkbox checked, and the Win7 partition had it unchecked. So I figured I could change those 2 and see if grub still saw a loader on sda3.
Removing the check on the xp partition went fine, but checking it on the win7 partition gave an error I can't remember what exactly was. It was a rather long message, but what seemed the faulty part of it was something like "ugh, offset or size changed". It kept the change I made, though, and gave the error again when I checked and unchecked it again and again. So I figured it was fine and just a weird error that was nothing to worry about. I think I was wrong.
grub still finds the windows 7 loader on sda3, but when I try to load windows 7 using it, it says the device couldn't be contacted (or something similar) and it was probably due to some recent software change.
And Ubuntu doesn't list the win7 partition. gParted can't recognize the filesystem. Disk Utitlity says "Unrecognized, Unknown or Unused".

tl;dr: I apparently busted my windows 7 partition by changing the bootable flag of it.

Any idea how I can fix this without reinstalling Windows 7 and GRUB2?

---

### Post by boytoreckonwith on 2009-12-29
I had pretty much the exact same problem. Check here: [http://ubuntuforums.org/showthread.php?t=1359474](http://ubuntuforums.org/showthread.php?t=1359474)
I found an easy fix. Copy the /Boot folder and bootmgr file from the xp partition to the windows 7 partition. Then delete them from the xp partition. Then from terminal run *sudo update-grub2*. You should see it update, and actually should find xp AND windows 7 boot loader. You can then delete the xp partition (and update grub2 again). You WILL have to edit the bootmgr from windows 7 to get rid of the xp option or to set time to 0 so it will go straight to windows 7. I had a post for this whole thing...You can look for it or google *edit bootmgr*

Hope this helps.

---

### Post by Shne on 2009-12-29
Well, that's great and all. And I'm marking this thread as solved now that there's apparently a usable answer.

But I ended up wiping the Windows 7 and XP partitions and reinstalling Windows 7 and GRUB2.

---

