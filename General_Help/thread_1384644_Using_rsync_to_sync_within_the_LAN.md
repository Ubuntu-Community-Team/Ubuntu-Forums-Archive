---
title: "Using rsync to sync within the LAN"
date: 2010-01-18
forum: General Help
---

### Post by feffer on 2010-01-18
I want to use rsync to synchronize some folders on my LAN. I have this working with two scripts; one runs at the beginning of my work session and gets the latest directory tree from the server, and the other runs at the end of the session to put any local changes back on the server. My "get" script looks something like this:```
rsync -avuzb --backup-dir=/home/user/rsync_backup_dir --delete my_server:/home/bak/common_data/ /home/user/data
```This works well, and with the "b" option any file that has been deleted from the master directory tree on the server will be deleted from the local machine and moved to the local backup directory. This is a safety measure to prevent the loss of files through a mistake (on my part). 

The problem is the "put" script: ```
rsync -avuzb --backup-dir=/home/user/rsync_backup_dir --delete /home/user/data/ my_server:/home/bak/common_data
``` I want to run both scripts from the local machine, but the "put" script will not save deleted files to a backup directory. I tried using a remote backup directory like "my_server:/home/user/rsync_backup_dir" but this did not work. Is there a way to backup files deleted from a remote server from an rsync script run locally? 

thx,
feffer

---

### Post by bryanagee on 2010-01-18
You might want to look at [rdiff]("http://rdiff-backup.nongnu.org/") instead; it has the backup feature you are trying for already built in.

---

### Post by feffer on 2010-01-18
thx, I'm already using rdiff-backup as my main backup app for data. However, I want to sync specific files between workstations. In other words something like Dropbox functionality but for a simpler sync within my LAN.

After playing with rsync some more, I find it will move deleted remote files to a remote backup dir if the option is at the end like:```
rsync -avuzb --delete /home/user/data/ my_server:/home/bak/common_data --backup-dir=/home/user_on_server/rback
```Eventually, I want to move all my data to the server and work from there, but this is an interim solution. 

regards,
feffer

---

### Post by altonbr on 2010-01-18
I didn't really understand your problem, but maybe try my rsync over ssh script in my signature? I have simple flags called 'push' and 'pull' which is what I think you're looking for.

---

### Post by bryanagee on 2010-01-18
Sweet--I hadn't seen the --backup-dir option. Thanks for the tip.

---

### Post by feffer on 2010-01-22
@altonbr I got my problem solved, so I didn't see your post right away. I did check out your script Brett and it looks really good! I may well use it in the future. For overall data backup I am presently using rdiff-backup and it works OK. My current issue was syncing a few directories between my laptop and workstation. I tried Dropbox and it worked OK, but was overkill compared to rsync.

My original post came because I did not understand how rsync handled the --backup-dir option. Further study of the man page showed that the backup dir will be on the "receiving" machine. I had been trying to force it to save locally whether I was pushing or pulling -- no good. Once I understood that, my simple rsync script worked OK. 

Although, I didn't mention it in the original post, I am using rsync over ssh (which I think is the default) and have ssh configured with key pairs to enable easy login. It looks like your script automates the creation of this part of the process.

In the end, I have 4 very short scripts. One pushes the local machine dirs whether on the laptop or ws to my NAS server and merges it with whatever is already there. The second pulls files from the NAS and merges them with the local machine. This pair is used initially to combine the dirs from laptop and ws without deleting anything. Then I can sort them manually and archive off if needed. Once this is done and I have the dirs looking like I want on one machine, a third script is used to push the organized dirs to the NAS. This script uses --delete to mirror the local machine. Now I can use the fourth script to pull the organized dirs to my other local machine and they will be synchronized. After this, the "merge" scripts are not used unless I want to add a new directory outside of the original sync group. Now at the beginning of a work-session, I use the "pull and mirror" script to get the latest files which will be on the NAS. At the end of a work-session, I use the "push and mirror" script to load my new changes to the NAS. 

This works for me, but I consider it an interim solution. Ideally, I want to work everything from the server, but my current setup is rather slow, so I went this route. Thx for everyone's input.

---

