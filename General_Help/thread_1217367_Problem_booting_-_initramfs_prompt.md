---
title: "Problem booting - initramfs prompt"
date: 2009-07-19
forum: General Help
---

### Post by T-Train on 2009-07-19
If someone could point me in the right direction that would be great.

I am having a problem booting into Ubuntu 9.4.  Ubuntu was installed and running for a couple of weeks.  I was also running a version of Windows in Virtualbox.  I got up this morning and received failed to write errors in Windows and read-only errors in Ubuntu.  I rebooted and am unable to boot into Ubuntu, I am receiving the attached error screen.  I am able to boot with the Ubuntu Live option.  When running GParted I am able to see my partitions.  I ran a check against the partition I was using and received the error below.  Also I had to install with the boot option pci=nomsi or the drive would not be recognized.

I had this problem a couple of months ago and I thought it was just a hard drive problem.  I reported the drive as bad and received a replacement.  The current drive I am using is only 2 weeks old.  It is possible that the drive could be locked for some reason?


Hardware: Asus A8V-XE, AMD Athlon 64 X2(3800+), WesternDigital 500GB SATA HDD.
Software: Ubuntu 9.4 (32bit) on a ext4 FS


Error from GParted:
e2fsck -f -y -v /dev/sda1
 /dev/sda1:recovering journal
 JBD: Failed to read block at offset 20156
e2fsck 1.41.4 (date)
 /dev/sda1: Attempt to read block from filesystem resulted in short read while reading block 36228796
e2fsck: Input/output error while recovering ext3 journal of /dev/sda1

---

### Post by T-Train on 2009-07-24
I guess no one has had this issue.  I am chalking it up to the drive overheating.  I was able to recover it by using spinrite.  Spinrite found a couple of bad sectors and repaired them.  I am going to look into purchasing a hard drive fan.  Let me know if anyone has any suggestions.

---

### Post by synapsys on 2009-07-24
What kind of hard drive do you have?

---

### Post by T-Train on 2009-07-25
I have a Seagate Barracuda 500GB SATA drive.  I have already sent one in for a replacement for the same issue.  The temp was probably between 50-60C, I would think that would be an acceptable temp.

---

### Post by synapsys on 2009-07-25
Wow! that's hot! I would get some extra cooling installed. I like to keep mine under 100f or around 40c

---

### Post by T-Train on 2009-07-25
Another possibility it is the ext4 file system.  It looks like someone had the same issue and posted in Launchpad.  I reformatted and am running with ext3.

---

### Post by munky99999 on 2009-07-25
The issue is that your booter cant find the directories. So the issue is... you cant read them. So where's the trouble?

Could be physical... you're overheating and the metals expand and you lose it.
Could be logical... your filesystem was busted up.

How do you fix it? Easiest way would be reinstalling. 

The others would be fsck tools and such.

---

### Post by T-Train on 2009-07-25
Yea, I have tried re-installing but the problem still occurs.  I think I am done with the ext4 FS.

---

### Post by vcppp_p on 2009-10-23
sorry for bumping the topic, I'm just experiencing the same issue!
What is the most important, I'm running U 9.04, hosting WinXP (as guest system) in VirtualBox... and it's all installed on Barracuda 500GB SATA !!

well the only major difference is the filesystem, I'm using ext3 ... do anyone have any clue what to do?

I *need* to get back the data from the drive...

---

### Post by T-Train on 2009-10-23
I know it sucks, I have not had the problems since installing with the ext3 FS.

---

