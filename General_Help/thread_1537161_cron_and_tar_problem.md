---
title: "cron and tar problem"
date: 2010-07-23
forum: General Help
---

### Post by Alan.Brown on 2010-07-23
Greetings Enlightened Folks!!  :grin:

I have a script  - called 'backit' - to back up files to a tarball - listed below (<backup.lst> contains files I want backed up)

    #!/bin/bash
    # 22/7/2010
    # Backup important files
    cd ~
    tar cvfz .backup/backup.tar.gz -T .backup/backup.lst
    cp .backup/backup.tar.gz /media/Archive/.backup


Typing 'Backit' in the shell works very well producing a backup file, <backup.tar.gz>,  of 2 298 953 bytes and contains all the correct files.

So far, so good!   :razz:

I put a line in crontab - 

    0 * * * * /home/alan/bin/backit

The program runs every hour on the hour and produces the <backup.tar.gz> file.    However, this file contains only some of the files and has a size of 76 762 bytes.   Using "tar tvf backup.tar.gz" lists some of the files and ends with an error indicating an EOF encountered before the end of file.     :sad:

If the script executes correctly when typed into the shell, why does it not run to completion correctly when run by cron?

Thanks for you help.

Alan.

---

### Post by DaithiF on 2010-07-23
Hi,
see [http://georgia.ubuntuforums.org/showpost.php?p=7954400&postcount=6](http://georgia.ubuntuforums.org/showpost.php?p=7954400&postcount=6)
You have 2 choices, either remove the verbose flag (v) from your tar options, or put MAILTO="" at the top of your crontab.

---

### Post by Alan.Brown on 2010-07-23
DaithiF

Thank you for your very quick reply

I removed the Verbose option and the process works fine now

Thank you

Alan

---

### Post by DaithiF on 2010-07-23
Hi, no problem, & welcome to the forums.  To mark a thread as solved, click on Thread Tools -> Mark thread as solved

cheers

---

### Post by Alan.Brown on 2010-07-23
Thanks!!   I just found it

Alan

---

