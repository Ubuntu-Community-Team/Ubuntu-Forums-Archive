---
title: "Vanishing ext4 Partition"
date: 2011-11-01
forum: General Help
---

### Post by monkeyman512 on 2011-11-01
First, my apology if this is posted in the wrong place.
My problem is that I have an Ubuntu Desktop machine with 3 hard drives. Last night I moved all the parts from an old crap case to a nice new one. Everything should have been exactly the same, minus a PCI raid card that was not being used. I was able to boot up no problem except:

80GB HDD with Ubuntu install – works fine
500GB HDD with movies – works fine
1TB HDD with shows – is recognized but now doesn’t show a partition.

I have no idea why this happened or how to fix it. If you need more information just tell me how to get it and I will. I have been running this machine as a simple NAS for a couple years so I have basic Linux knowledge, but for the purposes of instructions please consider me to be a noob.

---

### Post by WasMeHere on 2011-11-01
Hi monkeyman512,

Is *everything* except the RAID card the same? Even the power supply and the cables? And the order of the cables and cards?

Could you install the RAID card just for the sake of trying to have everything exactly the same (electrically)?

Have fun finding out :-)
Olle

---

### Post by monkeyman512 on 2011-11-01
I will add in the Raid card when I get home. I am using the same cables and power supply, but the cable to device to port number may not be exactly the same. The HDD does show up in Ubuntu, but is says that the entire drive is unallocated in the partition program that comes with Ubuntu.

If there any other information I should collect before responding if this doesn’t fix the problem?

---

### Post by WasMeHere on 2011-11-01
What about the big drive that is not recognized? Is it an internal or external drive? If external, can you change between different connectors (e.g. between different USB slots, and is there external power to that drive or power via USB)?

---

### Post by monkeyman512 on 2011-11-01
All the hard drives are internal. The big drive is WD Caviar Black 1TB, around 1-2 years old. 

I can see the drive in Ubuntu, the SMART status says everything is good, but the ext4 partition doesn’t show up. The drive says it is completely unallocated in the partition program.

---

### Post by WasMeHere on 2011-11-01
The partition might be damaged. It is *very* unlikely that it would happen when you moved it, but it is possible. There are tools for such problems.

*gpart* and *testdisk* attempt to identify information of the partition(s) if the partition table is damaged. Read about it on the internet and download the tools (or a live disk with several such tools)!

---

### Post by monkeyman512 on 2011-11-02
This should make things good and confusing. I unhooked my 80GB drive and my 500GB drive, leaving only my 1TB and a CDROM. I then booted off my Ubuntu 10.10 live disk and the 1TB showed up just fine. Then I hook up my 80GB with Ubuntu 11.10 and start up and the drive shows up as unallocated.

So I know the information is still in good shape, but why does it not show up on my install?

---

### Post by WasMeHere on 2011-11-02
> **monkeyman512 said:**
> ... So I know the information is still in good shape, but why does it not show up on my install?

I'm glad on your behalf, that the data are there :-)

Now why:

- How do you mount the disk in the installed environment? Is there a line in your **/etc/fstab** file for it, or will it be mounted when you try to 'go there' with your file browser?

Is this correct: It works in a live 'vanilla' Ubuntu 10.10 but it does not work in an installed 'vanilla' Ubuntu 11.10? No Kubuntu, Xubuntu, Lubuntu ...)?

Did you upgrade to 11.10 or did you do a fresh install? Are you sure that the big disk worked with 11.10 before swapping to the new computer case?

It would be valuable if you post the content of the file
**/etc/fstab** from both systems (the live and the installed one).

Also, please post the output of the following commands from both systems (the live and the installed one).
```

sudo fdisk -lu
df
sudo blkid
``` With that information we might find some reason why the big one is not recognized by the installed system.

---

### Post by monkeyman512 on 2011-11-02
I normally have a lines in /etc/fstab to mount the HDD for both the 500GB and 1TB drives. I have this drives shared out via Samba as my NAS for my windows machines.

The live disk is Vanilla Ubuntu 64bit. The live disk I am using is the same disk I did the original install on this machine with.

I had 11.?? when first ran into the problem with the HDD not showing up. It was the suggested upgrade before 11.10 that had the task bar on the side. After I ran into the problem with the HDD I upgraded to 11.10 in a hope it would magically fix it, it does not appear to have made any difference for better or worse.



Installed on HDD, Ubuntu 11.10, was upgraded from original install from 10.10 over multiple upgrades
dustin@server:~$ sudo fdisk -lu
[sudo] password for dustin: 

Disk /dev/sda: 80.0 GB, 80025280000 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156299375 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x05050505

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   150304139    75152038+  83  Linux
/dev/sda2       150304201   156296384     2996092    5  Extended
/dev/sda5       150304203   156296384     2996091   82  Linux swap / Solaris

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1   976773167   488386583+  ee  GPT

WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdc: 1000.2 GB, 1000203804160 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953523055 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1  1953525167   976762583+  ee  GPT
dustin@server:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             73971580  29437660  40776320  42% /
udev                   2019956        12   2019944   1% /dev
tmpfs                   811148      1100    810048   1% /run
none                      5120         0      5120   0% /run/lock
none                   2027864      1292   2026572   1% /run/shm
/dev/sdb1            480719068 199766400 256533468  44% /media/Movies
dustin@server:~$ sudo blkid
/dev/sda1: UUID="d1119b66-417d-483b-9b26-8f53844ef93b" TYPE="ext4" 
/dev/sda5: UUID="e04159da-db6f-40ec-9a5e-5182dd735bcf" TYPE="swap" 
/dev/sdb1: UUID="0605faaf-57f0-4a37-ba1b-ef957757d329" TYPE="ext3" 
dustin@server:~$
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc  nodev,noexec,nosuid            0  0  
# / was on /dev/sda1 during installation
UUID=d1119b66-417d-483b-9b26-8f53844ef93b  /              ext4  errors=remount-ro              0  1  
# swap was on /dev/sda5 during installation
UUID=e04159da-db6f-40ec-9a5e-5182dd735bcf  none           swap  sw                             0  0  

# 1tb hdd
UUID=26e74049-fba5-4f02-ac0e-9f94619885fb /media/Shows   ext4  defaults                    0  2
# 500gb hdd  
UUID=0605faaf-57f0-4a37-ba1b-ef957757d329 /media/Movies    ext3  defaults                    0  2















Live Disk, Ubuntu 10.10 64bit, This is the disk I originally installed from
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x05050505

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   150304139    75152038+  83  Linux
/dev/sda2       150304201   156296384     2996092    5  Extended
/dev/sda5       150304203   156296384     2996091   82  Linux swap / Solaris

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1   976773167   488386583+  ee  GPT

WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1  1953525167   976762583+  ee  GPT
ubuntu@ubuntu:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
aufs                   2028100     27624   2000476   2% /
none                   2020856       272   2020584   1% /dev
/dev/sr0                711674    711674         0 100% /cdrom
/dev/loop0              672384    672384         0 100% /rofs
none                   2028100       104   2027996   1% /dev/shm
tmpfs                  2028100        20   2028080   1% /tmp
none                   2028100        88   2028012   1% /var/run
none                   2028100         4   2028096   1% /var/lock
ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="d1119b66-417d-483b-9b26-8f53844ef93b" TYPE="ext4" 
/dev/sda5: UUID="e04159da-db6f-40ec-9a5e-5182dd735bcf" TYPE="swap" 
/dev/sdb1: UUID="0605faaf-57f0-4a37-ba1b-ef957757d329" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc1: UUID="9584e52a-fa6d-4bcc-9d96-9a4256b87309" TYPE="ext4" 
ubuntu@ubuntu:~$
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda5 swap swap defaults 0 0

---

### Post by monkeyman512 on 2011-11-03
Now I am confused again. I now have access to the drive again. I have not tested if this is going to stick or not after a few reboots yet. 

SO CONFUSED! :confused:

---

### Post by WasMeHere on 2011-11-03
> **monkeyman512 said:**
> ...
# /etc/fstab: static file system information.
...
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc  nodev,noexec,nosuid            0  0  
# / was on /dev/sda1 during installation
UUID=d1119b66-417d-483b-9b26-8f53844ef93b  /              ext4  errors=remount-ro              0  1  
# swap was on /dev/sda5 during installation
UUID=e04159da-db6f-40ec-9a5e-5182dd735bcf  none           swap  sw                             0  0  

# 1tb hdd
UUID=[COLOR="Red"]26e74049-fba5-4f02-ac0e-9f94619885fb[/COLOR] /media/Shows   ext4  defaults                    0  2
# 500gb hdd  
UUID=0605faaf-57f0-4a37-ba1b-ef957757d329 /media/Movies    ext3  defaults                    0  2
...
ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="d1119b66-417d-483b-9b26-8f53844ef93b" TYPE="ext4" 
/dev/sda5: UUID="e04159da-db6f-40ec-9a5e-5182dd735bcf" TYPE="swap" 
/dev/sdb1: UUID="0605faaf-57f0-4a37-ba1b-ef957757d329" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc1: [COLOR="Red"]UUID="9584e52a-fa6d-4bcc-9d96-9a4256b87309"[/COLOR] TYPE="ext4" 
ubuntu@ubuntu:~$
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda5 swap swap defaults 0 0
It seems that you try to mount a disk with another UUID in the fstab. That might be the problem. (Maybe you repartitioned or reformatted your disk?) What happens if you change the UUID in ***/etc/fstab***? It should be ***without*** double quotes **"** in fstab.

---

### Post by monkeyman512 on 2011-11-03
The incorrect UUID in the fstab file was my fault. I changed it at some point for some, probably stupid, reason. But the problem existed before and after that particular change.

But right now I have rebooted the computer a couple of times and I can mount the partition every time so far. Now I just need to fix the UUID in the fstab file and it should do it automatically at boot.

---

### Post by monkeyman512 on 2011-11-10
The problem was not going away so I took drastic steps that seem to have worked so far. I wiped my 80gb HDD and reinstalled the newest version of Ubuntu on it, moved all the data off my 1TB drive to other storage devices, wiped and reformatted it, then moved the data back onto the 1TB drive.

Fdisk. The cause of, and solution to, all of life's problems.

---

### Post by WasMeHere on 2011-11-11
You made quite an effort! I'm glad everything works now, and I hope and think it will continue :-)

Please mark the thread SOLVED

Olle

---

