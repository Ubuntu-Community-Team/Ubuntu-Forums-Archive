---
title: "Ubuntu 10.10 crashes when I start it up, drops to shell, etc."
date: 2011-04-07
forum: General Help
---

### Post by Theophastu on 2011-04-07
I'm entirely new to Ubuntu. Or, rather, I've been trying to get it to work on and off for a few years now. This time, I downloaded it, installed it through Windows, went to run Ubuntu after restarting my computer. It installed itself during this time, then it restarted my computer. Afterwards, I received this message: 

Gave up waiting for root device. Common problems:  
 - Boot args (cat /proc/cmdline)   
   - Check rootdelay= (did the system wait long enough?)   
   - Check root= (did the system wait for right device?)  
- Missing modules (cat /proc/modules; ls /dev) 
ALERT! /dev/sdb1 does not exist. Dropping to a shell!   BusyBox v1.15.3 (Ubuntu 1:1.15.3-1ubuntu5) built-in shell (ash) Enter 'help' for a list of built-in commands.
[FONT=monospace]


I've read some posts about how it could be the rootdelay and that typing exit after a few moments may solve it. It does not.

I've also read posts about a grub file or folder or something. It seems unaccessible in Windows.

I have no actual experience with Linux, so please talk me through any solutions as though I don't know any jargon.

Also, I screwed up my post due to my being unfamiliar with some of the post options. I apologize for that.
[/FONT]

---

### Post by LewRockwellFAN on 2011-04-07
You might check the cable connections, both power and data on your drives. Maybe unplug and plug them back in and make sure they are seated tightly. Or maybe boot from the live CD and see if you can access all your partitions. A worn connector, a loose seating, a flaky cable - I've experienced similar messages as a result of all of those.

---

### Post by Theophastu on 2011-04-07
I don't believe it would be a loose cable. It's on my laptop. The partition is on the only hard drive in the laptop and Windows boots fine from the laptop.

Also, I installed it with Wubi, so I don't have a Live CD.

---

### Post by smurphy_it on 2011-04-07
```
ALERT! /dev/sdb1 does not exist.
```

It would appear it is looking for a secondary hard drive.  The way the drive devices work in linux (for sata drives) is starting at sda.  Each partition on that drive has a partition #.

In this case, you are looking for sdb1 (1st partition, on second hdd).  As you stated you only have 1 disk drive / Hard drive, then it is trying to boot from a non-existant drive.  

You should get the grub script in my signature, run that, and paste the results back in here.  People can help you better then ;-)

---

### Post by Rubi1200 on 2011-04-07
If there is a problem with the Wubi install, we need to see the boot info script:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

You can download and burn the latest image to CD (there are instructions on the page how to do this):
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

---

