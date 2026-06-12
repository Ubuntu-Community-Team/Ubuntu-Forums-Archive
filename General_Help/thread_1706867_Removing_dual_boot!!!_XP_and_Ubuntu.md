---
title: "Removing dual boot!!! XP and Ubuntu"
date: 2011-03-14
forum: General Help
---

### Post by faz. on 2011-03-14
I have an Eee900, it was SO SLOW with XP, so I am fully migrated to Ubuntu now, just that I really want to remove XP as I will not use it, and it is taking up valuable space (I don't even have enough room to install updates!!!!! )

How can I go about removing XP from the boot list, would it be best to simply remove the WINDOWS folder/partition, thus destroying the boot.ini file....? I would just leave it, only XP is the default option, so if ever I missed the 30 secs it would try and boot into some oblivion!

I had a quick google but could only find results for editing it within windows.

Any help appreciated, cheers

---

### Post by oldfred on 2011-03-14
Do you want to back it up first? Some do end up with second thoughts later.

Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Then you can reformat partition. You can leave it as NTFS but then need a windows CD to run chkdsk periodically and would have to delete the windows boot files in windows root so os-prober would not see it. If you reformat to a Linux partition everything will be erased. Either way you then can use it as a data partition or if a Linux format  move /home into it.

After reformating/deleting windows, grub will not find a windows to add to the menu.

sudo update-grub

---

### Post by faz. on 2011-03-14
I see. I just got the machine last week so I don't have any desire to keep XP if I don't have to. There is nothing on there I want to keep.

Thing is, I don't think it's in a separate partition. I think it's all a bit confusing.

If, in Ubuntu, I go to /File System/Host, I see everything that one would see if they clicked on the "C drive" in Windows. EXCEPT. There is a folder called "ubuntu" which is 3.6gb, and I guess contains the whole ubuntu thing.

I don't want to go willy nilly deleting things.

I will post again in a min with some screenshots of the folder layout and also the disk usage thing..... it may all be normal, I am a bit of a noob to Ubuntu.

Cheers

---

### Post by faz. on 2011-03-14
[IMG]http://www1.picturepush.com/photo/a/5255309/img/ubuntu/host.png[/IMG]

[IMG]http://www2.picturepush.com/photo/a/5255305/img/ubuntu/disk-usage.png[/IMG]

Another funny thing. It says 4.1gb free.... but I just got a popup telling me I have 126mb free and I should clear some stuff up!!!

Is it possible that UBUNTU is on a small partition?? ! Find it hard to believe........

---

### Post by oldfred on 2011-03-14
It looks like you have wubi. Which is installed inside the windows NTFS partition and uses the windows boot loader to start. 

DO NOT erase windows.

HOWTO: migrate wubi install to partition - bcbc 
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

---

### Post by faz. on 2011-03-14
ahhh... yes I have Wubi.

But that looks damn, damn confusing!!!!!!!!!!!!!

will have a read but I think it's a bit ahead of me.

---

