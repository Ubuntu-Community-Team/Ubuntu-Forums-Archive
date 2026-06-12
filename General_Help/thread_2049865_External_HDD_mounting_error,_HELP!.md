---
title: "External HDD mounting error, HELP!"
date: 2012-08-29
forum: General Help
---

### Post by Alcidious on 2012-08-29
Hi everyone,

Last week I was doing some kernel testing for a bug submitted to launchpad/canonical.  So I began to do a backup to my external hard drive first, and then my system froze (obviously the kernel did not fix the issue).  In retrospect I should have logged out, booted my reliable kernel, and then did the backup before testing... So it goes. 

Anyway, today I was trying to load a file off of my external HDD (I tried this on my laptop and desktop), and received the following message:

Error mounting: mount exited with exit code 13: $MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

Any ideas? Please tell me I didn't just lose everything on my external, I will be utterly heartbroken.

---

### Post by coffeecat on 2012-08-29
Is the backup drive formatted NTFS? The error message indicates that it is. If so, this...

> **Alcidious said:**
> So I began to do a backup to my external hard drive first, and then my system froze

...means that of the three possible reasons listed in the error message, an inconsistency in the NTFS filesystem is most likely. In which case, the best (only) way of fixing this is to run a chkdsk from Windows on the external drive. You can check NTFS filesystems and fix inconsistencies from the GUI in Windows, so you don't necessarily need to run chkdsk from the command line.

---

### Post by Alcidious on 2012-08-29
CoffeeCat,

I no longer have any windows operating systems on any of my devices.  You are right, when I got the External HDD everything was backed up from Windows.  Then when I switched to Ubuntu I saw that I could still access everything, and it seemed to have been working fine.  Could I do this on a public computer? What exactly would I look at or do in Windows to fix the situation?

---

### Post by coffeecat on 2012-08-29
> **Alcidious said:**
> Could I do this on a public computer? What exactly would I look at or do in Windows to fix the situation?

Depends what you mean by a public computer. If you can find a computer running Windows that can mount an external drive, that should do. These instructions seem to be for Windows Vista:

[http://windows.microsoft.com/en-US/windows-vista/Check-your-hard-disk-for-errors](http://windows.microsoft.com/en-US/windows-vista/Check-your-hard-disk-for-errors)

But the procedure for Windows XP and Windows 7 would be more or less the same, if I remember correctly.

Once you've repaired the filesystem and recovered your files, I suggest you think about what filesystem you need on your external hard drive. If you are going to use NTFS, you need access to a Windows system for exactly this sort of situation.

---

### Post by Alcidious on 2012-09-03
Coffee cat, 

Im using my friends laptop to fix the external hdd.  However, I didn't realize how long it would take and he must go.  Will disconnecting the repair process or suspending the computer damage the disk drive? or rather, my files on the disk drive?

---

### Post by coffeecat on 2012-09-03
> **Alcidious said:**
> Coffee cat, 

Im using my friends laptop to fix the external hdd.  However, I didn't realize how long it would take and he must go.  Will disconnecting the repair process or suspending the computer damage the disk drive? or rather, my files on the disk drive?

If you are running a filesystem check and it is repairing the filesystem then, yes, disconnecting it could be unwise. If you are running a filesystem check from the GUI, there might be a cancel button for you to exit the process gracefully without further damaging files. If you are running chkdsk from the command prompt, I really don't know, but I should think there is no way of stopping it without the potential for further filesystem damage. How long it takes partly depends on the size of the drive being checked, so it's difficult to say how long it should take. If it finds problems, it should prompt you with what it is doing.

---

### Post by Alcidious on 2012-09-04
Thanks a bunch CoffeeCat!

My friend was gracious enough to keep his laptop running, with my ex-HDD still attached, all the way home (and until it finished). So I think all my stuff is saved! I have learned a huge lesson here, and won't get in this position ever again (Ensure file systems agree, and Redundancies, Redundancies, Redundancies)!

What do I need to do to reformat the x-HDD to a linux filesystem? Is there anyway to do that without moving the data off and then back on? I am happy to read and study any resources you can point me to. Thanks again! 

PS-I will mark this as solved as soon as I hear back from you

---

### Post by coffeecat on 2012-09-04
> **Alcidious said:**
> Redundancies, Redundancies, Redundancies)!

Agreed! The old "mantra backup, backup, backup again, don't forget to backup and, oh, did I mention backing up?" applies. :)

> **Alcidious said:**
> What do I need to do to reformat the x-HDD to a linux filesystem? Is there anyway to do that without moving the data off and then back on?

If you reformat you need to move the data off and on again. Formatting a drive doesn't literally erase the data, but you would need data recovery software to recover the files, and this would not be 100% guaranteed of success. In short, you need to copy the data off the drive before you reformat it.

You can reformat your external drive to a Linux fileystem - I would suggest ext4 - with Disk Utility that comes with a default installation of Ubuntu. Plug the drive in, open disk utility, highlight the drive where it appears in the left pane, and then in the right pane click on where it says "Format Volume". A small window will pop up which allows you to choose the filesystem type - it defaults to ext4 anyway, but check this - make sure the "Take ownership of filesystem" box is ticked and click on format. You can then use the drive in any Ubuntu or Linux system, but with one caveat.

The fact that NTFS does not support the Linux system of permissions and ownership ironically means that it can be more convenient in that you don't see the permissions problems which can occur with Linux filsystems. If you format the drive partition ext4 with Gparted, for example, the filesystem will be owned by root and you will get a permissions denied error if you try to use the drive as an ordinary user. This is easily dealt with by running a couple of terminal commands, and is partly prevented by making sure the "Take ownership of filesystem" box is ticked when using Disk Utility. However, if you have more than one user account on your machine, there could still be a problem if you try to use the drive from an account other than the one that ran disk utility - your main administrator account.

Explanation: your first created Ubuntu account - the administrator account - has a UID (user ID) of 1000. If you create a second account it will have a UID of 1001, a third 1002, and so on. Most Linux distros start their user accounts at UID 1000, but some (at least they used to) at 500. This means that when you format the drive using your adminstrator account and "take ownership of filesystem", the filesystem will be owned by UID 1000 and can only be used by accounts with that UID. If you need your external drive formatted ext4 to be usable by anyone, then there is one terminal command (chmod) that you will need to run. If this is your situation, post some details and I can give you the exact syntax of the command.

---

### Post by Alcidious on 2012-09-04
No, I'm the sole user of the the HDD.  But i'm a little familiar with the chmod command (not extremely), but I've rented "Ubuntu Unleashed" 2012 edition by Matt Helmke, so I'm absorbing as much as I can.  thanks so much for the help! The last paragraph was really helpful in terms of learning, so I think I'm good.  If I run into any problems though, would you mind if I sent you a message? Thanks again!

---

### Post by coffeecat on 2012-09-04
> **Alcidious said:**
> If I run into any problems though, would you mind if I sent you a message? 

Since this is a forum, support through PMs is frowned on, so as an admin I'd better do a bit of frowning myself! :wink: The main reason for this is that others apart from the OP benefit from what is written in threads.

If you do run into any problems, don't hesitate to add to this thread. If you do, you should be able to remove the solved tag that I see you've added. I autosubscribe to all threads I post in, so I'll see if you post again and can pick up the conversation.

BTW, Matt's book is excellent. I have a copy myself. And BTW2, the chmod command would be of the form:

```
sudo chmod 777 /media/mountpoint
```

Where the partition has been mounted to a mountpoint in /media. Obviously, change "mountpoint" to whatever it really is. And "777" gives read-write-execute access to the world and its granny. If you need more restrictive permissions, that can be changed, but we could pick that point up if you do need more help.

Good luck!

---

