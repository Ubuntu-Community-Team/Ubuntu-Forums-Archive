---
title: "Wubi Vs Full Install"
date: 2009-09-13
forum: General Help
---

### Post by CrusaderAD on 2009-09-13
Is there any benefit to running Ubuntu as a full installation vs running it with Wubi on a windows machine? Right now I'm just booting straight into Ubuntu and booting into windows when I absolutely have too (which isn't but maybe once every few months). I want to make a full install wiping everything else out and maybe run windows with a virtual machine. Any benefits doing it this way or should I stick with my current config?

---

### Post by QIII on 2009-09-13
If you are running a dual boot system, I would stay with that.  Running either inside the other may be "convenient", but neither would really be running natively.

Wubi is good for testing out Ubuntu if you are a Windows user, but not really a good final solution.

Using a virtual machine can tax your performance if your specs are marginal.

---

### Post by HalfCrackedTech on 2009-09-13
Well I have to say that I would love to be done with the Windows crutch but unfortunately I have online classes that want papers in Word.  I know that Ubuntu has a word processing program but I am not sure that my Professors would accept my word in that format.  

I find that Windows is so cluttered with BS that it causes your entire system to fall apart.

---

### Post by CrusaderAD on 2009-09-13
> **HalfCrackedTech said:**
> Well I have to say that I would love to be done with the Windows crutch but unfortunately I have online classes that want papers in Word.  I know that Ubuntu has a word processing program but I am not sure that my Professors would accept my word in that format.  

I find that Windows is so cluttered with BS that it causes your entire system to fall apart.

Open Office let you save in .doc format (word) and also lets you edit pre-existing documents. I'm finding fewer and fewer reasons to keep my windows partition.

---

### Post by HalfCrackedTech on 2009-09-13
OK well that is a relief but the only other thing that I use and need is a way to sync my iphone.  If i can do that with Ubuntu then I am going to get rid of the windows CRUTCH.

---

### Post by CrusaderAD on 2009-09-13
> **HalfCrackedTech said:**
> OK well that is a relief but the only other thing that I use and need is a way to sync my iphone.  If i can do that with Ubuntu then I am going to get rid of the windows CRUTCH.

I found this, it might work:

[http://www.downloadsquad.com/2008/03/04/itunes-syncing-now-works-in-linux-with-wine/]("http://www.downloadsquad.com/2008/03/04/itunes-syncing-now-works-in-linux-with-wine/")

---

### Post by HalfCrackedTech on 2009-09-13
Thank you very much.  Still need to get the  internet issue worked out but then I should be Windows free.

---

### Post by CrusaderAD on 2009-09-13
> **HalfCrackedTech said:**
> Thank you very much.  Still need to get the  internet issue worked out but then I should be Windows free.

Internet issue?

---

### Post by HalfCrackedTech on 2009-09-13
Yeah I have internet connection but can't access it.  In windows it works fine but in Ubuntu nothing.   I need to fix this issue but I am sure that it will go away when I full install Ubuntu.

The problem there lies in the fact that I am not going to be able to do that for a month when my wife gets her new laptop and I have something to transfer information to.

---

### Post by wilee-nilee on 2009-09-13
Wubi is not a true virtual as far as I know (which isn't very far) what can happen I also believe is that the wubi-Ubuntu can be acessed by windows which may reveal passwords-etc don't take my word on this though. A dual boot with seperate partitions will have Ubuntu running faster. A dual boot is easy, you get a gparted Iso burn it to a disc, or a live Ubuntu cd and reformat the hard-drive, leaving a blank for ubuntu then restart to windows due a thorough defrag then restart with the Ubuntu cd and let it install. when you get to the gui to pick your partitioning options choose side by side then you can adjust the partition with a slider at the lower portion of the screen. Personally I set that slider at where the disc is already partitioned and let it install in the free space. Also Supergrub is another great download for opening stuck partitions if your MBR is not set correctly so that you can edit bootloaders in windows or linux. As always though back up everything you might need including the windows program.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by HalfCrackedTech on 2009-09-13
So what you are saying is that I should not get rid of windows?

---

### Post by wilee-nilee on 2009-09-13
I have no opinion on windows persay, you never know when having it in the computer might be usefull. I am assuming that the windows version is a legit version so I would keep it for that reson alone, but I am not familiar with the EULA stuff.

---

### Post by CrusaderAD on 2009-09-13
> **HalfCrackedTech said:**
> So what you are saying is that I should not get rid of windows?

Windows is a good operating system. I don't mean to knock it. I'm a techie guy so I know what I like. To each his own. The only reason I really keep windows around is for Visual Basic programming. Other than that I have been capable of doing anything I need in linux. If you have any questions, feel free to drop me a message or start a thread. This is by far the most helpful forum I've ever been a part of and we're all glad to help.

---

### Post by CrusaderAD on 2009-09-13
> **wilee-nilee said:**
> Wubi is not a true virtual as far as I know (which isn't very far) what can happen I also believe is that the wubi-Ubuntu can be acessed by windows which may reveal passwords-etc don't take my word on this though. A dual boot with seperate partitions will have Ubuntu running faster. A dual boot is easy, you get a gparted Iso burn it to a disc, or a live Ubuntu cd and refrmat the hard-drive, leaving a blank for ubuntu then restart to windows due a thorough defrag then restart with the Ubuntu cd and let it install. when you get to the gui to pick your partitioning options choose sise by side then you can adjust the partition with a slider at th lower portion of the screen. Personally I set that slider at where the disc is already partitioned and let it install in the free space. Also Supergrub is another great download for opening stuck partitions if your MBR is not set correctly so that you can edit bootloaders in windows or linux. As always though back up everything you might need including the windows program.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

Thanks for the info... I might give it a try. It's almost that time of the year for a format. :)

---

### Post by wilee-nilee on 2009-09-13
> **raptormanad said:**
> Thanks for the info... I might give it a try. It's almost that time of the year for a format. :)

I have found gparted and super-grub to be invaluable as I don't have the terminal voodoo down. My friends who are true geeks can due some or most of what these option offer via the terminal or with a live cd. 

Good luck.

---

### Post by CrusaderAD on 2009-09-18
Well I did it. Full install and deleted all other partitions. I just decided to go for it. I know I won't regret it. Seems faster. Booting into windows once every few months won't be missed. :P

---

### Post by HalfCrackedTech on 2009-09-18
Me too not regretting it one bit, well I take that back I lost a folder that I am not happy about.  I had an ISO folder that had all my ISOs of Every OS and I lost it in translation. Not happy one bit. It was 50 gb of info gone. But other than that I am so happy Windows free YIPPIE!!!

---

### Post by CrusaderAD on 2009-09-21
> **HalfCrackedTech said:**
> It was 50 gb of info gone.

Whoa! Not good! I've had a few moments like that. The thought hits you like a piano and you suddenly get that gut wrenching feeling. I backup everything now with an external hard drive. Keep is a great program to back stuff up with.

```
sudo apt-get install keep
```

---

### Post by HalfCrackedTech on 2009-09-21
Thank you for that I was so mad cause it took me forever to get all those Iso's together and I also had some utility tools that I loved but whatever.

---

### Post by trixman on 2009-09-21
> **raptormanad said:**
> Well I did it. Full install and deleted all other partitions. I just decided to go for it. I know I won't regret it. Seems faster. Booting into windows once every few months won't be missed. :P

i did the same thing, i can do what  i need in Ubuntu do not miss windows at all.

---

