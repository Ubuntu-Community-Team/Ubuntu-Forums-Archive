---
title: "How to change I/O Scheduler to Deadline in Natty?"
date: 2011-07-12
forum: General Help
---

### Post by GECKYL on 2011-07-12
I wanted to try the I/O scheduler "Deadline" in Natty.  The reason is after about 5-10 minutes of inactivty the system becomes temporarily unresponsive and there is constant hard drive activity.  Firefox 4.0.1 is usually open but not always.  After about 20 seconds I can use everything again.  I have the " Alternative to 200 Line patch" and swappiness set at 10.  
I am using preload daemon, and additionally the noatime,nodiratime option in fstab.   Any help here?

---

### Post by macaholic on 2011-07-13
You have to edit /etc/default/grub and look for the line that starts with ```
GRUB_CMDLINE_LINUX_DEFAULT
```
Add to that line (within the quotes) ```
elevator="deadline"
```
e.g.: ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pcie_aspm=off elevator=deadline"
```
EDIT: Also run ```
sudo update-grub
``` (As GECKYL pointed out below)

I don't know if that will fix your issue, but that's how you change the scheduler. To find out what current scheduler you're using, you can run ```
cat /sys/block/sda/queue/scheduler
```
If you've properly enabled deadline, then the output should be 
```
noop [deadline] cfq 
```

---

### Post by GECKYL on 2011-07-13
Thanks!  You only forgot:

Code:
sudo update-grub

---

### Post by NightwishFan on 2011-07-13
Are you starved for memory when this happens? (Swapping?) The choice of elevator is probably not the cause of the loss of responsiveness in this situation. Also, preload tends to bunch up a lot of I/O at times which is why I have stopped using it.

The default swappiness value of 60 is fine. For workloads with a lot of huge processes like Firefox or Virtual Machines a value of 100 might be better.

200 line patch only isolates command line jobs into a single group so no help for this problem at all.

---

### Post by GECKYL on 2011-07-13
> **NightwishFan said:**
> Are you starved for memory when this happens? (Swapping?) The choice of elevator is probably not the cause of the loss of responsiveness in this situation. Also, preload tends to bunch up a lot of I/O at times which is why I have stopped using it.

The default swappiness value of 60 is fine. For workloads with a lot of huge processes like Firefox or Virtual Machines a value of 100 might be better.

200 line patch only isolates command line jobs into a single group so no help for this problem at all.


I will get rid of preload and see if that helps.
My used memory is less than 1GB when this happens.  I lose responsiveness for maybe 20 seconds and the hard drive led stays completely lit. It is swap activity I am sure of it.  The thing is the system monitor shows swap at 0% but then when I walk away from the computer and come back to it, it is unresponsive and the swap looks like this:

---

### Post by NightwishFan on 2011-07-13
You might have a runaway task. Check the top processes that are using memory in system monitor; You should also enable view -> all processes in the case it is xorg or another root owned process eating up all the memory. 

Using deadline will probably be of little use (in my opinion CFQ is better anyway). The 20 seconds or so of unresponsiveness is normal if your machine is swapping. This is peculiar as you have very little used ram. This may mean either the process that did this was already ended or its simply swapping cache. I have seen a similar issue but have not been able to get to the bottom of it.

Also you can tell the system to drop page-cache by running (one line at a time):
```
sudo su
sync; echo 3 > /proc/sys/vm/drop_caches
exit
```

Please tell me if you find out what process might be needing so much memory. If there is none that fit the bill this might be a bug.


Edit: Perhaps try this (will revert to default on a reboot). See if this helps.
```
sudo sysctl vm.overcommit_ratio=90
```

---

### Post by GECKYL on 2011-07-13
Ok it did it again.
I tried your suggestions above before this happened.  It seemed worse.
The swap was at 400 something MB and by the time I got the screenshot it dropped down...
Here a picture.

---

### Post by NightwishFan on 2011-07-13
Hmm.. This seems to be the same issue the other fellow on Kubuntu was having. I've been looking into this one (not that I am an expert or anything) and the problem is I am never able to reproduce it on my machine. Perhaps it is an Ubuntu only bug?

We should dub this "plenty of free ram but swaps anyway". So the overcommit_ratio tweak did nothing?

---

### Post by GECKYL on 2011-07-13
> So the overcommit_ratio tweak did nothing?It seemed to have an even harder time snapping out of whatever funk it was in.  :D
The screensaver became jittery and it took longer this time (maybe my imagination but I doubt it) to show the desktop and become responsive.
This has occured on many ubuntu based installs I have used.  (Pinguy, Mint, etc)
I use docky and conky and granola usually, but I don't think those would cause this.  I don't even have the video card driver installed for my Radeon 4670.

---

### Post by NightwishFan on 2011-07-13
Interesting. Well I am thinking this may be a bug related to the kernel. You should never be grinding to a halt with in the range of 3gb of free memory. There is not much else I can really suggest except perhaps to report a bug.

---

### Post by GECKYL on 2011-07-14
Switched to Mint 11 and no more problems.  :KS  Maybe it was some funky tweak that was implemented into Pinguy 11.04...  Mint 11 is using 1 kernel version lower on my current install however...

---

### Post by Quentusrex on 2011-07-24
I am getting what sound to be the same problem on a server install of 11.04. Clean server with only openssh-server and boinc installed. After X number of minutes one hard drive stays lit and the box is unresponsive. No process that isn't already started can start up. Anything that requires reading from the hard drive will block permanently. No new ssh session can connect, but existing ones are fine.

I think it is a kernel bug as well since it sound very similiar to this issue: [https://bugzilla.redhat.com/show_bug.cgi?id=605444](https://bugzilla.redhat.com/show_bug.cgi?id=605444)

---

