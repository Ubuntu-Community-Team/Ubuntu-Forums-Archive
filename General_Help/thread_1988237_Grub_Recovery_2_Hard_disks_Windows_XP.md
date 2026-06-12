---
title: "Grub Recovery 2 Hard disks Windows XP"
date: 2012-05-27
forum: General Help
---

### Post by GirishSharma on 2012-05-27
Hello,
 
PC is : P4 2GB RAM 2 HDDs 80 GB and 160 GB
 
On this my home PC earlier there was Ubuntu 11.04 LTS and Windows XP dual boot options were configured and running both OS.  Some reasons, I had to reinstall XP, so after it now I am not able to choose the OS menu as earlier i.e. I am not able to run Ubuntu 11.04.
 
I have 2 HDDs in which Windows and Ubuntu were installed.
 
After google, I found and tried below :
 
I boot pc from 10.04 LTS CD (I am not sure, I doing right or wrong for grub recovery of 11.04 from 10.04 CD).  It gave me two options: 1.Try Ubuntu 2.Install 10.04 LTS.  So, I choose 1st Option i.e. Try Ubuntu to get the terminal windows.  In the terminal I did :
 
sudo fdisk -l
It showed me in the first hard disk NTFS and Windows partition and in the 2nd HDD, Linux partition (I forgot to copy and paste those screens here; I you ask me I will provide in next post please).  Then;
 
sudo mount /dev/sdb1 /mnt <-- Because It is in 2nd HDD
 
sudo grub-install --root-directory=/mnt/ /dev/sdb  <-- In one of the thread of this forum I found that it should be --boot if It is 1.99 (Natty Narwhal for 11.04, but when I used --boot, it did not worked, it showed me help of grub command like that), anyway but It worked and gave me Installation complete, No Error reported.  Then,
 
sudo grub-install --recheck --root-directory=/mnt/ /dev/sdb
Worked fine, No error reported.
 
sudo reboot.
 
But, I am not able to get the OS options as it was earlier working.  Kindly tell me where I am missing, or how do I get already Installed 11.04 OS.
 
Regards
Girish Sharma

---

### Post by kc1di on 2012-05-27
you need to run 
```
sudo update-grub
```
Then reboot. 
you'll then find the linux is there.

---

### Post by GirishSharma on 2012-05-27
> **kc1di said:**
> you need to run 
```
sudo update-grub
```
Then reboot. 
you'll then find the linux is there.
 
Thanks for your reply. I am pasting the whole terminal window after update-grub, but no luck so far.
 
```

 
[SIZE=3][FONT=Times New Roman]To run a command as administrator (user "root"), use "sudo <command>".[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]See "man sudo_root" for details.[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]ubuntu@ubuntu:~$ sudo fdisk -l[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]Disk /dev/sda: 80.0 GB, 80026361856 bytes[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]255 heads, 63 sectors/track, 9729 cylinders[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Units = cylinders of 16065 * 512 = 8225280 bytes[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Sector size (logical/physical): 512 bytes / 512 bytes[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]I/O size (minimum/optimal): 512 bytes / 512 bytes[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Disk identifier: 0x000eaa82[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman] Device Boot      Start         End      Blocks   Id  System[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]/dev/sda2            2551        9728    57657285    f  W95 Ext'd (LBA)[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]/dev/sda5            2551        6374    30716248+   7  HPFS/NTFS[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]/dev/sda6            6375        9728    26940973+   7  HPFS/NTFS[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]Disk /dev/sdb: 160.0 GB, 160041885696 bytes[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]255 heads, 63 sectors/track, 19457 cylinders[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Units = cylinders of 16065 * 512 = 8225280 bytes[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Sector size (logical/physical): 512 bytes / 512 bytes[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]I/O size (minimum/optimal): 512 bytes / 512 bytes[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Disk identifier: 0x00025d03[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman] Device Boot      Start         End      Blocks   Id  System[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]/dev/sdb1               1       19197   154193920   83  Linux[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]/dev/sdb2           19197       19458     2094081    5  Extended[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]/dev/sdb5           19197       19458     2094080   82  Linux swap / Solaris[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]ubuntu@ubuntu:~$ sudo mount /dev/sdb1 /mnt[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/ /dev/sdb[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Installation finished. No error reported.[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]ubuntu@ubuntu:~$ sudo grub-install --recheck --root-directory=/mnt/ /dev/sdb[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]Installation finished. No error reported.[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]ubuntu@ubuntu:~$ sudo update-grub[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]ubuntu@ubuntu:~$ [/FONT][/SIZE]

```
 
Kindly tell me where I am missing. Thanks again for your participation in the thread.
 
Regards
Girish Sharma

---

### Post by kc1di on 2012-05-27
did you reboot after running updat-grub?

---

### Post by GirishSharma on 2012-05-27
> **kc1di said:**
> did you reboot after running updat-grub?
 
Yes please, after update-grub, I just said : sudo reboot, but no OS menu selection there and Windows XP started... :(
 
Thank you for your concern and continue reply.  Kindly tell me how do I get my earlier beautifully installed Ubuntu 11.04... I am missing that very much....:)
 
Regards
Girish Sharma

---

### Post by kc1di on 2012-05-27
I think the best way for you to got is boot repair 
you can find it here:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

good luck

---

### Post by GirishSharma on 2012-05-30
> **kc1di said:**
> I think the best way for you to got is boot repair 
you can find it here:
 
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
 
good luck
 
Thank you very much kc1di.  This worked and restored my ubuntu.
- I downloaded iso file, burnted on a blank cd.
- PC booted from the cd.
- It prompted me for ppa to install from internet, I did't have, even after saying yes it..
- After few seconds, it prompted me that is 160 GB HDD removable ?  I said No.
- Main menu appeared.  I clicked on 1st Option.
- After few seconds, it restored grub.
- Asked me for something like making a bootable disk (I am not rememberring what it was asking though, I just click on ok)
- PC rebooted (CD was in the ROM).
- Halted for taking CD and close the ROM door.
- Bingo ! I got the OS selection menu, checked that my 11.04 Natty Narwhal is working or not... it is working just like previously.
 
Thanks to you and Boot-Repair Team.
 
Best Regards
Girish Sharma

---

