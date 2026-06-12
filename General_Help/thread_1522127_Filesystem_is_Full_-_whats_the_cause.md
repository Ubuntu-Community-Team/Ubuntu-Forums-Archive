---
title: "Filesystem is Full - whats the cause?"
date: 2010-07-01
forum: General Help
---

### Post by Cybrmerc on 2010-07-01
Alright, I recently have received the message that my filesystem is  getting full. Even though I have it at the recommended size of 6.1GB,  the Disk Usage Analyzer is reporting that 4.0GB is being used. 
       I have removed old kernels; currently the only kernels installed are  linux-image- 2.6.33-020633 (current) and linux-image-2.6.32-23-generic  (backup) and linux-image-generic (?). I also have associated headers  installed:

[IMG]http://img441.imageshack.us/img441/3586/synaptickernels.png[/IMG]
[IMG]http://img8.imageshack.us/img8/2281/synapticheaders.png[/IMG]
       
       Please let me know if my headers/kernels are correct as I've  been trying to figure that out since I converted to Linux. Now the Disk  Usage Analyzer (DUA) shows that [IMG]file:///home/cybrmerc/Desktop/Synaptic-Headers%20.png[/IMG]the  file system size is 6.1 (4.0 being used) of which the /usr folder is the  main contributor:

[IMG]http://img4.imageshack.us/img4/7448/duashare.png[/IMG]
 
     The  two largest catalogs are /lib and /share/doc --- Lib: openoffice  (223mb), basis (223mb), program (183mb) and /share/doc:  texlive-latex-extra-doc (236mb), latex (233mb), minitox (79mb). Now I  don't know what basis, program, texlive, latex, or minitox are but all  together they are taking up 1GB+.
     Another curious thing that me  be an issue is when I run df -Th, I get this:
cybrmerc@GhostNet:~$ df  -Th
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda1      ext4    5.7G  4.0G  1.4G  75% /
none         tmpfs    1.5G  376K   1.5G   1% /dev
none         tmpfs    1.5G  116K  1.5G   1% /dev/shm
none          tmpfs    1.5G  196K  1.5G   1% /var/run
/dev/sda5     ext4    451G   9.4G  418G   3% /home

Now obviously sda1 is '/' and sda5 is my  seperate home partition - so what are the three tmpfrs? I assume they  are temp files but they don't disappear after restart. Lastly, the only  other thing that has occured since this problem started was I began  receiving a repeated error during boot: [B]
     
     mounting  none on /dev failed no such device [/B]
     
Now I figured this  may be related to the 'none' filesystems tmpfs. 

Everything else  runs fine on system and I still have 1.7 GB left on root. Just would  like to know (1) if the /usr/share/doc files are necessary (latex, etc.)  or if there is an error in my fstab, mnt or anything else. I am  relatively new to ubuntu so you may have to get specific in assistance  =P That said, any help would be majorly appreciated!

---

### Post by mike555 on 2010-07-01
empty your root trash , maybe that will help..

---

### Post by yetiman64 on 2010-07-01
[How to: recover lost disk space.]("http://ubuntuforums.org/showthread.php?t=1122670")
lots of possible reasons and solutions listed in this link.

---

### Post by Cybrmerc on 2010-07-01
> **yetiman64 said:**
> [How to: recover lost disk space.]("http://ubuntuforums.org/showthread.php?t=1122670")
lots of possible reasons and solutions listed in this link.

Tried this, emptied trash - all pointed to the /usr/docs and /lib catalogs taking up all the space. Tried clean, autoclean, and autoremove so its not leftover .debs - any other ideas? Can I just remove latex or clear out the docs folder? Are either of those extremely important?

---

### Post by yetiman64 on 2010-07-01
Have you tried all the possibilities in the thread such as error message log build ups, root trash (won't be removed on emptying the desktop trash etc). Those packages you mention don't seem particularly big to me (not sure about what latex is for). Personally I wouldn't recommend you remove any packages or libraries without first exhausting all possibilities in that thread as they are more than likely necessary.

1 more suggestion is to check your /tmp is being correctly emptied on each boot, there have been problems with it for some people in the past.

Your / (root partition) is showing as 75 % full - I'd double check error logs and other problems before removing any system packages or libraries etc.

That is a very detailed thread, but if your in a hurry check out sections 6 and 8 as noted at the top of the thread. Good luck.

---

### Post by Cybrmerc on 2010-07-09
After repeated scourings of the above page I finally noticed the SHIFT+DELETE Trash folder (which I found to have 3GB worth of files including the headers and system backups I had previously thought removed, lol). Thanks again for the help - I went through the trouble of creating a new /usr partition because I thought there was just too much data, but it was a good learning experience (fstab hurts my head) ;)

---

