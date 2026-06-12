---
title: "apt-get removed network-manager?"
date: 2010-11-16
forum: General Help
---

### Post by rillip on 2010-11-16
I had something unusual happen and thought I should mention it, see if it was worth reporting to someone.

I was going to arping something the other day and found it wasn't installed.  So I used sudo apt-get install arping. It went through fine, I was arpinging happily.  I shut down for the night, and then this morning, I couldn't connect to the internet.

I do some searching around and get eth0 added to me /etc/network/interfaces correctly, and I'm back online, but I can't see the network manager to connect to a wireless network; not a big deal since I have a dock here, but I might want to go on the move.

So, I start looking around forums and in the process of following some of those guides, I find NetworkManager is not installed!

I get it installed and everything managed properly again. My system is working as intended.  But now I'm curious what happened, so I start looking at some of the logs in /var/log.  Then I find this in /var/log/apt

peatheri@philip:/var/log/apt$ cat history.log | grep network-manager -B 4

Start-Date: 2010-11-15  09:48:40
Commandline: apt-get install arping
Install: arping:i386 (2.09-2)
Remove: network-manager:i386 (0.8.1+git.20100810t184654.ab580f4-0ubuntu2), network-manager-gnome:i386 (0.8.1+git.20100809t190028.290dc70-0ubuntu3), iputils-arping:i386 (20100418-2ubuntu1)
End-Date: 2010-11-15  09:49:01


Why is installing arping removing network-manager?  Is this a bug in the package, the repository, sunspots??  I was concerned so I figured I'd post it, and maybe if someone else has this issue, they'll see an answer.

---

### Post by gordintoronto on 2010-11-16
Please report this as a bug.

One of the benefits of using Synaptic is that you can see what will happen before it happens. I told it to install arping in Maverick, and it told me it would remove network manager. Cancel, cancel, cancel!

---

### Post by rillip on 2010-11-16
> **gordintoronto said:**
> Please report this as a bug.

One of the benefits of using Synaptic is that you can see what will happen before it happens. I told it to install arping in Maverick, and it told me it would remove network manager. Cancel, cancel, cancel!

I just double checked from another machine, apt-get warned me too, I'm just a big dumby :p

kids@efam1:/var/log/apt$ sudo apt-get install arping
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libnet1
The following packages will be REMOVED:
  iputils-arping network-manager network-manager-gnome
The following NEW packages will be installed:
  arping libnet1
0 upgraded, 2 newly installed, 3 to remove and 139 not upgraded.
Need to get 82.9kB of archives.
After this operation, 3,371kB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.


I'll go report it, what a kick in the pants way to learn to read! :)


----------------------------------------------------------------------------------------------
Edit
----------------------------------------------------------------------------------------------


Wow, this was reported in 2008 and listed as fixed.  arping conflicts with ip-utils arping, which is a dependency for network-manager.  The bug is listed as solved.

Removing three system packages isn't a bug, it's a feature! :p

---

### Post by 68omalley on 2010-11-19
I'd also be interested in a solution for installing arping without removing network-manager.

---

### Post by dcstar on 2010-11-19
> **68omalley said:**
> I'd also be interested in a solution for installing arping without removing network-manager.

So the existing arping version that **you want to replace** doesn't work?

---

### Post by 68omalley on 2010-11-19
As far as I can tell there are two versions of arping (see last entry [here]("http://www.linuxquestions.org/questions/linux-networking-3/how-to-find-ip-address-of-a-machine-if-i-know-their-mac-address-353239/")).  I know the MAC address of a machine and I am trying to figure out the IP (which is not static).  It seems that the iputils version cannot do this, but the other version can.

---

### Post by dcstar on 2010-11-20
> **68omalley said:**
> As far as I can tell there are two versions of arping (see last entry [here]("http://www.linuxquestions.org/questions/linux-networking-3/how-to-find-ip-address-of-a-machine-if-i-know-their-mac-address-353239/")).  I know the MAC address of a machine and I am trying to figure out the IP (which is not static).  It seems that the iputils version cannot do this, but the other version can.

Don't install the .deb, install a binary:

[http://www.habets.pp.se/synscan/programs.php?prog=arping](http://www.habets.pp.se/synscan/programs.php?prog=arping)

---

### Post by Shideneyu on 2013-03-31
Hello

First of all, I would like to kill the author of arping, who presents this bug as a feature. How can we use arping if we lack connnectivity?

I don't got any interfaces at all anymore, I had no idea of what happened and have already lost 2 hours of my life, and I'm quite sure it will waste my all evening;


I can't install the network manager as I don't have internet. Downloading the folder and ./configure make and so on won't make it, I got 5 unresolved dependances, and I got to download them one by one seperately.

Yeah, typing ifconfig gives me one and only one interface: lo.

If someone could help me it would greatly help me, I have no intention of reinstalling everything for such a trivial error...
I use linux as a main and only OS. I'm even borrowing the computer of a friend to tell you this.


Thanks you

---

### Post by oldos2er on 2013-03-31
[COLOR=#000000]If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.[/COLOR]

---

