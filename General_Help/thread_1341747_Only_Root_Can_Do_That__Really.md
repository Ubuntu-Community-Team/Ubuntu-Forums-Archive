---
title: "Only Root Can Do That?  Really?"
date: 2009-11-30
forum: General Help
---

### Post by oldefoxx on 2009-11-30
Interesting Issue at hand.  I have three hard drives installed, and after some juggling around, I have 13 partitions, one being swap.  Six are ntfs, four are ext3, and two are ext4.

I'm sole user here, in my own home, and want all partitions to be accessable from the word boot.  My experience is that can be done via the /etc/fstab table entries.  The root drive (/) is not available for any additional mount operation, but the remaining can be set up in /etc/fstab so that they mount at startup.  Put the mount point in /media, and they appear as icons on the desktop.  Put the mountpoint in /mnt or elsewhere, and they do not show on the desktop.  Matter of taste which way to go.

But of the 13 partitions, minus the swap and root, I should have eleven icons on my desktop for the remaining eleven partitions, but I only get ten.
For some reason, the entry I have for /dev/sdb9 refuses to mount at the time of the bootup.  The swap partition is /dev/sdb8, and the root partition is /dev/sdb10, which you can tell means one is just  before the the other just after the partiton that does not mount on its own.

If I use a sudo command of mount -t ext3 /dev/sdb9 /media/B9, I can get it to mount just fine.  But if I go to Places and try to mount it via the GUI, I'm told that I am not allowed to mount the volume, that only root is allowed to mount it.

Very strange.  Once mounted, it is fine, but getting it to mount automatically just doesn't work.  I've tried different options in the /etc/fstab entry to try and make it happen, but nothing has any effect.

Looking for something related online has not been helpful.  Nothing I've found seems to apply.  So I was wondering if anybody had any suggestions?
I mean, what makes /dev/sdb9 so different from /dev/sdb6 and /dev/sdb7 which are mounting as ext3 with no problems at all?

---

### Post by Agent ME on 2009-11-30
You're not able to mount it via the GUI because users only have permissions to mount external hard drives that way. There used to be a menu you could change that on but it seems to have been taken out of 9.10 or be a package I forgot to reinstall, but that's a different problem really.

Can you post the relevant contents of your fstab?

---

### Post by oldefoxx on 2009-12-20
By first looking around then trying different thngs, I seem to have hit on a solution.  Here is what a typical entry in /etc/fstab might look like when done:

/dev/sda3     /media/D    ntfs-3g     defaults,user,exec,rw    0   0


The defaults alone pick up some options, but create a read only access to the contents of that drive.  By adding user,exec,and rw, we override some of the defaults.  User (or users) extends access to someone other than the default owner (root).  Exec means you can run programs off this drive.  And rw means that it is no longer just read only.  Seems to work fine.  However, since you rarely find programs on an ntfs partition that will run under Linux (unless you have wine or something else as a crutch), you might want to drop the exec as well.

To make the above work, you have to create a folder in /media named D, so that it will look like /media/D.  It doesn't have to be situated in /media of course, but this is common if you want to access the drive directly via the Desktop.  And it does not have to be just a letter name, but D might serve to remind you which drive letter was assigned to it when running under Windows.  You could instead indicate the partition designation, such as /media/sda3, or you might choose to use the given partition name. such as /media/DATAFILES.  To then mount the partition, just do a sudo mount -a in a terminal window or do a reboot.

Note that I used /dev/sda3 instead of the UUID= method.  This is old style Linux, useful because it is easier to get right in cases like this.  UUID= is suppose to be more stable and more specific, but falls down whenever a designated partition is reformatted, because then a new UUID is generated, but /etc/fstab does not get updated automatically.  So if working with multiple operating systems alternatively, it may prove slightly better to use the /dev designation.  However, there is an exception to this as well.  If you delete, add, or merge partitions, the original /dev designation may get dropped and a new one created.  With 5 partitions on one drive, ranging from /dev/sda1, /dev/sda2, /dev/sda3, /dev/sda5, /dev/sda6 (what would have been /dev/sda4 is the extended partition here, and ignored). If I decided to delete /dev/sda3 and cut it to create a swap partition as well, I would likely end up with this mess::

/dev/sda1
/dev/sda2
/dev/sda7       - old sda3 slightly smaller in size
   ...          - unusable partition space
/dev/sda5
/dev/sda6

What makes it unusable where the swap partition should go is the fact that only four partitions can exist on a hard drive, and to get more,
we make one of those an extended partition, then through software magic, we can divide that into some number of logical parttitions.  So what has happened is that between the end of our new partition (dev/sda7) and just before the old /dev/sda5 (which is a logical partiton), we have the actual fourth partition, /dev/sda4.  We can't change /dev/sda4 without having some impact on the logical partitions contained within it, and we may not want to do that.  So instead, we decide to put /dev/sda3 back as it was, only if we delete and add it back, it then becomes /dev/sda8.  So that is why they decided to move soto the UUID as a better means of designating partitions in /etc/fstab.

There are tools that offer to create a new partition table, which would put things back in their original order and designations, but the warning there is often that it will wipe out the contents of the whole drive, which you really do not want to do in most cases.

So if you can't fully go with the UUID method, yet see the problems of trying to drop back to the old /dev designation method, what can you do?
Well, there is the partition label method, and you can pretty much control that as you choose.  So if for the original /dev/sda3 partition I gave it the label A3-ntfs,  I could designated where it is positioned with respect to other partitions and what file system is on it.

When it changed on me to /dev/sda7, I could still have it named as A3-ntfs and use /media/A3 as its mount point.  What I would not know is the actual partition designation now unless I check it out, and I would not know what drive letter or name it may have had originally under Windows.  But it is still better than nothing in my opinion, and more consistent with my plans to stick with Linux in place of Windows.

And this is not to say that the Windows method is perfect either.  You may not recognize the problems that can happen there unless you deal with multiple partitions, the add-in of external drives, and having more than one install of Windows to deal with, each on its own partition.  Then it is just as bad or worse.

Actually with multiple installs of Windows, it is much worse, because Windows is hung up on the principle of using the letter designation method for locating things in the system, so you can't run an applicaton or find data when needed if the drive letters switch around just because you installed the operating system on a separate partition.  This has such a disasterous effect on entries in shotcuts, in .INI files and particularly in the Registry that you essentially have to install all your applications all over again as well.

That about summarizes some of the most difficult things I've had to learn to recognize and find ways to deal with.  It is the latter aspect of Windows just described that has done the most to turn me off of Windows going forward.  Not that there weren't enough other hidden issues and problems to pull me away from Windows eventually, of which its whole authentication program that started with XP has irritated me the most.

---

### Post by dcstar on 2009-12-20
> **oldefoxx said:**
> Interesting Issue at hand.  I have three hard drives installed, and after some juggling around, I have 13 partitions, one being swap.  Six are ntfs, four are ext3, and two are ext4.
.........


Use the **pysdm** package to set up correct mounting in the fstab file.

---

### Post by oldefoxx on 2009-12-21
First I've heard of Psydm.  I took a look at it.  For what it does, it might be fine, but I don't feel it does enough.

See, here is the thing:  Any time you set out to make change to your hard drives, I mean almost anything you do there, the impact carries through.  Now as i see it, psydm does fine for the Linux distribution that you are currently running, but any changes made with it only carry through to the /etc/fstab that is currently in play.  If you set up any other partitions as / with any other Linux. there will also be a /etc/fstab on that partition as well, but pysdm isn't going to touch that one, so when you try to reboot into that other boot option, its fstab table is going to be out of whack because it no longer agrees with what the hard drives and partitions now look like.  And the effects can be that you no longer can boot up that alternate Linux install.  That means you change /etc/fstab here, you have to find and change it accordingly along with any other /etc/fstab found.  I don't see that pysmd does that, or recognizes the problem.

Pysdm might help Linux, but changes to the hard drives and partitions also carry to any other OS installed as well, such as Windows. With Windows, it is often the matter of changes that only involve FAT or NTFS volumes, but changes here can do things like assigned drive letters get changed, and that can keep windows from starting up or running as it should.

Pysdm takes you through a series of steps in making changes, and you already have to know something of Linux in order to make key decisions here.   But still, like I said, it isn't quite the whole picture when it comes to dealing with matters involving multiple OSes set up on several partitions.  And there are very few installs where two or more OSes can reside together on a single partition.

You cannot simply take one /etc/fstab and copy it over to another partition either.  This is because two key entries involve recognizing the root (/) partition and the swap partitions.  The swap partition may be the same in each case, but the root will have to be different, and what was root in the previous case will have to be removed, comented out, or changed to correspond to a given mount point.  The mount point will likely have to be manually added as well.  If these changes do not take place, then you might try to run an alternate Linux OS, but the contents of this clone of /etc/fstab will just direct you back to the first one for the root partition and below.  That might not be a sucessful matchup with the kernel just loaded from this partition.

In other words, it does get involved, and I don't know of any tool available to Linux or Windows that even strives to address all the questions that have come to light in this area.

---

### Post by sharaq on 2010-02-07
This will help you .....

[http://ubuntuforums.org/showthread.php?t=1395783]("http://ubuntuforums.org/showthread.php?t=1395783")

---

### Post by oldefoxx on 2010-02-12
I finally got back to this thread, and took a look at the link above.  Now that is interesting, but you see, my method has already helped get me write access to the ntfs volumes.

Now there are admitted exceptions to this, such as a VM client may also be inhibited from dealing with efforts to create new folders or write files on some media enabled for it though the VM settings, and to deal with this, I've just written instead to a mounted media that both can access, making it necessary to perform additional steps to bypass the restrictions that are imposed.  I may come back to that link later and see if it can make a difference in cases like that.

Sometimes it's just good to know there are other ways of doing things.

---

