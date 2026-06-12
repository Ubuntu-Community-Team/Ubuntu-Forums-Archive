---
title: "wont play movies or videos"
date: 2010-02-15
forum: General Help
---

### Post by rickd on 2010-02-15
I hope someone can help me with my problem this is my 1st exp. with ubuntu and i can not get it to play vidios on youtube or just poping a dvd in and trying to watch a movie it does say that it is missing a uri or somthing to that affect can someone help me with this problem.
thanks
Rick

---

### Post by arizonalarry2 on 2010-02-15
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by jimmers on 2010-02-15
Hi Rick,
Try this, 
sudo gedit /etc/apt/sources.list
Ensure that you save the following two lines:-
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) your dist universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) your dist universe multiverse
Now run sudo apt-get update
Then sudo apt-get install mplayer
Then:-
sudo wget [http://www.medibuntu.org/sources.list.d/your](http://www.medibuntu.org/sources.list.d/your) dist.list --output-document=/etc/apt/sources.list.d/medibuntu.list

Then sudo apt-get update and sudo apt-get install medibuntu-keyring then
 sudo apt-get update

For i386 users: sudo apt-get install w32codecs libdvdcss2

For amd64 users: sudo apt-get install w64codecs libdvdcss2

Hope it Helps, at least worth a try


jimmers

---

### Post by lvirden on 2010-03-09
I have a similar issue, but with a bigger problem. I installed ubuntu 9.10, from a ubuntu created CD, onto my wife's computer. We don't have internet access. 

I was surprised when, after inserting a dvd, ubuntu recommended a program to play the dvd, then reported being unable to resolve the uri 'dvd'. 

Is there a way, using the distributed CD only, to install the pieces needed?  If not, then is there a list of specific files that need to be downloaded to a USB drive then sneaker-netted home to the machine so that the setup can be completed?

---

### Post by zeroseven0183 on 2010-03-09
I found a site that offers the installer of ubuntu-restricted-extras offline. It's in [http://hacktolive.org/wiki/Ubuntu-restricted-extras_offline_installer](http://hacktolive.org/wiki/Ubuntu-restricted-extras_offline_installer)

Once you download it, follow the instructions:
1. unpack/extract
2. double-click the file "install.sh" on folder  "offline-installer"
3. Select "run in terminal"
4. Enter your password if/when the installer asks yo
5. Accept Java license when that appears, by pressing: <TAB>  <ENTER> <TAB> <ENTER>
6. When program finishes, close the window and remove the folder  "offline-installer"

ubuntu-restricted-extras is probably what you need

Hope that helps

---

