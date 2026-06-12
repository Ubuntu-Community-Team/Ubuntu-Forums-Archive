---
title: "Where to start in troubleshooting stability issues?"
date: 2010-04-19
forum: General Help
---

### Post by jonsayer on 2010-04-19
My system freezes every few hours or so. It is getting to the point where I can't work anymore.

The crashing usually occurs while the computer is in the middle of something, like loading a web page, booting a program, or saving a file. No single program seems to be the issue. 


I've tried changing window managers, updating my system, even upgrading to 9.10 (which my computer for some reason can't handle and it freezes when it boots the livecd). Nothing seems to fix it.

All I really know is that it is not my window manager, because it freezes whether I am using metacity or compiz.

I'm concerned it might be because I formatted my hard drive ext4 when I installed 9.04. Is ext4 new enough that it is unstable? If so, how do I fix this?

I'm using 9.04 on a generic laptop (it literally has no branding on it).

---

### Post by jonsayer on 2010-04-19
bump. I really do need a hand with this. I have no idea where to go from here.

---

### Post by quadproc on 2010-04-19
> **jonsayer said:**
> My system freezes every few hours or so. It is getting to the point where I can't work anymore.

The crashing usually occurs while the computer is in the middle of something, like loading a web page, booting a program, or saving a file. No single program seems to be the issue. 

You may be having hardware issues.  Can you check the power supply voltages and the temperature inside the computer case?  Often, the BIOS or a utility program can read the CPU's temperature sensor and report it.  Your system's tendency to fail when busy does suggest a temperature problem.
> 
I'm concerned it might be because I formatted my hard drive ext4 when I installed 9.04. Is ext4 new enough that it is unstable? If so, how do I fix this?

I'm using 9.04 on a generic laptop (it literally has no branding on it).When ext4 was first introduced it was sometimes known to corrupt a file system.  The problem seemed to occur most frequenctly when encryption was in use.  I do not know the current status of ext4; I stayed with ext3 because I want to avoid such problems.

quadproc

---

### Post by jonsayer on 2010-04-19
Thanks for responding! I hadn't thought of overheating issues. I've had other laptops that shut down with an overheat and they turn off, whereas this one just sort of stops. The screen still shows my windows and whatnot.

I will try keeping it up and well ventilated. I keep it stacked on phone books right now, which probably block vents.

---

### Post by dabl on 2010-04-22
You didn't really describe your "crash" -- does it shut the computer off completely, or is it more of a "freeze" of the screen and keyboard and mouse?

The idea of an ext4 filesystem causing the system to crash is pretty far-fetched, IMHO, if it was previously happy with ext3. There's nothing about the added features of ext4 that should induce such behavior.

Can you run top, and put that window where you can keep an eye on it?  When the freeze happens (if it's a freeze), it would be helpful to know what the top process is, and how much of the CPU it is using.

---

### Post by TheFu on 2010-04-22
Hopefully someone asked you to look at syslog, dmesg, and /proc for errors. Based on the first post, it could be anything. I'd start with the PSU, video card, and disk going bad first, assuming there was nothing in the error logs.

The next step is to reboot the system, don't let X/windows run and leave it overnight. Does it stay up or not? If you never start a GUI/X, remote in and give it lots of workload, does it stay up?

I consider EXT4 to be experimental. My data is worth 2+ yrs of other people testing it in production BEFORE I touch it. I'm still running JFS and have for over 10 yrs. EXT4 can wait until 2012, at least.  I haven't had a disk issue related to the file system in about 8 yrs. I'm religious about backups and place important data on a RAID external array tho - all running JFS.

---

### Post by ericrules on 2010-10-10
I have just installed 9.04, and I am having similar issues.  As soon as I installed it it started freezing straight away, so much so that it doesn't last long enough to change any settings, or even look at the bios.  Are there any solutions to this?  
Thanks

---

### Post by whalogreg on 2010-10-10
> 

I'm concerned it might be because I formatted my hard drive ext4 when I installed 9.04. Is ext4 new enough that it is unstable? If so, how do I fix this?



I had many problems with ext4, disk errors, problems playing video (which still doesn't make sense to me) and such. I made a fresh ext3 partition a few months ago and migrated everything and haven't had any problems since... I don't think you're having the same symptoms I was having, but it did solve problems for me..

---

### Post by petrasflorin on 2010-10-10
Do this:
Exit terminal, "sudo apt-get install hal"
after that is complete
do this, hal-disable-polling --device /dev/sr0 (or /dev/cdrom or /dev/dvd, but if the first one works that's fine)
and
hal-disable-polling --device /dev/sda (or whichever your hard drive is called)

---

