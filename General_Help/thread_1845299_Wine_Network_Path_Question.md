---
title: "Wine Network Path Question"
date: 2011-09-16
forum: General Help
---

### Post by kaustik on 2011-09-16
I've migrated quite a few of our office PCs over to Ubuntu 11.04 and was going to slowly start converting the call center.  There is one app that doesn't have a linux equivalent called inView LAN Wallboard.  It installs fine in Wine but when I start it is trying to connect to the phone server.

Could not find the file \\XXXXXX\XXXXX\MISGEN.INI  Is there anyway I can map this so the software can locate the configuration file?  I can get to the server fine through the network, it is just the win app that is oblivious.

---

### Post by Toz on 2011-09-16
If you run **winecfg** (or select the **Configure Wine** menu option), there is a "Drives" tab where you can specify drive mappings. If the network share that you need to get to is already mounted, simply assign it a drive letter.

---

### Post by kaustik on 2011-09-17
I don't think assigning a drive letter to the network path will work since there isn't a drive letter in the expected path.

---

### Post by grahammechanical on 2011-09-17
I had a problem running a certain Windows file in Wine because Wine put certain files in folders that the program did not look in. The answer was to copy the files over to where the program expected the files to be.

It is possible to run a program through wine using a terminal, then you will see error messages which will help you work out what files are missing and where they should be. This is the command.

```
$ wine "c:\program files\appname\appname.exe"
```

Also, when you install wine you get a utility called Browse C: Drive. That lets you look through the wine file structure just like browsing a Windows C: drive. This will help if you cannot find that file that you are looking for. Wine uses a file structure similar to Windows.

Finally, the wine user guide might be of help to you in your situation.

[http://www.winehq.org/docs/wineusr-guide/index]("http://www.winehq.org/docs/wineusr-guide/index")

Regards.

---

### Post by kaustik on 2011-09-17
Thanks for the link.  This might help me out.

---

4.3.2. Network Shares

Windows shares can are mapped into the unc/ directory so anything trying to access \\myserver\some\file will look in ~/.wine/dosdevices/unc/myserver/some/file/. For example, if you used Samba to mount \\myserver\some on /mnt/smb/myserver/some then you can do

            ln -s /mnt/smb/myserver/some unc/myserver/some
          
to make it available in wine (don't forget to create the unc directory if it doesn't alrady exist).

---

I'm a little unclear if putting this information in will actually help wine see the server the software is trying to access or if it is expecting me to put the files in the directory I create and mount.  If the latter is the case that won't work since I need to connect to the actual phone server.

I won't be back at work until Monday to test, but at least I have something to go on.  Thanks for your help.

---

### Post by Toz on 2011-09-17
All I had to do was mount the share locally in ubuntu using cifs and then, using winecfg, assign a drive letter to that mount point. From within the wine application, I then have access to that drive letter which is actually the mount point. There was no need for linking.

---

