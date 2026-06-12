---
title: "installing on partition"
date: 2012-09-06
forum: General Help
---

### Post by sniper8752 on 2012-09-06
Is this setup right to install Ubuntu on it?  i want this installed on a separate partition from my windows 7.

---

### Post by Kopkins on 2012-09-06
Looks good. What is occupying the space there currently?

From here you would just boot from the Ubuntu liveCD and manually configure partitions. You would have that partition reformatted and wiped and install Ubuntu to that partition.

Best of luck,
Kopkins

---

### Post by sniper8752 on 2012-09-06
> **Kopkins said:**
> Looks good. What is occupying the space there currently?

From here you would just boot from the Ubuntu liveCD and manually configure partitions. You would have that partition reformatted and wiped and install Ubuntu to that partition.

Best of luck,
Kopkins

I believe that I was getting an error before.  I will try it again though.  I have a recovery partition, as well as some others.  should have posted the other here.  it is kinda a mess, and needs to be cleaned up, I think.  I am not sure what the unallocated for.

---

### Post by Kopkins on 2012-09-06
Looks pretty okay to me. The unallocated is just unused space on the disk. Unused meaning it is not part of a partition. I looked at another thread of yours, you posted a link to pastebin. I looks like you were trying to install with WUBI the time you got those errors. 

Are you planning on setting this up to be a dual boot system? That is what you would do with a separate partition. You'll need to boot your computer directly from the liveCD.

Kopkins

---

### Post by sniper8752 on 2012-09-06
I clicked on install inside of windows 7.  it restarted, and nothing happened.  
yes, i would like to dual boot.  
and can't i just delete that unallocated partition?

---

### Post by oldfred on 2012-09-07
Installing inside Windows on a NTFS partition is a wubi install.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

It is good for an extended test where you do not have to repartition and uses the Windows boot loader. It is a file inside the NTFS partition so any issues with Windows will also prevent use of wubi. I think the max size of wubi is 30GB. If you want more then you need to do a full partitioned install, but that has to be to LInux formated partition(s) not NTFS.

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/](http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/)

---

### Post by Kopkins on 2012-09-07
> **sniper8752 said:**
> I clicked on install inside of windows 7.  it restarted, and nothing happened.  
yes, i would like to dual boot.  
and can't i just delete that unallocated partition?

Check out everything oldfred said. That should get you set. 

No, you can't delete that unallocated part of the disk. You may add it to an adjacent partition though. It's like pieces of a pie, but a pie made of magnetic material that can't actually be cut. You may divide the pie however you like, in fourths or however, but you can't just delete (cut) part of the pie. 

Basically, to delete it would be to remove part of your hard drive and you can't do that.

Good luck!
Kopkins

---

### Post by sniper8752 on 2012-09-07
does the exFat volume support ubuntu?

edit:  also, i am getting an error that no more than 4 partitions are supported.

---

### Post by oldfred on 2012-09-07
Ubuntu will not install to exFat. I have seen some discussion of a driver but not sure if it works well or not yet. So no.

Windows will convert to dynamic partitions if you try to create more than 4 primary partitions in Windows. Linux does not work with dynamic partitions. Use Windows to shrink Windows partitions, but use gparted from Ubuntu liveCD or a separate gparted liveCD to create or edit LInux partitions.

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)

---

### Post by sniper8752 on 2012-09-18
> **Kopkins said:**
> Check out everything oldfred said. That should get you set. 

No, you can't delete that unallocated part of the disk. You may add it to an adjacent partition though. It's like pieces of a pie, but a pie made of magnetic material that can't actually be cut. You may divide the pie however you like, in fourths or however, but you can't just delete (cut) part of the pie. 

Basically, to delete it would be to remove part of your hard drive and you can't do that.

Good luck!
Kopkins

so i right-clicked on my c drive to add both of the unallocated pieces to it.  I choose to extend it.  but there is nothing listed under "available".

edit: got this to work.  but now, i have the unallocated space before the c drive.  to combine, i must have it after, right?  so how do i get it to be after the c drive?

---

