---
title: "Running Windows software with Ubuntu"
date: 2011-06-16
forum: General Help
---

### Post by sajith9002 on 2011-06-16
Does anyone can tell How to use a windows based Software in ubantu?..:)

---

### Post by howefield on 2011-06-16
First off, there may be native alternatives to the Windows applications that you want to use, but in the event that there isn't or you have a another reason for using the Windows version, you could install an application called Wine and run your Windows application through that.

Can be installed via Ubuntu Software Centre or Synaptic Package Manager, please note that not all windows software will work appropriately in Linux via Wine. Browse the application database at for more information.

[http://www.winehq.org/](http://www.winehq.org/)
[http://appdb.winehq.org/](http://appdb.winehq.org/)

---

### Post by lisati on 2011-06-16
Thread title changed from OP's username to something more relevant to the question.

---

### Post by nomko on 2011-06-16
> **howefield said:**
> First off, there may be native alternatives to the Windows applications that you want to use, but in the event that there isn't or you have a another reason for using the Windows version, you could install an application called Wine and run your Windows application through that.
 
Can be installed via Ubuntu Software Centre or Synaptic Package Manager, please note that not all windows software will work appropriately in Linux via Wine. Browse the application database at for more information.
 
[http://www.winehq.org/](http://www.winehq.org/)
[http://appdb.winehq.org/](http://appdb.winehq.org/)
 
It is not obvious that all Windows software version will work under Wine. On the site mentioned here of Wine there's a list which software version does work and which software version doesn't work with Wine. Best to do is search for an equivalant software package under Linux, then look on the list of winehq which Windows software package and version does work properly under Wine and if that doesn't work there's a third solution: installing a virtual machine (for Ubuntu there's VirtualBox, works very pretty: [www.virtualbox.org]("http://www.virtualbox.org")). With this tool you can do a full install of Windows in a virtual environment without destroying your Linux system (in fact it won't change your Linux system at all). After this you can install your Windows software in the Windows environment as usual. You will be working in a normal Windows environment.

---

### Post by iclestu on 2011-06-16
> **nomko said:**
> It is not obvious that all Windows software version will work under Wine. On the site mentioned here of Wine there's a list which software version does work and which software version doesn't work with Wine. Best to do is search for an equivalant software package under Linux, then look on the list of winehq which Windows software package and version does work properly under Wine and if that doesn't work there's a third solution: installing a virtual machine (for Ubuntu there's VirtualBox, works very pretty: [www.virtualbox.org]("http://www.virtualbox.org")). With this tool you can do a full install of Windows in a virtual environment without destroying your Linux system (in fact it won't change your Linux system at all). After this you can install your Windows software in the Windows environment as usual. You will be working in a normal Windows environment.

At the risk of hijacking a thread.....

Is it in anyway feasible to install windows on a virtual box when you dont have the installation media? Win 7 was pre-installed on my hdd when i bought my current PC but I was not supplied with a cd. I just installed kubuntu straight away as i had used it on my previous computer. I still have win 7 on dual boot but would much prefer to be able to use the virtualbox hoodgy!

---

### Post by nomko on 2011-06-16
> **iclestu said:**
> At the risk of hijacking a thread.....
 
Is it in anyway feasible to install windows on a virtual box when you dont have the installation media? Win 7 was pre-installed on my hdd when i bought my current PC but I was not supplied with a cd. I just installed kubuntu straight away as i had used it on my previous computer. I still have win 7 on dual boot but would much prefer to be able to use the virtualbox hoodgy!
 
No, Virtual Box requires an installation cd or a .iso file which contains the installation cd.

---

### Post by anaconda on 2011-06-16
actually..
it is possible to run windows from an existing partition in wmware (maybe in virtualbox too? dunno)

I tried this once a few years ago, and it worked. Only problem was that every time I booted it normally (ie. from grub) it needed to be activated again, because the hardware profile is different in virtual environment and normal boot...

No problem, if you want to run it only virtually...

---

### Post by iclestu on 2011-06-16
> **anaconda said:**
> actually..
it is possible to run windows from an existing partition in wmware (maybe in virtualbox too? dunno)

I tried this once a few years ago, and it worked. Only problem was that every time I booted it normally (ie. from grub) it needed to be activated again, because the hardware profile is different in virtual environment and normal boot...

No problem, if you want to run it only virtually...

hmmm - v interesting....

what do you mean by 'activated again'?

---

### Post by nomko on 2011-06-16
> **iclestu said:**
> hmmm - v interesting....
 
what do you mean by 'activated again'?
 
When you install Windows fresh on a system it's need to be "activated". In other words: M$ want you to register your legal Windows version on their server so that they know what kind of version you're running (i.e.: XP or Vista or W7), what kind of hardware your system has and that you get all the latest bugfixes for Windows. This to avoid illegal copying and the usage of 1 license on several systems which aren't yours as they say. M$ even demands that you activate your Windows version every time you change something on your computer: hardware. In other words, if some hardware breaks down and needs to be replaced, M$ demands that you re-activate your already activated Windows version just for changing the hardware on your computer. 
 
And since virtual machines do have other specification than the host computer, you migth ran into the issue of activating your Windows version everytime you start it up in a virtual machine. Virtual machines mostly emulate their own hardware like video graphic cards and memory.

---

### Post by dragonfly41 on 2011-06-16
Usually there is another windows partition with name such as "recovery" which is used to restore windows to factory settings in event of a crash.  Look for this in gparted.   I've got one which I've not used so far.

I wonder if this "restore to factory default" image might be used in virtual box to restore an oem windows in virtual box in absence of the installation cd which oem computers don't have?

Just curious .. I've not tried it.

---

### Post by Mark Phelps on 2011-06-16
AFAIK, the recovery partition can NOT be used to install an MS Windows setup using VirtualBox -- because it generally reformats the drive in the process -- and that would wipe out the Virtualbox installation.

As to the reactivation problem, that is STILL the case with Win7.  Folks have tried this on other forums and still mention that doing this forces reactivation -- and with some versions (i.e., OEM), you do that too many times and it will NOT reactivate.

---

