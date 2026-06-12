---
title: "Hard Drive Partitions"
date: 2010-08-12
forum: General Help
---

### Post by Errandir on 2010-08-12
Hello all, I've got a question. It doesn't exactly have to do with Ubuntu, so I'm not sure if this is the right place to ask, but I figured I'd give it a shot.

I have a new lenovo laptop that came with Windows 7 64-bit installed, and I want to set it up to dual boot that and Ubuntu. I'm pretty new when it comes to this stuff, but I looked up a few things, and I figured I want three hard drive partitions: one for ubuntu, one for windows, and one for common files like documents, pictures, and music (maybe one for swap space too, but I read you can use a file for that, so I'm not sure). Problem is, when I look at my hard drive (I was using GParted from a live CD), it's got seven partitions already (click [here]("http://img686.imageshack.us/img686/9097/gpartedscreenshot.png") for a screenshot).

So basically, I want to know which partitions I can get rid of, and if it's okay to just leave the others there. I know one is the C drive, and one is for system restore files - the LEVOVO one, I think - which I can back up and then delete (but haven't yet since it takes 17 cds). The other lenovo one seems to have drivers or something stored on it, but I have no idea about the unallocated partitions, the "extended" partition, or the other ntfs partition.

---

### Post by Mark Phelps on 2010-08-12
> **Errandir said:**
> So basically, I want to know which partitions I can get rid of, and if it's okay to just leave the others there. I know one is the C drive, and one is for system restore files - the LEVOVO one, I think - which I can back up and then delete (but haven't yet since it takes 17 cds). The other lenovo one seems to have drivers or something stored on it, but I have no idea about the unallocated partitions, the "extended" partition, or the other ntfs partition.

My guess is that sda1 is your win7 boot partition -- don't touch this or Win7 may not boot anymore.

I think that sda2 is your primary Win7 OS partition -- which is the one I would shrink to make room.  And do that with the Win7 Disk Management utility. Do NOT use GParted to do that, or you run the risk of corrupting the partition.

Since you appear to already have three primary partitions and one extended partition, that's all you're allowed to have.  So, I would do the following:
1) Shrink the Win7 OS partition to make room
2) Expand the Extended partition to the left to fill up the new space
3) Install Ubuntu in the unallocated space now inside the Extended partition.

As to the existing unallocated areas -- they're a total of 1MB Each!  Not enough to even care about. Most probably due to alignment rounding.

---

### Post by libssd on 2010-08-12
Keep it simple: Ubuntu should be able to access data files on the Windows partition. Keep in mind that Linux will also need a swap partition = RAMx2 should be more than enough space to handle hibernate. I can get away with a small (256mb) swap, because I never use hibernate.

**SwapFAQ**: [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by Errandir on 2010-08-13
Thanks for the responses!

So how would I install ubuntu into the extended partition? Looks like it has two sub-partitions already... would I create a new sub-partition and install ubuntu on it? (And is that even possible? I have no idea what I'm talking about here...) Or can I just select the extended partition when I'm installing ubuntu and it will do the rest?

As for swap space - well, if I can't create any more partitions, where would that go? Also on the extended partition (how many things can you put on there anyway)? Or can I make a file somewhere for it? I have 4 GB RAM, and 8 GB seems like a large file.

---

### Post by libssd on 2010-08-13
I always choose the manual option when the installer gets to the partitioning stage. Let's assume that you have a Windows boot partition, a Windows OS partition, and a third partition that isn't being used for anything. I **think** you can delete that partition, then re-create it for Linux at a slightly smaller size, leaving 2-4gb of disk space for the swap partition. When you are creating the new Linux partition, choose Ext4 journalling, check the format box, and set / as the mount point (this is also known as the "root" partition) and generally the entire Linux directory structure, including user files, hangs off it. Except for the partition size, your screen should look something like the attached screen shot at this stage.

After creating the root partition, assign any remaining space to swap. You can go through this step as many times as you want, until you get the partition sizes where you want them to be. You can **not** use hibernate without a swap partition; 2gb should be big enough, but if you have 4gb of RAM, 4gb swap would be better. Then proceed with the installation.

As always, it is prudent to have a restorable Windows backup before proceeding. :P

---

### Post by Errandir on 2010-08-14
>  Let's assume that you have a Windows boot partition, a Windows OS  partition, and a third partition that isn't being used for anything. I **think**  you can delete that partition, then re-create it for Linux at a  slightly smaller size, leaving 2-4gb of disk space for the swap  partition.Problem is, the third partition *is* being used for something... plus, I can't create any more partitions. So do you know how I can clear a partition? I don't want to keep anything that's on it, just empty it so I can install ubuntu.

---

### Post by libssd on 2010-08-14
Assuming you don't care about the data (if any) just click on the delete button, then recreate the partition.

---

### Post by oldfred on 2010-08-14
Go back to Mark Phelps' post. His recommendations are correct.

You can create as many partitions as you want in the extended. Some say the limit is 16 and other say unlimited. But I have not needed 16 partitions so I do not know.

Swap only needs to be slightly larger than RAM. If you have 4GB and want to hibernate make it 4.1 or thereabouts as that will hold all your memory.

I still like having a NTFS shared directory for data between windows and Ubuntu. Then you are not writing into the windows system partition.

---

### Post by Errandir on 2010-08-14
> **oldfred said:**
> You can create as many partitions as you want in the extended. Some say the limit is 16 and other say unlimited. But I have not needed 16 partitions so I do not know.
Oh, okay! For some reason I thought there could only be two sub-partitions in the extended one. That should solve a number of problems.

Thanks for the help, all of you! I'll try that.

---

