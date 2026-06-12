---
title: "Hard drive problems"
date: 2010-08-05
forum: General Help
---

### Post by Dracona on 2010-08-05
Hi everyone, i am trying to recover some files from a friends hard drive, but the OS ( Ubuntu 10.01 64bit ) don't show the drive at all.  I can find the drive in bios.

If anyone has any ideas i would love to hear them.
I am wondering myself if the drive is completely shot, but not totally sure.

it is a WD 3200JS hard drive

Thank you
Dracona

---

### Post by inameiname on 2010-08-05
Have you tried using Disc Utilty or Gparted to see if the drive is shown there? Or how about using a LiveCD and boot from it and see if it pops up? Sometimes, if something is up with my main hard drive, stuff that isn't seen through it is seen through a Live session for some reason. Just an option.

---

### Post by Deadite81 on 2010-08-05
[Parted Magic]("http://partedmagic.com/") is great for solving problems like this.  It's an awesome User Friendly boot disk, like live CD but much faster.  I would recommend checking it with Gparted, which you'll have to install if you haven't already.  However, I have encountered problems using Gparted while booted into my normal system when dealing with corrupted drives.  If you encounter this, I recommend using Gparted within Parted Magic.  I recently recovered several corrupted partitions, external and internal with the disk check functionality of Parted Magic.  Fsck simply wouldn't work in Ubuntu booted normally, but did in Parted Magic.

You should also make sure your friend hasn't messed with the [fstab]("https://help.ubuntu.com/community/Fstab") file.

Good Luck!

---

### Post by Dracona on 2010-08-06
thank you for your help, using Disk Utility, the hard drive in question shows up and lists the disk as healthy, only having one partition and is flagged as bootable.

the Drive would not show up in places/computer after booting from ubuntu live cd.
Using gparted this is the info given from the print command

(parted) print                                                            
Model: ATA WDC WD3200JS-60P (scsi)
Disk /dev/sdb: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

at the moment i am trying to recover any files on the drive using ddrescue,  it looks like it might be working, but wont know until process is over.

my friend told me this morning that he tried to install windows xp but it gave him a strange error. so i am asuming that the hard drive was formated when he attempted to install xp. hopefully i am able to recover the family photos on the drive for him. 

Thanks again for your help
dracona

---

### Post by dino99 on 2010-08-06
here are usefull tools: [http://www.cgsecurity.org/](http://www.cgsecurity.org/)

---

### Post by Dracona on 2010-08-06
I am wanting to put together a troubleshooting/repair cd, and these look like they will be a good start to it.
If you have any suggestions as to what might be good to keep handy please let me know.

---

