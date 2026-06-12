---
title: "burning split tar.gz files to DVD"
date: 2010-02-04
forum: General Help
---

### Post by jtd361 on 2010-02-04
I am working on a backup solution for my Ubuntu web server and so far this is what I have.

I am using rsync to create rotating snapshot style backups of my web files and sending them via SSH to a remote location in order to burn them for offsite storage.  This is all working perfect.  The remote machine is a Windows Server 2003 which has data that I combine with my web files before burning.  I have cygwin installed on the remote server in order to archive and compress the entire backup using tar.  (This is not a post about cygwin, I just thought I would mention it in case anyone was wondering how I was running Linux commands after transferring it to the Windows box). After compression, the backup is over 12gb.  The next step in my process is to split this tar.gz file into smaller chunks in order to burn them to DVDs.  I use dual layer DVDs which are 8.5gb storage size.  I also use cygwin to split the tar.gz into multiple 2gb files using the split command.  When I burn them, I only put 3 files on each disk totaling 6gb to leave some padding in case this was a problem.  The burn completes and says successful, although it errors out when in verification.  I have tried this multiple times and it seems to fail verification at the same point every time which leads me to believe that it has something to do with the data.  I have also done tests such as creating smaller backups with completely different data and brning that to a CD-R which worked fine, so I'm convinced this process can work, I just cant get it to work in the right situation.  I have also tried burning one of the 7 split files to a dual DVD which also worked fine.  I'm wondering if their is a chunk of data that is causing this problem in one of the other split files?  Any help would be very appreciated.

I am using Ubuntu 8.04 LTS, SH-S182D Burner, and using Nero 6 for burning software.

Thanks.

---

### Post by ajgreeny on 2010-02-04
Have you tried splitting the tar.gz file on your linux box when and where it is made instead of sending it to windows and using cygwin?  Perhaps you can't do that because of the combining with files already on the windows box, and I have no idea about using cygwin so may be barking up the wrong tree entirely, but the idea seems worth raising.

---

### Post by jtd361 on 2010-02-05
The problem is that the files that im backing up from the Ubuntu server are minimal in size and could easily fit on one disk, so there is no need for a split.  It's only after I combine all these files from the windows box into an archive that I need to split them into DVD size.  As far as I know, the cygwin version of of split works the same way.

---

