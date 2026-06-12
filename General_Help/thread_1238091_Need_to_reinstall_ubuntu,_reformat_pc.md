---
title: "Need to reinstall ubuntu, reformat pc"
date: 2009-08-12
forum: General Help
---

### Post by darkenergy4 on 2009-08-12
On my PC which has ubuntu I want to reinstall the newest version and I don't care if all my data is deleted-there's nothing anyway. So I want a reinstall and reformat. 

What's the next step?

---

### Post by dcstar on 2009-08-12
> **darkenergy4 said:**
> On my PC which has ubuntu I want to reinstall the newest version and I don't care if all my data is deleted-there's nothing anyway. So I want a reinstall and reformat. 

What's the next step?

Simply select the existing Ubuntu partition to be overwritten at that stage of the install process.

---

### Post by darkenergy4 on 2009-08-12
What's the ubuntu partition?


I can't update new files. I think I have a virus.

I tried System-Admin-Update Mgr, and it doesn't update.

---

### Post by m4tic on 2009-08-12
boot into your newest ubuntu version cd, read through the steps and when reaching the partitioner, select guided, and ubuntu will reformat the whole drive if thats what you wanted. find other installation guides on this forum, they work.

The cd image can be found on [www.ubuntu.com](www.ubuntu.com)

---

### Post by darkenergy4 on 2009-08-12
> **m4tic said:**
> boot into your newest ubuntu version cd, read through the steps and when reaching the partitioner, select guided, and ubuntu will reformat the whole drive if thats what you wanted. find other installation guides on this forum, they work.

The cd image can be found on [www.ubuntu.com](www.ubuntu.com)

I went there and it failed. 

Is there a simple procedure to reformat my hard drive and reload ubuntu? 
I could have a virus.

---

### Post by DeMus on 2009-08-12
> **darkenergy4 said:**
> I went there and it failed. 

Is there a simple procedure to reformat my hard drive and reload ubuntu? 
I could have a virus.

Did you do exactly what m4tic said?

Put the CD with the new Ubuntu in your CD-drive and reboot, this time from CD. (Maybe you have to change the boot order in the bios of your computer)
When you get the menu, what you want to do, choose install.
Then at step 4 you choose guided.
The rest is an easy to follow step by step "questions and answers" thing.
Good luck.

---

### Post by fluffman86 on 2009-08-12
you don't have a virus, but if you really want to format your hard drive and install the latest ubuntu, you'll need to go to ubuntu.com and download the cd image, burn it to cd, and install off of that.

This guide is really helpful:
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

It tell you everything you need to know to install Ubuntu.

---

### Post by darkenergy4 on 2009-08-12
Gee, I got the impression from Free Geek in Vancouver that disks are redundant with ubuntu. I shall begin the atom based, realworld, non-online trek to get this task accomplshed.

---

### Post by QIII on 2009-08-12
You have only vaguely described your problems as "It didn't work".  You make it somewhat difficult for us mortals to diagnose the issue.

It is certainly not impossible that you might have a virus that affects Linux, but that is only an extremely remote possibility.

It seems that the atom based, realworld, non-online source you have already sought out has given you some misguided notion that discs are redundant in Ubuntu.

The electron-based, virtual world, online sources have given you the correct information.

You can repartition and reinstall.

Alternatively, you can download the file, burn it as an .iso, insert it in your cd drive and start your computer.

I'm not aware that there is a metaphysical method for doing this.

---

### Post by darkenergy4 on 2009-08-13
I tried to download ubuntu 9.04 deskyop - i386 and I got a failed message. That did not work.

I also can't update new files. That does not work also. When I try to update the 27 files in question I get a 'dpkg --configure -a' message. What's that?

So I might not need to reformat or get a new version of ubuntu/linux as mu current version seems to work okay. I'm not really knowledgeable enough with ubuntu to be proactive here.

---

### Post by jocko on 2009-08-13
> **darkenergy4 said:**
> I also can't update new files. That does not work also. When I try to update the 27 files in question I get a 'dpkg --configure -a' message. What's that?
That means you have probably interrupted the package manager when it was in the process of updating, installing or removing a package, and it can't do anything else until you let it finish that interrupted action.
Just do as it tells you, type this in a terminal:
```
sudo dpkg --configure -a
```
Input your password (you will not see that you type anything, but just type it anyway) and press enter.
After that the package manager should work fine again.

---

### Post by a2z on 2009-08-13
my error tells me I should reinstall dpkg. I don't know how to do this. And don't know where to even start. I would assume I need to uninstall it first?
Please help as I have been having this problem for some time. Which seems to be getting worse as time goes by.
Thanks to everyone's devotion to these forums,

a2z

---

### Post by jocko on 2009-08-13
> **a2z said:**
> my error tells me I should reinstall dpkg. I don't know how to do this. And don't know where to even start. I would assume I need to uninstall it first?
Please help as I have been having this problem for some time. Which seems to be getting worse as time goes by.
Thanks to everyone's devotion to these forums,

a2z
EDIT: Don't hi-jack other peoples threads with your own problems. If you want help and can't find an answer by searching the forums, start your own thread or post in a thread that discusses the exact same problem as the one you have.
But: You can't uninstall dpkg. It's such an integrated part of ubuntu that you would leave your system completely useless. If you get an error that tells you to reinstall dpkg, The only simple fix I can think of is to backup your home directory and reinstall the entire os.

> **darkenergy4 said:**
> I tried to download ubuntu 9.04 deskyop - i386 and I got a failed message. That did not work.
**When** did you get the "failed message"? **What** did it say?

---

### Post by zkriesse on 2009-08-13
At this point have somebody you know burn an ISO Ubuntu Jaunty disk for you and stick it in your system....

---

