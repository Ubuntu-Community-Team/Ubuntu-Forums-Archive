---
title: "I cant get WinFF to work"
date: 2011-12-19
forum: General Help
---

### Post by Spc 4 on 2011-12-19
I have Ubuntu11.10 and WinFF stoped working. I searched through the help forums and nothing seems to work. Any ideas?

---

### Post by dabl on 2011-12-19
What does "stopped working" mean?  When you launch it in a terminal window, what errors does it show?

---

### Post by Spc 4 on 2011-12-19
It will not transcode

---

### Post by Spc 4 on 2011-12-20
I cant get Winff to work. I have been asking for help, and I cant find a answer. Every time after I upgraded to 11.10 I can not trascode a MKV to a AVI. I can not transcode anything to any thing else. I searched the help forums and I am sure I have lbv52. But It jst does not do any thing when I try to transcode my videos.

---

### Post by coffeecat on 2011-12-20
Threads merged. Please do not start duplicate threads. This dilutes community effort.

---

### Post by Spc 4 on 2011-12-22
bump

---

### Post by Spc 4 on 2011-12-24
For some reason I cant get *libavcodec*-*extra*-*52* to install. I think that is what the problem is.

---

### Post by plucky on 2011-12-25
> **Spc 4 said:**
> For some reason I cant get *libavcodec*-*extra*-*52* to install. I think that is what the problem is.

Do you have the [Medibuntu Repository](http://medibuntu.org/repository.php) installed?

Good Luck

---

### Post by Spc 4 on 2011-12-25
Yes I have that. I followed these two tutorials and I cant get get WinFF to run. 
[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)
[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)
When I try transcoding anything the terminal window pops up for 1/10th of a second and nothing happens.

---

### Post by plucky on 2011-12-25
Try installing **libavcodec-extra-53**

```
sudo apt-get install libavcodec-extra-53
```

> For some reason I cant get libavcodec-extra-52 to install. I think that is what the problem is. 

This is what I get when I try to install libavcodec-extra-52 on 11.10 > sudo apt-get install libavcodec-extra-52
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libavcodec-extra-52 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'libavcodec-extra-52' has no installation candidate


Good Luck

---

### Post by Spc 4 on 2011-12-25
thank you  for the help but it did not work. This is what I got:

adam@adam-desktop:~$ sudo apt-get install libavcodec-extra-53
[sudo] password for adam: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libavcodec-extra-53 is already the newest version.
The following packages were automatically installed and are no longer required:
  libtaglib2.0-cil libgkeyfile1.0-cil libgudev1.0-cil libgnome-desktop-2-17
  libgladeui-1-11 libgdata1.7-cil wine1.2-gecko libgtk-sharp-beans-cil
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
adam@adam-desktop:~$ 


and whet I type "apt-get autoremove" without quotes I get this:

Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
adam@adam-desktop:~$ apt-get autoremove
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
adam@adam-desktop:~$ 

I apologise, the only thing I know about the terminal is how to copy/paste commands in.

---

### Post by andrew.46 on 2011-12-26
Does the terminal show an error message when you use WinFF? If so can you copy and paste this here.

---

### Post by Spc 4 on 2011-12-26
The terminal only pops up for 1/10th of a second. If I could figure out how to keep it from disappearing I could post it.

---

### Post by Spc 4 on 2011-12-30
Bump
 Happy new year!

---

### Post by plucky on 2011-12-31
Winff is a front end for ffmpeg.Within Winff (Options > Display CMD Line) there is an option to display the CMD line that Winff is using to call up ffmpeg from a terminal window.

If you copy & paste this line into a terminal window,you should then be able to see the error that causes the Winff window to close.

Copy and paste the whole terminal output to the forum and maybe someone will be able to help you.

Good Luck

---

### Post by satanselbow on 2011-12-31
Install WinFF from this ppa:

```
ppa:paul-climbing/ppa
```

The version in the repos was broken in 11.10 for me too ;)

---

### Post by plucky on 2012-01-01
Found [This](https://bugs.launchpad.net/ubuntu/+source/winff/+bug/871332)

You can just open your home folder and view hidden files and navigate to the .Winff folder.

**Rename the presets.xml file to old-presets.xml.**

Then restart WinFF and it will create a new presets.xml file which hopefully will fix your problem.

Good Luck

---

### Post by Spc 4 on 2012-01-01
IT WORKED!! Thank you so much! I renamed the xml file and it fixed it. I have been trying to get this to work for months.

---

