---
title: "Rosetta Stone v3 cd files not displaying"
date: 2009-10-25
forum: General Help
---

### Post by sedwa on 2009-10-25
Using Ubuntu 8.04 or 9.04 with Rosetta Stone version 3 application cd; the cd is mounted and the desktop shows the cd (RS_App) but when you open it is empty. (Show hidden files does not help).  From the terminal cd to /media/cdrom0 and ls also shows no files, evan as sudo.  However there is something there because df -h shows: /dev/scd0             409M  409M     0 100% /media/cdrom0, so it does "see" the contents.  The cd player works (will display the content of other cds) and the cd itself will work on my windows machine and displays the content.:confused:   I am trying to install with wine (Wine Hq indicates it will work) but need the "hiding" exe files.  Thanks

---

### Post by cellstije on 2010-06-03
I am having the extact same problem on Kubuntu 10.04, with Rosetta Stone 3.4.3A original CD. On linux it shows an emty directory (for the CD). Works fine under Mac OSX 10.5.

Typing dmesg, I get:

VFS: busy inodes on changed media or resized disk sr0
ISO 9660 Extensions: Microsoft Joilet Level 1
ISO 9660 Extensions: IEEE_P1282

I could not find any solution on the ubuntu forums.
Found another guy having the same problem on Fedora11.

[http://forums.fedoraforum.org/showthread.php?p=1305174](http://forums.fedoraforum.org/showthread.php?p=1305174)

The reply does not make any sense (at least to me): wine knows were 
the mount direcory for the CD is ... I can not find the .exe!

If anyone has an advice, it would be very much appreciated

c.

---

### Post by Flopy on 2010-06-16
I had the same problem, that the CD was being recognized but there were no files in it. I solved it by following this post on the winehq website: [http://appdb.winehq.org/commentview.php?iAppId=1867&iVersionId=15404&iThreadId=51180](http://appdb.winehq.org/commentview.php?iAppId=1867&iVersionId=15404&iThreadId=51180)

How I did it was to right click on the RS_App CD icon on the Desktop and select Copy Disc. I saved it as an ISO file, then used Archive Manager to extract it to a folder. Once the files were extracted, I had to make them executable by right-clicking on the folder, selecting Properties -> Permissions, and checking the Allow  executing this program... Then I could finally go into the folder, right-click on setup.exe and selected Run with Wine. Alternatively, you can select Open with, and either select or type "wine" on the command box.

From there on, I let the program decide on the default paths and everything installed without problems! \\:D/

---

### Post by thatstheguy on 2010-06-17
> **Flopy said:**
> I had the same problem, that the CD was being recognized but there were no files in it. I solved it by following this post on the winehq website: [http://appdb.winehq.org/commentview.php?iAppId=1867&iVersionId=15404&iThreadId=51180](http://appdb.winehq.org/commentview.php?iAppId=1867&iVersionId=15404&iThreadId=51180)

How I did it was to right click on the RS_App CD icon on the Desktop and select Copy Disc. I saved it as an ISO file, then used Archive Manager to extract it to a folder. Once the files were extracted, I had to make them executable by right-clicking on the folder, selecting Properties -> Permissions, and checking the Allow  executing this program... Then I could finally go into the folder, right-click on setup.exe and selected Run with Wine. Alternatively, you can select Open with, and either select or type "wine" on the command box.

From there on, I let the program decide on the default paths and everything installed without problems! \\:D/

I couldn't figure out how to save it as an ISO file after burning the Application CD; then I couldn't figure out to extract the files to a folder using the Archive Manager.  Please help!

Thanks,

Chris

---

