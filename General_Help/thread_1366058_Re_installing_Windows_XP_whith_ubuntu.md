---
title: "Re installing Windows XP whith ubuntu"
date: 2009-12-28
forum: General Help
---

### Post by ZekeWild on 2009-12-28
Gday i Loaded my windows XP disc to install on my PC. currently running ubuntu
i went to install and it came up with: No system Pations were found setup is unable to continue.

anybody know how i can install it?

---

### Post by dcstar on 2009-12-28
> **ZekeWild said:**
> Gday i Loaded my windows XP disc to install on my PC. currently running ubuntu
i went to install and it came up with: No system Pations were found setup is unable to continue.

anybody know how i can install it?

Shrink you existing partition(s) to make space.

---

### Post by ZekeWild on 2009-12-28
Thanks but how do i do that? I am a Total Noob and don't know how.
thanks.

---

### Post by Sef on 2009-12-28
> Gday i Loaded my windows XP disc to install on my PC. currently running ubuntu
i went to install and it came up with: No system Pations were found setup is unable to continue.

First >  Applications > Accessories > Terminal

Second > Copy and paste this command in the terminal: ```
sudo fdisk -l
```

Third > Copy and paste the results.

---

### Post by plusnplus on 2009-12-28
Hi ZekeWild,
it is more easy to intall ubuntu/ linux in pc run windows, then install windows in pc run ubuntu/ linux.
in your case, your pc harddisk have not other partition beside ubuntu partition.
it is not easy to shrink your existing partition to make another partition.

Better back up all data in your ubuntu, format the harddisk and make two partition(1 for windows and 1 for ubuntu), install windows 1st then install ubuntu again.

---

### Post by ZekeWild on 2009-12-28
How can I format the disk C: now everythings backed up? thanks.

---

### Post by ZekeWild on 2009-12-28
Reply to Sef:

zeke@badsatan:~$ sudo fdisk -l
[sudo] password for zeke: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc49f680c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1019     8185086   12  Compaq diagnostics
/dev/sda2   *        1020       10688    77666242+   7  HPFS/NTFS
/dev/sda3           10689       19457    70436992+   c  W95 FAT32 (LBA)

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x39dadfc4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       10030    80565943+   7  HPFS/NTFS
/dev/sdb2           10031       19457    75722377+   5  Extended
/dev/sdb5           10031       19067    72589671   83  Linux
/dev/sdb6           19068       19457     3132643+  82  Linux swap / Solaris
zeke@badsatan:~$ Disk /dev/sda: 160.0 GB, 160041885696 bytes
No command 'Disk' found, did you mean:
 Command 'risk' from package 'xfrisk' (universe)
Disk: command not found
zeke@badsatan:~$ 255 heads, 63 sectors/track, 19457 cylinders

255: command not found
zeke@badsatan:~$ Units = cylinders of 16065 * 512 = 8225280 bytes
No command 'Units' found, did you mean:
 Command 'units' from package 'units' (universe)
Units: command not found
zeke@badsatan:~$ Disk identifier: 0xc49f680c
No command 'Disk' found, did you mean:
 Command 'risk' from package 'xfrisk' (universe)
Disk: command not found
zeke@badsatan:~$ 
zeke@badsatan:~$    Device Boot      Start         End      Blocks   Id  System
Device: command not found
zeke@badsatan:~$ /dev/sda1               1        1019     8185086   12  Compaq diagnostics
bash: /dev/sda1: Permission denied
zeke@badsatan:~$ /dev/sda2   *        1020       10688    77666242+   7  HPFS/NTFS
bash: /dev/sda2: Permission denied
zeke@badsatan:~$ /dev/sda3           10689       19457    70436992+   c  W95 FAT32 (LBA)
bash: syntax error near unexpected token `('
zeke@badsatan:~$ 
zeke@badsatan:~$ Disk /dev/sdb: 160.0 GB, 160041885696 bytes
No command 'Disk' found, did you mean:
 Command 'risk' from package 'xfrisk' (universe)
Disk: command not found
zeke@badsatan:~$ 255 heads, 63 sectors/track, 19457 cylinders
255: command not found
zeke@badsatan:~$ Units = cylinders of 16065 * 512 = 8225280 bytes
No command 'Units' found, did you mean:
 Command 'units' from package 'units' (universe)
Units: command not found
zeke@badsatan:~$ Disk identifier: 0x39dadfc4
No command 'Disk' found, did you mean:
 Command 'risk' from package 'xfrisk' (universe)
Disk: command not found
zeke@badsatan:~$ 
zeke@badsatan:~$    Device Boot      Start         End      Blocks   Id  System
Device: command not found
zeke@badsatan:~$ /dev/sdb1               1       10030    80565943+   7  HPFS/NTFS
bash: /dev/sdb1: Permission denied
zeke@badsatan:~$ /dev/sdb2           10031       19457    75722377+   5  Extended
bash: /dev/sdb2: Permission denied
zeke@badsatan:~$ /dev/sdb5           10031       19067    72589671   83  Linux
bash: /dev/sdb5: Permission denied
zeke@badsatan:~$ /dev/sdb6           19068       19457     3132643+  82  Linux swap / Solaris
bash: /dev/sdb6: Permission denied
zeke@badsatan:~$ 
zeke@badsatan:~$

Is this helpfull to anyone? can i Wipe one of my pations or Wipe my PC and start all over agaain without any Operating Systems and install windows from there? I Relly need to get this working as quick as i can
thanks.

---

### Post by ZekeWild on 2009-12-28
HOW THE F#$K DO YOU UNINSTALL F$#@ING FROM MY PC SO I CAN INSTALL F@#$ING WINDOWS!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!1
thanlx!

---

### Post by Admiral Yi on 2009-12-28
Whoa, calm down! Try this:

1) Boot to the CD you installed Ubuntu from 
2) Go to system>administration>Partition editor
3) When that comes up, you'll see a big bar which is the main partition. You will also see a tool called 'resize/move'.
4) Click on resize move and use it to drag the partition to make it smaller. Shrink it in half maybe?
5) Hit ok and wait till its done before switching off and removing the disk. 
6) Install windows. 
7) You will now not be able to boot to Ubuntu. Follow this guide to fix: [HTML]http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/[/HTML]

If you want to remove Ubuntu entirely, when you're on the partitoner just delete everything and create a new NTFS partition to install windows on. This will destroy all data, so back up anything important.

---

### Post by ZekeWild on 2009-12-28
Can't find my F#$%ing CD i installed Pation Editor but can't find it anyware Thankx.

---

### Post by proxess on 2009-12-28
With those kind of posts, don't expect help, but do expect a ban from the forums.

---

### Post by ZekeWild on 2009-12-28
Sorry about all that just i really need windows at the monemt and it's really anoying what do you segest i do to get indows installed;

---

### Post by Primefalcon on 2009-12-28
> **ZekeWild said:**
> Sorry about all that just i really need windows at the monemt and it's really anoying what do you segest i do to get indows installed;
Just keep your cool, people are really helpful here :-)

---

### Post by vamega on 2009-12-28
The screenshot doesnt seem to have any linux partitions (not ext2/3/4 partitions and no reiserfs). But your fdisk output seems to show that linux was installed on the secondary hard disk.

You said that you dont mind just wiping everything clean and starting from there. In which case you can just delete all the partitions you see in the partition manager, and when you next boot up from the WinXP disk you should have no problems.

If you'd like to keep ubuntu, and dual boot, then I'd say that one possible option is to have ubuntu on the secondary hard disk (/dev/sdb) and install windows on the primary (/dev/sda). So just delete everything you see that starts with /dev/sda

Do note that this will erase all data on those partitions, so please backup the data before doing this.

Vamega

---

### Post by ZekeWild on 2009-12-28
OK I've backed everything up; So when i delete all the partions (if they delete) Will my pc automaticly Reset or and when i turn it back on what will the steps be that I'll go though? i just insert my Windows XP disc and it'll run buy it'sself?
thankx.

---

### Post by vamega on 2009-12-28
If you want to wipe your hard disks clean, and install windows XP, here is what you can do.

If I remember you should be able to do everything from your windows XP cd.

1. Boot from the windows XP cd
2. At the partioning stage, just delete everything
3. Install Windows XP

However if you can't get that to work (I am not particularly familar with Windows XP's partition handling), then boot from a ubuntu live CD

1. Go to System -> Administration -> GParted
2. Delete all the partitions
3. Shut down computer and remove ubuntu CD
4. Boot from Windows XP cd and install windows XP

Vamega

---

### Post by ZekeWild on 2009-12-28
I am unable to delete: 
/dev/sda3  (some carkeys symbol) fat 32  /media/acerdata acerdata 67.17GIB 20.00GIB 41.18GIB lba


i click on this and press the delete key but nothing happends i could delete the others but even when i go right click delete delete is unavailable

how can i delete it?

---

### Post by ZekeWild on 2009-12-28
I managed to delete all partions, and then i Booted my windows XP disck and it would go through to starting windows xp and then it would get a Blue Screen with wite writting 
saying it had to shut down of it would be harmful to the computer and all this stuff like check for errors in the hard drive and stufff. i tried it like 70 times and it awlays came up with it.

---

### Post by deeboe33 on 2010-01-19
> **zekewild said:**
> can't find my f#$%ing cd i installed pation editor but can't find it anyware thankx.

1

---

### Post by pricetech on 2010-01-19
It sounds like your XP disk is a restore disk specific to your computer, lacking the necessary utilities to install on a blank drive.  Blame your manufacturer for that one.

You might contact them and see if they can send you a new disk that will work with a blank drive.  Make sure the drive is indeed blank though, or that may not help you either.

---

