---
title: "lost of 20G after resizing partition"
date: 2009-07-14
forum: General Help
---

### Post by captainCK on 2009-07-14
HI folks! it's my first post here!  i switched to linux dumped windows and installed Ubuntu 2 weeks ago ... and as a curious guy, i've tried a lot of stuff on my own, kind of liked the partition changing without the need to reboot...so  i've tried it a lot...

here is the situation... i first made it dual boot... then... deleted the windows XP partition after couple of days... then made a single partition out of windows and document partition combined. then resized, deleted the combined partition to resize the linux FS to the whole disk.
 
now that i have done that... the file system partition shows only 1.5 gig of free space... and its supossed to use only about 6Gigs

here is the fdisk -l

Disk /dev/sda: 30 GB, 30737871360 bytes
255 heads, 63 sectors/track, 3737 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System 
/dev/sda3               1         973     7807590   83  Linux
/dev/sda4            3585        3737     1220940   82  Linux swap

...missing 974 to 3584

and the df -h

Sys. de fich.            Tail. Occ. Disp. %Occ. Monté sur
/dev/sda3             7,4G  5,5G  1,5G  79% /
tmpfs                 375M     0  375M   0% /lib/init/rw
varrun                375M  216K  375M   1% /var/run
varlock               375M     0  375M   0% /var/lock
udev                  375M  140K  375M   1% /dev
tmpfs                 375M   88K  375M   1% /dev/shm
lrm                   375M  2,2M  373M   1% /lib/modules/2.6.28-13-generic/volatile

Qparted see the disk as full but if i try reinstall from the live DVD the partition manager see the 6Gig total usage

i guess i should reinstall Ubuntu...giving the full disk but maybe you guys can surprise me with some  tricks. that show the system the real disk usage... a full reinstall might be exessive if a simple terminal command do the trick...thanks in advance folks!



Edit: 

Harddrive had bad sector... i changed my harddrive... everything is allright

---

