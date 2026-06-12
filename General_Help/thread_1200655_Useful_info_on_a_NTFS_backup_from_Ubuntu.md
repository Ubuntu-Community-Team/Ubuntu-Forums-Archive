---
title: "Useful info on a NTFS backup from Ubuntu"
date: 2009-06-30
forum: General Help
---

### Post by irv on 2009-06-30
I thought this would be some useful information. I have a duel boot laptop with Vista and Ubuntu 9.04. I wanted to backup my user directory from Vista to a USB 1TB drive. My user directory has locked file in Vista so if I try backing them up in Vista it will skip them. I wanted to get the whole folder with all the files and folder in tack, so this is how I did it. 
I booted into Ubuntu and opened my Vista OS which required root permission (my user password).(I mounted my Vista partition). I drilled down to /media/OS/Users and selected my user directory which contains 29,918 files and folders which is a Type: folder (inode/directory)  33.2GB in size. Remember I am backing up from a internal HD (NTFS) to a USB external HD (NTFS) from within Ubuntu. By the way, I was running the external HD through a USB Hub. Here is my backup stats: Rate of transfer avg. was 9.1 to 9.9GB and the time of backup was 58 minutes. 
I tried this through Vista and after 2 ½ hours I quit the backup.
From all this I would say Ubuntu has come a long way since it first appeared. I can remember how much of a problem it was to get it to just read a NTFS drive alone write to it. I just want to say thanks to all who played a part in making this OS as great as it is today. Because of all your hard work, us users can benefit from your work in improving the best OS on the market. Even working with other OS's has become much easier because of your dedication.  
Thanks again
Irv

---

### Post by irv on 2009-06-30
I am going to upgrade my server so I did some backups on it today also.
I am running one OS, Ubuntu 8.04 and I did a backup of my /var/www/ directory. Again I did a copy over to a 250GB USB External Hard Drive. The speed was 16.9 to 17.8MB/sec. I had 578 files, 12.8GB it took about 11 minutes. I am not sure why it ran faster then ver. 9.04? Maybe it was the NTFS partitions on the 9.04 backup. This last backup was on a Ext3 to a Fat32 partition. Next I will have to try doing a backup from my Ext4 partition to a USB Drive and see what speed it will run at.

---

### Post by irv on 2009-06-30
Ok I did 9.04 with the Ext4 partition to 1TB NTFS USB External drive and here is how it went.
10,372 files, 12.1GB. Took about 30 minutes at 6.3 to 8.0MB/sec. still not is fast as my server running 8.04.

---

### Post by irv on 2009-06-30
> **irv said:**
> I am going to upgrade my server so I did some backups on it today also.
I am running one OS, Ubuntu 8.04 and I did a backup of my /var/www/ directory. Again I did a copy over to a 250GB USB External Hard Drive. The speed was 16.9 to 17.8MB/sec. I had 578 files, 12.8GB it took about 11 minutes. I am not sure why it ran faster then ver. 9.04? Maybe it was the NTFS partitions on the 9.04 backup. This last backup was on a Ext3 to a Fat32 partition. Next I will have to try doing a backup from my Ext4 partition to a USB Drive and see what speed it will run at.
Now this is strange. I am copying the files back on my server since I did a clean install of ver 9.04 and the copy back is very slow. 993.7Kb/sec. Not even a MB. It is going to take 3 hour and 43 minutes to bring them back. I wonder if there is a problem or a bug in  Nautilus 2.26.2? or maybe the kernel?

---

