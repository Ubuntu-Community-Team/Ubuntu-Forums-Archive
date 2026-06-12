---
title: "Ubuntu 11.10 --&gt; won't boot (was booting)"
date: 2011-12-14
forum: General Help
---

### Post by BobDull on 2011-12-14
Hello,

I have been running Ubuntu 11.10 alternate for more than a month and just now am having some problems. The only thing that I did that I can think of that would've caused this random problem is the Software Center Updates. There was a group of 30~ that I installed yesterday, other than that, no fresh changes to the install. I'd prefer not to do a clean wipe, hopefully I don't have to.

Problem: When I boot the computer, it freezes at * Checking battery state...

The only "fail" message I have before this is:
mountall: Plymouth command failed
mountall: Disconnected from Plymouth.


Then it says: prosvc is running
>> Deleting stale PID file log/thin.pid

Starting web server apache2 [OK]
Checking batter state ....  [OK]



What I have tried: I thought it was maybe a PostgreSQL issue, so I modified the /etc/sysctl.conf file to contain "kernel.shmmax = 41943040", and that didn't fix anything.

I have tried going into CTRL + ALT + F1 terminal and: sudo apt-get install nvidia-173. Various different types of doing that, uninstall, reinstall, update, etc. I have also gone into the blacklist file and made sure it looks good.

Tried installing/updating/restarting lightdm.

basically I tried everything from: 
[http://askubuntu.com/questions/44373/how-to-fix-postgresql-installation](http://askubuntu.com/questions/44373/how-to-fix-postgresql-installation)
[http://ubuntuforums.org/showthread.php?t=1859820](http://ubuntuforums.org/showthread.php?t=1859820)
[http://askubuntu.com/questions/37590/nvidia-drivers-not-working-after-upgrade-why-can-i-only-see-terminal](http://askubuntu.com/questions/37590/nvidia-drivers-not-working-after-upgrade-why-can-i-only-see-terminal)
[http://techspear.com/2011/08/booting-ubuntu-oneiric-stops-at-checking-battery-state-ok/](http://techspear.com/2011/08/booting-ubuntu-oneiric-stops-at-checking-battery-state-ok/)


And no avail. Hoping someone can help me out. If you need any more information to help with this error, please and thanks.

Maybe someone knows if updates they rolled out recently causing errors? Thanks.

---

### Post by matt_symes on 2011-12-14
Hi

Can you boot into recovery mode or a root console ?

Kind regards

---

### Post by BobDull on 2011-12-14
Yes, I have my alternate CD in and I can get into a recovery mode through that.

I can also get into root terminal via CTRL + ALT + F1.

---

### Post by matt_symes on 2011-12-14
Hi

> **BobDull said:**
> Yes, I have my alternate CD in and I can get into a recovery mode through that.

Using it as a liveCD ?

> 
I can also get into root terminal via CTRL + ALT + F1.

When booting from the hard drive ?

Look at the logs in the /var/log directory. 

Post back the log file

```
/var/log/dmesg
```

from your hard drive or get the output of

```
dmesg > log.txt
```

and post back here. That may give some clues.

Kind regards

---

### Post by BobDull on 2011-12-14
Not using it as a LiveCD, just using it to try and fix this :)

Yes, if I choose to boot from the first hard disk and I reach the boot error/freeze, I am able to bring up CTRL+ALT+F1 terminal.



As far as posting the log.txt, I can't boot that computer, and am typing from another laptop. Is there anything I can re-type/look for in particular? I don't have any experience reading this dmesg file, so nothing is sticking out as good or bad to me.

Thanks for your help.

---

### Post by matt_symes on 2011-12-14
Hi

> Yes, if I choose to boot from the first hard disk and I reach the boot error/freeze, I am able to bring up CTRL+ALT+F1 terminal.What i was thing was something along these lines.

* Boot the broken computer as normal until you get to the freeze and bring up the console as you specified above.
* Enter a root console using ```
sudo -i 
```and entering your password.
* Plug in a USB stick and mount it manually using the mount command. ```
mount /dev/sdb /mnt
```* run ```
dmesg > /mnt/log.txt
```* unmount the usb stick ```
umount /dev/sdb
```* post the log file from your working computer.

This assumes your usb stick is given the device name sdb.

If we can look at dmesg's output then we may find out what failed and why.

Kind regards

---

### Post by BobDull on 2011-12-14
Ok, I've got the log.txt file.

*note* I had to rename it to .pdf because of file size limitations, original file was log.txt


btw: I got it to boot, but I don't think it was a very comprehensive fix. It may have only temporarily fixed it :-/ Looking for what caused the issue still, thanks.

---

### Post by matt_symes on 2011-12-14
Hi

Looking at the log file now. 

You have encrypted partitions ?

Kind regards

---

