---
title: "Wubi will not open on my computer."
date: 2012-01-22
forum: General Help
---

### Post by MourningsEnd on 2012-01-22
I click Wubi and it does not do anything at all. :/

[http://www.youtube.com/watch?v=HlriyU2qnZ8](http://www.youtube.com/watch?v=HlriyU2qnZ8)

---

### Post by MourningsEnd on 2012-01-22
I try to open Wubi and it does nothing.

I see it in Task Manager for a few seconds then it goes away.

Help?

---

### Post by MourningsEnd on 2012-01-22
No one knows?

---

### Post by MourningsEnd on 2012-01-22
If you watched the video I did Run as Admin..

---

### Post by mörgæs on 2012-01-22
For Wubi problems I would suggest 
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

---

### Post by MourningsEnd on 2012-01-22
I already looked at that..

I used an older version of Wubi and that one worked, but the latest one does not.

This is some Wubi log in my %temp% folder.

---

### Post by mörgæs on 2012-01-22
Please don't create multiple threads on the same topic. Merged. 

Also, bumping is not good manners.

---

### Post by MourningsEnd on 2012-01-25
Does anyone have a solution?

---

### Post by Karlchen on 2012-01-25
Hello, MourningsEnd.

I assume that what you wish to install is Ubuntu 11.10 Desktop 32-bit using Wubi.

Unless you have already done so, please, download the [**Ubuntu 11.10 Desktop 32-bit ISO**]("http://releases.ubuntu.com/oneiric/ubuntu-11.10-desktop-i386.iso") file and store it e.g. in your folder C:\Users\<YourWindowsAccount>\Downloads.
Next get the appropriate _**[[B]Wubi.exe**]("http://releases.ubuntu.com/oneiric/wubi.exe")[/B]_ and save it in the same folder where the ISO file is.

Launch Wubi.exe as Administrator - which you did - and tell Wubi to use the ISO file located in the same folder.

Hopefully, this way it is going to work. - I admit that the error message in the logfile wubi-11.10-rev245.log did not really ring a bell with me.

Kind regards,
Karl

---

### Post by MourningsEnd on 2012-01-25
I am 64-bit, and tried that.

Wubi just does not open.

---

### Post by bcbc on 2012-01-26
I actually have seen this error before, surprisingly. You need to create the missing startup folder... just got to remember what it is.

This is for Win 7 I guess:
C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup

Refer to this for more info: [http://askubuntu.com/questions/92157/why-does-wubi-exe-for-ubuntu-11-10-not-run-on-windows-7-32bit](http://askubuntu.com/questions/92157/why-does-wubi-exe-for-ubuntu-11-10-not-run-on-windows-7-32bit)
and the bug report here: [https://bugs.launchpad.net/wubi/+bug/910948](https://bugs.launchpad.net/wubi/+bug/910948)

---

### Post by MourningsEnd on 2012-01-30
I already had a StartUp folder..

To be safe I deleted it and re-made it.

Does not work.

---

### Post by bcbc on 2012-01-30
> **MourningsEnd said:**
> I already had a StartUp folder..

To be safe I deleted it and re-made it.

Does not work.

Strange because that's exactly the same dump as the other user had. In their case the registry entry was there but the folder was not. Can you confirm the contents of the registry (use regedit) for this key:
'HKEY_LOCAL_MACHINE', 'SOFTWARE\Microsoft\Windows\CurrentVersion' 
'\Explorer\Shell Folders', 'Common Startup'

And then confirm that the directory entered there also exists on your hard drive?

---

### Post by MourningsEnd on 2012-01-30
I just created the registry item, Wubi still does not work.

I even restarted to make sure.

Startup folder exists.

---

### Post by chughes27 on 2012-01-30
I also had a problem with the Wubi installer, not it starting in general but the install was very buggy and rarely started up properly.

What I did after this was downloaded the Ubuntu .iso image, mounted it as a virtual disk image, then ran the virtual disk and installed from there. Took a lot less time than the Wubi normal installer, and it worked like a charm.

I hope this helps with your install!

---

### Post by MourningsEnd on 2012-01-30
Does it install it along side Windows like Wubi?

---

### Post by chughes27 on 2012-01-30
Yes. The .iso contains Wubi, it is just running it from a virtual installation cd

---

### Post by bcbc on 2012-01-30
Running wubi from a CD, your computer, or a virtually mounted ISO... how will that prevent it checking the startup folder and failing?

The startup folder thing was introduced recently - I think 11.04. So just install [10.04]("http://releases.ubuntu.com/10.04/") instead. But if you saw that the registry entry was missing then this is most likely the issue - you need to double check the startup folder. Look at the wubi log each time and check - if it still says Startup Folder = None then it's going to fail.

---

### Post by chughes27 on 2012-01-30
> **bcbc said:**
> Running wubi from a CD, your computer, or a virtually mounted ISO... how will that prevent it checking the startup folder and failing?

I'm only trying to find a solution. I'm not the smartest person around but this is what worked for me.

---

