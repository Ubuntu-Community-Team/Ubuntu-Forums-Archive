---
title: "Karmic and fstab. Anybody having issues?"
date: 2009-10-30
forum: General Help
---

### Post by Roasted on 2009-10-30
I mount several backup drives by fstab with UUID. This process has worked great since I started on Ubuntu.

Installed 9.10 last night, and uh - no go. I just get errors when I try to access the "mounted" shares.

Anybody else having issues? Come to think of it Karmic also failed to acknowledge I had more than 1 other drive in my system when I installed it. It only saw my main backup, not the secondary drive... at all...

---

### Post by prem1er on 2009-10-30
Yes, I am. On bootup I get errors about not being able to mount several of my partitions. I haven't had much time to look into it, but I know this didn't happen about 2 weeks ago with the beta.

---

### Post by Roasted on 2009-10-30
I'm sorry to hear about your luck, but I am happy that I'm not alone.

I'll patiently and quietly wait until Ubuntu developers come up with a patch. :) 

I assume they are aware of the issue?

---

### Post by slakkie on 2009-10-30
The messages on boot is something you can ignore as your partitions are mounted. See bug: [https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/215666](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/215666)

What fstab errors do you have, could you post them? I've had no problems with my fstab, except for the bug as reported above.

---

### Post by Roasted on 2009-10-30
Well, I added my drives to fstab based on UUID, just like I did in 9.04, 8.10, 8.04, etc without any issues. I reboot and log in. No errors.

But, say I want to access one of the drives I mounted by UUID. I select places, then the drive, and it barfs out an error, something about only root can mount this device. I can't post the exact error because I'm at work now...

It's a definite fstab error with Karmic, I'm afraid. My setup has worked perfectly in 9.04 and previous, and in the Ubuntu IRC chat several people there claimed to have the same issues.

---

### Post by beachdaze on 2009-10-30
Similar problem here.  I don't use UUID, but this line in fstab has worked fine since 8.04, but now only gives access to root.

```
//192.xxx.xxx.xxx/Music /home/<user>/Music cifs auto 0 0
```

I've tried with user and users, adding a rw and the usual things.  This is a shared folder on an XP box, with NO password required.  Very strange.

---

### Post by entropy1 on 2009-10-30
I have been dual booting 9.04 and Windows Vista.  Yesterday I added 9.10 in a new partition that I created in some free space.

In my 9.04 fstab I have the line

/dev/sda3 /media/C ntfs-3g quiet,defaults,rw,uid=myname,gid=myname,fmask=177,dmask=077 0 0

so that when I boot 9.04, the Windows partition is automatically accessible.

I put the same line in my 9.10 fstab, but now the Windows partition does not show up in nautilus; it's like it does not exist.  The partition still shows up in gparted.

When I removed the line from the 9.10 fstab and reboot 9.10, the partition shows up in nautilus and I can click on it and it mounts.

I would prefer to do things automatically as I did in 9.04.  Does anyone know how?

---

### Post by Roasted on 2009-10-31
[http://blogs.zdnet.com/open-source/?p=5145](http://blogs.zdnet.com/open-source/?p=5145)

Boom....

```
Reviews on the release candidate of the desktop version are negative, 
due to the fact you can&#8217;t run multiple drives with the current code base. 
This means a netbook user may be happy but a desktop user (my desktop has 
three hard drives) will not be satisfied at all.
```

I definitely didn't get the release candidate, unless that's what was linked on the Ubuntu.com web site under "9.10 is here!" when it was released.

It's all good, though. I'm sure the bugs will be fixed soon. Just wanted to throw this review out there so users knew that there IS something definitely confirmed.

---

### Post by Roasted on 2009-10-31
I booted to the Jaunty 9.04 64 bit LiveCD and the Karmic 9.10 64 bit LiveCD. In each instance, I went to the partitioning screen and selected "manual partition" mode. These are direct screenshots from each instance.

Jaunty:
[http://img691.imageshack.us/img691/7972/jauntyscreenshot.png](http://img691.imageshack.us/img691/7972/jauntyscreenshot.png)


Karmic:
[http://img256.imageshack.us/img256/4171/karmicscreenshot.png](http://img256.imageshack.us/img256/4171/karmicscreenshot.png)



Jaunty = correct.

Karmic = wtf is happening there? What is dev mapper? Why aren't BOTH of my 250gb drives (sdc and sdd) showing up?

---

### Post by hadrurus on 2009-11-01
Hi

actually i have (had) 2 issued with fstab in 9.10 lately:

1. installed 9.10 along 9.04 and win xp on my laptop, and during boot process (bootspalsh) it was showing info about partitions being unable to mount, thou later on everything was ok. also, when i've changed UUIDs to /dev/sdXX notation i had no more errors.
So, i've decided to repartition a bit mentioned hdd and remove older ubuntu, and after new installation - im not getting any more errors (even thou still using UUIDs
... weird

2. this is a bit strange:
when i mount one of my partitions without any changes to fstab it works. when i change fstab entry to:
```
UUID=a966f889-a70e-4d35-b58d-4e3312702803 /mnt/docs       ext4    defaults,user,exec,fmask=111,dmask=000        0       2
```
(adding user,exec,fmask=111,dmask=000 options) it's no longer mounted and syslog says:
```
Nov  1 09:18:00 Deimos kernel: [   39.038689] EXT4-fs (sda5): barriers enabled
Nov  1 09:18:00 Deimos kernel: [   39.055452] kjournald2 starting: pid 778, dev sda5:8, commit interval 5 seconds
Nov  1 09:18:00 Deimos kernel: [   39.055691] EXT4-fs (sda5): internal journal on sda5:8
Nov  1 09:18:00 Deimos kernel: [   39.055696] EXT4-fs (sda5): delayed allocation enabled
Nov  1 09:18:00 Deimos kernel: [   39.061622] EXT4-fs (sda5): mounted filesystem with ordered data mode
Nov  1 09:13:50 Deimos kernel: [   19.247383]  sda1 sda2 sda3 sda4 < sda5 sda6 >
Nov  1 09:13:50 Deimos kernel: [   27.331876] EXT4-fs (sda5): Unrecognized mount option "fmask=111" or missing value
Nov  1 09:13:50 Deimos kernel: [   27.608208] EXT4-fs (sda5): Unrecognized mount option "fmask=111" or missing value
Nov  1 09:13:50 Deimos kernel: [   30.030409] EXT4-fs (sda5): Unrecognized mount option "fmask=111" or missing value
Nov  1 09:14:07 Deimos kernel: [   46.805934] EXT4-fs (sda5): Unrecognized mount option "fmask=111" or missing value
Nov  1 09:14:25 Deimos kernel: [   64.661794] EXT4-fs (sda5): Unrecognized mount option "fmask=111" or missing value
```
removing fmask and dmask causes the partiotion to mount witout any problems


regs

---

### Post by b0b138 on 2009-11-01
> **Roasted said:**
> Karmic = wtf is happening there? What is dev mapper? Why aren't BOTH of my 250gb drives (sdc and sdd) showing up?

Were your drives setup for raid?

---

### Post by Roasted on 2009-11-01
> **b0b138 said:**
> Were your drives setup for raid?

Nope. They were simply mounted by UUID, and then I had samba shares on the first 250gb drive, and I would rsync data on that 250gb drive to my other 250gb.

One = Samba network drive.
Second = Backup of Samba drive.

No RAID. All rsync within Ubuntu.

To my knowledge, my motherboard doesn't even support RAID.

---

### Post by beattyrp on 2009-11-06
I'm not a UBUNTU wizard. Can anyone put this in simple terms? After upgrading from 9.04 my computer won't even finish booting. It hits the fstab problem and just waits and waits and waits...

I tried reinstalling from a CD onto a second, empty hard drive, but that has the same fstab issues and won't boot either. Booting from the CD seems to work fine.

Dead in the water

---

### Post by Roasted on 2009-11-06
> **beattyrp said:**
> I'm not a UBUNTU wizard. Can anyone put this in simple terms? After upgrading from 9.04 my computer won't even finish booting. It hits the fstab problem and just waits and waits and waits...

I tried reinstalling from a CD onto a second, empty hard drive, but that has the same fstab issues and won't boot either. Booting from the CD seems to work fine.

Dead in the water

Surely. :) 

fstab is file system table. It's where the "media devices" in your system are told to mount. Media devices include CD Rom drives, hard drives, etc. In our case, the problem lies within hard drives being mounted properly.

You see, in Windows, you plop the drive in and it just kinda comes up as Local Disk - D, E, whatever. In Ubuntu, you have more control as you can actually set a directory for the drive to mount to. Meaning, I made a folder in /media called "localbackup." Okay, fine. So I edit fstab (which again, tells the drives upon booting to mount automatically) and it'll tell my hard drive to mount to /media/localbackup.

That way when I navigate to /media/localbackup, that folder is a completely different hard drive than my main drive. As a result, I have the ability to set up rsync (backup) scripts to synchronize all of my data from any other location on my computer TO /media/localbackup. So, naturally, I chose /home/jason to /media/localbackup. That way all of my stuff is backed up.

There lies a problem somewhere with Karmic in regard to fstab working properly, along with Karmic thinking certain drives are RAID when they are not. Even after I manually edit fstab, it still errors out to successfully mount the devices - something Hardy/Intrepid/Jaunty have all done fine with me.

If you need a stable, working Ubuntu system, I highly recommend staying with Jaunty. Karmic offers some nice new features, but nothing too earth shattering that should be a true setback if you didn't have them. I had trouble installing Karmic on my system which has 4 SATA drives, but Karmic runs GREAT virtually on my Jaunty box. However, Karmic also has 1 "virtual" hard drive to recognize in Virtualbox, whereas it had 4 to see on my main system.

Just keep in mind, Karmic is brand new. It's a week old. Problems always arise with new releases, which is the reason why majority of the Ubuntu users here on the forum recommend waiting 3-5 weeks before trying out a new release.

---

### Post by beattyrp on 2009-11-07
I wish the developers had thought about that before dangling it out there right up top as an upgrade. I'm still dead in the water, having trouble getting back to a working 9.04

geez


[QUOTE=Roasted;8258388]Surely. :) 

...

If you need a stable, working Ubuntu system, I highly recommend staying with Jaunty.
...

---

### Post by Roasted on 2009-11-07
I've heard from numerous resources that the beta was completely fine and stable, so everybody saw no reason to push it (as scheduled) for final release. Then once the final release came out, the issues came up and everybody was like omg??

Jaunty was exceptionally solid, and it's a mature version of the distro since it's been out for six months. You can't go wrong with it, and since the next Ubuntu is an LTS, the scheme of things really isn't that bad.

If Karmic gets fixed so you can work with it, great. I'm sure it will be solid. Otherwise, it's not such a bad deal to stick with Jaunty till 10.04 comes out. Granted, that doesn't help people who are stuck at the moment with problems in Karmic, but it's the best I can offer as a community member (not a developer).

---

### Post by navinmistry on 2009-11-08
> **entropy1 said:**
> I have been dual booting 9.04 and Windows Vista.  Yesterday I added 9.10 in a new partition that I created in some free space.

In my 9.04 fstab I have the line

/dev/sda3 /media/C ntfs-3g quiet,defaults,rw,uid=myname,gid=myname,fmask=177,dmask=077 0 0

so that when I boot 9.04, the Windows partition is automatically accessible.

I put the same line in my 9.10 fstab, but now the Windows partition does not show up in nautilus; it's like it does not exist.  The partition still shows up in gparted.

When I removed the line from the 9.10 fstab and reboot 9.10, the partition shows up in nautilus and I can click on it and it mounts.

I would prefer to do things automatically as I did in 9.04.  Does anyone know how?
I have my ntfs drive working absoluetly fine in karmic.

here is my fstab entry of that for ref.

/dev/sda6       /media/ENTERTAINMENT    ntfs-3g rw,nosuid,nodev,allow_other,default_permissions         0       0

---

### Post by balee86 on 2009-11-08
Hello!

I don't exactly know if my problem belongs here, but:
After upgrade from jaunty in the 'Places' menu all my ntfs drives appear two times.

Each has a working link, and one which gives this error (Unprivileged user can not mount NTFS block devices using the external FUSE)

How can I find out where the wrong links come from? Whether the problem is in my fstab or not.

Thanks.

---

### Post by ofb on 2009-11-08
> **Roasted said:**
> There lies a problem somewhere with Karmic in regard to fstab working properly, along with Karmic thinking certain drives are RAID when they are not. Even after I manually edit fstab, it still errors out to successfully mount the devices - something Hardy/Intrepid/Jaunty have all done fine with me.

It's not fstab. As you've seen yourself using GParted on the LiveCDs, Karmic cannot recognize some partitons. This is very strange.

My thread of woe is here, [http://ubuntuforums.org/showthread.php?t=1319023](http://ubuntuforums.org/showthread.php?t=1319023)

Similar deal - even the LiveCD for Karmic cannot recognize one partition, even though it sees the others on the same drive. Jaunty and Knoppix see all the partitions just fine.

There's a raft of UUID complaints with Karmic. Seems like a core error cropping up in different ways. Some people can fudge the fstab. Some people only get the error message *"One or more of the mounts listed in /etc/fstab cannot yet be mounted"* with no problems. And then there's us, who don't get a partition recognized at all.

It's just so capricious. I haven't found anyone getting to the core of it yet. It's flatly bizarre that Karmic doesn't recognize one partition, and moreso that something so basic is only showing up for a handful of people in the final release.

---

### Post by Roasted on 2009-11-08
> **ofb said:**
> It's not fstab. As you've seen yourself using GParted on the LiveCDs, Karmic cannot recognize some partitons. This is very strange.

My thread of woe is here, [http://ubuntuforums.org/showthread.php?t=1319023](http://ubuntuforums.org/showthread.php?t=1319023)

Similar deal - even the LiveCD for Karmic cannot recognize one partition, even though it sees the others on the same drive. Jaunty and Knoppix see all the partitions just fine.

There's a raft of UUID complaints with Karmic. Seems like a core error cropping up in different ways. Some people can fudge the fstab. Some people only get the error message *"One or more of the mounts listed in /etc/fstab cannot yet be mounted"* with no problems. And then there's us, who don't get a partition recognized at all.

It's just so capricious. I haven't found anyone getting to the core of it yet. It's flatly bizarre that Karmic doesn't recognize one partition, and moreso that something so basic is only showing up for a handful of people in the final release.

How can you say it's GParted? Karmic clearly has an issue with fstab - even after I install it. I installed Karmic on ONE hard drive with the other 3 disconnected, then manually edited my fstab afterwards to accommodate those drives - all failed with the same errors. GParted is not part of the situation then.

I guess we either have one problem, or several problems. Either way... damnit! :mad::lolflag:

Could it be the Linux kernel? I forget what kernel the latest GParted it running (0.4.8-1) but I JUST downloaded it from the web site and burned it. GParted can sense all 4 drives, but it comes up with /dev/mapper, which is what Karmic did (where I had the issues).

Could it be the Linux kernel?

---

### Post by ofb on 2009-11-08
Oh, I'm not saying it's GParted. I think it and fstab are just reflecting something deeper.

I'm only calling it a 'problem with UUIDs' because that seems to be the one common factor. Something in Karmic seems confused with UUIDs. Did you try the 'ls /dev/disk/by-uuid/' mentioned in my thread?

I also just had a look with lshw in 9.10 Live, an lo, there's sda1 with the proper UUID. I mean like what the heck, eh? Where's the consistency?

And yeah, I'd *guess* this would be kernel territory. I guess you could check that by seeing if the equivalent Debian lists have similar complaints.

---

### Post by Roasted on 2009-11-08
> **ofb said:**
> Oh, I'm not saying it's GParted. I think it and fstab are just reflecting something deeper.

I'm only calling it a 'problem with UUIDs' because that seems to be the one common factor. Something in Karmic seems confused with UUIDs. Did you try the 'ls /dev/disk/by-uuid/' mentioned in my thread?

I also just had a look with lshw in 9.10 Live, an lo, there's sda1 with the proper UUID. I mean like what the heck, eh? Where's the consistency?

And yeah, I'd *guess* this would be kernel territory. I guess you could check that by seeing if the equivalent Debian lists have similar complaints.

Yeah, and GParted being Debian based is a pretty solid indication it may spill into the Debian side of things as well.

---

### Post by jpeterse on 2009-11-09
I have the same problem, with boot stopped with message about not being able to mount drives. I've tried the tricks mentioned in various posts, replacing UUID's with /dev/sd* references, and removing fsck checks in the fstab. But nothing helped.

Then I noticed, that the root filesystem is mounted read-only, and that I can get the system to boot past the error messages with this workaround:

1.
at the mount error message, press Esc, then type in root passwd at prompt to enter recovery console
2.
remount / filesystem with "mount -n -o remount,rw /"
3.
type "exit", now the system reboots, still showing mount errors, but this time booting past the errors.

---

### Post by ELF_O8 on 2009-12-31
I realize this is an old thread, but seeing as no one really posted any answers, I thought I'd lend some insight.
All you need to add to fstab in 9.10 (that you didn't have to in previous versions) is the "user" flag to the options of each device you want auto-mounted.
For example:
```
# Entry for Storage Volume
/dev/sda4 /media/disk ext4 defaults 0 2
```
won't mount in Karmic, but
```
# Entry for Storage Volume
/dev/sda4 /media/disk ext4 defaults,user 0 2
```
will. You may also have to ```
 sudo mkdir /mount/point 
``` if it says it doesn't exist yet.
This has worked for me, but I can't say it works for everyone.

---

### Post by Roasted on 2009-12-31
I wonder what's happening here that prompted Karmic to fall short in this department while every other version of *buntu out there can handle this fine?

---

### Post by ELF_O8 on 2010-01-01
Perhaps it has something to do with the new kernel?
I encountered a lot of problems with my laptop (touchpad drivers mysteriously vanished, wireless drivers didn't function properly, etc) when I upgraded from 9.04.

---

### Post by kyle2595 on 2010-01-01
I was getting an error message on startup about fstab, this may help: [URL="http://ubuntuforums.org/showthread.php?t=1365936"]http://ubuntuforums.org/showthread.php?t=1365936
[/URL]

---

