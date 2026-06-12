---
title: "ubuntu apache www on USB"
date: 2010-11-04
forum: General Help
---

### Post by aussieolly on 2010-11-04
This is my first post in these forums. I am pulling out what little hair i have left with this problem. 

I have an old unwanted eeepc with about 12GB total HDD space (solid state) I decided to attempt to set up this machine as a apache server. I have got apache installed and with the default directory of /var/www everything works well. 

I would like to add a large USB drive to this machine and use that to store the webfiles for localhost.

I am currently testing configuration with a 4GB flash drive installed into the machine. I keep getting stuck with a permission error when attempting to access the directory on the USB drive. Now I have tried to mount the drive into the /var/www folder and also changing the directory in /etc/apache2/sites-available/default to point to /media/TOSHIBA/WebServer and the story is the same.

I also don't have enough of an understanding of linux users and groups to fully work out what is going on. 

I would really love someone to point me in the right direction or give me a strategy to follow to tackle this task. I also want to set up an ftp server (for external use) and a samba share (for LAN users) but i think once I can understand the apache2 issues I will be able to apply the same ideas to the next problems.

Thanks in advance
Olly

---

### Post by efflandt on 2010-11-04
If you are using a FAT32 file system on the USB, then that could be your problem.  FAT32 has no concept of owner or file permissions, so depending upon how it is mounted, all files may appear to have 777 permission which may be misinterpreted as scripts, and is so insecure, that such directories and files might be blocked by apache configuration.

Try a real Linux file system on the flash, maybe ext2 (which without journal would be written to less).  Then you could set proper directory and file ownership and permissions.

---

### Post by aussieolly on 2010-11-04
Thanks for the response efflandt, I was hoping there would be another way to get this working. I have a 750GB drive that i want to use as the USB drive on this machine. That drive is almost half full already and I was hoping not to have to reformat. Are there any tools that let you change the way a drive is formatted without losing the data?

I guess this is going to take longer than i first expected.

---

