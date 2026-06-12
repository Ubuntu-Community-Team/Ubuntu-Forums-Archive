---
title: "Update Manager Errors Ubuntu 10.04 (Lucid)"
date: 2010-07-05
forum: General Help
---

### Post by rsmedude on 2010-07-05
Hi everyone,

                                 I am new to Linux. I did some research and decided to go with Ubuntu because it appeared that this flavor of Linux had some really good support out on the web. Unfortunately while so far my experience has been mostly positive and is become more positive with every turn I have run into one little problem. My Update manager does not want to run right for me. It keeps giving me an error and I have not been able to find a way to fix it. I would greatly appreciated any and all help on this topic as I am trying to learn Linux.

The errors that I am receiving:
 
> 

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/Release](http://us.archive.ubuntu.com/ubuntu/dists/lucid/Release)  

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/Release](http://security.ubuntu.com/ubuntu/dists/lucid-security/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.




---

### Post by plucky on 2010-07-05
Welcome to the forum.

Open a terminal **Applications > Accessories > Terminal** and copy and paste these commands one at a time```
sudo apt-get update
sudo apt-get upgrade
```

Post back any output that has errors in it.

Good Luck

---

### Post by rsmedude on 2010-07-05
Hi Plucky,

Thank you for the welcome and the reply. I have a bad feeling it didn't work though. However I am going to post what I got so that you and anyone else can see and hopefully help me out. As of right now I have not tried installing any other software or do much of anything else because I figure fix one problem before possibly making more for myself.


The First Commands Output:
    sudo apt-get update
```


james@James-NIX:~$ sudo apt-get update
[sudo] password for james: 
Get:1 http://us.archive.ubuntu.com lucid Release.gpg [189B]
Hit http://archive.canonical.com lucid Release.gpg                       
Get:2 http://security.ubuntu.com lucid-security Release.gpg [189B]   
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US
Ign http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Hit http://archive.canonical.com lucid Release                       
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Hit http://archive.canonical.com lucid/partner Packages              
Hit http://us.archive.ubuntu.com lucid-updates Release.gpg           
Get:3 http://security.ubuntu.com lucid-security Release [38.5kB]
Err http://security.ubuntu.com lucid-security Release  
  
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Get:4 http://us.archive.ubuntu.com lucid Release [57.2kB]
Err http://us.archive.ubuntu.com lucid Release
  
Get:5 http://us.archive.ubuntu.com lucid-updates Release [44.7kB]
Hit http://us.archive.ubuntu.com lucid-updates/main Packages
Hit http://us.archive.ubuntu.com lucid-updates/restricted Packages
Hit http://us.archive.ubuntu.com lucid-updates/main Sources
Hit http://us.archive.ubuntu.com lucid-updates/restricted Sources
Hit http://us.archive.ubuntu.com lucid-updates/universe Packages
Hit http://us.archive.ubuntu.com lucid-updates/universe Sources
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Packages
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Sources
Fetched 45.0kB in 3s (13.4kB/s)
Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://security.ubuntu.com lucid-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://us.archive.ubuntu.com lucid Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/Release  

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.


```The Second Commands Output:
    sudo apt-get upgrade

```


james@James-NIX:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


```Unfortunately when I go and run the Update Manager I get the same error message(s) that I was getting before.

---

### Post by plucky on 2010-07-05
Try switching servers.

**System > Administration > Software Sources** and on the first page in the "Download From" window,select the "Main Server".


Good luck

---

### Post by rsmedude on 2010-07-05
[COLOR=black][FONT=Verdana]Ok I will try it tonight at work. The machine I am working on is actually a personal machine that my boss was kind enough to let me keep at work to mess with during the slow times![/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I will let you know and post what the results are later tonight! [/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Again thanks for the help![/FONT][/COLOR]

---

### Post by rsmedude on 2010-07-05
Plucky,

YOU ROCK... That last post from you completely fixed me up I greatly appreciate the help on this!

EDIT:

I just wanted to add that I ran the Update Manger and got like 6 updates (I should have noted them) and then for the heck of it I put the source back to being the US server. Now the Update Manager works just fine. I am just speculating here but I think something got horked in my settings and the updates may have inadvertently straightened it out.

I just thought I would throw this tid bit out there as a possible work around for anyone experiencing the same or similar issue as I did!

---

### Post by rsmedude on 2010-08-15
OK everyone,

Sorry but I need to revive this old post. I am having issues getting updates again and what worked in the past does not want o work again. I will post all the information I have here for you guys.


Error from Update Manager:
> 
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://archive.canonical.com](http://archive.canonical.com) lucid Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/lucid/Release](http://archive.canonical.com/ubuntu/dists/lucid/Release)  

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-updates/Release](http://archive.ubuntu.com/ubuntu/dists/lucid-updates/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.


sudo apt-get update Output:
> 
james@James-NIX:~$ sudo apt-get update
Get:1 [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg [189B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release.gpg [189B]
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US
Get:3 [http://archive.canonical.com](http://archive.canonical.com) lucid Release [8,215B]
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
Err [http://archive.canonical.com](http://archive.canonical.com) lucid Release         
  
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release.gpg [189B]
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security Release.gpg [189B]
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release [57.2kB]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release [44.7kB]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release
  
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security Release [38.5kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/multiverse Sources
Fetched 760B in 3s (201B/s)
Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://archive.canonical.com](http://archive.canonical.com) lucid Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/lucid/Release](http://archive.canonical.com/ubuntu/dists/lucid/Release)  

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-updates/Release](http://archive.ubuntu.com/ubuntu/dists/lucid-updates/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.


sudo apt-get upgrade output:
> 
james@James-NIX:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


So I guess my main question here is what the heck am I missing. It was working fine. Then one day it just decided to not update again. I do have Software sources set to main again and I have tried switching it to Server for united States just for the heck of it. Unfortunately neither one of these options seems to resolve the issue.

Thanks in advance for any and all help. I really do hope to get a better handle on this so that i do not have to keep revisiting this issue.

---

### Post by deserthowler on 2010-08-16
I think I got an update for update manager a few days ago.  Try synaptic and see if that works for you.  I'm not sure because I usually use synaptic to update and haven't had any problems.

Earl

---

### Post by girishgargdce on 2010-09-13
i am also facing the same issue.
W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/lucid/Release](http://archive.canonical.com/ubuntu/dists/lucid/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.
 please help me.
Girish , Bangalore, India

---

