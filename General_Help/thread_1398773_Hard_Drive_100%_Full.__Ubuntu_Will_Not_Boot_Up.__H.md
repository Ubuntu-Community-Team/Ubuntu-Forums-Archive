---
title: "Hard Drive 100% Full.  Ubuntu Will Not Boot Up.  Help!"
date: 2010-02-04
forum: General Help
---

### Post by umechanism on 2010-02-04
I dual boot with Vista and Ubuntu 9.10.  My drive is 100% full on the Ubuntu partition so now I can't even boot up Ubuntu.  I am currently using an Ubuntu 8.10 Live CD to get into my system.  Here is my drive status now:

```
Filesystem            Size  Used Avail Use% Mounted on
tmpfs                 1.7G  2.0M  1.7G   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                 1.7G  2.0M  1.7G   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                 1.7G     0  1.7G   0% /lib/init/rw
varrun                1.7G  100K  1.7G   1% /var/run
varlock               1.7G     0  1.7G   0% /var/lock
udev                  1.7G  3.0M  1.7G   1% /dev
tmpfs                 1.7G  104K  1.7G   1% /dev/shm
rootfs                1.7G   42M  1.6G   3% /
/dev/scd0             699M  699M     0 100% /cdrom
/dev/loop0            676M  676M     0 100% /rofs
tmpfs                 1.7G   16K  1.7G   1% /tmp
/dev/sda5             330G  330G     0 100% /media/disk
/dev/sda3             340G  277G   64G  82% /media/OS
ubuntu@ubuntu:~$ 

```

sda5 is the Linux partition.  sda3 is the Windows partition.  I've tried sudo apt-get clean and auto clean as well as deleting most of my home directory via the Live CD.  The capacity never seems to change.  I still can't get in.  What can I do?

Thanks!

---

### Post by cariboo on 2010-02-05
Check ~/.local/share/Trash and /root/.local/share/Trash to make sure you don't have any large files stuck in trash.

---

### Post by Sef on 2010-02-05
How big is the linux partition?

---

### Post by umechanism on 2010-02-05
> **cariboo907 said:**
> Check ~/.local/share/Trash and /root/.local/share/Trash to make sure you don't have any large files stuck in trash.

Ok.  I did that and removed about 4 Gigs of trash but I still can't boot into it.  However, even after deleting the trash the free space on the drive did not seem to change...at least according to the GUI interface disc utility.

```
ubuntu@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
tmpfs                 1.7G  2.0M  1.7G   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                 1.7G  2.0M  1.7G   1% /lib/modules/2.6.27-7-generic/volatile
tmpfs                 1.7G     0  1.7G   0% /lib/init/rw
varrun                1.7G  100K  1.7G   1% /var/run
varlock               1.7G     0  1.7G   0% /var/lock
udev                  1.7G  3.0M  1.7G   1% /dev
tmpfs                 1.7G  104K  1.7G   1% /dev/shm
rootfs                1.7G   36M  1.6G   3% /
/dev/scd0             699M  699M     0 100% /cdrom
/dev/loop0            676M  676M     0 100% /rofs
tmpfs                 1.7G   12K  1.7G   1% /tmp
/dev/sda5             330G  321G     0 100% /media/disk

```
Where sda5 is the Linux partition.

Thanks!

---

### Post by umechanism on 2010-02-05
> **Sef said:**
> How big is the linux partition?

About 350 Gigs.

---

### Post by houseworkshy on 2010-02-05
I was just totally wrong but couldn't delete, sorry.  /dev/sda5 is usually where the swap file is on a default install which *may* have something to do with it.

---

### Post by umechanism on 2010-02-05
Well, I don't want to erase partitions just yet.  I've made backups of the home directory and my config files so I'm good in that regard.  However, I've got lots of manually compiled programs that I wish to save.

Not sure why the swap file is not enabled.  I mean, it was before. Maybe it is because the drive is full?

Something just doesn't seem right here.  I delete 4 gigs and no space is freed up.  The disc utility says I have a capacity that is different than what "df -h" gives, and there is no way I've got 350 some odd gigs of data on my Linux partition especially after I erased my home directory.

Is there a way to use the command line to list file size of each folder in the file system?

Also, is there a temp directory or other location where installation files are download via Synaptic and stored which take up room on the drive?  I've performed Autoclean but I'm not sure it worked seeing how I'm using a Live CD.  I need to check that directory for old .deb files.

What I'd give right now for a "System Restore" option like there is in Windows.  :>/

---

### Post by houseworkshy on 2010-02-05
Without actually doing anything with it ( as in back out again ) you could take a look from the partition manager or gparted ( not sure in 9.10 ) on the live cd and see what that says.  Whilst there see if the bootable flag is set.

---

### Post by houseworkshy on 2010-02-05
You clearly read my first post before I corrected it.  Sorry about that one.  "I've got lots of manually compiled programs" suggests you know more than me anyway.  I have seen a similar problem, not the same one, but that involved messed up swap files too.  That one was about them vanishing altogether however it suggested that a UUID mis-match was to blame.  I guess you've done the obvious with making swaps and swapon/swapoff.  The man pages are good on that. Don't know if any of this could be relevant but it's here  [http://www.linuxquestions.org/questions/ubuntu-63/ubuntu-swap-is-not-being-used-709485/](http://www.linuxquestions.org/questions/ubuntu-63/ubuntu-swap-is-not-being-used-709485/)

---

### Post by audiomick on 2010-02-05
> **houseworkshy said:**
> Without actually doing anything with it ( as in back out again ) you could take a look from the partition manager or gparted ( not sure in 9.10 ) on the live cd and see what that says.  Whilst there see if the bootable flag is set.
It's gparted on the 9.10 live CD. In system> administration> gparted.

Gparted wont tell you file for file, but it does show you how full it thinks the various partitions are. Good for a cross check, at least.

---

### Post by umechanism on 2010-02-05
The Swap may be the problem so I'll have to read up on the links provided.  Thanks for that.

I used "Disk Usage Analyzer" to check the free space.  I've attached the image.  It says I have a 330.5 GB drive (used 322.2 GB, and have 8.3 GB free).  This is a different value to what coding "df -h" gives me.  I find that....strange.  Yes?

---

### Post by houseworkshy on 2010-02-05
Another offchance thought.  Bleachbit could do something like that.  It can unmount swaps and run sfill.  If that is what has happened there will be a huge file somewhere full of rubbish which you can safely delete.  After which you'd have to fix the swap manually and probably ( as it would count as a new partition) the UUID too.

---

### Post by houseworkshy on 2010-02-05
Remember one can install small programs to ram from the live cd.  So perhaps you could use synaptic to pull in some diagnostics too.

---

### Post by warfacegod on 2010-02-05
> **umechanism said:**
> The Swap may be the problem so I'll have to read up on the links provided.  Thanks for that.

I used "Disk Usage Analyzer" to check the free space.  I've attached the image.  It says I have a 330.5 GB drive (used 322.2 GB, and have 8.3 GB free).  This is a different value to what coding "df -h" gives me.  I find that....strange.  Yes?

Not necessarily. Disk Usage Analyzer does not take into account your system reserve which is set at 5% by default. Which, in your case, would be about 16 GB.

---

### Post by houseworkshy on 2010-02-05
How about du -sk * | sort -rn
I think that there may be a monster in there.  Actually I hardly ever use du so maybe just look at the man page for it. Just realised I've forgoten how to look from a cd to a hard drive with it.  I'll take that as a "stop giving advice now" signal and go eat.

---

### Post by HiImTye on 2010-02-05
the way to check folder contents by size (and a handy pie chart on the right hand side) is to use the 'Disk Usage Analyzer'
```
baobab
```
when you're deleting trash files from a liveCD make sure you're deleting them and not moving them to trash (use the terminal or in nautilus make it create a right click option to 'delete' or 'skip trash' or whatever)

---

### Post by john newbuntu on 2010-02-05
cd to /media/disk.  My suspect directory is /var/log.  cd to that directory and try the du -sk * | sort -n command there and see where the monster is.  Get rid of (or move) some of those .gz files.  
/home is another suspect (under /media/disk).  Delete irrelevant files (or move these files off of this filesystem to another one if you suspect you need them)

---

### Post by warfacegod on 2010-02-05
> **HiImTye said:**
> the way to check folder contents by size (and a handy pie chart on the right hand side) is to use the 'Disk Usage Analyzer'
```
baobab
```
when you're deleting trash files from a liveCD make sure you're deleting them and not moving them to trash (use the terminal or in nautilus make it create a right click option to 'delete' or 'skip trash' or whatever)

Shift+Delete is an easier way to go about this.

---

### Post by SecretCode on 2010-02-05
Are you getting anywhere in resolving this?

Post the output of
```
sudo du -xk --max-depth 1 /media/disk | sort -n
```
or 
```
sudo du -xks /media/disk/* | sort -n
```
(sudo is just to make sure it scans directories only readable by root)

---

### Post by umechanism on 2010-02-05
> **houseworkshy said:**
> How about du -sk * | sort -rn
I think that there may be a monster in there.  Actually I hardly ever use du so maybe just look at the man page for it. Just realised I've forgoten how to look from a cd to a hard drive with it.  I'll take that as a "stop giving advice now" signal and go eat.

Here's the output:

```
ubuntu@ubuntu:/media/disk$ sudo du -sk * | sort -rn
297651712	mnt
22035072	var
8190860	home
4372316	root
3361608	usr
324480	lib
255328	opt
38220	boot
20908	etc
8268	sbin
6852	bin
24	tmp
16	lost+found
12	media
12	dev
4	sys
4	srv
4	selinux
4	proc
0	vmlinuz.old
0	vmlinuz
0	initrd.img.old
0	initrd.img
0	cdrom
ubuntu@ubuntu:/media/disk$ 


```

---

### Post by SecretCode on 2010-02-05
There's a monster in /mnt ... please add the -x parameter to make sure it's not including files from other filesystems ... and let's look inside /mnt

```
sudo du -xks /media/disk/mnt/* | sort -rn
```

Probably another drive or directory has been *copied* into /mnt when it should just have been mounted there.

(The /var directory is pretty big too, at 22G, but you can sort that out later.)

---

### Post by umechanism on 2010-02-05
> **SecretCode said:**
> Are you getting anywhere in resolving this?

Post the output of
```
sudo du -xk --max-depth 1 /media/disk | sort -n
```
or 
```
sudo du -xks /media/disk/* | sort -n
```
(sudo is just to make sure it scans directories only readable by root)

Not making a lot of progress at all.  I really appreciate anything that can help.

Here is the output you requested.  The /media/disk/mnt is a remote share.
```
ubuntu@ubuntu:/media/disk$ sudo du -xk --max-depth 1 /media/disk | sort -n
4	/media/disk/proc
4	/media/disk/selinux
4	/media/disk/srv
4	/media/disk/sys
4	/media/disk/.Trash-0
12	/media/disk/dev
12	/media/disk/media
16	/media/disk/lost+found
24	/media/disk/tmp
6852	/media/disk/bin
8268	/media/disk/sbin
20908	/media/disk/etc
38220	/media/disk/boot
255328	/media/disk/opt
324480	/media/disk/lib
3361608	/media/disk/usr
4372316	/media/disk/root
8190860	/media/disk/home
22035072	/media/disk/var
297651712	/media/disk/mnt
336265712	/media/disk
ubuntu@ubuntu:/media/disk$ 

```

---

### Post by SecretCode on 2010-02-05
I'm sure you're just about to reply to this ;)
> **SecretCode said:**
> 
```
sudo du -xks /media/disk/mnt/* | sort -rn
```


---

### Post by rnerwein on 2010-02-05
hi
it looks like it's in /var what are you looking for. i guess it's in /var/log - a runaway logfile.
cd /var and do your "du" command again.
ciao

---

### Post by umechanism on 2010-02-05
> **SecretCode said:**
> I'm sure you're just about to reply to this ;)

Here's the output
```
ubuntu@ubuntu:~$ sudo du -xks /media/disk/mnt/* | sort -rn
297651704	/media/disk/mnt/hpmediavault
4	/media/disk/mnt/Windows

```

Hpmediavault is my remote NAS.

---

### Post by umechanism on 2010-02-05
I moved about 4 gigs worth of .gz files out of the /var folder. I have space but why can't I boot up.

Now when it boots, I get this message after the Ubuntu splash screen appears:
```
**Install Problem**
The configuration defaults for Gnome Power Manager 
have not been installed correctly. Please contact 
your computer administrator
```

What does that mean?

Also, I used Gparted to inspect the partitions:  Under /dev, I have sda1, sda2,and sda3 which are Windows partitions.  Next I have:

**sda4**      extended  343.83 GiB (Total Size)
   **sda5**   ext3   334.41 GiB (Size)  326.15 (Used) 8.25 Gib (Free)
   **sda6**  linux-swap    9.42 GiB (used)  ---(used)  ---(Free)

Thoughts?

---

### Post by warfacegod on 2010-02-05
I've seen several similar threads with this problem. If my memory serves, the /var folder is usually a wild goose chase.

---

### Post by SecretCode on 2010-02-05
> **umechanism said:**
> Here's the output
```
ubuntu@ubuntu:~$ sudo du -xks /media/disk/mnt/* | sort -rn
297651704	/media/disk/mnt/hpmediavault
4	/media/disk/mnt/Windows

```

Hpmediavault is my remote NAS.

According to the -x parameter it's not remote - it's on the same filesystem. Maybe it got copied over (or as much as would fit, until the drive was full ... how big is the real hpmediavault?)

See what this says:
```
sudo du -xks /media/disk/mnt/hpmediavault/* | sort -rn
```

Also 
```
ls -l /media/disk/mnt/
```

I think you're going to have to delete that directory. Take it off the network so you can be sure you're not touching the real NAS.

---

### Post by umechanism on 2010-02-05
Here's the output:
```
ubuntu@ubuntu:~$ sudo du -xks /media/disk/mnt/hpmediavault/* | sort -rn
236921176	/media/disk/mnt/hpmediavault/Volume2
60730520	/media/disk/mnt/hpmediavault/Volume1
4	/media/disk/mnt/hpmediavault/Videos

```

and
```
ubuntu@ubuntu:~$ ls -l /media/disk/mnt/
total 8
drwxr-xr-x 5 root root 4096 2009-04-12 17:23 hpmediavault
drwxr-xr-x 2 root root 4096 2009-04-03 22:37 Windows

```

The Hpmediavault is mounted to the /mnt directory via the fstab file so I find it curious that the Live CD is picking up on the MediaVault's location in the first place.  I mean, it didn't load my fstab so how would it know?  No need to jump off topic tracking down this oddity...just seems strange to me.

Thanks for your continued help.

---

### Post by SecretCode on 2010-02-05
> **umechanism said:**
> The Hpmediavault is mounted to the /mnt directory via the fstab file so I find it curious that the Live CD is picking up on the MediaVault's location in the first place.  I mean, it didn't load my fstab so how would it know?  No need to jump off topic tracking down this oddity...just seems strange to me.
Only it's not picking it up via the fstab. It's not mounting it. Look at /etc/mtab (which shows you the current mounts) - it won't be there. 

These directories, all 297GB, are actually on your internal hard drive.

Can you access the media vault from another machine?

Disconnect your machine from your network (no ethernet no wireless). Explore through /media/disk/mnt/hpmediavault - you'll still see the files. Delete a few GB. Check from another machine: the files will still be on the NAS.

After deleting several GB *and still off the network* try booting into the disk installation. I don't know if it will work yet - the failed boots may have left some system files in inconsistent states - but there's a good chance. [eta: had not read the gnome-power-manager post - I see that booting is still not working]

The reason I say stay off the network is just in case there's a pending file copy from the NAS to your hard drive - that would explain why when you deleted 4GB earlier, the free space didn't change.

---

### Post by SecretCode on 2010-02-05
> **umechanism said:**
> 
Now when it boots, I get this message after the Ubuntu splash screen appears:
```
**Install Problem**
The configuration defaults for Gnome Power Manager 
have not been installed correctly. Please contact 
your computer administrator
```


My guess is that some of the files required during boot up were deleted or corrupted or not closed correctly when it first failed to boot up due to no free space. Somehow you need to find which ones they are and replace them, either from the live CD or from backups you may perhaps have taken.

Knowing what files/directories to replace might take a lot of trial and error though. 

I'm no expert on this but searching for "repair ubuntu installation" might give some clues.

sudo apt-get install --fix-broken

or this page: [How to repair a broken Ubuntu Desktop installation - Karmic Koala — Dharwadkar's Home on the web](http://www.dharwadkar.com/weblog/ubuntu06)

Can you boot into the 'recovery' mode from GRUB?

---

### Post by umechanism on 2010-02-05
Ok.  I read through the link you provided (thanks) and followed the directions.  Basically, this guy discovered that his x11 file had become corrupted. So, using the live CD, I browsed out to my X11.conf file in Nautilus (under sudo) and renamed it to xll.conf.backup.  I then rebooted the machine. Still did not work.

So, I booted into recovery mode and looked in /etc for an x11 file or directory but can not find any.  There is no X11 in my subfolder of /etc now.  What gives?  Is it because I've booted into a recovery mode?

Still though...the partition remains full even after I've deleted my home directory, .gz files from /var, etc.  I have 8 Gigs free on this drive but that apparently isn't enough and I can't locate where the mass amount of data is. Going nuts here.  :>?

---

### Post by umechanism on 2010-02-05
I just noticed something...I can boot into recovery mode then select from the menu to "Resume Normal Boot" which takes me to a command line prompt.  I'm in Ubuntu at this point but only at the command line.  I can't get the GUI up.  So is my issue with the GUI?  I can't find the X11 file either.

Hmmm...

---

### Post by umechanism on 2010-02-05
Making progress...

[LIST=1]
[*]Boot into recovery mode.
[*]At menu, select "Continue with normal boot"
[*]This gives you a command prompt (not in GUI).
[*]Type "startx"
[*]Gui starts and all files seem to be there.
[/LIST]

Not sure what this means...just progress.  Maybe I have an issue with my x11 server?
Thoughts?

---

### Post by umechanism on 2010-02-05
Now that I'm in, I got a warning saying that less than 1% of space was left on the disc.  So, I used Disk Analyzer to scan the drive and it showed that the /.Trash-0 has 304 Gigs of stuff in it.  I tried to empty the trash but it keeps putting it back in there.  It won't go away.

So now I've opened a terminal and coded:
```
sudo rm -r /.Trash-0
```
Waiting now on results.  Taking a long time and not visually doing anything.

---

### Post by umechanism on 2010-02-06
**MARK IT SOLVED!**

The above method seemed to have worked.  Once I used 'startx" to open a gui, it opened as root so that gave me permissions to delete as needed.  I deleted the /.trash folder as well as some videos in my home directory.  Disk Usage Analyzer now says I have 440.9 GB total, used 77.4 Gigs, have 363.5 Gigs free.

The system is up and running with a little more pep in its step.  I was on the verge of blowing the whole thing away and doing a fresh install.  Glad I didn't!

Thanks to all who helped.

---

### Post by SecretCode on 2010-02-06
Good! I think you can marked it solved yourself, under the 'thread tools' menu.

Can you boot up as normal yet?

---

### Post by umechanism on 2010-02-06
Yes.  Booting up normally.

---

