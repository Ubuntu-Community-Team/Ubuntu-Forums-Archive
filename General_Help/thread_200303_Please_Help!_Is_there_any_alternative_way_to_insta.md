---
title: "Please Help! Is there any alternative way to install kubuntu dapper??"
date: 2006-06-20
forum: General Help
---

### Post by CyberAngel on 2006-06-20
I have installed dapper amd64 on my home machine and it runs smoothly!
I am very happy with it :)

Now after the extended test on my home machine, the time has come to upgrade my office machine (It used to run breezy).
I am putting the Kubuntu Dapper DVD into my DVDRom and first of all I am trying the alternative installation (Text mode) because I want to format my partitions as reiserfs and the graphical installer of kubuntu doesn`t support reiserfs formating :(
Everything seems OK and the installer keeps on going to the file copying until it stuck (I left it there at least 15 minutes) to 86% (Preparing to configure libuiconf4.2).
The system is still functioning (If you press alt+f2 you are entering another console) but the installer hungs there ](*,) 
So I am trying my second chance... The graphical installer..
I have already formated my partitions using reiserfs from text so when I am entering the livecd I am starting the installer. I am not changing the partitions (Just reformat them. Works fine if it is already reiserfs) and continuing the installation.
Everything again seems fine until 62% this time (Copying Files 1:51 Remaining) that that the installer is crashing with the following error!!!!

```
Traceback (most recent call last):
  File "/usr/bin/ubiquity", line 130, in ?
    install(sys.argv[1])
  File "/usr/bin/ubiquity", line 55, in install
    ret = wizard.run()
  File "/usr/lib/python2.4/site-packages/ubiquity/frontend/kde-ui.py", line 311, in run
    self.process_step()
  File "/usr/lib/python2.4/site-packages/ubiquity/frontend/kde-ui.py", line 734, in process_step
    self.mountpoints_to_summary()
  File "/usr/lib/python2.4/site-packages/ubiquity/frontend/kde-ui.py", line 1047, in mountpoints_to_summary
    self.progress_loop()
  File "/usr/lib/python2.4/site-packages/ubiquity/frontend/kde-ui.py", line 524, in progress_loop
    raise RuntimeError, ("Install failed with exit code %s; see "
RuntimeError: Install failed with exit code 1; see /var/log/installer/syslog and /var/log/syslog

```

How can I install dapper on that machine when neither of two ways to install works?????

---

### Post by Lunar_Lamp on 2006-06-20
Have you checked the integrity of the cd by it's MD5 checksum?  It may have been damaged in transit even if it's worked before.

---

### Post by maskd on 2006-06-20
Try reburning the cd at a slower speed, it fixed all issues that I had with my installer

---

### Post by CyberAngel on 2006-06-20
[QUOTE=maskd]Try reburning the cd at a slower speed, it fixed all issues that I had with my installer[/QUOTE]

The Disc was burned at 4x so I don`t think that`s the fault :(

To Lunar_Lamp: I checked the md5 and it is OK :(

Anyway I am rebooting now (I am online using the live cd now) to try the text installer again. I will let it more time to the point it hanged.

I hope to pass it this time..
Wish me luck :)

Byeee, I will return with news about the installation later (I hope from this machine with dapper Installed)

---

