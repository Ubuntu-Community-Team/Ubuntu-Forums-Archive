---
title: "Cant boot to windows 7"
date: 2009-12-29
forum: General Help
---

### Post by Darkz_Soul on 2009-12-29
I hate to say it but there is some software that i need that only windows can use.. Before i had had a dual boot working just fine, something happened and my mbr got screwed up and after some tedious work i got ubuntu booting. Now i want to boot to windows 7 but it wont i have used all of windows 7 repair tools, to my knowledge, to no avail so i have concluded that grub. If i select windows it just reloads grub in a cycle i will post my fstab file to help but with the new revision of grub im at a lost on its files that are you guys might need. I know it might not do much good but its all i know were to look

Here is the fstab if i need to add something let me know. BTW the windows partition is sda1 i can get the UUID but i don't think it will help

------------------------------

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=765cb870-1f82-457e-94ae-3326c1315690 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=10b01184-bf23-4f98-8501-9daaecd02f7c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#windows backup partition
UUID=637d7df3-a2ae-4a1c-99ec-7376e4f93f94	/media/winbackup	ext4	errors=remount-ro 0	1
#/dev/sda3	/media/"Windows BACKUP"	ext4	defaults	0	1

----------------------------

Please let me know of any files needed to clear this up.. i really don't want to sound like im begging but i don't want to reinstall windows again so just let me know

---

### Post by nikhilbhardwaj on 2009-12-30
your best bet would be
to use the windows7 install disk to reset the boot sector
and then install grub using a live cd

---

### Post by Darkz_Soul on 2009-12-30
> **nikhilbhardwaj said:**
> your best bet would be
to use the windows7 install disk to reset the boot sector
and then install grub using a live cd
Windows doesn't exactly offer that as an option... ill take a look around. I was afraid of having to redo grub.. but i guess that is what ill have to do

---

### Post by simonday99 on 2009-12-30
i too got the same problem,
pease help me

---

### Post by Darkz_Soul on 2009-12-30
I've given up on windows so I'm working on fixinh my HDD and making Kubuntu my true primary operating system and making windows the afterthought... Using windows tools i ended up breaking my mbr and it still wouldn't boot even with a clean install. So I've concluded that windows is lame... i'm going to install it once i get my other version of KDE running as smooth as this one... and then i get to deal with this crap again :(. I'll post any more problems i run into with this dual boot but i doubt i will again

---

### Post by Leppie on 2009-12-30
please [download and run meierfra's script]("http://sourceforge.net/projects/bootinfoscript/") and post the generated RESULTS.txt.

---

### Post by Mark Phelps on 2009-12-30
> **Darkz_Soul said:**
> Windows doesn't exactly offer that as an option... 

Actually, YES IT DOES!  

Win7, unlike it's predecessor Vista, provides a builtin capability to create and burn a Win7 Repair CD. 

This was provided by default by MS to deal specifically with the situation that OEM's generally do not supply a repair CD, only a restore CD -- which often simply wipes and restores the entire hard drive.

Also, if you'd done some searching, you would have discovered that the NeoSmart Technology forums offer the ability to download an ISO of an already created Win7 Repair CD -- both in 32-bit and 64-bit flavors.

---

### Post by Darkz_Soul on 2010-01-12
> **Mark Phelps said:**
> Actually, YES IT DOES!  

Win7, unlike it's predecessor Vista, provides a builtin capability to create and burn a Win7 Repair CD. 

This was provided by default by MS to deal specifically with the situation that OEM's generally do not supply a repair CD, only a restore CD -- which often simply wipes and restores the entire hard drive.

Also, if you'd done some searching, you would have discovered that the NeoSmart Technology forums offer the ability to download an ISO of an already created Win7 Repair CD -- both in 32-bit and 64-bit flavors.
I didn't have much luck with windows options and at the time lacked the abiltity to get into windows. While a repair cd would have been very nice i fixed the problem by reninstalling windows to a different location on the HDD and then reinstalling grub. That was what worked. I'm not sure as to why win7 was unable to get the MBR and boot loader set up properly but as of now i have windows working and some missing driver for Kubuntu but that is really easy to fix when at least on operating system as quick access to the internet

---

