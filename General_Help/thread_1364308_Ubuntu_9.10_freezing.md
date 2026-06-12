---
title: "Ubuntu 9.10 freezing"
date: 2009-12-25
forum: General Help
---

### Post by mvashi on 2009-12-25
I have been very happy with my Ubuntu installations since the days of Ubuntu 7.However lately , since installation of Ubuntu 9.10 , the system freezes up frequently.

Previously I used the system for weeks at a time without rebooting and now I have to force shutdown atleast once in a day.

Is there any kind of log generated when system crashes which can point to problem areas ?

I have already done the memtest as suggested in one of the posts and all was ok 
I have P4 2.4ghz,1.25 GB RAM with 80 GB HD

---

### Post by droadtrip on 2009-12-25
[COLOR=Navy][SIZE=3][FONT=Georgia]Looks like you need more Ram. I can't stand to do things on less than 2 GB unless it is a severe lightweight alternative linux distro. [/FONT][/SIZE][/COLOR]

---

### Post by Norwal on 2009-12-29
I'm having the same problem.  Random freezing, in my case with in the 1st 2 or 3 minutes of startup.  I followed the advice of this thread,
 
[http://ubuntuforums.org/showthread.php?t=1306275](http://ubuntuforums.org/showthread.php?t=1306275)

and uninstalled  Compiz.  This worked for the rest of the day but this morning it started freezing again.  I went back into Synaptic and got rid of Compiz-Plugins, -Wrapper, and -Core as well.  I have been stable since then, but I guess tomorrow will be the true judge.

If you find a "System Crash Log" please post here.

Thanks

---

### Post by Norwal on 2009-12-29
Well Compiz was not the culprit after all.  The freezing was back after I turn off the computer for a few hours.  I had to reboot 7 times before I got a stable session. Run for 2 1/2 hrs now. This is getting to be a big pain in the neck.

---

### Post by damontallen on 2009-12-29
I'm having the same problem as Norwal.  I've turned off Compiz because I have an older machine and only have 768MB of memory.  I have an external hard drive the is formatted as ext4 so if I'm abandoning Ubuntu I'll need a distro that can read it.  Are there any light weight Dedian distros out there that can do that?

---

### Post by emoguitarist06 on 2009-12-29
> **droadtrip said:**
> [COLOR=Navy][SIZE=3][FONT=Georgia]Looks like you need more Ram. I can't stand to do things on less than 2 GB unless it is a severe lightweight alternative linux distro. [/FONT][/SIZE][/COLOR]
No he has way more than the recommended RAM by ubuntu

---

### Post by emoguitarist06 on 2009-12-29
> **damontallen said:**
> I'm having the same problem as Norwal.  I've turned off Compiz because I have an older machine and only have 768MB of memory.  I have an external hard drive the is formatted as ext4 so if I'm abandoning Ubuntu I'll need a distro that can read it.  Are there any light weight Dedian distros out there that can do that?

Try Xubuntu, it's a lightweight ubuntu.
or Mint
or Puppylinux

---

### Post by john newbuntu on 2009-12-30
I have'nt experienced the freeze yet in Karmic, but I suspect some part of the memory to be bad when it happens. I would suggest a thorough memory test, probably keeping just one memory module at a time.
The other option would be to significantly reduce the memory taken up by the kernel (alter the kernel boot command by adding, say mem=256) and see if you still get the hang (assuming that you have enough swap space).  But this would be a trial and error method.

---

### Post by damontallen on 2009-12-30
> **john newbuntu said:**
> 
The other option would be to significantly reduce the memory taken up by the kernel (alter the kernel boot command by adding, say mem=256) and see if you still get the hang (assuming that you have enough swap space).  But this would be a trial and error method.

Thanks for the tip but how do I do this?

Edit: Installed Xubuntu and still have the problem so it is hardware issue that can't be ignored.  I'll try to replace the memory and see if that works.

---

### Post by Norwal on 2009-12-30
I gave up on sorting out the problem and did a fresh install of 9.10.  Now to get everything else up and running. Wine,WOW,Vent and worst of all Nvidia Drivers.

I guess it was to much to hope that Ubuntu had reached the point of smooth transitioning from version to version.  But still, once Ubuntu is running stable, it beat the heck out of anything MS puts out.

Good luck everyone. If you hear from me again, the freezing back and I've loaded 9.04. LOL

 Update:  Running smoothly. No freezing up. Runtime 3 hrs.

---

### Post by damontallen on 2009-12-31
I'm glad to hear Norwal is up and running but with a fresh install of Xubunu my computer froze during its first update.  After that I ran about 3hrs on a memory test from the live cd (11 passes) without and problems.  My problem is not a memory issue nor is it a problem with over heating.

I'm running:
9.10 Xubuntu
733.3 MiB
Mobile Intel Celeron CPU 2.40GHz
30 GiB Hard drive

I attach the syslog and the kern log files shortly.

Edit: Added Attachments

---

### Post by john newbuntu on 2009-12-31
[FONT=Verdana]Since memory apparently appears to be ok, since we look lost here, here are a few things to try if you have some time:
Edit your /etc/default/grub file.  Set the following and save it.
GRUB_CMDLINE_LINUX="mem=256M"
Reboot and see if you still get the freeze/hang.  The idea here is to use only a small portion of the memory(apparently the good portion).  Note that I have not done this and it will definitely slow your system down. You can always undo this change if it does not work.

The other thing is to do a complete file system check (e2fsck) from liveCD to rule out any filesystem issues replacing sda2 with your paritition 
sudo e2fsck -C0 -p -f -v /dev/sda2

I must admit have not experienced any freezing so far with Karmic with my Dell E1505 - Intel Centrino Duo -80GB HD.  I run both Ubuntu and Kubuntu.
[/FONT]

---

### Post by lyall on 2010-01-01
test your memory the the Ubuntu boot disk and run the test memory
to is if your memory is okay

also run the system Monitor the check which apps are using the most of the CPU or the memory the apps are using

I would check them first before re-installing it all over again

Also test the condition of your hard drive.
most hard drive company have a program to test the hard drive to see the condition of the drive
I  brought a new seagate 1 tb and the cd to test it came with it
It also allow me to clone the data from the old drive to the new drive.  then I had to expand the partition 

good luck and have fun learning

---

### Post by damontallen on 2010-01-04
Well I've found that if I'm running grub 1 and ext3 I don't crash.  Well I guess I'm done upgrading.

---

### Post by ashokgm on 2010-01-27
[http://linux-solution-for-us.blogspot.com/](http://linux-solution-for-us.blogspot.com/)

---

