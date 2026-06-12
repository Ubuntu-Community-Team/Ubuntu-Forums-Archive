---
title: "Software Index broken on Natty Narwhal. Can anyone help?"
date: 2012-05-22
forum: General Help
---

### Post by SteveL1990 on 2012-05-22
Hi there. I'm a new guy who's in a bit of a fix and I was wondering if someone could help.

I've had 11.04 for about a month now(installed it to run within Windows), and I've already become addicted to it. :popcorn:
I've installed a few programs on here since, and earlier today I thought I might try installing 'Kate', one of the fancier text editors out there. Unfortunately, I ran into a bit of a problem.

My computer is a 3-year-old Toshiba, and while it's pretty reliable 90% of the time, it does unfortunately have the occasional overheating issue, which causes the computer to switch off(presumably a safety feature, I would think). 

Unfortunately, this issue occurred a few hours ago, just as I had started installing Kate. Now, this had occurred on a few previous occasions, where the computer happened to overheat and power off while I was in the middle of downloading a program, but I had never had any problems. This time was different; upon rebooting, I was informed that the Software Index was broken. 

I have already tried the terminal options but nothing seems to work. Is there any way I can repair this without having to re-install Ubuntu? My system in general seems to be working fine, except for the fact that I can't install or uninstall any programs, and I'd like to have this fixed ASAP.

I really do need the help.

(BTW, here are some screenshots that may prove to be helpful: )

---

### Post by plucky on 2012-05-22
> I have already tried the terminal options but nothing seems to work. Is there any way I can repair this without having to re-install Ubuntu?

From a terminal ```
sudo rm /var/lib/dpkg/updates/* -vf
``` then run ```
sudo dpkg --configure -a
``` and post output.

Good Luck

---

### Post by SteveL1990 on 2012-05-22
> **plucky said:**
> From a terminal ```
sudo rm /var/lib/dpkg/updates/* -vf
``` then run ```
sudo dpkg --configure -a
``` and post output.

Good Luck

Okay, plucky. This is what I got after I did that. 

> stevenspc@ubuntu:~$ sudo rm /var/lib/dpkg/updates/* -vf
[sudo] password for stevenspc: 
removed `/var/lib/dpkg/updates/0000'
removed `/var/lib/dpkg/updates/0001'
removed `/var/lib/dpkg/updates/0002'
removed `/var/lib/dpkg/updates/0003'
removed `/var/lib/dpkg/updates/0004'
removed `/var/lib/dpkg/updates/0005'
removed `/var/lib/dpkg/updates/0006'
removed `/var/lib/dpkg/updates/0007'
removed `/var/lib/dpkg/updates/0008'
removed `/var/lib/dpkg/updates/0009'
removed `/var/lib/dpkg/updates/0010'
removed `/var/lib/dpkg/updates/0011'
removed `/var/lib/dpkg/updates/0012'
removed `/var/lib/dpkg/updates/0013'
removed `/var/lib/dpkg/updates/0014'
removed `/var/lib/dpkg/updates/0015'
removed `/var/lib/dpkg/updates/0016'
removed `/var/lib/dpkg/updates/0017'
removed `/var/lib/dpkg/updates/0018'
removed `/var/lib/dpkg/updates/0019'
removed `/var/lib/dpkg/updates/0020'
removed `/var/lib/dpkg/updates/0021'
removed `/var/lib/dpkg/updates/0022'
removed `/var/lib/dpkg/updates/0023'
removed `/var/lib/dpkg/updates/0024'
removed `/var/lib/dpkg/updates/0025'
removed `/var/lib/dpkg/updates/0026'
removed `/var/lib/dpkg/updates/0027'
removed `/var/lib/dpkg/updates/0028'
removed `/var/lib/dpkg/updates/0029'
removed `/var/lib/dpkg/updates/0030'
removed `/var/lib/dpkg/updates/0031'
removed `/var/lib/dpkg/updates/0032'
removed `/var/lib/dpkg/updates/0033'
removed `/var/lib/dpkg/updates/0034'
removed `/var/lib/dpkg/updates/0035'
removed `/var/lib/dpkg/updates/0036'
removed `/var/lib/dpkg/updates/0037'
removed `/var/lib/dpkg/updates/0038'
removed `/var/lib/dpkg/updates/0039'
removed `/var/lib/dpkg/updates/0040'
removed `/var/lib/dpkg/updates/0041'
removed `/var/lib/dpkg/updates/0042'
removed `/var/lib/dpkg/updates/0043'
removed `/var/lib/dpkg/updates/0044'
removed `/var/lib/dpkg/updates/0045'
removed `/var/lib/dpkg/updates/0046'
removed `/var/lib/dpkg/updates/0047'
removed `/var/lib/dpkg/updates/0048'
removed `/var/lib/dpkg/updates/0049'
removed `/var/lib/dpkg/updates/0050'
removed `/var/lib/dpkg/updates/0051'
removed `/var/lib/dpkg/updates/0052'
removed `/var/lib/dpkg/updates/0053'
removed `/var/lib/dpkg/updates/0054'
removed `/var/lib/dpkg/updates/0055'
removed `/var/lib/dpkg/updates/0056'
removed `/var/lib/dpkg/updates/0057'
removed `/var/lib/dpkg/updates/0058'
removed `/var/lib/dpkg/updates/0059'
removed `/var/lib/dpkg/updates/0060'
removed `/var/lib/dpkg/updates/0061'
removed `/var/lib/dpkg/updates/0062'
removed `/var/lib/dpkg/updates/0063'
removed `/var/lib/dpkg/updates/0064'
removed `/var/lib/dpkg/updates/0065'
removed `/var/lib/dpkg/updates/0066'
removed `/var/lib/dpkg/updates/0067'
removed `/var/lib/dpkg/updates/0068'
removed `/var/lib/dpkg/updates/0069'
removed `/var/lib/dpkg/updates/0070'
removed `/var/lib/dpkg/updates/0071'
removed `/var/lib/dpkg/updates/0072'
removed `/var/lib/dpkg/updates/0073'
removed `/var/lib/dpkg/updates/0074'
removed `/var/lib/dpkg/updates/0075'
removed `/var/lib/dpkg/updates/0076'
removed `/var/lib/dpkg/updates/0077'
removed `/var/lib/dpkg/updates/0078'
removed `/var/lib/dpkg/updates/0079'
removed `/var/lib/dpkg/updates/0080'
removed `/var/lib/dpkg/updates/0081'
removed `/var/lib/dpkg/updates/0082'
removed `/var/lib/dpkg/updates/0083'
removed `/var/lib/dpkg/updates/0084'
removed `/var/lib/dpkg/updates/0085'
removed `/var/lib/dpkg/updates/0086'
removed `/var/lib/dpkg/updates/0087'
removed `/var/lib/dpkg/updates/0088'
removed `/var/lib/dpkg/updates/0089'
removed `/var/lib/dpkg/updates/0090'
removed `/var/lib/dpkg/updates/0091'
removed `/var/lib/dpkg/updates/0092'
removed `/var/lib/dpkg/updates/0093'
removed `/var/lib/dpkg/updates/0094'
removed `/var/lib/dpkg/updates/0095'
removed `/var/lib/dpkg/updates/0096'
removed `/var/lib/dpkg/updates/0097'
removed `/var/lib/dpkg/updates/0098'
removed `/var/lib/dpkg/updates/0099'
removed `/var/lib/dpkg/updates/0100'
removed `/var/lib/dpkg/updates/0101'
removed `/var/lib/dpkg/updates/0102'
removed `/var/lib/dpkg/updates/0103'
removed `/var/lib/dpkg/updates/0104'
removed `/var/lib/dpkg/updates/0105'
removed `/var/lib/dpkg/updates/0106'
removed `/var/lib/dpkg/updates/0107'
removed `/var/lib/dpkg/updates/0108'
removed `/var/lib/dpkg/updates/0109'
stevenspc@ubuntu:~$ sudo dpkg --configure -a
stevenspc@ubuntu:~$ sudo dpkg --configure -a
stevenspc@ubuntu:~$ 


BTW, thanks for the help, plucky. That just solved my problem because I was finally able to install Kate.:guitar:

---

### Post by sk8brding on 2013-02-06
That fixed a similar problem for me on 12.10 when my pc froze during an update. Thx.
The command; sudo rm /var/lib/dpkg/updates/* -vf
Removes all the files in the updates folder?
Anyway, Thx.

---

