---
title: "Copying entire partitions"
date: 2010-02-27
forum: General Help
---

### Post by Hybird on 2010-02-27
Ok, I need help copying my partitions so I can take apart my computer and fix a problem and then re-install the partitions. Hopefully I won't have to re-install, but I want to make backups just in case

Here's what i have:

-HP laptop with a windows (NTFS) and an Ubuntu (ext3) partition ~ 500GB total
-Iomega 1TB external hard drive partitioned into a 500GB NTFS storage, 250GH BLANK ext3 Linux Backup, and 250GB BLANK NTFS Windows Backup.

I want to copy my windows and linux to their respective 250GB spaces on the External HD.

Questions:
1.) Can you direct me to places on the net that describes this in detail?
2.) Can I copy a partition while running that partition?
3.) Will copying C:/ in windows over to the external HD copy entire partition?
4.) Can I copy a Laptop partition to a external HD partition that is bigger?
5.) Do I have to use partition manager software or can I do this from terminal/cmd prompt?

Sorry for all the questions.

---

### Post by 2hot6ft2 on 2010-02-27
> **Hybird said:**
> Ok, I need help copying my partitions so I can take apart my computer and fix a problem and then re-install the partitions. Hopefully I won't have to re-install, but I want to make backups just in case

Here's what i have:

-HP laptop with a windows (NTFS) and an Ubuntu (ext3) partition ~ 500GB total
-Iomega 1TB external hard drive partitioned into a 500GB NTFS storage, 250GH BLANK ext3 Linux Backup, and 250GB BLANK NTFS Windows Backup.

I want to copy my windows and linux to their respective 250GB spaces on the External HD.

Questions:
1.) Can you direct me to places on the net that describes this in detail?
2.) Can I copy a partition while running that partition?
3.) Will copying C:/ in windows over to the external HD copy entire partition?
4.) Can I copy a Laptop partition to a external HD partition that is bigger?
5.) Do I have to use partition manager software or can I do this from terminal/cmd prompt?

Sorry for all the questions.
Answers:
1.)
[http://www.justlinux.com/forum/showthread.php?threadid=134457](http://www.justlinux.com/forum/showthread.php?threadid=134457)
[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)
[http://ubuntuforums.org/archive/index.php/t-1080626.html](http://ubuntuforums.org/archive/index.php/t-1080626.html)

2.) No. since it would be changing while copying it. At least I wouldn't.

3.) Yes

4.) Yes

5.) No, and yes

---

### Post by Hybird on 2010-02-28
Great! Thanks for the quick response, I can finally tear into my comp and fix its noisy CPU fan.

---

