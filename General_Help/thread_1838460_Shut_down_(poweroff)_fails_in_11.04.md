---
title: "Shut down (poweroff) fails in 11.04"
date: 2011-09-03
forum: General Help
---

### Post by brucehohl on 2011-09-03
I just upgraded from 10.04 to 11.04 on a Lenovo B575 laptop. Under 10.04 the B575 shut down (power off) properly if "Shut down" was clicked on the Gnome desktop.  

Under 11.04 shut down (power off) fails. That is, 'Will now halt' is displayed in terminal but the computer does not power off.  The 11.04 install is updated to kernel 2.6.38-11-generic x86_64. The only way to power off the B575 is by holding the power button down for about 6 seconds.

Please see trial & error in post #2 for attempted work arounds.
Thanks for any suggestions for fixing this annoyance.

There is a Launchpad confirmed bug report for this problem: 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/762203](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/762203)

The bug is currently unassigned so if this bug affects you please go to the bug report above and click: "This bug affects X people. Does this bug affect you?", and then click: "Yes, it affects me". If all of us affected report being affected the "bug heat" might get high enough to attract some attention.

---

### Post by brucehohl on 2011-09-11
With a system updated to kernel 2.6.38-11-generic NONE of the trial & error below (based on other posts) resulted in a working poweroff:

VARIOUS SHUTDOWN COMMANDS:
$ sudo poweroff
$ sudo shutdown -P now
$ sudo shutdown -h now
$ sudo shutdown -hP now
$ sudo shutdown -P 0
$ sudo halt
$ sudo reboot # also fails


REMOVING VARIOUS KERNEL MODULES:
Adding 'rmmod snd-hda-intel' to top of /etc/init.d/halt
$ sudo rmmod ath9k  # Before shutdown.
$ sudo rmmod r8169  # Before shutdown.


USING VARIOUS GRUB PARAMETERS:
noapic
pnpacpi=off
acpi=noirq
acpi=noacpi
acpi=off      # B575 will not boot with acpi=off
nomodeset


BIOS:
There are no network or power settings that can be changed.


PACKAGES/SERVICES/SETTINGS:
Making sure the following packages/services/setting are not installed/running/used before shutdown/poweroff:

-laptop-mode-tools
-gnome auto login
-LibreOffice quickstart
-Turning off wireless via (1) Gnome tool, (2) Fn+F5 or (3) Wireless switch BEFORE shutdown.


UBUNTU VERSIONS:
10.04 install or LiveCD: shutdown and poweroff OK!
11.04 install or LiveCD Kernel 2.6.38-11-generic x86_64: shutdown and poweroff FAIL!
11.10 BETA2 LiveCD Kernel 3.0.0-11-generic x86_64: shutdown and poweroff FAIL!

Can anyone suggest how to find the cause of this problem?

---

### Post by AbtZ on 2011-09-11
This happens to me as well, on an ASUS U36SD. It worked, then all of a sudden stopped working, perhaps after a kernel upgrade.

---

### Post by brucehohl on 2011-09-11
There is a Launchpad confirmed bug report for this problem:  [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/762203](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/762203)

The bug is currently unassigned so if this bug affects you please go to the bug report above and click: "This bug affects X people. Does this bug affect you?", and then click: "Yes, it affects me". If all of us affected report being affected the "bug heat" might get high enough to attract some attention.

---

### Post by TeoBigusGeekus on 2011-09-11
One more command for you to try:
```
sudo halt
```

---

### Post by brucehohl on 2011-09-11
$ sudo halt does not power off the B575 either. I added that to the list in post #3.

I also took a careful look at the log files dmesg, kern.log and syslog and found nothing unusual. There seems to be a fair number of reports of shutdown problems for computers under 11.04 that shutdown normally under previous versions (like 10.04 in this case). The problem may be fixed with a subsequent up but it would be nice to find a fix now.

---

### Post by aura7 on 2011-09-11
what about sudo reboot

---

### Post by AbtZ on 2011-09-11
Poweroff does not work for me, while reboot does.

Consequently, sudo halt does not work, while sudo reboot does.

Anyway, I solved the problem by uninstalling laptop-mode-tools. It seems there's a bug possibly related to the cpufreq governor ondemand that causes this problem. Found it in this thread:
[https://bbs.archlinux.org/viewtopic.php?id=113985](https://bbs.archlinux.org/viewtopic.php?id=113985)

---

### Post by brucehohl on 2011-09-14
AbtZ, thanks for that reply and link. My default install of 11.04 does not includ laptop-mode-tools.  I also tried to remove the wireless module before shutdown (rmmod ath9k) but that had no effect. The link indicated that others have found other modules which if removed prior to shutdown allowed the computer to poweroff properly.  I will do some trial & error with removing modules.

If anyone can suggest anything else that has corrected this annoyance please do so.

---

### Post by frozen.fire on 2011-09-14
Issue the below command in terminal:

```
sudo apt-get update && sudo apt-get upgrade
```You may think that your system is completely updated as it says but at times when you check in your update manager (alternatively), you will still find that the updates are available. 

This will perhaps solve your problems relating to shutdown (freeze) and/or reboot (black screen). There is never a harm in trying an update.

Try it and let us know. :)

---

### Post by frozen.fire on 2011-09-14
By the way, i just checked the post above that other shudown commands too dont work for you. Try issuing 
```
sudo modprobe -rf rt2860sta
sudo modprobe rt2860sta
echo blacklist rt2800pci | sudotee -a /etc/modprobe.d/blacklist.conf
```

Do a forced shutdown on your ubuntu and then reboot. Perhaps this should also help you fix your normal shutdown issue. if it doesn't do a force shutdown another time and check if a normal shutdown works for you after reboot. 

Hope it helps. Take care.. :)

---

### Post by brucehohl on 2011-09-14
Performed updates and the problem remains.  These upgrades did not include a kernel update.  This is, kernel remains 2.6.38-11. (The problem was not present with the kernel from 10.04 or LUPU528 (Puppy) which is based on 10.04.)

Module rt2860sta is not loaded. Module r8169 is loaded so I '$ sudo rmmod r8169' but poweroff still failed.

It is a shame there is not a established method for resolving poweroff problems. Not only does poweroff fail but also suspend, hibernate and reboot.

---

### Post by frozen.fire on 2011-09-15
Ok... I found a few similar posts scattered across the web and for many users, disabling the quickstart of open office (or libre office or whatever) did the trick. And further for some, disabling auto login from the login has solved the problem. 

Also try if 
```
sudo shutdown -h now
or
sudo shutdown -hP now
or
sudo shutdown -P 0
```

Being very honest, i really don't know why or how the disabling open office helped... but amazingly, it did...

---

### Post by brucehohl on 2011-09-17
frozen.fire, thanks for those suggestions.  I tried each without success. I did add them to my list of things tried in Post #2.

---

### Post by DeMus on 2011-09-18
I don't think another version of shutdown will work since the shutdown process does start, it just doesn't finish.
I have the same with LinuxMint Katya, LMDE and Ubuntu 11.04. So I wrote that on the original bugreport, mentioned at the top of this page.
Let's hope they find it fast.

---

### Post by magicland on 2011-09-18
Hi there,

Whenever you're on ubuntu do you mount another partition of your hard drive to access files, music, docs, etc? Or an iso?

---

### Post by brucehohl on 2011-09-18
magicland, no other mounts are made. Also, this is default install of Ubuntu 11.04 using the entire disk. The install includes updates to the latest kernel: 2.6.38-11-generic. The same result (computer fails to shutdown) occurs if the computer is started with the Ubuntu 11.04 LiveCD using kernel 2.6.38-8-generic). 

AND last weekend I tried without success the Ubuntu 11.10 beta using kernel 3.0.0-x from the LiveCD. Thus, the problem may not magically go away with a future update.

---

