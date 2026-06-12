---
title: "unknown file system all over"
date: 2011-05-13
forum: General Help
---

### Post by Newbeatontheblock on 2011-05-13
Hi i have the following error : unknown filesystem. 
grub rescue after incorrect dual boot with Windows 7. - i was so stupid to install Linux and windows 7 on the same partition ....
I did some investigation i found online that i should continue with supergrub disk

steps i have taken
first i installed rescatux iso on dvd then cd then usb changed BIOS offcourse to boot from these locations
Then i tried SuperGrub disk 2 did exactly the same but still i am not able to recover anything
then i tried supergrub disk 1 all over again dvd cd rom and usb but i don t get the option to recover windows bootloaders
After that i was able to start my pc with the ubuntu run from USB 

Is there anybody who any tips where to start now i really need my windows for workrelated stuff
the usb version gives me the option to fully install UBUNTU.
If i do this do i then overwrite my windows 7 partition again?
As i m getting pretty desperate i m already greatefull for any advice.
i could really need some help as not many in my town have knowledge about Ubuntu
  Also my hardware is in fine quality just bought a new laptop

---

### Post by SecretCode on 2011-05-13
I'm not clear what's happened or why - installing Ubuntu and Win7 on the same partition should not cause file system corruption, just the complete overwriting of one with the other. But an incomplete install could do that.

Do you have an Ubuntu Live CD? 

Boot it and post the results of 
```
sudo fdisk -l
```
This will show what partitions are on the hard disk.

Is your main objective to recover existing data from the machine? Or to get it up and running quickly with a new OS? You may not be able to do both! In that recovering data could take a while.

---

### Post by Newbeatontheblock on 2012-06-10
Thanks very much for your assistance 
Problem is fixed 
Thank you

---

