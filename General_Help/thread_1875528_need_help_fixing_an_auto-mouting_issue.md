---
title: "need help fixing an auto-mouting issue"
date: 2011-11-04
forum: General Help
---

### Post by jabema on 2011-11-04
My setup: 

Old HP pavilion, p4 3.0Ghz
1gb ram
sda: is a 60gb hd, single ntfs partition with windows xp, mbr, and grub.
sdb: is a 40gb hd;  sdb1 is a 25gb ntfs partition
                               sdb2 is a 9.31gb ext4 partition with linux Ubuntu 11.04 
                               sdb3 is a swap file partiton using the balance of the hd, 2.94gb
Before I explain my dilemma let me explain quickly how I got here.  The 60gb hd has roughly 25gb free.  I have a teenage son who plays WoW, which happens to be about 23gb total file size.  So rather than max out the sda1(c) drive, I figured I would put the WoW folder neatly next to linux in the 25gb ntfs partition on sdb1 (d) drive.  Thus making file sharing between windows and linux on this machine all happen on sda1 (c).  

Fast forward to this week.  I switched my laptop over to linux mint ldxe and set up both machines with ssh.  In my infinite laziness I decided to set sdb1 and sda1 to auto-mount upon boot to make it easier to grab files with the laptop.  I used the pysm package and if memory serves correct I selected the mount on boot option for both partitions and unchecked the read-only option.  

The computer now seems to be hanging on the splash screen and wont load Ubuntu at all.  It launches through grub just fine, I tried loading regular Ubuntu as well as recovery mode, both without any luck.  

I'm pretty new to linux, but I'm sure if I can get to a terminal I could work through the file system table and unmount those drives.  Which I am assuming is the issue I'm having, not totally sure though.

I appreciate any advice or opinions, thanks in advance

---

### Post by llamabr on 2011-11-04
I'm not totally sure, either.  But if you can get to a term, then post the output of:

```
cat /etc/fstab
```

---

### Post by jabema on 2011-11-04
That's my issue.  I'm basically locked out of Ubuntu.  I get through the grub screen and select Ubuntu as the OS then  the system just hangs at a black screen.  

I'm pretty much stuck atm, unless there's something I can do through grub or maybe through ssh?  I have no idea.

---

### Post by cbowman57 on 2011-11-04
Listen to llamabr, but here's a link to an article that Andrew put up just a few hours ago, you may find it informative [http://www.webupd8.org/2011/11/how-to-mount-partitions-automatically.html#more](http://www.webupd8.org/2011/11/how-to-mount-partitions-automatically.html#more)

---

### Post by llamabr on 2011-11-04
It's hard to say without seeing where you get stuck.  But you might try a livecd, which should pretty easily mount your hd when you boot, and then you can have a look at your /etc/fstab.

NB, I didn't follow the link in the post above.

---

### Post by jabema on 2011-11-04
Thanks Chuck, that looks like exactly what I did (or so I thought).  Everything of course except make a copy of the original fstab.

I guess right now it's really a moot point seeing as how I can't even get the OS to run.  I did try to leave it at the blank screen while trying to load and then try to access it with my laptop through ssh, but apparently it doesnt get that far in to the boot up as I got a 'could not connect to host' error.

Let me ask this:  The other half of that machine is windows xp which loads just fine.  If I install Putty in xp, could I then access the Ubuntu partition through ssh?  Or am I looking at a reinstall at this point?

---

### Post by jabema on 2011-11-04
sorry, was writing the reply as you wrote yours.  will the live cd help me out of this mess? I didn't think of that, I'll give it a try

---

### Post by llamabr on 2011-11-04
> **jabema said:**
> 

Let me ask this:  The other half of that machine is windows xp which loads just fine.  If I install Putty in xp, could I then access the Ubuntu partition through ssh?  Or am I looking at a reinstall at this point?

I don't know enough about windows, and whether it can mount your linux partition (I rather doubt it, but maybe).  

[https://www.google.com/search?q=mount+linux+partition+in+windows&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:unofficial&client=iceweasel-a](https://www.google.com/search?q=mount+linux+partition+in+windows&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:unofficial&client=iceweasel-a)

But no, you can't use putty to ssh into it.  You're not ready to start thinking about re-installing yet, though.

---

### Post by cbowman57 on 2011-11-05
> **jabema said:**
> Thanks Chuck, that looks like exactly what I did (or so I thought).  Everything of course except make a copy of the original fstab.

I guess right now it's really a moot point seeing as how I can't even get the OS to run.  I did try to leave it at the blank screen while trying to load and then try to access it with my laptop through ssh, but apparently it doesnt get that far in to the boot up as I got a 'could not connect to host' error.

**Let me ask this:  The other half of that machine is windows xp which loads just fine.  If I install Putty in xp, could I then access the Ubuntu partition through ssh?  Or am I looking at a reinstall at this point?**

I've become so unfamiliar with Windows I really can't comment, I think llamabr is probably better versed in such things. (I see he already replied)

Are you able to use the Recovery option in grub?  When you get to the black screen can you hit ctl+alt+f1 and get to a full screen terminal?  If so then all you need is sudo nano /etc/fstab & you can probably comment out your problem partitions, start with the essential / , even mounting the swap partition can be figured out later.  If you need to check things like uuid or /dev/sdx you can use another terminal ctl+alt+f2, f3, etc..

A simple **blkid** in a terminal will give you tons of info that is helpful for cleaning your fstab.

It's the weekend so hopefully you'll have some time to tinker, don't give up on it quite yet.  A lot of people get frustrated & go the re-install route too early.

Try some of these tips & let us know where you're at in a bit.

---

### Post by jabema on 2011-11-05
Thanks for the encouragement.  I managed to get the live cd to work and mounted all the partitions and pulled up the cat /etc/fstab.  The only issue is its, on the other computer so I can't link the code... not sure i really know how any ways, Is there a site you might recommend that could walk me through a step by step process of setting it right again?

---

### Post by cbowman57 on 2011-11-05
There are a lot of people much more qualified than I but for starters I'd comment out everything non-essential to linux.  Did you just install to a single / (root) partition?

I wish oldfred would pop in, he's really good at sorting these things out.

---

### Post by jabema on 2011-11-05
from fstab I have:

filesystem__________          mount point________          type______          options________________                                dump___         pass

proc________________                    /proc____________                    proc______          nodev,noexec,nosuid_______               0_____                0
UUID=....            ____________/                            ________________ext4______          users____________________                                        0_____                1
/dev/sdb5____________           none____________                     swap_____         sw_______________________                                            0_____                0
/dev/fd0              _____________/media/floppy0_____      auto______          rw,user,noauto,exec,utf8______          0_____                0
/dev/sbd1___________           /media/sbd1_______          ntfs_______           nls=iso8859-1, unmask=000___    0_____                0


running blkid from the command line shows

/dev/loop0: Type="squashfs"
/dev/sda1: UUID="..." TYPE="ntfs"
/dev/sdb1: UUID="..." TYPE="ntfs
/dev/sdb5: UUID="..." TYPE="swap"
/dev/sdb6: UUID="..." TYPS="ext4"

---

### Post by cbowman57 on 2011-11-05
Ok, let's try this for starters.

Comment out /dev/fd0 & sdb1.

Verify that the fstab matches the results of your blkid for the ext4 & swap partitions.  To simplify things you can even comment out swap while you're trying to sort this out.

---

### Post by jabema on 2011-11-05
I commented out /dev/fdo and /dev/sdb1 with no luck, I'll try commenting out the swap file next.  

BTW i did forget to say there is a comment in fstab:

# / was on /dev/sbd6 during installation

mean anything to you?

And also the UUIDs match up from blkid to fstab as well as the types

sdb6 is my     /     ext4    prartition
in fstab it doesn't list it as sdb6, it shows the above comment followed buy the UUID, then shows the mount point as    /    and type as ext4, options as users, and dump pass as 0,1

---

### Post by cbowman57 on 2011-11-05
> **jabema said:**
> I commented out /dev/fdo and /dev/sdb1 with no luck, I'll try commenting out the swap file next.  

BTW i did forget to say there is a comment in fstab:

# / was on /dev/sbd6 during installation

mean anything to you?

And also the UUIDs match up from blkid to fstab as well as the types

sdb6 is my     /     ext4    prartition
in fstab it doesn't list it as sdb6, it shows the above comment followed buy the UUID, then shows the mount point as    /    and type as ext4, options as users, and dump pass as 0,1

Ok, sounds like you've done everything you can with the fstab.

On your grub kernel line, probably looks something like this: ```
linux /boot/vmlinuz-3.0.0-12-generic root=UUID=11a2b514-dc28-4d48-a533-ae3821a6507b ro quiet splash
```When your grub starts loading hit 'e' to edit and comment out everything after the ro, probably quiet splash, but it may also say quiet splash vt.handoff=7, or something like that.  Make sure you just arrow down and delete those kernel modifiers.  What I'm hoping to accomplish is giving you  verbose screen for the boot process that may give you some clues.

While you're doing that you may also want to download a copy of supergrub2 &/or Rescatux, you may need those later if we've hit a wall here.

---

### Post by jabema on 2011-11-05
Okay, your beginning to push the limits of my knowledge with command line usage=)

Do you just want me to drop a "#" in between ro and quiet splash vt.......  or do you want me to delete everything after ro?

---

### Post by jabema on 2011-11-05
Real quick before it gets too ungodly late, let me ask this:

I know its the weekend and all, but for the sake of time, I mean my linux partition is 10gb total, ext4 + swap, I have literally no files that I don't pull from other partitions, would a reinstall be quicker? I know I'd have to spiffy-up my desktop again and reinstall the handful of programs I use.

I just don't want to spend all weekend grasping at straws, although I don't mind it so much as I am actually learning a few things along the way.  I'd hate to still be trying to chase this down Sunday night, when I could probably finish up a reinstall while watching college football tomorrow morning=)

Just wondering your opinion

---

### Post by cbowman57 on 2011-11-05
Ok, sorry about that. :)

No, just arrow down to the line, hit the END key and backspace until those words are erased, the changes that you perform here are not permanent, when you reboot you will find it just as you find it now.

After you delete those then hit f10 or ctl+x and it will start to boot.  

Hopefully the culprit will be obvious & will give us a couple more clues.

One other thing we may have to look at is if the / partition is full, linux won't boot if it runs out of disk space, but we can cure that if it turns out to be the problem. :)

---

### Post by cbowman57 on 2011-11-05
Yeah, no problem.  As long as trying to solve the puzzle is something you're up for we'll keep plugging away, the worse that can happen is that you will end up reinstalling while the game is on tomorrow.

---

### Post by jabema on 2011-11-05
well I started this thread on my "first cup" so at the very least I'm getting coffee credit =)

ok, started the boot and saw the usual  [    1.089965] 0800......... scrolling text

stopped at: [      1.091272] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

it ran a few more lines and stopped completely

---

### Post by cbowman57 on 2011-11-05
Ok, sounds like there may either be some file system corruption of the partition is full.

Boot it back up with the liveCD, once you've done that open GParted and check that root partition.  Gparted has a check function, also check to see how full the partition is.

---

### Post by jabema on 2011-11-05
ran GParted, / partition shows size of 9.31gb with 4.36 free and 4.95 used

i then ran the check application, went pretty quick and didn't seem to have any issues, I saved the details

---

### Post by cbowman57 on 2011-11-05
I don't imagine it booted up after that?

Ok, I'm running out of ideas but here's another one for you.  Download Rescatux [http://www.supergrubdisk.org/category/download/rescatuxdownloads/](http://www.supergrubdisk.org/category/download/rescatuxdownloads/) burn it to CD and reinstall grub, it's really simple but if you use CD it's a little slow on the uptake so give it a little time between button presses so it can do its thing.

If that doesn't clear up I suggest we take a rest & hopefully someone with some fresh ideas finds this thread.

---

### Post by jabema on 2011-11-05
Sounds good to me, I'll check back tomorrow.  Hopefully even if I end up with a reinstall I can figure out what I did wrong, so it doesn't happen again.  By the looks of all the mounting links I have been scouting out I did every thing with pydsm the right way.

I really appreciate your effort, I'll let you know tomorrow how the grub install went

---

### Post by cbowman57 on 2011-11-05
Yeah, I really want to know if we accomplished anything or not.

If you have a few gigs of drive space to spare for backup you may want to take a look at Clonezilla.  It allows you to backup or restore a partition in just a few minutes.

Catch you later on.  Would be nice to start the day with a success story. :)

---

### Post by jabema on 2011-11-05
eh... my last two CDs turned into coasters.  Guess that's what I get for buying the bulk cheapo 50 pack, had about 8 bad disks in the bunch.

After a little more thought, I believe I'm going to set my system up a little different this time and try to give the linux  /  partition a little more breathing room.  

I am going to do a little bit of digging and research the best way of setting up partitions for linux before I jump into a fresh install.  

I appreciate your efforts, and I did learn a few things through it all.  

I'll keep an eye on this thread until I start the re-install to see if anyone else comes up with any thing new.

Thanks again

---

### Post by cbowman57 on 2011-11-05
No problem, here's my fstab.  I install to only / and bind all my large folders from designated partitions so the OS itself only occupies about 4-6Gb.

```
# 
# /etc/fstab: static file system information
#
# <file system>    <dir>    <type>    <options>    <dump>    <pass>
tmpfs        /tmp    tmpfs    nodev,nosuid    0    0
UUID=1eaaec42-6f9c-4909-8b4a-0c5da3659ec8 / ext4 relatime 0 1
UUID=47e6b514-2d7e-4c2e-b1b9-da49f63e08b5 swap swap defaults 0 0
UUID=cdc71aee-75bc-4199-86a3-07eb10e875d0 swap swap defaults 0 0
###################################################
### Mount & Bind  #################################
###################################################
UUID=b2724164-3dcb-4f0a-a3b2-9ffdae1421a3  /mnt/bind/Downloads ext4    relatime 0       0
UUID=2f407e00-4b94-44c1-8c22-f3492f410767  /mnt/bind/Maintenance ext4    relatime 0       0
UUID=13b3f8d5-ca84-4e51-8316-a1c0aa930c46  /mnt/bind/Music ext4    relatime 0       0
UUID=7c01f5fd-e741-4505-ac4b-62260a4c6943 /mnt/bind/Pictures ext4 relatime 0 0
UUID=7db8537c-2a6d-464b-be16-df0e556ed6e2 /mnt/bind/Backups  ext4 relatime 0 0
/mnt/bind/Pictures /home/chuck/Pictures bind defaults,bind 0 0
/mnt/bind/Downloads /home/chuck/Downloads bind defaults,bind 0 0
/mnt/bind/Maintenance /home/chuck/Maintenance bind defaults,bind 0 0
/mnt/bind/Music /home/chuck/Music bind defaults,bind 0 0
/mnt/bind/Backups /home/chuck/Backups bind defaults,bind 0 0
/home/chuck/Downloads/Wallpaper /home/chuck/Wallpaper bind defaults,bind 0 0
```

Might be food for thought as to how you want to set up the fresh install.

Too bad we couldn't solve the problem, at least we tried. :)

---

### Post by jabema on 2011-11-05
So what would you recommend for my set up? The most ideal partition layout I mean?

This is what I'm working with again:
40gb Western Digital HD
60gb Samsung HD

I have Windows XP installed on the 60gb drive right now using approx 19gb of space with all my programs (minus my kids WoW game).  Right now the entire drive is dedicated to windows and formatted NTFS.

Linux is installed on 40gb drive in a 9.31gb ext4 partition with a 3gb swap partition, leaving the remaining 25gb of the drive as a 25gb NTFS partition for file sharing.  

I have a 1tb Segate external that I store all of my files on.  Typically I only use the hard drives to house programs/apps and any space i set up for file sharing is really only a temp holding place for things I'm working on.  I do a lot of graphic design work with images and 3d modelling, and some times those files get a little big so its faster and easier to have them on the physical drive instead of the external while I'm working on them.  

My revised thoughts are to shrink the windows partition down to 30gb on the 60gb hard drive and give linux the balance of the drive for  swap and root partitions.  Since the drive actually shows as 55gb, I'm figuring on 22gb root partition with a 3gb swap.

That will leave me around 10gb to play with in the windows partition if I need and double the size of my current linux partition.

That would also free up the entire 40gb drive so I could format the entire drive as NTFS and throw my kids windows games on it and have a 10gb or so spot for file sharing if needed.

I am curious about your mount bind method though, what sort of benefits does it offer over typical installs? 

I do have one other concern as well.  What to do with my music files.  In my last install I tried to set my music file in the NTFS partition so I could have access to it from both windows and linux, but I had issues being able to access if form my laptop through ssh which lead me to the auto mounting of the drives which lead me to this point.  I know that's another thread for another time, but if there was a way to address it during the reconfiguring of partitions, that would be a bonus.

---

### Post by cbowman57 on 2011-11-05
Well I'm no whiz at it, I arrived at my setup after a lot of suffering. :)

I also don't mix & match with ntfs so that throws a wrinkle in it possibly.

Your plan sounds good from what I can tell.

The advantages to doing it the way I do it.  I've usually got a bunch of different linux installations installed & got tired of moving & copying files every time I wanted to remove one, or add another.  Music, Downloads, Pictures, etc.. take up a lot of room and Ubuntu can easily run on a 10Gb partition if you offload those files to other partitions. When you mount & bind those partitions to your home folder they become that folder, but if the system crashes or you reinstall you don't lose anything or have to relocate them.  You can also do it with links but I feel it's more reliable with /mnt/bind

So, not encouraging you to do it that way, just wanted to throw out some alternate ideas that you might not otherwise come across.

Think about how you use it, factor in the ntfs, and come up with a simple solution that makes sense to you. :)

---

### Post by jabema on 2011-11-05
Sounds good, Thanks again for all the help.  

I guess with that, I'll sign off on this thread.  I'm sure I'll pop up again somewhere in the forums this weekend trying to get that music sharing issue worked out.

Have a good one.

-Jabema

---

### Post by cbowman57 on 2011-11-05
You have a good one too. :)

---

