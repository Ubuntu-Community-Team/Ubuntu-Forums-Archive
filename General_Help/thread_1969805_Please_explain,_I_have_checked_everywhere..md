---
title: "Please explain, I have checked everywhere."
date: 2012-04-30
forum: General Help
---

### Post by civilianpoppy on 2012-04-30
Hi,
    I'm new to Linux, I tried Fedora Core a couple times and ... ran into some of the same problems I am now, but a lot more of them - maybe it wasn't ideal for my hardware.  Anyways, I installed Ubuntu 12.04LTS on an Acer Aspire m1202 - as a partition off of windows vista... copied all the stuff I wanted to keep... now I have deleted Vista for another partition of Ubuntu.  Both home folders are encrypted, and I cannot transfer files to and fro -but I don't need to now, and I will figure it out.  No problems installing, even with no mouse!  I love this system.  

THE QUESTION:  
Ubuntu 8.10 on an Acer Aspire 4520 laptop with a 7000m Geforce (Nvidia)- no partitions:  I have checked everything, my respositories are correct, my kernel is 2.26.7-7.  I have tried manually retrieving the packages just about every way I can in terminal.  
"sudo apt-get update"   the first 30 lines work... and then nothing else can be retrieved?  Error 404.  I tried switched from US repositories to "main server."  
"sudo apt-get dist-upgrade" does not work from terminal but I can find it somewhere in settings after I look around.  I did not try to upgrade to version 9.10 - my fear is that it will make my graphics problems worse?  Upon rechecking Synaptic I do have the package 'nvidia-177-modaliases' INSTALLED (????)  They are installed in the /user/share/jockey/modaliases/nvidia-177  folder.  There are 0 dependencies, it is dependent of 'nvidia-common.'  
I read someone that Ubuntu maintained its repositories for 5 years for each distro?  To my understanding this was release it 2008, am I under the wrong impression?  My point: after just now looking at this I realize I do have the drivers?  Am I correct?  There are no unusual boot messages, post code is fine...

In synaptic I click reload in Synaptic package manager it tells me it cannot download all repository indexes. 
I did some work in Terminal trying to get these packages... from a few different sources... my problems seems to be in connecting to any sort package respositories... while the desktop with 12.04TLS is running perfect, from a fresh install.  
I will post the error message I get when in a second from the other computer.  

Is my best bet to upgrade to 9.10?  Pop the 12.04 live cd in?  I have tried just about everything terminal wise and yes I know what sudo and apt-get means, but not much more :\ I am learning.  Did I inadvertantly mess something up while my noob self was in terminal?  
By the way... the system hangs when I shut it down.  I have to hit the enter button for it turn off .. weird?  Members can email me - and I'm sorry for the rant but I spend so much time trying to figure it out by myself and by other people experiences... I have tried everything.  I understand these are restricted drivers... I have been working on this for atleast 12 hours...  (well both the computers).  12.04TLS is running like a charm on the aspire m1202 but this darn aspire 4520 laptop will not cooperate - and we all know it is waaay to slow for windoz.  
I had no problem activating the wireless.  However, I haven't connected to any networks... shouldn't it scan for them?  Synaptic says it is installed and in use.  

Any help would be very much appreciated, I just fear I have messed up something I shouldn't have.  
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
[https://wiki.ubuntu.com/IntrepidReleaseNotes#Recommended_packages_installed_by_default](https://wiki.ubuntu.com/IntrepidReleaseNotes#Recommended_packages_installed_by_default)

I thought this one was going to fix it... but repository problems:

[http://ubuntuforums.org/archive/index.php/t-1038900.html](http://ubuntuforums.org/archive/index.php/t-1038900.html)

I uploaded my information to launchpad, if that helps?  Sorry to waste your time, but I really have tried everything.  I am no stranger to problem solving but I cannot solve this :\  HELP!! lol

Thank you very much,
Luke

---

### Post by uylug on 2012-04-30
Updating from 8.04 to 12.04 could take ages, really. 7 updates? Seriously?

You should backup all your data, and run a fresh install.

---

### Post by civilianpoppy on 2012-04-30
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/main/source/Sources.gz)  404 Not Found [IP: 91.189.88.26 80]    

That is the first of about 50 error message when I enter synaptic and click reload.  

Ok I will back it up and do a fresh install of 8.10.  This will be done within 2 hours.  I'll see if that fixes it.  

Thank you for your advice.

---

### Post by wojox on 2012-04-30
> **civilianpoppy said:**
> Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/main/source/Sources.gz)  404 Not Found [IP: 91.189.88.26 80]    

That is the first of about 50 error message when I enter synaptic and click reload.  

Ok I will back it up and do a fresh install of 8.10.  This will be done within 2 hours.  I'll see if that fixes it.  

Thank you for your advice.

8.10 is EOL show it won't matter to much if you reinstall. What is it you are trying to accomplish?

---

### Post by civilianpoppy on 2012-04-30
I just want the graphics card to work so I'm not stuck in 800x600 resolution!  I have been trouble shooting extensively, I think he recommended reinstalling because I was working in terminal and I don't know 100% of what I'm doing, but even if I did (I first used a command line at age 8... DOS where you had those two 3" diskettes... I can run a command prompt - so I know I wasn't typing the commands wrong), I don't know Linux well and I very well could have?  

It's like the laptop cannot contact ANY repositories... 

Everything is fine on the desktop... seamless install great performance.  (12.04TLS)

EOL - okay so that would be the repository problems?  Because it will let me upgrade to 9.10.... I just didn't click it for fear of messing it up more... lol

---

### Post by uylug on 2012-04-30
The problem is that your distribution is too old - April 2008 - so its no longer supported.

Trust me, you should totally get the [Precise iso]("http://releases.ubuntu.com/12.04/ubuntu-12.04-desktop-i386.iso") and install from there.

---

### Post by civilianpoppy on 2012-04-30
I need the 64 bit version ^^ .... Precise on a aspire 4520?  It's going to be sloooow.... 

Is this the only option? 

I thought it was supported for 1 more year, my bad.

There is only a live CD for this correct?  If so I already have it, and will start now.  Let you know how that goes... hehe.

---

