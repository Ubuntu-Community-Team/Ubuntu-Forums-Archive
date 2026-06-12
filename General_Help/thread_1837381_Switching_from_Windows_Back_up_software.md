---
title: "Switching from Windows Back up software"
date: 2011-09-01
forum: General Help
---

### Post by SuperFreak on 2011-09-01
I have a few external drives that I have always backed up with a Windows utility called NTI Shadow which does incremental back ups. Eventually I want to use only Linux (I have a dual boot with XP now). Is there a Ubuntu back up software that will: 1) do back ups to NTFS 2) do incremental back ups 3) continue the back ups that NTI Shadow does without having to reformat my disks and starting over.
The hard drives contain about 1 TB of material at present

Second question is how would I keep these disks defragged as they are NTFS . Is there a simple Ubuntu utility that can defrag NTS disks?

The reason I will be moving to a Linux only system is I have a license for my present computer for XP and plan to build another computer and get rid of my old one with the license. I don't want to have to buy a new Windows OS just for the above purposes

---

### Post by searchfgold6789 on 2011-09-01
I recommend rsync. Also, you can look [here]("http://http://www.techrepublic.com/blog/10things/10-outstanding-linux-backup-utilities/895") for others. Otherwise, I'm sure you could find what you want with a quick google search.
Secondly, There is no NTFS defragmenter in linux.

---

### Post by SuperFreak on 2011-09-01
Would the files backed up by rsync be readable by a Windows machine? From what I read rsync compresses files or pieces of files. I really am not after compression but backups that preserve old files on the external drive and add new files and can be read by both Windows and Linux computers. The link to other back up systems seems to be broken but as you say I can google for other back up systems

---

### Post by drdos2006 on 2011-09-01
Here is how I set up my incremental, non-compressed backup file.
I loaded the command into a bash file named "backup-web.sh" and run it from the terminal with "bash backup-web.sh".

```

    #!/bin/bash
  rsync --verbose --recursive  --archive --modify-window=1 --times --update    --delete-after  --progress --itemize-changes --log-file=/home/me/Documents/backup-log-web.txt	  /media/sda2/Install/WebPages/*  /media/sda2/Install/Backup/WebPages

```

The commands can be shortened to -vramtu ... Check out "man rsync"

regards

---

### Post by SuperFreak on 2011-09-01
I have started to lok at the Man pages and it looks a little daunting. I seem to have grsync on my computer which gives a graphical interface for rsync I presume. This seems to be an easier way of using rsync. Thanks for your help.

Now if I can only find a way of defragging the external drives from time to time

---

