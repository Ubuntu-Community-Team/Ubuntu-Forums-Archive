---
title: "Installing Nvidia graphics driver from a folder"
date: 2010-07-09
forum: General Help
---

### Post by lanceman63 on 2010-07-09
I am running Ubuntu 10.04 LTS. I have downloaded a graphics driver for my Nvidia graphics card it is in the "Downloads" folder. The name of the file is "NVIDIA-Linux-x86-256.35.run." I downloaded this driver from the NVIDIA website. I have gone to permissions and checked the box to "run as a file." When I right click on the file and choose open or double click on the file I get a dialog box with the choices  to "Run in Terminal", "Display", "Cancel", and "Run". When I click on "Run" nothing happens. When I click on "Run in Terminal" the terminal opens then begins to install the file and suddenly stops saying that it needs to be run as "root". Can someone please give me instructions to install this file?

Thank you

---

### Post by lanceman63 on 2010-07-15
No replies yet.

---

### Post by WildeBeest on 2010-07-15
That file needs to be run from a command line with X turned off.
 
The following guide should help you.
 
[http://ubuntuforums.org/showthread.php?t=990978](http://ubuntuforums.org/showthread.php?t=990978)

---

### Post by dannyboy79 on 2010-07-15
> **WildeBeest said:**
> That file needs to be run from a command line with X turned off.
 
The following guide should help you.
 
[http://ubuntuforums.org/showthread.php?t=990978](http://ubuntuforums.org/showthread.php?t=990978)

is you're goal to get the latest and greatest nvidia proprietary driver or just get nvidia driver installed?

if it's the first, follow that link but also read the last page of that thread.

if it's the later i would just use aptitude, it will install version 195 to the best of my knowledge and I have no problems with that driver at all, i don't however run a composite style WM though.

```
sudo aptitude update && aptitude install nvidia-current
```

good luck

---

### Post by Linuxforall on 2010-07-15
Another easy way to get latest nvidia is to simply add Ubuntu X ppa which is maintained by Ubuntu X team, they have latest within a day of release, in terminal sudo add-apt-repository ppa:ubuntu-x-swat/x-updates

sudo apt-get update

Check update manager for latest nvidia listed there.

---

