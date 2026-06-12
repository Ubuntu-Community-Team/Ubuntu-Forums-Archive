---
title: "Creating Windows Bootable USB/CD/DVD on Ubuntu 9.10"
date: 2009-11-14
forum: General Help
---

### Post by gR15104 on 2009-11-14
[SIZE=2]hi, 

with ubuntu 9.10 installed on a system, i am curious to know how the following is done:


1. to create a Windows 7 bootable USB drive and [/SIZE][SIZE=2]Windows 7 bootable CD/DVD[/SIZE][SIZE=2] (when a Windows 7 DVD image file is available)



2. to create a Windows XP bootable USB drive [/SIZE][SIZE=2]and [/SIZE][SIZE=2]Windows XP bootable CD/DVD[/SIZE] [SIZE=2](when only a folder containing the OS setup and related files are available) 




Thank You

[/SIZE][gR15104]("http://ubuntuforums.org/member.php?u=955548")

---

### Post by Olav on 2009-11-14
1. I would start by trying to transfer the "boot image" from the DVD to the USB drive using the dd command. Haven't tried it yet though and I'm not sure USB drives boot exactly the same way as CDs or DVDs do.

2. You can't. Your folder will almost certainly not contain this mentioned boot image if the files were just copied from the disc.

Good luck.

---

