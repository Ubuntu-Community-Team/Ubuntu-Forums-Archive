---
title: "Software RAID?"
date: 2010-04-15
forum: General Help
---

### Post by Nxion on 2010-04-15
I have a question I am hoping that someone can answer. So not to long ago I wanted to try CentOS. After I installed it I figured I would have to setup my other 2 drives I have in my machine. I have three. One is a 80GB one is a 160 and the other is a 320. 

After the CentOS install was complete I noticed that I had only one drive show up and it was a huge drive. So what it did was recently create a stripe of my hard drives with out me doing anything extra which I thought was cool. Is there a way to set this up on Ubuntu during the setup or is there another way I have to do this.?

---

### Post by ian dobson on 2010-04-15
Hi,

mdadm is the linux tool to maintain/setup RAID arrays.

I have a 6tb RAID5 array running on 4 2Tb wd drives, this was a 4tb array on 3 drives until I added an extra drive and grew the array to use the new drive "online". What I mean with online is that I could still use the system/watch TV recordings/Record TV programs while the array was reshaping. Software RAID has come along way and in some ways it's better than a using a dedicated hardware raif controller.

Regards
Ian Dobson

---

### Post by Nxion on 2010-04-15
> **ian dobson said:**
> Hi,

mdadm is the linux tool to maintain/setup RAID arrays.

I have a 6tb RAID5 array running on 4 2Tb wd drives, this was a 4tb array on 3 drives until I added an extra drive and grew the array to use the new drive "online". What I mean with online is that I could still use the system/watch TV recordings/Record TV programs while the array was reshaping. Software RAID has come along way and in some ways it's better than a using a dedicated hardware raif controller.

Regards
Ian Dobson

Hi Ian,

So if I understand you right is I can build the system on one hard drive and then add the other two later? My apologies if this sounds like a stupid question, I am just not that familiar with RAID.

---

### Post by ian dobson on 2010-04-16
> **Nxion said:**
> Hi Ian,

So if I understand you right is I can build the system on one hard drive and then add the other two later? My apologies if this sounds like a stupid question, I am just not that familiar with RAID.

Hi,

Well yes and no. In my case when I setup the box I used 3 drives each with 2 partitions (First partition 20Gb for /, second partition for data). As linux cannot boot from a mdadm RAID5 partition (data i mycase) I setup the system to boot from the small partition (setup as RAID1). It is possible to convert a partion from non-raid to raid but it's not that easy, extra if it's your boot partition.

Once a system is setup to use RAID it's quite easy to add new drives/reshape/resize the RAID partion, it just takes some time to process all the data (when I added the 4th drive to my RAID5 array it took 24hours to reshape so that the systm used all 4 drives).

Regards
Ian Dobson

---

### Post by srs5694 on 2010-04-16
Iit sounds like what's under discussion is RAID 0 (striped RAID), in which the volumes are added together to create a larger virtual disk. This contrasts with RAID 1 (mirroring), in which the extra space is used to create a real-time duplicate as insurance against drive failure, or other levels of RAID that are variants of or in-between these two.

IMHO, RAID 0 is not very flexible; logical volume management (LVM) is much better. Like RAID 0, LVM enables you to create filesystems that are bigger than any one disk; however, LVM also enables you to carve up the volume group (as it's called in LVM terminology) into smaller segments, known as logical volumes. Logical volumes can be created, deleted, and resized much like files on a filesystem, which means you can use logical volumes much like you'd use partitions, but with less worry about the hassles of moving and resizing partitions should you run out of space on one of them. You can also create an LVM that's bigger than any one disk. The biggest drawback is that LVM adds complexity, compared to using regular partitions. Unfortunately, the standard Ubuntu desktop installer doesn't directly support LVM, although some other Ubuntu installers do. Googling "Linux LVM" will turn up lots of documentation on the topic of LVM.

FWIW, I've got seven computers with Linux installations on them, and all but one of them use LVM. Of course, the fact that I've got seven computers with Linux installations tells you that I'm not exactly the average Linux user! ;) (I write about Linux and do Linux consulting for a living.)

---

