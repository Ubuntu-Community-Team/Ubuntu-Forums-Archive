---
title: "Ubuntu Software Center fails"
date: 2011-08-13
forum: General Help
---

### Post by dlazov on 2011-08-13
Greetings, brand new to Ubuntu and for the most part loving it a lot.

For some reason (unknown to me) my Ubuntu Software Center will no longer do installs, I keep getting a pop up window with the message: 

**Items cannot be installed or removed until the package catalog is repaired. Do you want to repair it now?**

If I click Repair and then input in my password I get a another pop-up window which says:

**Package operation failed**
[I][COLOR=Blue]The installation or removal of a software package failed. [/COLOR]
[/I]
The Details say:

[COLOR=Blue][I]installArchives() failed: Preconfiguring packages ... 
Preconfiguring packages ... 
Preconfiguring packages ... 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 202950 files and directories currently installed.) 
Unpacking sun-java6-jre (from .../sun-java6-jre_6.26-1natty1_all.deb) ... 
 
sun-dlj-v1-1 license could not be presented 
try 'dpkg-reconfigure debconf' to select a frontend other than noninteractive 
 
dpkg: error processing /var/cache/apt/archives/sun-java6-jre_6.26-1natty1_all.deb (--unpack): 
 subprocess new pre-installation script returned error exit status 2 
No apport report written because MaxReports is reached already
Unpacking sun-java6-bin (from .../sun-java6-bin_6.26-1natty1_amd64.deb) ... 
 
sun-dlj-v1-1 license could not be presented 
try 'dpkg-reconfigure debconf' to select a frontend other than noninteractive 
 
dpkg: error processing /var/cache/apt/archives/sun-java6-bin_6.26-1natty1_amd64.deb (--unpack): 
 subprocess new pre-installation script returned error exit status 2 
No apport report written because MaxReports is reached already
Unpacking sun-java6-jdk (from .../sun-java6-jdk_6.26-1natty1_amd64.deb) ... 
 
sun-dlj-v1-1 license could not be presented 
try 'dpkg-reconfigure debconf' to select a frontend other than noninteractive 
 
dpkg: error processing /var/cache/apt/archives/sun-java6-jdk_6.26-1natty1_amd64.deb (--unpack): 
 subprocess new pre-installation script returned error exit status 2 
No apport report written because MaxReports is reached already
Errors were encountered while processing: 
 /var/cache/apt/archives/sun-java6-jre_6.26-1natty1_all.deb 
 /var/cache/apt/archives/sun-java6-bin_6.26-1natty1_amd64.deb 
 /var/cache/apt/archives/sun-java6-jdk_6.26-1natty1_amd64.deb 
dpkg: dependency problems prevent configuration of jonas-5.2: 
 jonas-5.2 depends on sun-java6-jdk | java5-jdk; however: 
  Package sun-java6-jdk is not installed. 
  Package java5-jdk is not installed. 
dpkg: error processing jonas-5.2 (--configure):  dependency problems - leaving unconfigured [/I][/COLOR]


And then the first pop-up pops up again and the whole process repeats for a while, until I hit cancel enough times that I get another pop-up window which says:

**The package system is broken**
[I][COLOR=Blue]Check if you are using third party repositories. If so disable them, since they are a common source of problems. Furthermore run the following command in a Terminal: apt-get install -f[/COLOR]
[/I]
The details say this:

[COLOR=Blue][I]The following packages have unmet dependencies:

jonas-5.2: Depends: java5-jdk but it is not installed
           Depends: upstart-job but it is a virtual package
[/I][/COLOR]

When I run that command in a terminal I get:
[FONT=Courier New][COLOR=Blue]
dlazov@ubuntu:~$ apt-get install -f
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?[/COLOR][/FONT]

I also tried the following but not sure what exactly it means or how to fix or repair any of this:

[FONT=Courier New][COLOR=Blue]dlazov@ubuntu:~$ gsettings set com.canonical.Unity.Panel systray-whitelist "['all']"
dlazov@ubuntu:~$ sudo apt-get install compizconfig-settings-manager
[sudo] password for dlazov: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
compizconfig-settings-manager is already the newest version.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 jonas-5.2 : Depends: sun-java6-jdk but it is not going to be installed or
                      java5-jdk but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
dlazov@ubuntu:~$ [/COLOR]
[/FONT]

If some kind soul could help me out it would be much appreciated, I am running Ubuntu in side-by-side mode with my Windows 7 box, and I am loving it and in fact I have been in Ubuntu world for 3 days and not booted into Windows at all. But this little glitch is really a pain and I can't figure out how to fix it.

Oh, I saw in the error log a command to type in I tried that but got this:

[COLOR=Blue]dlazov@ubuntu:~$ dpkg-reconfigure debconf
/usr/sbin/dpkg-reconfigure must be run as root
dlazov@ubuntu:~$ 

[COLOR=Black]I never created a root user during installation and I have no idea on how to login as root. ?[/COLOR]
[/COLOR]

---

### Post by realzippy on 2011-08-13
Try with "sudo":
(makes you "root" like for a while..)

```
sudo apt-get install -f
```

---

### Post by dlazov on 2011-08-13
Well I figured it out...lol

what I did was to take a clue from using a sudo root and ran this command:

sudo apt-get -f install

And all is now well....

+1 for me...lol sorry to take up web space....

---

### Post by dlazov on 2011-08-13
Thanks real zippy, we cross-posted...lol

---

### Post by realzippy on 2011-08-13
yeah.
Please set thread as solved then  (Threadtools)
Have fun!

---

### Post by 3rdalbum on 2011-08-13
File a bug report against Ubuntu Software Center. The window should say "sudo apt-get install -f", not just "apt-get install -f".

---

