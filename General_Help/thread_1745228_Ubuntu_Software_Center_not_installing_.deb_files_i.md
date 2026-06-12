---
title: "Ubuntu Software Center not installing .deb files in Ubuntu 11.04"
date: 2011-04-30
forum: General Help
---

### Post by rasfl3 on 2011-04-30
I've installed Ubuntu 11.04 on two of my computers, one of them an upgrade and the other one was a clean install, both are having the same issue. When installing .deb files, the Ubuntu Software Center launches as usual although when I click install, the installation starts and it shows the progress bar for a very short time and then the progress just disappears as if the installation stopped. I'm not sure if the installation has actually stopped or if the Software Center is just not showing the progress. Applications that are in the Ubuntu Software Center database works just fine, only .deb files are giving this problem. I installed GDebi Package Manager (Ubuntu 10.04 used to install .deb files with this application) and I can install just fine using that. Is this an 11.04 bug? The issue occurs both in Unity and in GNOME. I appreciate any help received regarding this issue. Thanks!

---

### Post by rasfl3 on 2011-04-30
bump

---

### Post by 5149.5 on 2011-04-30
It works fine for me.

---

### Post by cymbaline42 on 2011-05-01
Try installing it from the Terminal.

Use the syntax: ***sudo apt-get install (package name without brackets)***

---

### Post by rasfl3 on 2011-05-02
It works fine with GDebi Package Manger and Terminal but I need it to work with Ubuntu Software Center. This computer I'm setting up will be for someone else and they are not computer literate. On my computer which is also having the problem, it's not an issue to use GDebi or Terminal for me.

---

### Post by 4Orbs on 2011-05-02
For me, the Software Center finishes the installation, but it doesn't give very good feedback on the progress of the install process. I just wait it out and eventually the "Finished" notice will appear. I prefer gdebi, quicker and understandable.

---

### Post by lakerssuperman on 2011-05-02
What program are you installing and where did you get the .deb file.  Was it a download or did you create it yourself?

---

### Post by mybunche on 2011-05-02
As 4Orbs said above it doesn't give very good feedback. The same thing happened to me when installing the Google Chrome deb, I thought it didn't work but it did. There is obviously lots more work need to be done.

---

### Post by rasfl3 on 2011-05-03
I've tried installing several programs. As others said above, the problem seems to be that it's not giving very good feedback. Chrome was one of the ones I tried to install. I guess it's just a bug in Ubuntu 11.04. Hopefully an update that corrects the problem is released soon. I guess I'm going to be using GDebi meanwhile.

---

### Post by 4Orbs on 2011-05-03
On the Software Center I've noticed that clicking the left bar over the spot where the progress spinner first showed will bring up the progress page. Only tried it one time, though.

---

### Post by dewsworld on 2011-05-21
I have a .deb file. Now I want to install it by clicking it.
What problem occurs is - it simply open software manager and want to download it from the internet! What I'm supposed to do ?

---

### Post by wildmanne39 on 2011-05-21
> **dewsworld said:**
> I have a .deb file. Now I want to install it by clicking it.
What problem occurs is - it simply open software manager and want to download it from the internet! What I'm supposed to do ?

Hi, I had an issue too, I right click on it and open it that way.

---

### Post by linuxinstalledfromhdd on 2011-05-21
from the command line use wget to download your package file..  and gdebi to install it.

sudo apt-get install gdebi
wget <URLofFile> 
sudo gdebi <NameOfFile>

---

### Post by wildmanne39 on 2011-05-21
> **dewsworld said:**
> I have a .deb file. Now I want to install it by clicking it.
What problem occurs is - it simply open software manager and want to download it from the internet! What I'm supposed to do ?
Hi,also I can open deb files by going to the folder they are in then double clicking it.

---

