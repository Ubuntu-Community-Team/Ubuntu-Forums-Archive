---
title: "How do I install updates?"
date: 2009-08-22
forum: General Help
---

### Post by tdrobbin on 2009-08-22
I am new to Linux, terrible with computers, and I have no clue what I am doing. I tried to install my updates and was told that I have 1 broken package.  So I went to my synaptic to search for the broken package. I found it, it was in broken dependencies and is labeled: libaccess-bridge-java. I tried to fix it, but was turned away by this message:

E: /var/cache/apt/archives/openjdk-6-jre-lib_6b11-2ubuntu2.1_all.deb: files list file for package `openjdk-6-jre-headless' is missing final newline

Can anyone help me?

---

### Post by Vakman on 2009-08-22
To fix broken packages refer to [https://help.ubuntu.com/community/SynapticHowto#How](https://help.ubuntu.com/community/SynapticHowto#How) to fix broken packages or [http://ubuntuforums.org/showthread.php?t=186672](http://ubuntuforums.org/showthread.php?t=186672) for more options.

---

### Post by michy99 on 2009-08-22
Run these commands in a terminal```
sudo rm /var/cache/apt/archives/openjdk-6-jre-lib_6b11-2ubuntu2.1_all.deb
sudo apt-get update
```

---

### Post by tdrobbin on 2009-08-22
It is no telling me that I:

rm: cannot remove `/var/cache/apt/archives/openjdk-6-jre-lib_6b11-2ubuntu2.1_all.deb': No such file or directory

I have been trying everything, but I cannot remove "openjdk-6-jre" because it says it cannot find any such file.

---

### Post by michy99 on 2009-08-22
What errors do you get if you run```
sudo apt-get update
```

---

### Post by zkriesse on 2009-08-22
It sounds like you need flash player. Go to [www.hulu.com](www.hulu.com) and download the adobe flash player. click on the download link and let it do it's thing...then try updating. let me know how it turns out.

---

### Post by tdrobbin on 2009-08-22
Michy, 

If I run sudo apt-get update I get no errors. It reads:

user@ubuntu:~$ sudo apt-get update
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Sources
Reading package lists... Done

Thank you for taking your time with me.

---

### Post by tdrobbin on 2009-08-22
The irony is, attempting to install Flash Player is what alerted me to broken dependeny in the first place. I have been having huge problems ever since.

---

### Post by tdrobbin on 2009-08-22
I tried flash player again, and again it says I have a broken package. A package I cannot remove, install, or reinstall, because it cannot find any file for the package it says is broken.

I think I finally understand Heller's "Catch 22" now though.

---

### Post by zkriesse on 2009-08-22
Did you stop any processes or shut down the pc while updating? If so that might have caused it. Tell you what, if you still have the Live CD, (I'm assuming you used a Live CD for the installation of Ubuntu...) stick it in and use the repair system option. After that tell me if it's all good. If not I'll research it for you either until we fix this bitch of a problem or someone else gives you an answer ok?

---

### Post by tdrobbin on 2009-08-22
Thank you much Zach. This pc actually came with Ubuntu already installed, so no I don't have a CD. By stopping the processes, do you mean quitting the download? Once the screen says that I have a broken package, I have been aborting the download to see what else I can do. Are you saying to try to let flashplayer download anyway?

---

### Post by tdrobbin on 2009-08-22
"files list file for package `openjdk-6-jre-headless' is missing final newline"

This message has been my reoccurring nightmare. Because openjdk is only an optional file, I then try to remove it, but it cannot be found. 

Does this message mean anything to anyone?

---

### Post by zkriesse on 2009-08-22
Yes...try letting the adobe flash download anyway.

---

### Post by michy99 on 2009-08-22
Do you get anything for```
ls /var/cache/apt/archives/partial
```

---

### Post by tdrobbin on 2009-08-22
Zach, adobe flash does not let me continue the download with a broken package.

Michy, I tried that command but it literally did nothing. It only sent me to the next blank 
line in the terminal.

---

### Post by michy99 on 2009-08-22
Try this:```
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
```

---

### Post by tdrobbin on 2009-08-22
Michy, again it only sent me to the next line. No changes. Is there somthing I should be putting in after that? Thank you for your help.

---

### Post by michy99 on 2009-08-22
Try installing updates again.

---

