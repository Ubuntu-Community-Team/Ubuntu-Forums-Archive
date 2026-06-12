---
title: "How to recover from crash .."
date: 2012-02-22
forum: General Help
---

### Post by susja on 2012-02-22
Hello,
Please help me ... I have an issue.
I'm using Ubuntu 11.10 on my laptop for around 3 weeks, everything was OK, it worked without problem. Today I noticed that my laptop hung so I pushed the button. After that I have a problem. When I start the system it does not boot as before but bring me to the prompt where offers:
Ubuntu, with Linux 3.0.0-16-generic
Ubuntu, with Linux 3.0.0-16-generic ( recovery mode )
Previous Linux versions
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)
I tried all options but none of it restore my environment. 
Could someone please help, I'm really desperate with it.
Thanks in advance.
susja

---

### Post by aura7 on 2012-02-22
Restore your GRUB using live CD or any other bootable media... in case you are not getting the boot screen.
 
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by susja on 2012-02-23
- aura7,
thanks a lot for your fast reply.
Sorry that I'm not much familiar with recovery process so could you please be more detailed?
I'm able to access Ubuntu from live CD but it's not clear how it's related to Boot-Repair-Disk. I burned Boot-Repair-Disk. Should I now remove live CD and set Boot-Repair-Disk and click 'Recommended Repair'?
thanks

---

### Post by aura7 on 2012-02-23
There was a discussion prior to this thread too.. take a look at this
 
[http://ubuntuforums.org/showthread.php?t=76652](http://ubuntuforums.org/showthread.php?t=76652)

---

### Post by wildmanne39 on 2012-02-23
Hi, you probably damaged your file system with the hard shut down, you can use this method to shutdown or reboot safely.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)
Thanks

---

### Post by susja on 2012-02-23
well ... it didn't help ... After I ran Boot-Repair-Disk and rebooted system I've another error:
PXE-E61: Media test failure, check cable
PXE-M0F: Exiting PXE ROM.
Operating System not found

What else I could do?
thanks

---

### Post by susja on 2012-02-23
It looks that after running Boot-Repair I can't even get boot list option as I had before. Am I completele dead or still something could be done to recover?
Thanks for any help.  ... I hate to think that I will have to do everything from scratch.

---

### Post by susja on 2012-02-25
> **susja said:**
> It looks that after running Boot-Repair I can't even get boot list option as I had before. Am I completele dead or still something could be done to recover?
Thanks for any help.  ... I hate to think that I will have to do everything from scratch.

Really last question on this subject :)
I re-installed OS and restored all my previous data and settings from DVD backup.
Just afraid what would happen again if my PC freeze like it was in this case? Actually I'm not sure why OS get corrupted and was my push on the button the root of the problem or it's was crashed already and my hard push didn't make a difference.
Just question for future issues: in case my PC freeze again ... is it save to push of power down button or I could shut it down somehow more gracefully?
Thanks,
susja

---

### Post by wildmanne39 on 2012-02-25
Hi, the answer is in post five of this thread, please go to the link for directions on shutting down safely.
Thanks

---

### Post by susja on 2012-02-25
- wildmanne39,
how try that combination of keys?
I'm asking because I tried and it didn't work for me ... so just was curious if it's my local issue of misleading article.
thanks,
susja

---

### Post by wildmanne39 on 2012-02-25
Hi, it works just like this.> Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB will get you safely restarted. REISUO will do a shutdown rather than a restart.You do have to hold the Alt and SysRq and press the keys one every 3 to 5 seconds if that does not work then your keyboard must be frozen too.
Thanks

---

