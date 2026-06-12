---
title: "Need assistance with RSNAPSHOT"
date: 2012-07-19
forum: General Help
---

### Post by Tilde88 on 2012-07-19
Hello, world! :) First time poster. Wanted to say before anything, thanks for all the info I have been able to acquire in these forums over time browsing by. But now, I am really in a jam, and have spent about a week and a half on this project but am now sincerely stuck. Here goes...

 Well, I am an intern at a company which troubleshoots our clients' PC / Network issues remotely. My project is as follows:
1. Using Ubuntu (or any Linux platform) backup an entire filesystem, and incrementally back it up on the hour every hour. I assume I don't HAVE to use Linux to make the FS backup, but I believe this is the best route, as it is able to access files which are live (open or in use). Here is where it gets tricky. 
  
  I can make rSnapshot pull the entire system, but only if it is from Ubuntu/Linux. Using the same rsnapshot.conf, I change only the local IP to connect to a Windows 2003 Server R2, and the source to backup ("test@192.168.1.115:/cygdrive/c/"). SSH is setup on the Windows box, and I can putty in, put my password, get the DOS to actually run. I also have Cygwin installed with all the rSync, rSnap, SSH, SSL, Cygrunsrv, etc.. installed on the Windows box. I also set the Environment Variables, and added "C:\cygwin\bin;" into the PATH field (for cygwin to work properly). However, when I run "rsnapshot hourly" [from my Ubuntu terminal] to the Windows box, it connects, then asks me if I want to accept the connection since it is an unknown host or whatnot. After accepting, and connecting, Terminal just hangs there until I Ctrl+C. I am attaching my rsnapshot.conf which I use   for the Windows box, as well as the one which I use to pull from another Ubuntu box. Again, I can pull from Ubuntu, but not from Windows.

  Furthermore, I notice that even when pulling from an Ubuntu box, many files are denied permission (though I always run as "sudo rsnapshot"). How may I surpass these errors? How may I force rsnapshot to copy Windows files that are in use? I was able to PUSH the Windows box to Ubuntu with rSync, but it still had a few missing files. I need the rsnapshot of Windows to be as complete as possible (bootable). 
  Finally, I would like to convert the first full backup into a Virtual Image which may be run in a VMWare/Vsphere client, I know, now I am asking too much... I'm sorry! I have worked nonstop these past 10 days or so... But I am at a brick wall!

  Phew, I know it was a lot to read, and evenmoreso to help... But I thank you profusely for any information you may have for me. TIA!!! (Reminder, the 2 rSnap confs are identical except for the user/IP.)

Edit: Not sure that it matters, but the Windows and Ubuntu that I pull FROM, are virtualized. My actual PC that receives (er- supposed to) the data, is physical Ubuntu install.

---

### Post by Tilde88 on 2012-07-19
> josh@Josh-Laptop:~$ sudo rsnapshot hourly
require Lchown
Lchown module loaded successfully
Setting locale to POSIX "C"
echo 3667 > /var/run/rsnapshot.pid 
mkdir -m 0700 -p /home/josh/Desktop/backup/ 
mkdir -m 0755 -p /home/josh/Desktop/backup/hourly.0/ 
/usr/bin/rsync -av --archive --hard-links --human-readable --inplace \
    --numeric-ids --link-dest=/home/josh/Desktop/backup/backup2/ \
    --rsh=/usr/bin/ssh test@192.168.1.115:/cygdrive/c/ \
    /home/josh/Desktop/backup/hourly.0/localhost/ 
test@192.168.1.115's password: 

After entering my password (which it does accept), I just have a blank blinking cursor under it. It makes the rsnapshot_root/ directory as instructed in the conf, and it has the proper RWX values. Thanks again, all!

---

### Post by Tilde88 on 2012-07-20
Small bump :\, sorry please don't hate me!

---

