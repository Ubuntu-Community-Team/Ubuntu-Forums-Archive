---
title: "can't install ubuntu netbook remix using wubi"
date: 2009-12-12
forum: General Help
---

### Post by skinnytree on 2009-12-12
I am using wubi on Windows XP to install Ubuntu Netbook Remix. I select that option for the Desktop in the installer and when I click install I get the following error:  Ubuntu Netbook Remix Installer ==============================  An error occured:   Cannot download the metalink therefore the ISO  For more information see the log file c:\docume~1\user\locals~1\temp\wubi9.10ubuntu1-rev160.log  The log shows lots of stuff but most relevant lines appear to be the following:  12-12 12:13 DEBUG  downloader: downloading [http://releases.ubuntu.com/9.10/ubunt](http://releases.ubuntu.com/9.10/ubunt) u-9.10-netbook-remix-i386.metalink > C:\ubuntu\install 12-12 12:13 ERROR  CommonBackend: Cannot download metalink file [http://releases](http://releases). ubuntu.com/9.10/ubuntu-9.10-netbook-remix-i386.metalink err=[Errno 14] HTTP Erro r 404: Not Found 12-12 12:13 DEBUG  downloader: downloading [http://cdimage.ubuntu.com/ubuntu-netb](http://cdimage.ubuntu.com/ubuntu-netb) ook-remix/daily-live/current/karmic-netbook-remix-i386.metalink > C:\ubuntu\inst all 12-12 12:13 ERROR  CommonBackend: Cannot download metalink file2 [http://cdimage](http://cdimage). ubuntu.com/ubuntu-netbook-remix/daily-live/current/karmic-netbook-remix-i386.met alink err=[Errno 14] HTTP Error 404: Not Found 12-12 12:13 DEBUG  TaskList: ### Finished get_metalink

---

### Post by espo111 on 2009-12-13
I am getting this same error. tried downloading, having a copy of the ISO in the dir and it still errors out. both netbook remix and kubuntu netbook--same error.

any ideas ?

---

### Post by dcstar on 2009-12-14
> **espo111 said:**
> I am getting this same error. tried downloading, having a copy of the ISO in the dir and it still errors out. both netbook remix and kubuntu netbook--same error.

any ideas ?

The metalink files for the netbook version is no longer on that website - although metalink files for the other versions seem to be there!

I have just sent an e-mail to the webmaster.

---

### Post by Headloq on 2009-12-29
Pleased to see I am not missing a trick ... had precisely the same error & nothing fixed it. 

Thx, dcstar.

---

### Post by billyjmc on 2010-01-02
Here's one solution to your problem:

1) Download the Ubuntu Netbook Remix ISO

2) Download Microsoft's Virtual CD tool:
[http://download.microsoft.com/download/7/b/6/7b6abd84-7841-4978-96f5-bd58df02efa2/winxpvirtualcdcontrolpanel_21.exe](http://download.microsoft.com/download/7/b/6/7b6abd84-7841-4978-96f5-bd58df02efa2/winxpvirtualcdcontrolpanel_21.exe)
Extract it somewhere useful. Don't just let it download to the temporary directory, because then you'll just have to track it all down.

3a) Run VCdControlTool.exe from wherever you just extracted it to
3b) Click "Driver Control"
3c) Click "Install Driver"
3d) Click "Start"
3e) Click "Ok" closing the dialog
3f) Click "Add Drive" which will create a virtual CD drive, Z:
3g) Click "Mount" and point it to the Ubuntu Netbook Remix ISO

4) Go to My Computer, double click the Z: icon, and autorun should take over, giving you the option to do the Wubi install, or a full install.

5) You can now go back and delete the extra drive you created, and uninstall the driver, if desired. But being able to mount ISOs in Windows is pretty handy, so I keep everything installed. You can even make the drives persistent, so they stay mounted over reboots. Nice for video games that require the CDs....

---

