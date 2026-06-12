---
title: "Help!!!"
date: 2010-08-01
forum: General Help
---

### Post by pompanojoe2 on 2010-08-01
I recently downloaded Ubuntu to an old Toshiba laptop. Initially I had both Ubuntu and Windows xp pro loaded but I decided to use the option of allowing Ububtu to delete Windows and be the only OS. At first it worked, everything booted right up, but I could not access internet. Someone told me to try using an ethernet cord for the first attempt to go online.
 
When I tried the next day all I can get is a message as follows once I turn on the laptop with or without the disc or ethernet cord.
 
GRUB loading
then the option to choose....
Use keys to choose OS, e to edit, or c for a command line
1. U.B Linux 2.6.37-14-generic
2. U.B. Linux 2.6.37-14-generic recovery mode
3. memory test memtest 86+
4. memory test memtest 86+ serial console 115200
 
no matter which I choose the next message is....
mount of filesystem failed
a maintenance shell will now be started
control d will terminate this shell and retry
root at ha12~#......or some kind of symbol at the end
 
I did the memory test properly, I think. But no matter what option I choose nothing happens but the above. Am i out of luck?
 
Thanks,
Joe

---

### Post by amite on 2010-08-01
it seems problem with grub,try this :


Try this one:
1.boot up from ubuntu Live CD.
2.open terminal
3. Then use these commands:

 	Code:
 	sudo fdisk -l 
You will see something like:

 	Quote:
 	 	 		 			 				   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13        9253    74218496    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3            9253       29126   159629400    5  Extended
Partition 3 does not end on cylinder boundary.
/dev/sda4           29127       30402    10240000    7  HPFS/NTFS
Partition 4 does not end on cylinder boundary.
/dev/sda5            9253       28923   157996408+  83  Linux
/dev/sda6           28923       29126     1632928+  82  Linux swap / Solaris 			 		 	 	 
that was mine filesystem, so, as you can see mine ubuntu installed on /dev/sda5

Get last number of your linux-sda.

after that try these commands:

 	Code:
 	sudo mount /dev/sdaX /mnt    (X is your sda number)
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo chroot /mnt
grub-install /dev/sda                (without number of sda) 
If you get an error with last command try that one:
 	Code:
 	grub-install --recheck /dev/sda 
And  after that just exit with these commands:
 	Code:
 	exit
sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /mnt
sudo reboot

---

### Post by pompanojoe2 on 2010-08-04
many thanks

---

