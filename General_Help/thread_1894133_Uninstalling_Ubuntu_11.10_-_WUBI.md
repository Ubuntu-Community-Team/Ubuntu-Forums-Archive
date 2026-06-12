---
title: "Uninstalling Ubuntu 11.10 - WUBI"
date: 2011-12-11
forum: General Help
---

### Post by Panthers493 on 2011-12-11
TLDR: I can't uninstall Ubunutu even though I used WUBI. The option to remove isn't in the Remove Program feature of Windows.

Note: I'm using Windows 7

I searched around for a solution to this, but couldn't find one. I understand that there SHOULD be an uninstall option in the Remove Programs area of Windows, but its not there.

I have confirmed that I used the WUBI installation (At least I'm pretty sure I did.. the file I downloaded from ubuntu.com was called wubi.exe...) and went with the default installation. After reboot, my laptop automatically booted Ubuntu and I experimented with it a little before going to Windows to download drivers so my wireless card would work with Ubuntu. 

When I switched back to windows, the screen started to flicker and commands weren't going all the way through (For example, I could scroll down, and it would go for half a second and then flash back to the original position. Each screen flicker cancels out any mouse click command that I was in the process of giving.)

I have done a full virus scan and tried restoring a previous point prior to installing Ubuntu, but neither fixed the problem. I am confident that the issue is with the Ubuntu install and would like to install it, but I can't find the uninstall file and its not in the Remove Programs where it should be.

---

### Post by critin on 2011-12-11
You might check your Windows disk management and see if another partition has been added for ubuntu.  It's either Wubi installed inside of Windows, or it was installed in a side-by-side Windows partition .

---

### Post by bcbc on 2011-12-11
The entry is "Ubuntu" not "Wubi". Maybe that helps. Otherwise, find and run C:\ubuntu\uninstall-wubi.exe

Maybe running System restore removed the entry in Add/remove

---

### Post by Panthers493 on 2011-12-11
@Critin - I checked and there isn't another partition. The only two partitions are the main Windows partition and a recovery partition. 

@bcbc - I checked for the uninstall before and after the recovery tool was ran, and it wasn't there in either case. I have checked for the uninstall file you mentioned and I can't find it either.

Edit: The directory is there, and all the folders, but there aren't any files in the folders.

The installer ran all the way through, and I waited to restart when it asked me too, so I don't think its a problem with that.

I could try to upload a video to show you what exactly is happening on Windows. Its pretty annoying to deal with, and makes some tasks impossible to do. 

Thank you for your time by the way.

---

### Post by bcbc on 2011-12-11
So there are no more files, but you still get a boot menu offering Windows and Ubuntu? And if you select Ubuntu you get errors?

If that's the case, you'll need to use Windows' command line tool "bcdedit" to remove the boot entry, or you could install a tool called easyBCD.

For bcdedit, go to an administrator command prompt (hit windows key, type cmd, right click above on cmd.exe and Run as administrator). Then enter: bcdedit to see the current boot entries. Look for the guid corresponding to the ubuntu entry and remove it:
```
bcdedit /delete {guid}
```

---

### Post by Panthers493 on 2011-12-11
I get a boot menu offering both Windows and Ubuntu, and both load without errors other than Windows, which when I log in displays about 20 error messages saying that it can't load the H drive, which doesn't exist. (There aren't any USB devices plugged in and there is not a CD in the drive.) I've checked the disk management and there isn't a H partition listed there.

Ubuntu loads without error, so I assume the files are somewhere, but I don't know where.

---

### Post by bcbc on 2011-12-11
Where did you install Ubuntu (which 'drive')? You said the \ubuntu directory was empty but it's not possible for it to boot in that case.

---

### Post by Panthers493 on 2011-12-11
Where ever it is set to install by default in the wubi.exe install is where I installed it. The install didn't give me the option to set an install directory, just a drive, which was set to drive C.

---

### Post by Panthers493 on 2011-12-11
Update:

Alright, turns out that port H is my SD Card drive, which was malfunctioning and reading that something was in it, and updating from that to being empty rapidly, so what was happening was that dialog was opening and closing before I could see it.

I disabled the port and the solution has been fixed. If it was because of Ubuntu or not, I don't know. I don't really care though since I never use SD cards. 

Thank you everyone for trying to help, its much appreciated and nice to see a community so quick to respond with advice :)

---

