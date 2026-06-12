---
title: "Hard disk clicking sound, hdparm fix offers no solution, not a hardware problem"
date: 2012-09-07
forum: General Help
---

### Post by chilloutmo on 2012-09-07
Hello everybody!

When on battery, my laptop hard drive makes a tock tock every couple of seconds. Now if you think "this one is easy, hdparm...", wait a second, it gets trickier.

First of all: this is not a hardware issue, I have no problem under Windows 7 (I dual boot) and when the AC cable is plugged in. 

The first time this happened, a couple of months or years ago, I used the standard "sudo hdparm -B 254 /dev/sda" workaround which eventually fixed the problem permanently. 

Now it reappeared, and I tried all of the most commonly known hdparm fixes but none of them solve the problem. Currently, I am on battery power and hdparm is set to 254 (I tried setting it to 255 but it makes no difference either) and the clicking sound still appears. I also tried using tools such as tlp or laptop-mode-tools but nothing helped. I have no idea why this problem is back now as I haven't really changed anything that I can think of. 

The weird thing is also that it definitely has something to do with the parking of the head and with power management, because the clicking sound appears only when the disk is idle, and only when on battery power. 

I use Ubuntu 12.04 64 bit on an Asus 1215n machine bought back in 2010. 

Any help would be much appreciated!

chilloutmo

---

### Post by TheFu on 2012-09-07
Clicking sounds from a HD that happen too often are doing something bad.  **Backups now!**  I would start researching the exact HDD model involved for known issues and a firmware update.  If you have SMART enabled - and you should - use ```
smartctl --all /dev/sda
``` to get the exact vendor + model number to start your knowledge search.

It may not be a hardware issue, but simply something that Linux is not setup to address correctly.

**Backup NOW!**

I just received a few new HDDs at fantastic prices.  After ordering, I started doing research to discover they probably have a clicking issue too. Not some of the drives, but every one of them, regardless of the OS.  The vendor has produced 3 firmware updates to address the noise, but not to stop the APM from happening.  These are not "green" drives, so there is not expectation of saving power.  Since those aren't laptop drives, the model/vendor won't help you.

Did I mention, **BACKUP NOW?!!!**

---

### Post by chilloutmo on 2012-09-08
Thanks for your reply (and I back up regularly, don't worry :-)), but it is definitely not a hardware issue. The problem does not appear when the laptop is plugged-in, and the problem does not appear alltogether when I boot to windows. 

So it is basically something with how linux manages power management of the hard disk, only that the typical "hdparm" solutions that you find when googling around won't work anymore.

---

### Post by TheFu on 2012-09-08
I think you are missing the point. **Something is wrong.  **It is a hardware issue when a HDD makes noise.  Something is happening.  If it happens all the time, that is bad.  HDDs have moving parts that wear out.  Just because it works today, doesn't mean nothing bad is happening. It doesn't mean that the life of the HDD isn't being significantly shortened.

IMHO, this is like a drip coming from the roof of a home.  If it isn't fixed quick, you'll going to cause other issues when it is not convenient.  I'd get the vendor, model and S/N and start searching the drive manufacturer's support forums for answers. I'd report the HDD to the manufacturer support team and see if they have any solutions too. 

Data is more important than hardware any day of the week.

I've lost data before I got the **backup religion.**  I'm paranoid.

---

### Post by 2F4U on 2012-09-08
A clicking hdd is often due to an agressive power management, but there may be other reasons. Here is a great article on how to track down possible causes:

[http://www.thinkwiki.org/wiki/Problem_with_hard_drive_clicking](http://www.thinkwiki.org/wiki/Problem_with_hard_drive_clicking)

---

