---
title: "Remove Windows Vista from a Dual Boot?"
date: 2010-06-25
forum: General Help
---

### Post by Jessi on 2010-06-25
Hello there fellow Ubuntu users. 

Today I've decided that I would like to remove my useless, freezing windows install from my Ubuntu laptop and only use Ubuntu... booting windows XP from a virtual box whenever I need to use a Windows application with poor Wine support. 

Any safe way I can go about doing that? I tried googling this, but all I found was the opposite, remove ubuntu from windows... which is quite sad. 

Anyway, windows is using up a ton of space that it doesn't need to. It takes me 5 minutes to even get it booted and after using Ubuntu, I have no patience left for the program. 

What should I do?

---

### Post by Dustin2128 on 2010-06-25
use gparted to edit your partition table, shouldn't be too hard.
EDIT: Assuming it's not a wubi install.

---

### Post by WorMzy on 2010-06-25
It could potentially be more difficult than simply opening up gparted and deleting the Windows partition, if grub is installed to the MBR of the Windows partition. Can you open up a terminal and post the output of 'fdisk -l' here?

---

### Post by burton247 on 2010-06-25
This isn't the answer you want to hear really but I suggest a reinstall. Wiping windows and growing the partition isn't reliable. Growing partitions isn't reliable even for experienced users, I have done it before and not had trouble but I doubt I'll do it again. Even if you do succeed your partition table might need editing (not too tricky though) and the issue before about your MBR too.

---

### Post by oldfred on 2010-06-25
You can convert the windows partition to a /home or just a data partition just by reformatting it. Then you are not moving your root and the massive data move that is required to move it.

---

### Post by burton247 on 2010-06-27
> **oldfred said:**
> You can convert the windows partition to a /home or just a data partition just by reformatting it. Then you are not moving your root and the massive data move that is required to move it.

If your home isn't on a different partition at the moment this sounds the best to me. Even if it is, back it up, wipe vista and merge the two partitions. If it's successful great, if not just recover stuff from the backup. You'll just need to edit fstab

---

### Post by Jessi on 2010-07-02
> **burton247 said:**
> If your home isn't on a different partition at the moment this sounds the best to me. Even if it is, back it up, wipe vista and merge the two partitions. If it's successful great, if not just recover stuff from the backup. You'll just need to edit fstab

Wait, what do you mean by reformatting it to home? Because that sounds just about perfect, but how do I do that? Do I used the format c: command in MS-DOS?

---

### Post by artemyv on 2010-07-02
> **Jessi said:**
> Wait, what do you mean by reformatting it to home? Because that sounds just about perfect, but how do I do that? Do I used the format c: command in MS-DOS?

No, You use GParted application for formating partitions
and Storage Dvice manager to selct where it is mounted


To move all files from current home folder to new partion is a little bit more tricky

I suggest to read and understand the following link [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by yetiman64 on 2010-07-02
> **Jessi said:**
> Wait, what do you mean by reformatting it to home? Because that sounds just about perfect, but how do I do that? Do I used the format c: command in MS-DOS?

No, if you're planning on reformatting the windows drive to an ext filesystem you'll need to use gparted (easily done from an Ubuntu live cd).

It's as easy as opening gparted from the live cd System > Administration menu and right clicking the Windows partition and selecting format > ext? (eg. ext4 if you're using Lucid, other versions can use ext3 or ext2).

Further work will be needed to convert to /home or merge partitions. It is probably easiest and safest to  go with what oldfred suggested,
> ....or just a data partition just by reformatting it. Then you are not  moving your root and the massive data move that is required to move it..  IMO this is the best suggestion for you to consider. Also this makes no change to booting, except for the removal of the Windows boot entry by running "sudo update-grub" at the very end of the process.

---

