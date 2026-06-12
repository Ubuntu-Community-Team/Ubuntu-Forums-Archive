---
title: "Shared Home Foler w/ 32-bit &amp; 64-bit Dual Boot"
date: 2011-11-05
forum: General Help
---

### Post by wadedesk on 2011-11-05
I've used Ubuntu on both an external USB and internal IDE drives that I moved from one 32-bit system to another with no problems.  Ubuntu has always been able to load new drivers and run correctly.

Last spring I purchased a 64-bit laptop and upgraded to Ubuntu 64-bit that installed on an eSATA drive.  I was able to migrate my home folder with not too much trouble.

I would like to be able to move the eSATA drive to other computers as needed once again.  Is it possible to install both 32-bit and 64-bit versions of Ubuntu on the same eSATA drive (in different partitions) and have both OSes use a shared home partition?  (Example: sda1 = Ubuntu AMD64, sda5 = Ubuntu i386, sda6 = Home folder.)

Will apps like Firefox and Thunderbird still work when accessing the same home folder? or will my data become corrupted?  

I assume that Grub2 would just show delicate entries with the first being the 64-bit OS and the second being the 32-bit OS.  

Thanks for any thoughts you can give on the advisability of trying this.

---

### Post by duke.tim on 2011-11-05
It is possible to set the home drive to another partition, I am not 100% sure how this would affect your programs and settings when using 2 OSes but it is likely that there will be slightly different configurations between the 64bit os and 32bit .

A simple first step you could take is compare the folder/files structure of the 64bit and 32bit OS Home directory.

This is a tutorial about how to set home as another partition.

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Unless someone else has tried this you would need to experiment to see if it works. If you decide to continue I would be Very Interesting in the results :P

---

### Post by oldfred on 2011-11-05
Generally you do not want to share /home. 

I prefer to create a data partition and put all data and even hidden data folders like Firefox & Thunderbird profiles into the data partition. Then the settings in /home are tiny and you can copy over those you may want without having one write settings that conflict.

The actual user settings are small. My /home is 1GB with about 3/4 of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root).
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives.

I have some data in a NTFS partition from when I used XP and some in a ext3 partition for most newer data. So I have two data partitions.

Update to tb3, Firefox is similar in use of profile
[http://ubuntuforums.org/showthread.php?t=1349889](http://ubuntuforums.org/showthread.php?t=1349889)
new 
[http://kb.mozillazine.org/Moving_your_profile_folder](http://kb.mozillazine.org/Moving_your_profile_folder)
[http://support.mozillamessaging.com/en-US/kb/Profiles](http://support.mozillamessaging.com/en-US/kb/Profiles)
[http://www.mozilla.org/support/thunderbird/profile](http://www.mozilla.org/support/thunderbird/profile)

---

### Post by wadedesk on 2011-11-17
I created a Ubuntu 32-bit/64-bit Dual boot installation with a shared Home folder between the two OSes.  How I did it and the results are posted here ... 
[http://project.fixmypc99.com/dual-boot-ubuntu.html]("http://project.fixmypc99.com/dual-boot-ubuntu.html")

---

