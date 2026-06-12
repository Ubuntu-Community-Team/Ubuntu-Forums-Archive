---
title: "need help in manual partitioning to install 9.10"
date: 2010-04-11
forum: General Help
---

### Post by Dactula on 2010-04-11
Hi All,
I am new to the world of Linux and don't have much technical knowledge . I have an old P3 machine with 256MB RAM which runs WIN XP fine. I want to set it up to dual boot  with WIN XP & Ubuntu 9.10 (which I downloaded from the Net and burnt the CD). Live CD option isn't working on my machine. When I tried to install  Ubuntu 9.10 the only practical option I had was to manually partition  the Windows drive to make space for Ubuntu but couldn't figure out how to do it. This may seem simple to many folks out here but sounds complicated to me. Please help. :confused:

---

### Post by Joeb454 on 2010-04-11
*Thread moved to **General Help**.*

---

### Post by spiky001 on 2010-04-11
I think you are abit lite on ram that will be 1 problem I know thats not the answer you want but it will cause problems even with loading

---

### Post by akakingess on 2010-04-11
> **spiky001 said:**
> I think you are abit lite on ram that will be 1 problem I know thats not the answer you want but it will cause problems even with loading

First of all @ Joeb454, Thanks for moving this thread.

Now, dactula, running on a machine with those dimensions for lack of a better word, you might be better off buying a newer machine to run Windows on as it is such a resource hog, I imagine that your XP may not run at it's full potential or at least as fast as you would like. I have found (through personal experience) that I could take a computer that Windows would run at a crawl on and use Ubuntu on it and be completely exstatic. That aside, if you wish to dual-boot, you need to make sure and defrag your windows drive so you could resize it and make room for Ubuntu (whichover version of it you choose) and then boot off of the CD and install using the manual partitioner (you will see what I am talking about when it gets to the partitioning point). What worries me is that the Live CD won't run on your computer, that is a sign that Ubuntu wouldn't run even after being installed. Please try the Live CD again, perhaps download and burn a new one to be sure and let us know what happens. Aside from that, you shouldn't have problems running Ubuntu and if the RAM appears to be an issue, than I would look at some lighter-weight GUIs, such as XFCE or KDE, they have been better for me on machines with less RAM. Please respond to let us know where you stand or where exactly you are having the precise issues.  Wow, didn't realize how long-winded I had gotten, sorry for all of the babbling. Good luck, and look forward to you responding so we can help find the best solution for you.

---

### Post by BrokeMahPC on 2010-04-11
I would recommend going with Xubuntu 9.10 on such a machine. It is almost the same but with the Xfce desktop which does not require as much resources as Gnome, and uses software that doesn't tax the memory as much but you can install what you like. 
[http://www.xubuntu.org/news/9.10-release](http://www.xubuntu.org/news/9.10-release)
[https://wiki.ubuntu.com/Xubuntu](https://wiki.ubuntu.com/Xubuntu)
Give this live CD a try - see if it works (does this have Gparted on it? - anyone? - probably does? GParted is the partitioning app that you can use to shrink windows partitions and make room for ubuntu / xubuntu)

What size is the hard disk?
Generally to dual boot you would de-fragment windows thoroughly, back up ur data, then choose the install windows / xubuntu side by side in the live CD installer. It will shrink the windows partition and install xubuntu in another partition next to it. You will have to specify how much space to give windows using the slider, drag it with your mouse.
If you want more advice, pre-partitioning etc, look at /  search for:
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html) - illustrated dual boot site
GParted - the partitioning app used
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome) - create a separate home partition if you have the space

Another popular option is to use Wubi to install Ubuntu inside windows, but check the minimum system requirements to see if you meet them.
[http://www.psychocats.net/ubuntu/wubi](http://www.psychocats.net/ubuntu/wubi)

---

### Post by Dactula on 2010-04-14
Thanks for your tips. Tried Xubuntu. Live CD works ok though takes about 8-10 minutes to load. Tried to install Xubuntu under WinXP but failed as RAM was a problem. Seems dual boot with XP on my machine is not a practical option; its got to be either / or. It will take a while for me to be comfortable with Linux and only then can seriously consider getting rid of XP and installing Xubuntu . Thanks for your advice once again. BTW is there a Xubuntu forum or should I post Xubuntu related queries in this forum itself ?

---

### Post by akakingess on 2010-04-14
You can post Xubuntu questions/comments here, just select it as the distro that you are talking about in the thread. Good Luck and have fun!

---

