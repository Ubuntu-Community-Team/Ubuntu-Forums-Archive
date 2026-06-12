---
title: "Suspend and Hibernation Resume Immediately"
date: 2010-02-27
forum: General Help
---

### Post by brianafischer on 2010-02-27
After some diligent research, I cannot find a solution to the issues I am having with 9.10 and suspend/hibernation.

The main issue I am having is that suspend and hibernation appear to work properly, but they immediately resume and I am displayed the password screen to unlock the computer.

I found a thread that suggested adding [usbcore.autosuspend=-1]("http://ubuntuforums.org/showpost.php?p=8706667&postcount=33") to the GRUB2 config file, but that did not seem to make a difference.

I cannot find a solution for this, and would like some assistance in either obtaining the root cause of the issue to file a proper bug report OR (better option) fix the issue.

Any help would be appreciated, below are my notes to date:

From my research:
[LIST]
    [*]The majority of threads on the ubuntu forums are dealing with issues when resuming from suspend or hibernate.
    [*]Does not seem to be a common command to suspend or hibernate.  There are a lot of different commands listed here - [http://ubuntuforums.org/showthread.php?t=813387](http://ubuntuforums.org/showthread.php?t=813387)
    [*]Others in this thread also have immediate wakeup - [http://ubuntuforums.org/showpost.php?p=8625727](http://ubuntuforums.org/showpost.php?p=8625727)
    [*] Other threads:
      [http://ubuntuforums.org/showthread.php?t=1144999](http://ubuntuforums.org/showthread.php?t=1144999)
      [http://ubuntuforums.org/showthread.php?t=505890](http://ubuntuforums.org/showthread.php?t=505890)
[/LIST]


-Brian

---

### Post by brianafischer on 2010-03-01
Can anyone assist with this?  It would be greatly appreciated.

---

### Post by d3v1150m471c on 2010-03-01
I want to say suspend is a ram exclusive operation while hibernate is swap space. Have you ever altered these settings at any point in time? By that I mean your swappiness.

---

### Post by drewsus on 2010-03-01
I found that if I had an SD card in my laptop then I would see this behaviour. 
Might this be the case for you?

---

### Post by brianafischer on 2010-03-01
> **d3v1150m471c said:**
> I want to say suspend is a ram exclusive operation while hibernate is swap space. Have you ever altered these settings at any point in time? By that I mean your swappiness.
Have not altered any settings.

---

### Post by brianafischer on 2010-03-01
> **drewsus said:**
> I found that if I had an SD card in my laptop then I would see this behaviour. 
Might this be the case for you?
This is in a desktop.  There is no SD card reader.

---

### Post by schmickers on 2010-03-05
I have the same problem. In Ubuntu 9.10 Netbook Remix, (running on a noetbook computer, not a netbook) Occasionally, it will suspend and stay suspended, but most of the time it spins down the HDD, switches off the screen, there is a click, and then the computer immediately begins powering up and waking.

Is there any log file we can look at that records what events triggered a wake from sleep?

---

