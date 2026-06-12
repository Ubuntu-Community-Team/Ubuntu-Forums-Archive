---
title: "apt-get install freezes"
date: 2011-09-30
forum: General Help
---

### Post by tim coddington on 2011-09-30
Ubuntu 11.04

According to Synaptic Package Manager sun-java6-jre is "in a very bad state".  Attemps to remove or reinstall fail through synaptic.  Based on comments for similar problems on this forum I've tried to use "apt-get" but in every case the process freeze.

Background: As a prerequisite to installing Netbeans I needed to install the JDK,  While followed instructions I executed: 
    "apt-get install sun-java6-jdk sun-java6-jre"

At some point a Sun document appeared in the terminal windows, but it seemed to freeze.  After about 10min I managed to kill the process--I'm sure is how I screwed things up.  Maybe my network was very slow and I should have waited.  Regardless, I'm now in a state where all attempts result in a freeze of the terminal windows executing apt-get.

I've tried:

sudo apt-get update then the command...still freezes when installing sun-java6-jre

sudo apt-get -f install....freezes

sudo apt-get dist-upgrade....freezes

But I'm sure these all end up at the same point.

Here's the output from the last attempt:

....
tim@RPS-Laptop4:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  libeigen3-dev
The following packages will be upgraded:
  firefox firefox-globalmenu firefox-gnome-support firefox-locale-en libgksu2-0
  ros-electric-desktop-full ros-electric-visualization ros-electric-visualization-tutorials
  sun-java6-bin sun-java6-jre tomboy xul-ext-ubufox
12 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
2 not fully installed or removed.
Need to get 41.3 MB/77.8 MB of archives.
After this operation, 104 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://packages.ros.org/ros/ubuntu/](http://packages.ros.org/ros/ubuntu/) natty/main ros-electric-desktop-full i386 1.0.0-s1316973576~natty [1,316 B]
Get:2 [http://packages.ros.org/ros/ubuntu/](http://packages.ros.org/ros/ubuntu/) natty/main ros-electric-visualization-tutorials i386 0.2.3-s1316944151~natty [2,301 kB]
Get:3 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates/main firefox-globalmenu i386 7.0.1+build1+nobinonly-0ubuntu0.11.04.1 [47.7 kB]
Get:4 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates/main firefox i386 7.0.1+build1+nobinonly-0ubuntu0.11.04.1 [15.1 MB]
Get:5 [http://packages.ros.org/ros/ubuntu/](http://packages.ros.org/ros/ubuntu/) natty/main ros-electric-visualization i386 1.6.4-s1316798335~natty [22.9 MB]
Get:6 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates/main firefox-gnome-support i386 7.0.1+build1+nobinonly-0ubuntu0.11.04.1 [15.9 kB]
Get:7 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates/main firefox-locale-en all 7.0.1+build1+nobinonly-0ubuntu0.11.04.1 [384 kB]
Get:8 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates/main libgksu2-0 i386 2.0.13~pre1-3ubuntu3.1 [44.1 kB]
Get:9 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates/main tomboy i386 1.6.0-0ubuntu4 [506 kB]
Get:10 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates/main xul-ext-ubufox all 0.9.2-0ubuntu0.11.04.1 [49.2 kB]
Fetched 41.3 MB in 50s (811 kB/s)                                                           
Preconfiguring packages ...
(Reading database ... 
dpkg: warning: files list file for package `sun-java6-bin' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `sun-java6-jre' missing, assuming package has no files currently installed.
(Reading database ... 293167 files and directories currently installed.)
Preparing to replace sun-java6-jre 6.26-1natty1 (using .../sun-java6-jre_6.26-1natty1_all.deb) ...

<freezes here>

===============
What do I have to do to get past this problem?  Can remove...can't reinstall

---

### Post by seawolf167 on 2011-09-30
Why are you running *dist-upgrade*?

What is the output from the commands

```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```

Any error output from this command?

```
sudo apt-get -f install
```

---

### Post by tim coddington on 2011-09-30
I was preparing to execute and capture output of the suggested command sequence, but decided to open and "install" latest updated in Update Manager.  The first sign that somehow all might be working better was Sun Microsystem agreement confirmation message I hadn't seen since the problem started.  All updates were installed without incident.

With continued sense that the state of the JRE related packages had improved I used Synaptic to find and install the JDK, which it did without incident.   recall when I did this last it warned that the JRE package was in "very bad state" and only suggested I reinstall.  Same for removal or reinstallation.

So, it appears that after an over night  shutdown (note: I had shutdown and restarted several times and still could not get synaptic or apt-get to install/reinstall JRE) and installation of Update Manager's update today seems to have made a difference.   BTW, I ran updates earlier on the day that I started having problems, without incident.

Thanks

---

### Post by oldos2er on 2011-09-30
Run ```
sudo dpkg --configure -a
``` when the license agreement comes up, use Tab to highlight 'Ok' then Enter.

---

