---
title: "Offline Install Problems (NOTE: I did do my research)"
date: 2011-11-07
forum: General Help
---

### Post by WillemVoigt on 2011-11-07
I am running Ubuntu 11.10 and I am trying to install several applications on an offline PC. I have heard of "Keryx", but that does not work very well. "APTonCD" was next on my list. This works perfectly when creating a DVD that contains all the needed DEB files, but unfortunately this application is also needed on the offline PC. After much research I have found that I need to copy all the DEB files from the DVD that was created with "APTonCD" to the "/var/cache/apt/archive" directory, after which I need to run the "sudo apt-get install vlc" command (where VLC represents any other application I need to install).
The first problem I encountered was when trying to copy the DEB files to the required directory. The system generated an error stating "Permission Denied". I eventually found a solution where I have to run the "gksu nautilus" command, after which I can easily copy the DEB files to where I need them. I then ran the "sudo apt-get install vlc" command and everything worked fine.
 
Now for the kicker.
 
I formatted the PC, did a clean install and tried the above process. This time the "gksu nautilus" command generates an error stating that I need to create the ".config" file in my root directory (although this already exists). I ran the "mkdir /root/.config/nautilus" command. This command only works once I have attempted to run the "gksu nautilus" command. If I run the "mkdir /root/.config/nautilus" before running the "gksu nautilus" command an error message is generated stating that the directory cannot be found.
 
So I run the "gksu nautilus" command, receive the error message, run the "mkdir /root/.config/nautilus" command and the run the "gksu nautilus" command. This now allows me to copy all the DEB files into the "/var/cache/apt/archive" directory.
 
When I try to run the "sudo apt-get install vlc" command the system generates an error stating that the package cannot be found.
 
Why is this happening? The exact same process is generating different results.
 
I did find another command that installs ALL the DEB packages copied to that directory, but there are certain applications that I not want to install on the PC. Also, this command will also install any random packages that might have been copied on the DVD created with "APTonCD" and I don't like having random packages on my PC.
Any advice?

---

### Post by robert shearer on 2011-11-07
After copying the deb files to the /var/cache/apt/archive have you done...
```
sudo apt-get update
```
Then try...
sudo apt-get install <whatever package name>

---

### Post by WillemVoigt on 2011-11-07
If I understand this command correctly, the ONLY thing that will be altered is the "sources.list" file found in the "/etc/apt/" directory and NOTHING else will be altered. Will it be the same if I just replace that file with the "source.list" file from the online PC that has all the applications installed? What about those "unwanted" DEB files that will appear on the "source.list" file. Or am I right in saying this is JUST a list with the names and locations of the DEB files, and just because these DEB files are on the list does not mean that they will be installed?

---

### Post by robert shearer on 2011-11-07
> **WillemVoigt said:**
> If I understand this command correctly, the ONLY thing that will be altered is the "sources.list" file found in the "/etc/apt/" directory and NOTHING else will be altered. Will it be the same if I just replace that file with the "source.list" file from the online PC that has all the applications installed? What about those "unwanted" DEB files that will appear on the "source.list" file. **Or am I right in saying this is JUST a list with the names and locations of the DEB files, and just because these DEB files are on the list does not mean that they will be installed?**

The bolded as I recall. It has been some time since I used aptoncd, however, once the packages have been added to cache then apt must be made to recognise their location and availability. Hence the apt-get update to update apt.

If you were to then run apt-get **upgrade** then all newer package versions (of currently installed packages) now in the cache **would** be installed. 

From what you have indicated you wish to run... ```
apt-get install <specific package>
```
and that will install only that package PLUS any dependencies needed for it AND upgrade any packages associated that it requires to operate correctly.

Also try in a terminal...
```
man apt-get
``` 
for a fuller description.

---

### Post by WillemVoigt on 2011-11-07
Thanks. I'll try this tonight after work and update the results here.

---

### Post by WillemVoigt on 2011-11-07
The "sudo apt-get update" command does not work. It seems to only try an fetch information from the internet and not the "archives" folder. Obviously, seeing that my PC is offline it generates an error stating something along the lines of "failed to fetch...".

Any ideas?

---

### Post by robert shearer on 2011-11-07
Yes, memory is a wonderful thing and I now recall that I usually installed direct from the aptoncd disc that I had made rather than copying the packages to cache.

If I recall correctly when the cd is in the drive you can open **synaptic** and add it to your sources list there, then reload sources and use synaptic to install direct from the cd.

Alternatively, on the command line you would run (with the cd in the drive)...
```
sudo apt-cdrom add
```
followed at completion  by..
```
sudo apt-get update
```
then..
```
sudo apt-get install <specific package>
```

(if fstab is correct and/or you have only one drive then I don't think you need to specify the drive however if the first command throws errors post back.

also more info at...
```
man apt-cdrom
```

and..```
Adding a CD-ROM to the sources.list file

If you'd rather use your CD-ROM for installing packages or updating your system automatically with APT, you can put it in your sources.list. To do so, you can use the apt-cdrom program like this:

     # apt-cdrom add

with the Debian CD-ROM in the drive. It will mount the CD-ROM, and if it's a valid Debian CD it will look for package information on the disk. If your CD-ROM configuration is a little unusual, you can also use the following options:

     -h           - program help
     -d directory - CD-ROM mount point
     -r           - Rename a recognized CD-ROM
     -m           - No mounting
     -f           - Fast mode, don't check package files
     -a           - Thorough scan mode

For example:

     # apt-cdrom -d /home/kov/mycdrom add

You can also identify a CD-ROM, without adding it to your list:

     # apt-cdrom ident

Note that this program only works if your CD-ROM is properly configured in your system's /etc/fstab. 

```

---

### Post by WillemVoigt on 2011-11-08
Ubuntu 11.10 does not come standard with Synaptic Package Manager, but on Software Centre there is an option to "Add Volume", which does the same thing as the "sudo apt-cdrom add" command. I have tried this before, but the problem is that in this version, there seems to be no "Load" button like there was in previous versions of Ubuntu. So the "Terminal" command works. I disabled all other repositories and then ran the command. The "source.list" file was updated successfully. When I run the "sudo apt-get install vlc" command, it generates an error stating something like "media change - please insert cdrom labelled...", but the same cdrom disc that I just added is still in the drive.

Any more repressed memories that you can salvage? :D

---

### Post by WillemVoigt on 2011-11-09
Does anyone else have any input as well?

---

### Post by robert shearer on 2011-11-09
Hmmm, I am almost out of suggestions though you could navigate to the package on the cd, select it with a right-click and choose to 'open with' Software centre then, if it loads, hit the install button in Software centre.

This is why Keryx is generally more reliable and consistent for this process.

---

