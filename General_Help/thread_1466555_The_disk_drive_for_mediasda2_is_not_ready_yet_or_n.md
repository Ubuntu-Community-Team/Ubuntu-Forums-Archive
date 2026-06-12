---
title: "The disk drive for /media/sda2 is not ready yet or not present"
date: 2010-04-30
forum: General Help
---

### Post by danootz on 2010-04-30
I am trying to dual boot Win7 and Lucid Lynx. I had a near perfect setup of Win7 and Karmic Koala before. I went into Win7, deleted the previous Ubuntu installation and popped the installation disk in and restarted. I did a clean installation, installing Lucid using the "install in largest continuous free space"

Installation went just fine, I installed ATI drivers and used one of those install scripts to get Medibuntu and all the other good stuff installed in one fell swoop. I went into the file system directory and noticed that in addition to listing Ubuntu's partition, Win7 partition and a third partition I created to share media files between 7 and Ubuntu, there are three things listed as SDA1, SDA2, SDA3. None of which I have any access to and get an error when trying to double click. I can get access to the three partitions I listed above (Ubuntu, Win7, media partition)

Once I rebooted my computer though and get passed GRUB by selecting to boot Ubuntu I get this message on the loading splash screen:

[I][B]The disk drive for /media/sda2 is not ready yet or not present.

Continue to wait, press S to skip or M for manual recovery.[/B][/I]

All it does is hang and I have to skip it. What can I do to fix this?

---

### Post by asuastrophysics on 2010-05-03
> **danootz said:**
> I am trying to dual boot Win7 and Lucid Lynx. I had a near perfect setup of Win7 and Karmic Koala before. I went into Win7, deleted the previous Ubuntu installation and popped the installation disk in and restarted. I did a clean installation, installing Lucid using the "install in largest continuous free space"

Installation went just fine, I installed ATI drivers and used one of those install scripts to get Medibuntu and all the other good stuff installed in one fell swoop. I went into the file system directory and noticed that in addition to listing Ubuntu's partition, Win7 partition and a third partition I created to share media files between 7 and Ubuntu, there are three things listed as SDA1, SDA2, SDA3. None of which I have any access to and get an error when trying to double click. I can get access to the three partitions I listed above (Ubuntu, Win7, media partition)

Once I rebooted my computer though and get passed GRUB by selecting to boot Ubuntu I get this message on the loading splash screen:

[I][B]The disk drive for /media/sda2 is not ready yet or not present.

Continue to wait, press S to skip or M for manual recovery.[/B][/I]

All it does is hang and I have to skip it. What can I do to fix this?

I am having the EXACT same problem. My machine is bricked until either more people get this bug and complain or I figure it out :(

Only mine says "The disk drive for / is not ready yet"

---

### Post by mariano.j on 2010-05-04
Same problem here (and [here]("http://ubuntuforums.org/showpost.php?p=9227953&postcount=433") and [here]("http://ubuntuforums.org/showpost.php?p=9228449&postcount=441")  and probably elsewhere...)


Dual install of Windows XP and Lucid Lynx, bootup process stops with the  message:
> 
The disk drive for /exchange is not ready yet or not present.
Continue to wait; or Press S to skip mounting or M for manual recovery
Skipping is the only solution to me. The FAT partition "exchange" can be  accessed after bootup under both Windows and Ubuntu.

Has anyone of you filed [a bug report]("https://launchpad.net/ubuntu/+bugs")?

---

### Post by Nobre on 2010-05-06
Same problem.
Not fixed yet

---

### Post by asuastrophysics on 2010-05-06
I spent a good 20 solid hours trying to find a solution to this online. There just isn't one. Even though some of the people on this very forum are the very same ones who are the programmers behind ubuntu, nobody seems to have a clue how the operating system really works, and thus, how to fix it when it really breaks.

I had to back up all of my stuff off my computer onto a portable hard drive, insert the livecd and completely reformat the hard drive and reinstall. 

Even this hasn't fixed the problem. Grub2, being the royal piece of useless crap that it is, complains that it can't find the old partition. Apparently when you reinstall, the livecd "forgets" to update the grub for you. It makes me wonder what else it's forgotten to do. I thought that when you installed an operating system, part of the installation script contains instructions for making sure the OS can actually boot. Nope, that's a task for the end-user to enjoy. 

Also, when I copied all my files over to the portable hard drive, none of them can be accessed in windows even though the portable hdd is NTFS formatted. You can only view them through ubuntu. So I can't even ditch ubuntu if I wanted to, because the OS is holding 3 years worth of files hostage. 

Touche, ubuntu, touche. My computer goes through more down time and data loss due to updates breaking it than a windows PC would ever go through.

---

### Post by MMSpeer on 2010-05-08
I have the same experience. After upgrading my dual boot laptop (XP and Ubuntu 9.10) to Lucid Lynx I got the same message that the disk drive wasn't ready yet. 

In my case the message referred to the absence of an external USB HD (happens when you do not switch it on). After switching it on, the reboot went perfectly fine. So the Lucid Lynx's message actually was correct, indeed the device wasn't ready yet.

As I read your posts, it appears that you all have problems with internal devices (partitions) instead of external ones. However I do note that most of the messages refer to none-Lucid Lynx related devices like /media or /srv or /mnt. In other words, mounts to devices created or used by other OS's like Mickysoft too. Or, like in my case, to an external HD (ntfs-formatted).

So my guess is that your problems have to do with the unability of Lucid Lynx to automatically mount the desired devices properly. Have you all tried to manually mount the requested devices using the mount command (of course using the right type and option settings that apply to your device)? Remember that you have to create a mount point somewhere to actually being able to mount the device. In this way (by trial and error probably) you may find the right type and option setting so that the right device can actually be mounted in the way it needs to be. And if you have found a working solution via this manual procedure, you should modify your /etc/fstab file accordingly in order to have Lucid Lynx automatically mount the right devices in the right manner to the right mount-point during the boot process.

Hope my information leads you to the solution. Please let me know about the results.

MSpeer

P.S. When modifying your /etc/fstab consider using UUID instead of /dev/sda..(or something like that) in order to identify the device you want to mount. And of course, be aware that making mistakes when modififying your fstab may also result in incorrectly starting your system. So make a backup of the original file before you modify it.

---

### Post by hernanp on 2010-05-08
> **MMSpeer said:**
> So my guess is that your problems have to do with the unability of Lucid Lynx to automatically mount the desired devices properly. Have you all tried to manually mount the requested devices using the mount command (of course using the right type and option settings that apply to your device)? Remember that you have to create a mount point somewhere to actually being able to mount the device. In this way (by trial and error probably) you may find the right type and option setting so that the right device can actually be mounted in the way it needs to be. And if you have found a working solution via this manual procedure, you should modify your /etc/fstab file accordingly in order to have Lucid Lynx automatically mount the right devices in the right manner to the right mount-point during the boot process.


That's correct ! In my case the uuid of one drive in fstab is wrong, it seems that older versions of ubuntu ignore the problem.
Just comment out the line (because I don't need that mount) and Lucid boot without messages
Command "blkid" list UUIDs

---

### Post by havenoname on 2010-05-11
I had a similar problem and it is solved, try the following:

[http://www.nyutech.com/2009/03/make-ubuntu-mount-partitions-and-drives.html](http://www.nyutech.com/2009/03/make-ubuntu-mount-partitions-and-drives.html)

---

### Post by Blond on 2010-05-11
Hello, I had the same problem after upgrading from kubuntu 9.10 to 10.04 on a dual boot system with WindowsXP 64 bit.

But now I solved it thanks to "havenoname". I followed the link he published and this triggered me.

In my case /media/sda2 is an extended pertition in which my Windows partition sits.

So there is no need to mount this extended partition and therefore I removed it from /etc/fstab.

In the proces I also added my WindowsXP drive with the GUID as found with the command 'sudo blkid'.

Succes, it worked for me :-)

---

### Post by MMSpeer on 2010-05-15
Good to see your problems seem to be solved. 

I would like to add though that you should be careful with automatically mounting disks using /dev/sda1, /dev/sda2, /dev/sdb1 etc. Especially when you use more than one external hard drives, but even in case of two or more internal drives it may lead to confusion/problems. The order in which linux mounts may change depending on what drives are physically attached to (external) or in (internal) the system. In my case I generally use two external USB HD's ('DATA' and 'BACKUP') on one Linux-server, but sometimes I use one of them ('DATA') on another computer. When I re-attach my 'DATA' HD to my Linux-server and then restart it, it has happened more than once that the one disk is on the other /dev/sd'x'. This of course results in the wrong mount. That is very confusing, because I would expect 'DATA' on mount /srv/DATA and 'BACKUP' on mount /srv/BACKUP, but as I said, after physically changing the drives it sometimes mounts the other way round ('DATA' on mount /srv/BACKUP and 'BACKUP' on mount /srv/DATA). That is confusing and frustrating, because then again you have to re-configure your fstab. Although one doesn't change internal drives that often, the same problem can occur with internal drives!

Solution: Use UUIDs in /etc/fstab to mount the device to the desired mount-point! Then the order of attaching the physical drives does not matter anymore, it will always mount at the right position.

Good luck.

MMSpeer

---

### Post by ryan858 on 2010-05-15
I didn't read the solution link, and am glad to see that all these people have found a solution. But just my two cents here... I think it has something to do with grub.cfg or fstab... and definately use UUID's in fstab and grub. Actually, use them in all scripts, or anything that is executed at startup... anything automated. Because if you remove a device or partition, then the names will change, but UUID will always stay the same... I think it is based on the device's serial number.. I'm probably wrong though, but it *sounds* good. Lol.

***The above is not advice in any way, shape, or form. It is just my opinion, and no research has actually been done on any of these statements.***
In other words, they could be complete lies!

---

### Post by virtualman on 2010-06-06
**I hope this might help you.It worked out for me.**

[http://neophyteman.wordpress.com/2010/06/06/ubuntu-10-04-boot-or-devsda-startup-mount-problem/](http://neophyteman.wordpress.com/2010/06/06/ubuntu-10-04-boot-or-devsda-startup-mount-problem/)

---

### Post by Picro on 2010-06-15
I was facing a similar problem after reinstalling Ubuntu 10.04 NRE along with Win 7 on my netbook. While installing, I'd created a FAT32 partition, mounted on /windows. Later on I formatted that to NTFS and mounted on /media/data. That change led to Ubuntu giving the error message "The disk drive for /windows is not ready yet or not present". The solution provided by Havenoname was of good help and commenting out the appropriate entry in the /etc/fstab solved the issue! Thank you folks! :guitar:

---

### Post by cougar4u on 2010-06-22
I had a similar problem as well. I had to do my monthly reformat of Windows and after restoring GRUB through live CD I was getting this error.

I found this tutorial to be very useful and much more condensed then the previous one posted.

[http://neophyteman.wordpress.com/2010/06/06/ubuntu-10-04-boot-or-devsda-startup-mount-problem](http://neophyteman.wordpress.com/2010/06/06/ubuntu-10-04-boot-or-devsda-startup-mount-problem)

I simply had to edit my fstab and remove the entry that wasn't mounting. Once I did that, all was well.

---

### Post by tubunu on 2010-06-26
I followed the advice in this thread but the problem remains. "The disk drive for /winc is not ready yet or not present". I skip it by pressing "S" and then mount the Windows C drive by doing this in the Terminal: 

```
sudo mount /dev/sda1 /winc
```

Any way of making this command permanent? Thanks.

---

### Post by tubunu on 2010-06-27
I followed all the advice in this thread (and the links) but I can't get the C drive (/dev/sda1) to auto mount at boot... Here is the output of the command: 

```
tubunu@lucid:~$ sudo mount -a
ntfs-3g: Failed to access volume 'UUID=c05caf2b-a192-43d9-97d3-bcba66edc3cc': No such file or directory

```

My fstab file:
```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb3 during installation
UUID=29862247-002d-46ad-a71b-ad0b653c545a /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb5 during installation
UUID=6b46faa6-dbf5-4e5a-97f8-4bec996aa800 /home           ext4    defaults        0       2
# /studio was on /dev/sda5 during installation
UUID=0A706EBB706EAD5F /studio         ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
# /winc was on /dev/sda1 during installation
UUID=c05caf2b-a192-43d9-97d3-bcba66edc3cc /winc           ntfs    defaults        0       2
# /wind was on /dev/sdb1 during installation
UUID=F6002588002550C3 /wind           ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
# swap was on /dev/sdb6 during installation
UUID=b02b84ed-caeb-43b0-a7d7-7a35e848c5a1 none            swap    sw              0       0
```

and 

```
tubunu@lucid:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x875a90b9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sda2            3825        9729    47431882    f  W95 Ext'd (LBA)
/dev/sda5            3825        9729    47431881    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf35e0f24

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        7831    62902476    7  HPFS/NTFS
/dev/sdb2            9149       19457    82807012    5  Extended
/dev/sdb3            7832        9148    10578802+  83  Linux
/dev/sdb5            9149       19386    82236703+  83  Linux
/dev/sdb6           19387       19457      570276   82  Linux swap / Solaris

```

What am I missing?

---

### Post by NormInNorman on 2010-07-01
My machine gave me the same error screen every time I booted with my USB drive plugged in.  It was pretty annoying because every time I rebooted I had to do it twice because I'd forget to unplug my drive beforehand. I changed everything I could in my fstab from /dev/xxx to UUID=yyy like the links above and it worked!  The only thing I can figure out is maybe the USB stuff is mounting before fstab and it was using what I had set as my /home partition's dev, thus causing a conflict.

This was a clean install - I wonder why my fstab didn't use UUIDs in the first place?  I hope this doesn't mean I'll have problems in the future.

---

### Post by NormInNorman on 2010-07-01
> **tubunu said:**
> What am I missing?
Is it possible that the UUID in your fstab is wrong?  You could try doing "ls -l /dev/disk/by-uuid" and double checking.

---

### Post by tubunu on 2010-07-15
> **NormInNorman said:**
> Is it possible that the UUID in your fstab is wrong?  You could try doing "ls -l /dev/disk/by-uuid" and double checking.

You were right. Thanks for the help, it is fixed now.

---

### Post by chouf on 2010-08-13
I had the same issue but I'm pretty sure it was related to a USB external HDD that was plugged in.

I was getting the message

```
The drive for /media/sdb1 is not ready or not present.
```

I followed the instructions provided on [neophyteman's page]("http://neophyteman.wordpress.com/2010/06/06/ubuntu-10-04-boot-or-devsda-startup-mount-problem/") linked above and fixed the issue.

I did not entirely follow the procedure and ended up simply removing the line with */media/sdb1* in my fstab file.

So to summarize for my problem:

```
gksudo gedit /etc/fstab
```

located the line that was similar to something like > UUID=a647ea33-74ee-4123-84bf-7edc32e2e39b /media/sdb1 defaults 0 0 and simply deleted it.

Reboot the machine and it was solved.

I took the risk of deleting the line as I was sure it was not one of the partition on which the machine would boot. If it would have been a /sda I do not think I would have removed the line.

Anyway this was just to add a bit more of documentation on this problem

PS: I'm also dual booting W7/Ubuntu 10.04

---

### Post by yagolf on 2010-08-23
**@Chouf**

If it so happens that you're not sure of taking the risk of deleting a line in fstab, you can just "comment" the line and it will be bypassed.

so, in your case the line
> UUID=a647ea33-74ee-4123-84bf-7edc32e2e39b /media/sdb1 defaults 0 0 
would look like
#UUID=a647ea33-74ee-4123-84bf-7edc32e2e39b /media/sdb1 defaults 0 0 
and that would be sufficient.

I also encountered the same problem after installing Windows7 on top of my old XP where fstab ended up having 1 logic partition addressed in 2 different lines with 2 different mounting points... :lolflag:
In this case I did delete the line that pointed to the old XP partition, obviously, and problem solved!

:guitar:

---

### Post by aenesias on 2010-08-23
i have a similar problem related with it if u dont mind. I am using win xp and ubuntu 10.4 dual booting. I am okey with file system checks it does it sometimes without a problem with the ntfs partition and ubuntu partition but for the last check i got this message “The disk drive for /media/25C74B07FB07878 is not ready or not present continue waiting or press s to skip or M for manual recovery” i waited for it but nothing happened. Then now i have to press “s” to skip everytime. I have my ubuntu working fine and the ntsf drives and the xp everything is fine. I couldnt find which "media" does this message is talking aboout? Do u have any ideas for this problem thanx in advance

---

### Post by junior2 on 2010-10-08
I have a related question to this thread.  I have several removable storage drives that are set to mount by UUID in fstab, however one or more of them is actually not present when booting.  Is there a way to just ignore any drives that are not found automatically, rather than having to wait for the user to hit 's'?  It's quite inconvenient in our setup.

---

### Post by pricinosus on 2010-10-21
> **junior2 said:**
> I have a related question to this thread.  I have several removable storage drives that are set to mount by UUID in fstab, however one or more of them is actually not present when booting.  Is there a way to just ignore any drives that are not found automatically, rather than having to wait for the user to hit 's'?  It's quite inconvenient in our setup.

This is the next, common sense, step improving grub, for developers.
My devices are listed in fstab, mounting and working properly. But sometimes I remove physically a device, and boot system without it.
It would be nice if it will be ignored and system boot automatically, without my interaction.

    

I'm looking for answer of this question too.

---

### Post by SilverWave on 2010-12-09
Just happened to me after an update.... needed to restart...

On boot up:

**backup2 is not ready yet or not present**
***Continue to wait, press S to skip or M for manual recovery.***
**backup3 is not ready yet or not present**
***Continue to wait, press S to skip or M for manual recovery.***

Skipped then checked out this thread...

Checked:

```
gksudo gedit /etc/fstab
```Checked:

```
 ls -l /dev/disk/by-uuid
```Did not show the uuid for "../../sdc1" noted in fstab.

sdc2 sdc1 not showing in gparted

Shut down and then restarted. **All working again.**

Notes: Both partitions are ntfs for server2008 r2
So this could just be a one off issue reading sdc...
Or possibly grub2 needed a second pass to sort things out?

---

### Post by sergeantkeg on 2010-12-21
I also got this problem after installing some updates.

I'm not dual-booting, though; I have only 10.04 on my laptop.

I get "The disk drive for / is not ready yet or not present" and when I skip that, I get "The disk drive for /tmp is not ready yet or not present."  After about five seconds, I get a blinking underscore in the upper right-hand corner of the screen but nothing happens.

Whenever I press "M" to go to the root menu, I'm unable to use the "gksudo gedit /etc/fstab" because I get "Gtk-WARNING **: cannot open display:" so I basically can't edit anything.

What should I do?  Thanks!

---

### Post by Echhzperienz on 2011-01-07
> **pricinosus said:**
> This is the next, common sense, step improving grub, for developers.
My devices are listed in fstab, mounting and working properly. But sometimes I remove physically a device, and boot system without it.
It would be nice if it will be ignored and system boot automatically, without my interaction.

    

I'm looking for answer of this question too.

The problem is not in grub, grub finished well before these messages occur.  If the problem is fixable in fstab, then it is a problem with mount (executed from an init.d script, AFTER the partition table has been read and Linux is starting).

I found this interaction during boot completely unacceptable.  I have fstab entries to mount removable media that I don't want -- and in Hardy, didn't need -- to have installed normally.

Found this post : [http://askubuntu.com/questions/120/how-do-i-avoid-the-s-to-skip-message-on-boot](http://askubuntu.com/questions/120/how-do-i-avoid-the-s-to-skip-message-on-boot) .  If you want to keep your fstab entry, but not have to press 'S' during boot, add the 'nobootwait' option to the volume's options in /etc/fstab.

This seems like a common enough expectation that it should really be in the Ubuntu Help menu, or in the release notes!

---

### Post by Echhzperienz on 2011-01-07
> **sergeantkeg said:**
> I also got this problem after installing some updates.

I'm not dual-booting, though; I have only 10.04 on my laptop.

I get "The disk drive for / is not ready yet or not present" and when I skip that, I get "The disk drive for /tmp is not ready yet or not present."  After about five seconds, I get a blinking underscore in the upper right-hand corner of the screen but nothing happens.

Whenever I press "M" to go to the root menu, I'm unable to use the "gksudo gedit /etc/fstab" because I get "Gtk-WARNING **: cannot open display:" so I basically can't edit anything.

What should I do?  Thanks!

Use a non-graphical editor, like emacs or vi.  Try Ctl+Alt+F3 -- you should get a login prompt.  Login to an account with admin privileges (like, the first account you created, for example), and then type 'sudo vi /etc/fstab'; that will open /etc/fstab in the vi editor.  Make your changes, save them, exit the editor, reboot...

... but if you're not used to working with a non-graphics-based editor, you'll have a bit of research to do.  It's not hard, though, just tedious.

---

### Post by pulppure on 2011-02-22
I had the same problem for /dos after moving the partitions using gparted. Before /dos was /dev/sda9 and after /dev/sda11

What I did :

Using gparted I found that /dos was now /dev/sda11

I decided to edit fstab

sudo gedit /etc/fstab

it showed :

# /dos was on /dev/sda9 during installation
UUID=E541-A9E7  /dos            vfat    utf8,umask=007,gid=46 0       1

I thought the UUID was wrong... google pointed to this excellent explanation

[http://www.arsgeek.com/2008/01/02/how-to-find-your-uuids-for-devices-in-ubuntu-and-other-debian-based-distros/](http://www.arsgeek.com/2008/01/02/how-to-find-your-uuids-for-devices-in-ubuntu-and-other-debian-based-distros/)

in the terminal typing "blkid" showed me the right UUID for /dev/sda11
I copy pasted the right UUID for /dos and everything worked fine again :)

---

### Post by sitheris on 2011-03-01
I have experienced this issue after installing some updates on a 10.10 standalone machine (no dual-boot).

I will try the solutions suggested in this thread and update this post with the results later tonight.

Thanks!

FYI, I'd be interested in knowing what actually causes this to happen, if anyone knows?  Why would an update cause it?

---

### Post by BLTicklemonster on 2011-03-21
I have three hard drives.

sda has 5 partitions, / and four others and of course swap. 
sdb has one partition and swap.
sdc has one partition and swap.

/ and sdb1 and sdc1 come up just fine, but none of the 4 partitions on sda will come up at all. They all get the error message we are talking about here.

I've tried everything here, but nothing appears to get them to all mount when I start my computer. I have to open nautilus and mount them manually.

I've even tried pysdm to get them to mount on boot, but it doesn't work either.

So at least one partition per drive will mount on boot.

I wonder if this is significant?

(now if I can get them to mount when I boot, I just hope I can find a way to get the shared folders on each partition to be shared when I boot, too)

---

### Post by gwoodruff on 2011-03-25
Can you post the output of the following commands from the terminal?

```
sudo blkid /dev/sd??
``````
sudo fdisk -l
``````
cat /etc/fstab
```With a little more info we may be able to help.

Thanks, Gary

---

### Post by BLTicklemonster on 2011-03-25
It got it to stop somehow.

Here's my fstab, everything done manually, mkdir, mount, you name it.

```
# <file system>                            <mount point>   <type>    <options>            <dump>  <pass>
proc                                       /proc           proc      nodev,noexec,nosuid  0  0  
# / was on /dev/sda1 during installation
UUID=0064ed53-ee8b-4d16-aaba-17829b442149  /            reiserfs  notail                  0  1  
# swap was on /dev/sda3 during installation
UUID=edc3d64f-31c5-4ef3-8beb-5e6eabe018b7  none            swap      sw                   0  0  

/dev/sda2                                  /media/sda2     reiserfs  defaults             0  0
/dev/sda5                                  /media/sda5     reiserfs  defaults             0  0  
/dev/sda6                                  /media/sda6     reiserfs  defaults             0  0  
/dev/sda7                                  /media/sda7     ntfs      defaults             0  0  
/dev/sda8                                  /media/sda8     reiserfs  defaults             0  0  
/dev/sdb1                                  /media/sdb1     reiserfs  defaults             0  0  
/dev/sdc1                                  /media/sdc1     reiserfs  defaults             0  0  
```

I get no error now, and when I boot up, every drive is sitting mounted on my desktop.

And I don't know if it made any difference, but I listed all the drives/partitions in order.

---

### Post by Glix on 2011-05-07
I have the same problem, upgraded ubuntu last night from maverick, but if I try to skip, it changes to:
The disk drive for /tmp is not ready yet or not present
and if I skip that I get:
mountall: Plymouth command failedj
mountall: Disconnected from Plymouth

So I'm confused as to how I'm supposed to get to a place where I can run terminal.

---

### Post by opodaniel on 2011-08-19
this is strange for me too
I try on linux Mint 11 monunting ntfs partition using fstab
If I use UUID obtained from blkid I can't mount it , it at start that partition is not ready and to chose S or M
I I use /dev/sda5 is working 
Strange....

---

### Post by mpbinil on 2012-02-14
Dont worry, there is a simple method

use ntfs configuration tool,download from software centre,  only few KBs
it works

---

### Post by mpbinil on 2012-02-14
i have another solution for u guys,use ntfs configuration tool, download from software centre ,only few kbs ,

it works,it tells u sda2 is unmounted and it will do everything click ok,

but it change properties of all drives to read only,change it back to read and write

---

### Post by algent on 2012-06-20
> **chouf said:**
> I had the same issue but I'm pretty sure it was related to a USB external HDD that was plugged in.

I was getting the message

```
The drive for /media/sdb1 is not ready or not present.
```I followed the instructions provided on [neophyteman's page]("http://neophyteman.wordpress.com/2010/06/06/ubuntu-10-04-boot-or-devsda-startup-mount-problem/") linked above and fixed the issue.

I did not entirely follow the procedure and ended up simply removing the line with */media/sdb1* in my fstab file.

So to summarize for my problem:

```
gksudo gedit /etc/fstab
```located the line that was similar to something like  and simply deleted it.

Reboot the machine and it was solved.

I took the risk of deleting the line as I was sure it was not one of the partition on which the machine would boot. If it would have been a /sda I do not think I would have removed the line.

Anyway this was just to add a bit more of documentation on this problem

PS: I'm also dual booting W7/Ubuntu 10.04

Thank you **chouf ** i followed your instructions and solved my  problem.

i found something like this
```
UUID=9F5A-A32A         /windows     vfat  utf8,umask=007,gid=46     0  1   
```and simply deleted it.  

The problem was created because, i have dual boot system XP SP3/Ubuntu 12.04. When I installed ubuntu i formated that partition in FAT32 and mounted /windows. Then I booted Windows and formated the partition with NTFS file system.

---

### Post by algent on 2012-06-20
Thanks!

---

### Post by BLTicklemonster on 2012-06-20
Another upgrade last week messed fstab up. Could not attach a usb device (my camera or a thumb drive).
Had to manually edit fstab.

Somebody needs to be aware of this somewhere, I think. This is the kind of stuff that will run new folks off in droves.

---

### Post by bth73 on 2012-06-27
I too have this problem. NO windows, no dual boot, happened after replacing pata dvd with sata dvd. 
Nothing I try works. Tried all links. fstab not saving changes.
Hasn't been a good linux distro since 2008. Getting worse with every update.
Second time in less than a year the system has failed. (still better than windows XP that would not work for one day on this computer).
Not sure what to do. Switched from Ubuntu to Mint and still have stupid problems that should not exist.

Any personal help would be appreciated.
Thanks, Bruce

---

### Post by lakshyavision on 2012-08-14
> **Blond said:**
> Hello, I had the same problem after upgrading from kubuntu 9.10 to 10.04 on a dual boot system with WindowsXP 64 bit.

But now I solved it thanks to "havenoname". I followed the link he published and this triggered me.

In my case /media/sda2 is an extended pertition in which my Windows partition sits.

So there is no need to mount this extended partition and therefore I removed it from /etc/fstab.

In the proces I also added my WindowsXP drive with the GUID as found with the command 'sudo blkid'.

Succes, it worked for me :-)
============================================================
Thank you sir.It also worked for me

1.open terminal(ctrl+alt+t)
2.type: gksu gedit /etc/fstab
3.press enter
4.text editer appears
5.all your partitions will be listed there
6.only delete the line indicating the drive shown error during boot.
7.save the document.
8.close it.

9.bootloader will be automatically updated in the terminal.
10.after that close the terminal.
11.reboot to see the problem is solved.
thanks
manish nirvan

---

