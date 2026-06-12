---
title: "Dual boot w/ 2 hd's (grub/mbr)"
date: 2006-02-06
forum: General Help
---

### Post by gatorbait on 2006-02-06
I wanted to use norton ghost to backup a windows installation onto an blank 100 gig external hard drive. So I used the ubuntu installation cd to partition the hd in this manner: 

35 gigs ext3, primary, mount @ root, for ubuntu with 1.5 gig swap partition
60 gigs fat32, logical

leaving the master laptop hard drive untouched.

After finished the partitioning, I exited the installation, booted into windows on the laptop's hard drive, and used norton to copy the C:\ drive into the newly created 65 gig FAT32 partition. So far so good.

Booted back to the install cd and selected the reserved ubuntu partition for installation. Now I've run into two problems:

1. after the ubuntu cd ejects to continue the installation, getting an error after the ubuntu bootup with a message along the lines of ~ "can't find the hardrive ( /media/sda2 ) dropping to a shell!" and goes to a command line interface without finishing the installation.

2. when the laptop is turned on grub loads, and you can boot into xp or the unfinished ubuntu installation. however, grub only appears when the external hd is plugged in! so without it the mbr on the laptop hd doesnt load to windows anymore. the external hd has to be plugged in...!

questions: why isnt ubuntu finishing the installation? and how can i set this dual boot system up so windows loads when the external hd is not plugged in, and grub/ubuntu can load only when the external hd is plugged in.

at the time of the installation it seemed grub would only be copied to the mbr  of the second hd, but apparently that was not the case.

tia!

I can get more specific error messages later tonight.

---

### Post by cotcot on 2006-02-06
I think that ubuntu cannot boot from an external hard drive without editing the kernel. I tried it several times without succes. Then i searched in forums and found a couple of treads explaining how to edit the kernel but that was more than i am used to.
I also read somewhere that it woull be possible with Dapper.

---

### Post by gatorbait on 2006-02-06
thanks for the reply. 

is it possible to recover the mbr as a pointer to windows without reformatting? bootcfg?
(so xp loads at boot without hd plugged in)

i guess i will be forced to reconsider the design of this system.

tia!

---

### Post by cotcot on 2006-02-07
Boot the installation XP CD and press R for recovery. 
Enter the command FIXMBR.
Exit and reboot without the installCD. It will boot directly into XP.
This restores the previous MBR.
It is also possible in DOS with FDISK/mbr.

---

