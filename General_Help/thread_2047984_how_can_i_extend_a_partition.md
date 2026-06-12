---
title: "how can i extend a partition?"
date: 2012-08-25
forum: General Help
---

### Post by z3nhakr on 2012-08-25
here is how my partitions are set up:

1. Windows Boot (NTFS)
2. Windows 7    (NTFS)
3. Ubuntu 12.04 (Ext4)
4. Linux Swap
5. Free Space

I have almost 300gb of free space and id like to give some of it to ubuntu and windows.,as i understand it, i need to rearrange the partitions so that the free space is in-between my windows and ubuntu partition before i can extend them. how do i do this?

---

### Post by lindsay7 on 2012-08-25
Go to the Gparted web site and read up on how to do all of this.

---

### Post by z3nhakr on 2012-08-26
ive read a ton but i cant find out how to rearranging partitions without completely redoing them. if your just going to tell me to find the answer myself then don't bother replying because i have looked, and i am looking.

---

### Post by Miljet on 2012-08-26
If you are wanting detailed instructions, then you will have to furnish more details to work with. For example what size disk do you have? How is it partitioned? Your original post lists 5 primary partitions which is impossible with MBR partitioning.

Open a terminal and enter  ```
sudo fdisk -l
``` and post the results here.

Or better yet, boot a live CD, start gparted, and post a screen shot.

That way the people who would like to help you can see what needs to be done.

Thank you.

---

### Post by z3nhakr on 2012-08-26
[URL="http://ubuntuone.com/0OKO5FQ5SAI0rEShn9mmKy"]heres a gparted screenshot
http://ubuntuone.com/0OKO5FQ5SAI0rEShn9mmKy[/URL]

---

### Post by jim_deadlock on 2012-08-26
z3nhakr, using Gparted I would move the swap to the end, then either grow or move ubuntu to the right, then if necessary grow your windows to the right.

Note: back up your important stuff to removable media first if you can.

---

### Post by oldfred on 2012-08-26
You can move partitions around as posted above or another alternative:

You have used all 4 primary partitions. Often the swap is in a logical so then you can rearrange the extended to add partitions.

I might delete swap and create two new partitions in a new extended partition. I would create a shared data partition formatted NTFS and a new swap. You will have to edit fstab with new swap's new UUID and mount new NTFS partition in fstab to mount it permanently. 

Windows does not like a lot of writes into its system partition and Ubuntu's NTFS driver allows you to see all the hidden files & folders which can lead to accidents. Best to mount it read-only and use a shared data partition.

Shared /data (NTFS)-see post #3 oldfred
[http://ubuntuforums.org/showthread.php?t=1772620](http://ubuntuforums.org/showthread.php?t=1772620)
Mount, hide & link windows partition
[http://ubuntuforums.org/showthread.php?t=1397508](http://ubuntuforums.org/showthread.php?t=1397508)
Mount NTFS partition:
[http://ubuntuforums.org/showthread.php?t=1927504](http://ubuntuforums.org/showthread.php?t=1927504)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
Partitioning basics with some info on /data, older but still good bodhi.zazen
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

---

### Post by z3nhakr on 2012-08-26
Is there a way I can rearrange it so that the free space is between windows and ubuntu?

---

### Post by oldfred on 2012-08-26
See post #6. You have to slide partitions around as you can only grow to the right. 

Just be sure to have good backups as any power failure or corruption of the process can totally corrupt partition you are working on. That said I have done it many times and not had issues, but it is always the one you skip backups on that causes bigger issues.

---

### Post by jim_deadlock on 2012-08-26
z3nhakr, a couple of basic points about Gparted in case you didn't know.

1. You must boot from a Live CD (select 'try ubuntu') and then run Gparted so the partitions you're playing with are not mounted.

2. You can use your mouse to slide the coloured blocks back and forth. Each time you do it the action will be listed at the bottom of the screen. When you have everything how you want it you hit the green tick icon to apply all the changes.

To answer your question, to put the blank space in between you would need to move sda4 and sda3 over to the right. However, by the looks of it you probably want to move sda4 to the far right and then grow sda3 to fill the gap.

The small amount of unallocated space currently between sda2 and sda3 may not be fillable due to the formatting rules (but you can try), this is normal.

---

### Post by z3nhakr on 2012-08-26
thank you jim_deadlock. i couldn't move the partitions because they were mounted which i should have known and im embarrassed i didnt think of that from the start

---

