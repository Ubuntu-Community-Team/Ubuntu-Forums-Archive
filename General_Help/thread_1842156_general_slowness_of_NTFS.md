---
title: "general slowness of NTFS?"
date: 2011-09-10
forum: General Help
---

### Post by princeofnam on 2011-09-10
lately I've had to split my time between ubuntu and windows almost evenly.  that means it's a hassle to access the majority of my files through extexplorer.  I think I may format my /home/ directory to NTFS.  or perhaps just use a communal partition between Windows and Ubuntu.  Is Ubuntu's access speeds to NTFS formatted partitions significantly slower tha ext4?

---

### Post by LowSky on 2011-09-10
DO NOT FORMAT ANY LINUX PARTITION TO NFTS!!!!

NTFS does not use file permissions and will screen up your /home folder.

A better idea would be to use dropbox for file sharing over a system, or create a large NTFS folder, and then link the files to be shared within your home folder.

so lets say you have a bunch of music on a NTFS partition.

simply in a terminal you can make a link folder by using the this command
```

ln -s /path/to/ntfs/share /home/username/Music
```

---

### Post by princeofnam on 2011-09-10
If I began saving and opening files from the Windows NTFS partition would the speed at which it performs that be noticably slower?

---

### Post by SoFl W on 2011-09-10
For my dual boot system I had a partition I labeled "WinShare" which was formated NTFS.  I used that when I wanted to transfer files.  I don't recall exactly what I did but I am almost sure I formated it from the Windows boot.  C: = Windows system, D: = WinShare.  Winshare was accessible from both the Linux side and Windows.

---

### Post by princeofnam on 2011-09-10
Hmm.  Why have a separate partition from windows though unless they're physically separate HDs?  Economically I think it'd make sense to have one giant Windows partition and a smaller Linux partition right?

---

### Post by Enigmapond on 2011-09-10
No...at least not in my world. I spend most of my time on Linux and only do some Music editing with 'doze. I have one HDD the larger portion is ext4 but I do share some files with Win7 so I have 3 partions. Win7 OS, a NTFS share partition and then Ubuntu/ext4. That works best for me. I don't encounter any "slowness" at all.

---

### Post by princeofnam on 2011-09-10
Why have a share partition separate from your Windows 7 OS partition though if both are NTFS?  To prevent loss of files in the event that you plan to format the Windows 7 OS partition?  Is it best to make the share partition using Ubuntu or Windows you think?

---

### Post by Enigmapond on 2011-09-10
Well no...I keep the win7 OS partition quarantined..so it can't effect anything else if corrupted by anything and since I share music files between the two it only makes sense to have it NTFS so I can record/edit in windoze and and still access them with Ubuntu. Given the reverse I couldn't edit the files...windows wouldn't see them. The programmes I use are strictly windows and don't run in Linux...Reason, Cubase & Adobe Audtions. The three and only reasons I even KEEP windows...

---

### Post by princeofnam on 2011-09-10
No sorry, I plan to make it NFTS, I just mean what application is best to create new share partitions between Ubuntu and Windows 7, e.g. Gparted, Disk Manager on Windows, etc.

---

### Post by Enigmapond on 2011-09-10
Oh.. I would just use gparted. The way I did it was to boot into a liveCD of Ubuntu and did it that way. The drive needs to be un-mounted to resize and partition.

---

