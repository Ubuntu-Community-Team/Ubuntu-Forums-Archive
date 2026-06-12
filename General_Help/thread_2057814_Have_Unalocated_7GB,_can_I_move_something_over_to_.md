---
title: "Have Unalocated 7GB, can I move something over to fill it? Screenshot."
date: 2012-09-14
forum: General Help
---

### Post by 777funk on 2012-09-14
[SIZE=3]Here's a screenshot of how I have my current Ubuntu 12.04 install setup.[/SIZE]

[IMG]http://www.rocketfireguitars.com/forums/other/Computing/Screenshot%20from%202012-09-14%2007:30:23.png[/IMG]


[SIZE=3]1. I'm not sure Swap is doing anything (don't see any space used)
2. To the right of Swap I have around 7GB of Unallocated space. Is there a way to combine this with my main Home Directory.

3. Semi related... I have 269 GB in my Home Directory. I'd like to make this or most of also accessible in Windows. I prefer to store my files so I can access it from both OS's. I don't really need much storage in Home. Is there a good way to split that drive up and say keep 20GB for Home and use the rest as a Format that both OS's can read?

thanks!! [/SIZE]

---

### Post by Primefalcon on 2012-09-14
first off you wll ahve to do it from a live disk and have eveything unmounted.

then you'll want to enlarge /dev/sda2 and then what container partition you want.... btw back up... sometimes partition resizing can go..... bad

if it does you can usualy recover partitions with testdisk as long as nothing has been overwritten.... and yes I have had this happen myself and fixed it using testdisk

---

### Post by zombifier25 on 2012-09-14
Just to add more info, [GParted LiveCD](http://gparted.sourceforge.net/download.php) is a good live disk to use. Just burn it to a CD or use Unetbootin to write it to a USB drive.
Also, concerning the 3rd point in your post, if you want Windows to be able to read ext4 partitions, you can just install a tool like Ext2Fsd. Instructions [here](http://www.webupd8.org/2011/08/access-ext4-ext3-or-ext2-partitions-in.html). Note that write support is *experimental*, and it may corrupt your drive, so mount it in read-only mode. (I never find myself needing to write to a Linux partition in Windows anyway)

---

### Post by oldfred on 2012-09-14
After you move the extended partition to include the unallocated, move swap right to the end of the drive/extended partition.

You can shrink /home and create a new shared NTFS data partition. Mount it in fstab. I still have my NTFS shared partition from when I used XP and still have my photos for Picasa, Firefox & Thunderbird profiles in the NTFS. But I now put all new data in a shared ext3 partition. Because I moved all data from my /home, it is now less than 2GB even with .wine for the Windows version of Picasa using over 1GB.

Shared /data (NTFS)-see post #3 oldfred
[http://ubuntuforums.org/showthread.php?t=1772620](http://ubuntuforums.org/showthread.php?t=1772620)

[http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
suggest using templates instead. Post #6
For ntfs UUID shown is example only see below:
UUID=DA9056C19056A3B3 /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters &#8221; * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well:

** To find the correct UUID for your partitions:
sudo blkid -c /dev/null -o list
** You will have to create the mount point yourself, for example:
sudo mkdir /media/WinD

** Then add the template with the correct UUID and mount point to fstab:
sudo cp /etc/fstab /etc/fstab.backup
gksu gedit /etc/fstab
** And when you are done editing fstab and saving it run the following command to test for errors and mount the partitions without requiring a reboot. You will know before you reboot if something is amiss. :
sudo mount -a

---

