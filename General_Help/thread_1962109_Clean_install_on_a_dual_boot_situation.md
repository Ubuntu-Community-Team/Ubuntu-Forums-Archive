---
title: "Clean install on a dual boot situation"
date: 2012-04-20
forum: General Help
---

### Post by Mazate on 2012-04-20
Hola... I just tried to upgrade my laptop to 12.04 last night and it didn't go well.  My Ubuntu install is totally trashed so I'm going to have to do a clean install.  I have windows on one of my partitions.  I'd like to know if anyone knows of any sort of guide to doing a clean install of Ubuntu in a scenario where I can't just wipe the hard drive and go from scratch.  I need to reinstall it on the same partition(s) that were setup when I installed it for the first time.  I don't have my windows recovery disk so I want to avoid any problems with that partition as much as possible.

Thanks in advance.

---

### Post by oldfred on 2012-04-20
You can just reinstall using the manual install or Something Else. It will automatically find an existing swap, you specify your current root as / and format as ext4 and is /home is separate partition select/mount it also but DO NOT format it. 

I might install a Windows boot loader and create a Windows repairCD and Windows recovery DVD set and a full backup of Windows before doing anything. Always have good backups and repair tools handy, just in case something goes wrong.

---

### Post by Mazate on 2012-04-20
> **oldfred said:**
> You can just reinstall using the manual install or Something Else. It will automatically find an existing swap, you specify your current root as / and format as ext4 and is /home is separate partition select/mount it also but DO NOT format it. 

Forgive my ignorance but would you be willing to explain this in simple terms?  When I boot up with the 12.04 USB drive in and click install, it takes me to the page where it shows my partitions but I'm not sure what to do once I get to that point.

---

### Post by oldfred on 2012-04-20
Do you know which partitions were your old install? I always create in advance and once created a bunch of partitions one was large & for data & the other for my system. Of course I forgot which was which and not paying attention installed to the wrong partition.

If unsure boot into liveCD and at terminal run this. It should show NTFS partition(s) for Windows and ext3 or ext4 partition(s) for Linux and a swap partition.

sudo fdisk -lu

It may be easier to to see it graphically. Just ignore the screenshots on creating partitions as you have those.

[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)
or see post #9 and later as the hedge has created the partitions and is then choosing them.
The Hedge show graphically how to delete & create partitions:
[http://ubuntuforums.org/showthread.php?t=1713649](http://ubuntuforums.org/showthread.php?t=1713649)

---

### Post by Mazate on 2012-04-20
Ok, I'm attaching a screenshot of the window showing my partitions.

---

### Post by oldfred on 2012-04-20
When you get to the install screen select sda5 as / (root) and reformat to ext4. It should auto  find swap and let the boot loader (grub2) install to the MBR of sda.

Only if you had a separate /home would you then also select it as /home  and DO NOT format it. But it does not look like you have a separate /home and if saving most of you data in the shared NTFS you have less need for a separate /home. 

Just be sure to back up /home from inside your install with any new installs in the future to save what data and hidden settings you have made.

---

