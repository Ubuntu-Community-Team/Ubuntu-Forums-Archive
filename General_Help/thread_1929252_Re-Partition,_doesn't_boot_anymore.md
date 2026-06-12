---
title: "Re-Partition, doesn't boot anymore"
date: 2012-02-21
forum: General Help
---

### Post by mhenschel on 2012-02-21
Dear Forum Users,
I have a notebook where I have installed Ubuntu alongside Windows Vista. The HD originally had partition C for Windows and D for data. There was a recovery partition (hidden) in front of C.
When I installed Ubuntu, the C partition was split to create space for Ubuntu. This was done by the Ubuntu installation.
So far so good. When I booted the notebook I had to choose between Ubuntu and Windows.
The Ubuntu partition turned out to be too small. I therefore chose to use Acronis Disc Manager and make the hidden Recovery (Windows) partition smaller (from 10Gb to 7Gb) and allocate this new space to the Windows partition. This was done in one session.
WHen the process was finished by Acronis, the notebook tried to reboot, which failed. The booting process stops after loading the bios, then starts the same process again.
When I boot with a CD I can see that the partition resizing has worked. 
What did I screw up? Any chance to repair this?

Thanks for any replies,
Michael

---

### Post by bluexrider on 2012-02-21
You are going to need the Windows Vista Installation CD and this tutorial

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

If the data on the hidden partition isn't damaged you should be able to boot from it using the choice from the BIOS or during the boot process, pressing F12 or whatever corresponding key for your machine is for the recovery mode.

If it fails-over to a repair prompt, this would be good, proceed to repair MBR. 

I recommend reading the link before proceeding, this will give you instructions on how to fix the issue.

The other option is to boot from Ubuntu Live CD then install boot-repair
 
```
sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt-get update
sudo apt-get install boot-repair
```

---

### Post by oldfred on 2012-02-21
Windows has information in the PBR or partition boot sector that is the same start and end as the partition table. If changes are made the PBR also has to be updated. Not all partition tools make that change. Often chkdsk and fixBoot are required from a Windows repairCd.

[http://www.sevenforums.com/tutorials/681-startup-repair.html](http://www.sevenforums.com/tutorials/681-startup-repair.html)
[http://www.w7forums.com/startup-repair-t441.html](http://www.w7forums.com/startup-repair-t441.html)
[http://www.bleepingcomputer.com/tutorials/tutorial148.html](http://www.bleepingcomputer.com/tutorials/tutorial148.html)

---

### Post by mhenschel on 2012-02-22
Thanks for your answers. I used boot-repair, which solved the problem.

---

### Post by bluexrider on 2012-02-22
Glad to get you going. Happy *buntu!

---

