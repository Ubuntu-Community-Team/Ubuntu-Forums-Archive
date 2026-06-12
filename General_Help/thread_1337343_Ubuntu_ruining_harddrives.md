---
title: "Ubuntu ruining harddrives?"
date: 2009-11-25
forum: General Help
---

### Post by Sentience on 2009-11-25
Immediately after I upgraded to Karmic from Jaunty on my Presario V5000 I started getting the disk error warning. The computer was a little outdated anyway so I decided to order myself a new one. The day I get it in the mail I install Karmic as a clean install after adjusting the bios to boot from CD which really threw me off because Im not that tech savvy and expected it to just work on its own. The same thing has happened! 
       The problems dont seem limited to the Ubuntu section. There are some errors when I log into windows7 as well. I think this is almost certainly a problem with Karmic and not with both hard drives, as I have seen other threads talking about this. I think the problem is that Karmic is messing up the drivers or the bios or the disk format or something on the actual hardware. Its a real problem. Has anyone else been experiencing this or have a solution? What can I do to salvage my hard drives?

---

### Post by mkvnmtr on 2009-11-25
The idea that an OS install has damaged your hard drive is so far fetched that I do not think you can get an answer.
 Maybe you should post the errors you see and someone will be able to explain them.

---

### Post by Sentience on 2009-11-25
Have you read all the other posts about the same problem? Obviously its not doing physical damage to the HD, but I have been hearing reports of drivers being damaged by this distro. Do a search and you will find some reports of this.

Apparently lots of people are having this problem. I am going to log back into windows to see if I am still having problems after reflashing the bios. I dont have a recovery disk for this computer or else I would just do a clean install. I better order one.

---

### Post by Sam on 2009-11-25
Have you check the SMART status of your drives ?
System > Administration > Disk Utility
Click a harddrive then "More information"

---

### Post by Sentience on 2009-11-25
Looks like I was right.

[http://www.breakitdownblog.com/ubuntu-power-saver-settings-could-damage-hard-drive/](http://www.breakitdownblog.com/ubuntu-power-saver-settings-could-damage-hard-drive/)

I will go back and check the hard drives on my laptop. Its only mad laptops that are breaking. Ubuntu is fine on my desk top.

---

### Post by yoasif on 2009-11-25
this bug was fixed... [https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/785](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/785)

---

### Post by Sentience on 2009-11-25
So was it the power settings killing hard drives or was it something else?

My other laptop wont even turn on anymore. It just shuts off when I attempt to load a new operating system. While its possible that at least the older system was already on its last legs, the fact that something similar happened to my new laptop and also my external hard drive makes me think that Ubuntu did this.

Not good. This is a major blow to Ubuntus credibility. Karmic shouldnt have been released in its current state.

---

### Post by Sentience on 2009-11-25
At least my external hard drive is still under warranty.

I dont really trust Karmic at this point, even if this bug is allegedly fixed. I am either going back to jaunty or maybe open Suse. 

Can anyone direct me to a thread that talks about deleting Karmic to reinstall Jaunty under a dual operating system with windows 7?

---

### Post by yoasif on 2009-11-25
> **Sentience said:**
> I dont really trust Karmic at this point, even if this bug is allegedly fixed. I am either going back to jaunty or maybe open Suse. Look at the bug report, it affected Suse as well.

[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695)
[https://bugzilla.novell.com/show_bug.cgi?id=386555](https://bugzilla.novell.com/show_bug.cgi?id=386555)

---

### Post by Sentience on 2009-11-25
Maybe I should just stick with Windows 7 :(


Ubuntu broke my laptop hard drive and my external hard drive, and the laptop was not under warranty :(
I like supporting the non-corporate alternative, but I cant afford this. My faith has been shattered.

---

