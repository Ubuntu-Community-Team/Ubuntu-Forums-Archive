---
title: "Downloaded video not playing in Windows"
date: 2011-11-28
forum: General Help
---

### Post by TheNixObserver on 2011-11-28
I use Windows XP SP2 with Ubuntu 10.04 on dual boot.  I use XP more than Ubuntu.  Once I downloaded videos from Youtube when using Ubuntu and later tried to play them in XP.  I use Media Player Classic and vlc.  MPC said that the file was not found while vlc displayed an error message.  This happened on two occasions when flv files downloaded in Ubuntu could not be played in XP, though I was able to play them in Ubuntu.

On another occasion, the flv files downloaded in Ubuntu got associated with some jpg files that I had downloaded in XP and the file size was reduced from 10 MB to 400kb.  Weirder still, I am unable to delete these files in XP and Ubuntu and I get the message that the directory is corrupt.  What is happening?:confused:

Is it that files downloaded in non Windows environment are not "registered" i.e. there is no registry entry for these files and so Windows is unable to find them?  What is the solution for these kind of situations?  Ditching Gates's product is not a solution :).

---

### Post by 3Miro on 2011-11-28
There are two possible issues here. One is that Windows relies on file extensions to identify the type of file that you have, if you change the filename then Windows doesn't know what to do with the file. Under Ubuntu, the system is able to "guess" which file is what (I am not sure about the details), hence you don't need to have any extension. I download Starcraft replays to watch off-line later and I never have extensions to the file names, Linux is fine, Windows doesn't know what to do.

Another possible issue is a problem with converting files between the Linux ext4 and Windows NTFS file system. Can you describe your HDD layout, how many partitions you have for Linux how many for Windows, are you downloading the files directly to NTFS or are you first storing them as ext4.

---

### Post by lisati on 2011-11-28
Please note: we do not support breaking the Youtube EULA by downloading videos. Please see this thread for more information: [http://ubuntuforums.org/showthread.php?t=1850955](http://ubuntuforums.org/showthread.php?t=1850955)

---

