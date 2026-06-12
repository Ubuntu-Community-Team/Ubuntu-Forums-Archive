---
title: "I can't enter my ubuntu anymore... please help"
date: 2010-07-25
forum: General Help
---

### Post by q8.legend on 2010-07-25
Hi
I tried to mount one of my HDD with ubuntu, since it was having problem( 1 of 5 HDD won't mount in ubuntu, the rest working fine)...
when I tried to mount it with a tool called I think "NtFS congfiguration tool", it tolled me after doing it to restart ubuntu. 
when I did that I can't enter ubuntu anymore. I stuck in a screen that it said "error in mounting" & I can press M to recovery mode or S to continue...
when I press S also gave me another screen have similar message, but in this one when I press S or M I got stuck & I can't do anything...

I read from other thread that you should enter "fstab" & comment the drive or Hdd that cause the problem... The problem is that when I tried to enter "fstab"
from recovery mode (from the first message that came I press M, to enter Recovery) I tried to comment the drive that cause problem but unfortunately I can't save the changes,
it said that it's only for read .... I read that I can do the job from terminal using live cd, but when I enter the fstab command it show me the fstab of the live cd not the one that in the HDD...
How can I fix that ??? I can't enter my ubuntu anymore now...

Note: I'm a newbie in ubuntu command line & to ubuntu...


Thanks alot......

---

### Post by robsoles on 2010-07-25
Boot from LiveCD, look under 'Places' menu - Just under "Computer" in 'Places' should be one or more HDDs/Partitions listed from your PC, identify the one which has your OS and click it, it will open in nautilus and it will mount under /media in the LiveCD's file-system in R/W instead of R/O.

Click up arrow in menubar of nautilus window that opened and take note of the name that is listed in the window - it should be the name of the folder you need to insert where I put 'your-hdd' in the following line

```
sudo nano /media/your-hdd/etc/fstab
```Should open your fstab file for editing in nano, an easy enough file editor for terminal. When you put '#' in front of line with offending HDD (or delete it) press [Ctrl]+[X] and program will ask you if you want to save changes, press [Y] and then [Enter] to commit changes to original file.

Restart and post back whether or not that got you back into your GUI/Desktop.

---

### Post by q8.legend on 2010-07-25
> **robsoles said:**
> Boot from LiveCD, look under 'Places' menu - Just under "Computer" in 'Places' should be one or more HDDs/Partitions listed from your PC, identify the one which has your OS and click it, it will open in nautilus and it will mount under /media in the LiveCD's file-system in R/W instead of R/O.

Click up arrow in menubar of nautilus window that opened and take note of the name that is listed in the window - it should be the name of the folder you need to insert where I put 'your-hdd' in the following line

```
sudo nano /media/your-hdd/etc/fstab
```Should open your fstab file for editing in nano, an easy enough file editor for terminal. When you put '#' in front of line with offending HDD (or delete it) press [Ctrl]+[X] and program will ask you if you want to save changes, press [Y] and then [Enter] to commit changes to original file.

Restart and post back whether or not that got you back into your GUI/Desktop.


Thanks alot .. It does works, I have my ubuntu back to me :)

---

### Post by robsoles on 2010-07-25
Very welcome - maybe you can mount your problem HDD using the same way I got you to mount your OS HDD and that won't pose as much threat to your desktop?

---

