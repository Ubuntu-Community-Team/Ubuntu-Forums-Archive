---
title: "Restoring a partition, dd denied permission to open file"
date: 2011-07-03
forum: General Help
---

### Post by gearond on 2011-07-03
Really weird situation.

DOES WORK:
-------------
sudo bzip2 -dck /media/MTECH_LAPTOP_BACKUPS/backup.raw.bz2 | sudo dd bs=4k conv=sync,noerror of=/dev/sda1 bs=4k


DOES WORK: (just testing if ANYTHING would work)
-------------
sudo dd if=/media/MTECH_LAPTOP_BACKUPS/100MB_file.dat bs=4k conv=sync,noerror of=/dev/sda1 bs=4k

DOESN'T WORK:
-------------
sudo bzip2 -dck /media/MTECH_LAPTOP_BACKUPS/backup.raw.bz2 | dd bs=4k conv=sync,noerror of=/dev/sda1 bs=4k


THE LESSON:
-------------
See the difference between the 1st and the 3rd examples . . .? 

Used 'sudo' again in the command which has the output of bzip2 -dck piped to it. For some reason, after a pipe, '|', the first sudo is no longer in effect. 


OTHER THREAD ABOUT THIS:
--------------------------
[http://ubuntuforums.org/showthread.php?t=518299](http://ubuntuforums.org/showthread.php?t=518299)
That thred covers some issues, but I had to play with the commands to find my solution. If I knew more about CLI and redirection, I'd know why. But it's probably a safety thing.


EXTRA NOTES:
--------------
What may affect it? I have my installation set up to start with no login, although the user has a password. Had same problem using the 'Try 10.04' CD, however.

---

