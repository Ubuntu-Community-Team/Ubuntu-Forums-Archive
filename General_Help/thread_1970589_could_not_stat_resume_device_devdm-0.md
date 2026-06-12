---
title: "could not stat resume device dev/dm-0"
date: 2012-05-01
forum: General Help
---

### Post by johnycage on 2012-05-01
After installing 'hibernate';
when I first reboot my PC I encountered following *similar message

```
libcrypt version: 1.5.0
Could not stat the resume device file /dev/dm-0
Please type in the full path name to try again or press enter to boot the system
```

[Very Similar situation with this thread]("http://ubuntuforums.org/showthread.php?t=1672532"), when restarts I get GRUB option where I can get access to system via earlier versions of Linux (with no GPU/ graphics cards supported.) So I can post this query from firefox. But not able to boot normally. 
Please help. 

In past I'd stuck at worse situation & GParted with boot'd through pendrive saved my life, but this time I've access to GUI & CLI and can edit files conf if required so I should try that first (GParted is the last resort of course)
I've removed 'hibernate'
as well as 'uswsusp' But it's not helpful. It's stuck at above message. :(
On internet I couldn't find proper solutions (hence the thread)

I recently upgraded to 12.04 from 10.04 LTS Ubuntu Server edition (with Ubuntu Desktop on top of it). Now I regret it most, as new problems are surfacing every hour.

---

### Post by johnycage on 2012-05-02
viola! Resolved!
What I did this time, 
I hibernate my PC ```
sudo pm-hibernate
```
which switched the computer off & when I resumed it booted normally. 
I dont know what I did, but the issue is resolved.
Now reading all threads I'm not gonna touch suspend, hibernate, standby in my Ubuntu Machines for sure. :)

---

### Post by shukuboy on 2012-06-05
I just had the exact same problem.  
I installed 12.04 LTS Desktop version on my laptop yesterday and managed to install all my apps and get everything working which took me over a day.

```

libcrypt version: 1.5.0 Could not stat the resume device file /dev/dm-0 Please type in the full path name to try again or press enter to boot the system


```

After installing hibernate in synaptic, I rebooted to set the power-options ( hibernate on closing the laptop lid ), but I never saw the light of Ubuntu's day again.

I have a working linux (suse 11.4) on my laptop which I can use to go through the Ubuntu installation on filesystem and possibly make minor changes, but have no clue how to fix this.

Any help would be appreciated.

---

### Post by geethujerry on 2013-01-08
After installing 'hibernate';
when I first reboot my PC I encountered following *similar message

libcrypt version: 1.5.0
Could not stat the resume device file /dev/dm-0
Please type in the full path name to try again or press enter to boot the system

---

### Post by geethujerry on 2013-01-08
After installing 'hibernate';
when I first reboot my PC I encountered following *similar message

> libcrypt version: 1.5.0
Could not stat the resume device file /dev/dm-0
Please type in the full path name to try again or press enter to boot the system

---

### Post by blind3d on 2013-01-27
Just experienced this, I almost shat bricks when I thought my encrypted filesystem would never see light of day again. I too fell victim of this hibernate program, as suspend doesnt seem to work properly, and I want something to just put computer to sleep, tried hibernate and this happened... I would think that this is a bug and they should remove it from the repos...   EDIT: I am on 12.10 btw

---

