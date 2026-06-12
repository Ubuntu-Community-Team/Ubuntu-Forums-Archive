---
title: "copy home partition to new hard drive and new Ubuntu install"
date: 2011-02-01
forum: General Help
---

### Post by ChrisC on 2011-02-01
Hello -

I've been running Ubuntu for several years.  I'm currently (still!) running 8.04 LTS and it's time to upgrade to 10.04 LTS, along with brand new hardware (currently running 2004-vintage HW).

So, here are the three salient facts of my desired install:

1.  I already have the new PC hardware ready to go, including new hard drive.

2.  I have a separate /home partition on the old PC's drive.

3.  I would like to copy the /home partition to the new drive, where the new Ubuntu installation will go in.

I don't know if I copy in the /home partition first then install Ubuntu on top of it, or if I do a vanilla Ubuntu install and overwrite the /home partition that it creates ...

I believe that I'm supposed to use gparted to do the actual partition copy, and I can probably figure it out.  I expect to do this step with a LiveCD, so I'm not dealing with mount/unmount conflicts, right?

What's this about UUID conflicts?  If I need to assign a new UUID to the partition after copying it, how do I pick that?  When in the process do I do that -- before the copy, during the copy, after the copy?

Please help me put together a sequence to execute for this upgrade!  The next rainy weekend we've got, I'm doing it!

Thanks!

- Chris

P.S.  I did search this site quite a bit but didn't find a thread addressing this specifically.  Well, I did find one from 2006, that was quite complicated, with fstab and cpio commands and the like.  The newer threads I found typically addressed how to separate out your home partition, or enlarge it.  Thanks, I did that part years ago :)

---

### Post by colin.p on 2011-02-01
When I went from karmic to lucid, I used the entire hd and got rid of the win partition. I had religiously backed up my /home to a secondary drive the whole time I was in karmic.
Now because most of the home info is data, I just copied and pasted that into the new lucid home. Any programs, I just re-installed and then copied and pasted over any of those hidden folders, and they overwrote what was in there.
Everything worked just fine, with no permission errors.
I used grsync to do the backups.
I don't know if that was what you were looking for, but I'm lazy and look for the easiest way to do things.

---

### Post by oldfred on 2011-02-01
I believe in partitioning in advance, so I would partition and then copy the data. Then you would not have any UUID issues.  But you can copy the partition with gparted or even dd, but then you may have to change the UUID if you are still mounting your old partition.

Then with manual install you choose / & format, swap & /home but with /home choose DO NOT format.

the copy commands would be just like you did when you moved /home to a new partition.

To move /home uses rsync  (create mount may be missing)
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
Uses cp -ax
[http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html](http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html)
cp without -a and copying as sudo root takes ownership
Uses cpio
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)


Then if you have any issues with ownship:
Sometimes there are dmrc errors or permission errors and this has how to correct them:
[https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)
#Replace all instances of username with your login name.
sudo chown username:username /home/username/.dmrc
chmod 644 /home/username/.dmrc
sudo chown username:username /home/username     
chmod 755 /home/username

---

### Post by ChrisC on 2011-02-02
Thanks for the responses so far.  I would prefer the lower-level gparted partition copy method over mounting the drive in the OS and then copying files within the Linux OS, because I'm paranoid about permissions and ownership and whatnot.  So, a few specific questions:

1.  Should I copy in the /home partition first then install Ubuntu on top of it?

2.  Or should I do a vanilla Ubuntu install and overwrite the /home partition that it creates?

3.  Since I will never mount both the old /home and the /new home at the same time, do I need to bother with the UUID rename?

4.  If I need to assign a new UUID to the partition, how do I pick that number exactly?  I believe the UUID of my current/old /home partition is 4560f278-7c61-4388-9664-130409c410f1 .  Can I just increment that by 1 ( to ...410f2) or are there some rules that constrain UUID numbers?

[EDIT:  #4 I figured out:  type "uuidgen" at a command prompt.]

Thanks!

---

### Post by SeijiSensei on 2011-02-02
> **ChrisC said:**
> Thanks for the responses so far.  I would prefer the lower-level gparted partition copy method over mounting the drive in the OS and then copying files within the Linux OS, because I'm paranoid about permissions and ownership and whatnot. 

"rsync -a" will preserve all Unix file system features like ownership and permissions.

I've migrated /home a number of times by formatting the partition with mkfs, creating a mount point and mounting the partition there, then using rsync:

```

sudo mkfs -t ext4 /dev/sdb1
sudo mkdir /mnt/home
sudo mount /dev/sdb1 /mnt/home
sudo cd /home
sudo rsync -a . /mnt/home

```

You'll have an exact copy on /mnt/home when it's finished.

---

### Post by ChrisC on 2011-02-02
Thank you Sensei!  (bows deeply)

Just so I'm sure I understand, the /dev/sdb1 and /mnt/home locations are my new drive, and this copies the files over.  What if there are existing files on /home, and some of them are unique, or newer?  I don't want to merge any files.  That's why I kind of liked the gparted/partition level solution.

Further, in my particular case, I won't be able to mount the new drive in the old computer (for reasons I won't go into).  I will however by able to mount the old drive in the new computer.  Can you help me turn your example around to fit that situation?  I think I know how to do it, but this is serious business (for me at least) and I don't want to goof it up.

Any ideas on my questions #1 and #2 ?  Even if I do the copy with this mount/rsync method, those two questions still apply ...

---

### Post by SeijiSensei on 2011-02-02
> **ChrisC said:**
> What if there are existing files on /home, and some of them are unique, or newer?  I don't want to merge any files.  That's why I kind of liked the gparted/partition level solution.

Further, in my particular case, I won't be able to mount the new drive in the old computer (for reasons I won't go into).  I will however by able to mount the old drive in the new computer.  Can you help me turn your example around to fit that situation?  I think I know how to do it, but this is serious business (for me at least) and I don't want to goof it up.

Well, then you won't be needing to format the new drive as that will happen during installation.  The new drive will probably be /dev/sda and the old drive, when mounted in the new box, will be /dev/sdb.  The /home on /dev/sda will be brand new and empty except for configuration files (see below).

So with that setup you'd want to do:
```

sudo mkdir /mnt/oldhome
sudo mount /dev/sdb1 /mnt/old
sudo cd /mnt/old/home
sudo rsync -a . /home

```

(Here I'm assuming /home is in the same filesystem as / on the old drive.)

Make sure you have a backup of the original /home before you start, or at least backup copies of any critical files.  That's just common sense.  

The only concern I might have with this method concerns configuration files written to your home directories during installation.  For instance, if you were using Kubuntu and upgrading from 8.04 to 10.04, I'd be concerned because of the major version change in KDE between these two releases.  The .kde directory for KDE4 is rather different from that used by KDE3.  If you're running GNOME (the Ubuntu default), I don't think this will be an issue, but you might want to browse a couple of items on the Internet about upgrading from 8.04 to 10.04 just to make sure.

Here's one approach you can try to protect against such problems.  Install 10.04 and have it create an account with your existing username.  Now, as root, do "mv /home/me /home/me.new".  Then use rsync to copy over /home/me from the old drive.  Reboot. Does everything work as expected?  

Another possibility is to use rsync's "--exclude-from" parameter with a list of directories you don't want to touch.  I'd probably put .config, .gnome2, .gnome2_private, and .kde if you're using KDE, in that list.  Then rsync will leave these desktop configuration directories alone while copying over everything else.

Remember that, no matter what happens, you'll always still have the original /home directory on the old drive so you can't lose stuff.  The worst that can happen is you'll need to blow away the newly-created home directory and try again.

---

### Post by ChrisC on 2011-02-07
A followup ...

I elected to just do a straight partition copy as I originally planned. The rsync method proposed here probably would have worked, but I was more comfortable with the lower level partition copy.

Then with the old hard drive safely removed from the system, I booted into a live CD and mounted the NEW home partition and then CLEANED OUT the config files I didn't need.  This to me is the critical step for a long term stable OS install -- abandon old configs if you don't really need them!  The .nautilus file?  Gone!  .gstreamer?  Gone!  The entire .gconf directory?  GONE.  It's upgrading those old configs that I think trips up most new application installs.  Of course I did inspect the various files and directories and do some research on each one before blowing them away.

What I preserved was A) my data, naturally, and B) application configs for a FEW key apps.  Things like PuTTY, Filezilla, Firefox profile (was already running 3.6 anyway), Thunderbird profile.

So, with the stripped down /home partition in place, I THEN installed Ubuntu, and made sure to select manual partitioning and worked around the existing /home partition.  Then during the OS install I specified the same username and password as before and ...

VOILA!  Everything worked perfectly.  Applications that had old config were able to read them in, and the rest just installed as new.

BTW, I never did resolve the conflicting UUIDs.  Unfortunately the GPartEd live CD does not have uuidgen on it.  However this shouldn't be a problem since I don't plan to mount both the old /home and the new /home on the same computer.  If I ever do, I'll have to first do a UUID reassign on one of them.

---

