---
title: "Can't access cd/dvd in 10.04"
date: 2011-05-07
forum: General Help
---

### Post by perolad on 2011-05-07
I have a Dell Studio XPS that came preloaded with Ubuntu 10.04 LTS.  I messed up and killed the install to the point that it wouldn't boot.  So I downloaded the 10.04 .iso from [https://help.ubuntu.com/community](https://help.ubuntu.com/community) on my XP machine, burned it to CD, changed the bios in the Linux machine to boot from the CD, and it installed swimmingly, to wit:

perola@perola-desktop:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 10.04.2 LTS
Release:    10.04
Codename:    lucid

However, after resetting the bios to boot from the HD, which it does, I can no longer access or read the cd/dvd drive. It's obviously there according to these verifications:

perola@perola-desktop:~$ sudo mkdir /media/cdrom
mkdir: cannot create directory `/media/cdrom': File exists
perola@perola-desktop:~$ 

perola@perola-desktop:~$ grep -i dvd /var/log/messages
May  6 21:35:05 perola-desktop kernel: [    1.411547] ata2.00: ATAPI: HL-DT-ST DVD+/-RW GH50N, B104, max UDMA/100
May  6 21:35:05 perola-desktop kernel: [    1.440094] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVD+-RW GH50N    B104 PQ: 0 ANSI: 5
May  6 21:35:05 perola-desktop kernel: [    1.444103] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
May  6 22:33:27 perola-desktop kernel: [    1.403750] ata2.00: ATAPI: HL-DT-ST DVD+/-RW GH50N, B104, max UDMA/100
May  6 22:33:27 perola-desktop kernel: [    1.448806] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVD+-RW GH50N    B104 PQ: 0 ANSI: 5
May  6 22:33:27 perola-desktop kernel: [    1.469900] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
May  7 09:20:48 perola-desktop kernel: [    1.407080] ata2.00: ATAPI: HL-DT-ST DVD+/-RW GH50N, B104, max UDMA/100
May  7 09:20:48 perola-desktop kernel: [    1.436452] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVD+-RW GH50N    B104 PQ: 0 ANSI: 5
May  7 09:20:48 perola-desktop kernel: [    1.457556] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw 

Yet, couldn't access the drive, so I tried to mount it to no avail:

perola@perola-desktop:~$ sudo mkdir /media/cdrom; sudo mount /dev/cdrom/ /media/cdrom/
[sudo] password for perola: 
mount: /dev/sr0: unknown device
perola@perola-desktop:~$ ^C
perola@perola-desktop:~$ 

What do I do to make the system see and read this cd/dvd drive?

Thanks for any help...

Per

---

