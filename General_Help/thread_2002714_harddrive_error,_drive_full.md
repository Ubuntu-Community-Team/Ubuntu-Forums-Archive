---
title: "harddrive error, drive full"
date: 2012-06-13
forum: General Help
---

### Post by qwertyjjj on 2012-06-13
Looked at my computer this morning (it had been on for 48hrs or so) and the screen said there is less than 1MB available with a screen warning. This was strange as it is a 1TB drive but I was doing some backups to an external drive so I thought maybe the mount points had got screwed up or something.
So, I restarted but ubuntu will not start.
I get an error of:
ata2.00 exception Emask oxo sact 0x0 serr 0x0 action 0x6 frozen
failed command: IDENTIFY PACKET DEVICE
etc.

Any ideas what could cause this or how to solve?

---

### Post by roelforg on 2012-06-13
Bad HDD

---

### Post by qwertyjjj on 2012-06-13
> **roelforg said:**
> Bad HDD

Anyway I can test that?
I've seen some fixes online but not sure what they are fixing.
Also, when it said drive full, I could still play videos and use internet so the drive is working somehow...it's just not loading.

---

### Post by roelforg on 2012-06-13
> **qwertyjjj said:**
> Anyway I can test that?
 
[https://help.ubuntu.com/community/TestingStorageMedia](https://help.ubuntu.com/community/TestingStorageMedia)

---

### Post by qwertyjjj on 2012-06-13
> **roelforg said:**
> [https://help.ubuntu.com/community/TestingStorageMedia](https://help.ubuntu.com/community/TestingStorageMedia)

How do I repair it or workaround it?
Like I said, the drive was working fine before I restarted...it was full but I could still access data so what would stop it starting up?

Also, do I have to boot off a live CD to run those tests?

---

### Post by roelforg on 2012-06-13
> **qwertyjjj said:**
> How do I repair it or workaround it?
Like I said, the drive was working fine before I restarted...it was full but I could still access data so what would stop it starting up?
 
Also, do I have to boot off a live CD to run those tests?
 
Yes, you might have to install the programs you need for testing and that can't be done on a full hdd.
It's a bad idea to run fsck on a mounted drive anyways.
 
The system might stop booting if it can't put it's temp files somewhere.
You might want to check the partition layout, i've seen someone who accidentally let the end of the swap partition overlap with the begin of the root partition, the thing worked fine for months until that evening... He was doing some ram-hogging jobs so the swap kicked in action, he didn't notice that the swap was actually overwriting and corrupting the rootpartition. When i took a look at it (he knew i'm good at resolving bootproblems) because it wouldn't boot anymore, it dawned on me that the swap overlap caused the kernel image to become corrupted. One livecd-copy-livekernel-boot-reinstallkernel and adjustment of the swap later, he was up and running again. I told him he was lucky that it was only the kernel. It kept running that evening because the kernel was already loaded into ram (at boot) so you couldn't notice the corruption.
It might be that in a similar way, your system has a corruption on a different spot.

---

### Post by qwertyjjj on 2012-06-13
> **roelforg said:**
> Yes, you might have to install the programs you need for testing and that can't be done on a full hdd.
It's a bad idea to run fsck on a mounted drive anyways.
 
The system might stop booting if it can't put it's temp files somewhere.
You might want to check the partition layout, i've seen someone who accidentally let the end of the swap partition overlap with the begin of the root partition, the thing worked fine for months until that evening... He was doing some ram-hogging jobs so the swap kicked in action, he didn't notice that the swap was actually overwriting and corrupting the rootpartition. When i took a look at it (he knew i'm good at resolving bootproblems) because it wouldn't boot anymore, it dawned on me that the swap overlap caused the kernel image to become corrupted. One livecd-copy-livekernel-boot-reinstallkernel and adjustment of the swap later, he was up and running again. I told him he was lucky that it was only the kernel. It kept running that evening because the kernel was already loaded into ram (at boot) so you couldn't notice the corruption.
It might be that in a similar way, your system has a corruption on a different spot.

Is there an automatic repair tool on the live CD or do I have to run gparted and terminal commands?
So, do I do the testing first and see what it returns? The drive mas maxed out when I looked at the disk usage analyzer so maybe that's it...nowhere to put temporary files. I'm thinking somehow the backup I was running has copied files to the hard drive instead of the network drive...

---

### Post by roelforg on 2012-06-13
> **qwertyjjj said:**
> Is there an automatic repair tool on the live CD or do I have to run gparted and terminal commands?
So, do I do the testing first and see what it returns? The drive mas maxed out when I looked at the disk usage analyzer so maybe that's it...nowhere to put temporary files. I'm thinking somehow the backup I was running has copied files to the hard drive instead of the network drive...
 
The link i posted tells you a lot, googling well tell you even more.
I don't know the exact situation.
 
Stuff might go wrong for the weirest and unnoticed reasons (see my tale about the partition overlay).

---

### Post by qwertyjjj on 2012-06-13
> **roelforg said:**
> The link i posted tells you a lot, googling well tell you even more.
I don't know the exact situation.
 
Stuff might go wrong for the weirest and unnoticed reasons (see my tale about the partition overlay).

If I am booting off a live CD then how am I supposed to unmount the drive? Surely the live CD will always mount the hard drive won't it?
The command below won't persist when I restart and boot from the live cd again

[B]Hard Drive
To run a filesystem integrity check on an ext2 or ext3 partition the drive must be unmounted (Running fsck on a mounted drive is a very bad idea.). In the case of your hard drive you will need to force a fsck on next boot up. To do this you create a file called forcefsk in the root directory. 

In a terminal run : 
sudo touch /forcefsck[/B]

---

### Post by roelforg on 2012-06-13
> **qwertyjjj said:**
> If I am booting off a live CD then how am I supposed to unmount the drive? Surely the live CD will always mount the hard drive won't it?
The command below won't persist when I restart and boot from the live cd again
 
**Hard Drive**
**To run a filesystem integrity check on an ext2 or ext3 partition the drive must be unmounted (Running fsck on a mounted drive is a very bad idea.). In the case of your hard drive you will need to force a fsck on next boot up. To do this you create a file called forcefsk in the root directory. **
 
**In a terminal run : **
**sudo touch /forcefsck**
 
Open the filemanager and click on the eject button next to your hdd (it'll unmount the hdd and nothing else).

---

### Post by qwertyjjj on 2012-06-13
Right...fixed...it's working again.
The drive was full, I found a folder called mnt that had a 350Gb tar backup and deleted it then restarted.
The odd thing is is that this backup was supposed to be on the network drive so how did it get onto the hard drive?

I ran this command before doing the backup.
mkdir  ~/mnt
sudo mount -t cifs  //iomega/backups  mnt/
this thread: [http://ubuntuforums.org/showthread.php?t=2000508](http://ubuntuforums.org/showthread.php?t=2000508)

---

