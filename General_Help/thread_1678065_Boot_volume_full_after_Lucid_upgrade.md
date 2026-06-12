---
title: "Boot volume full after Lucid upgrade"
date: 2011-01-29
forum: General Help
---

### Post by justpoppingin on 2011-01-29
Hello,

although this is my first post here, I have been using this forum as a mine of help over the last couple of years, so thank you for past help. 

I have just upgraded to Lucid from Hardy using the Update Manager.  I had a message that my boot volume is full, which pointed me to the Disk Usage Analyser.  DUA indicates that /boot is indeed full at 11.5G, but it doesn't point me to what I can do about it.  I'm completely unfamiliar with the contents of /boot so don't know if there's anything there that shouldn't be (or whether 11.5G is normal?  Is it?)  Do I just need to allocate more space?  If so, how?

Everything is very sluggish and many keystrokes are not registering.  Frustrating!  Could this be a symptom of the /boot issue?

Thanks in advance for any help.

jpi

---

### Post by justpoppingin on 2011-01-29
Ooops, meant to post this under Absolute Beginner Talk.

---

### Post by TeoBigusGeekus on 2011-01-29
/boot holds the kernels installed on your system.
If you've never deleted any old kernels, open Synaptic package manager and search for linux-image. Keep the 2 most recent ones - completely remove all others.
After that, do a 
```
sudo update-grub
```
to inform grub of your changes and I believe that you should be ok.

---

### Post by drs305 on 2011-01-29
You can free up some space in the /boot partition by removing older kernels. One of the easiest ways to do this is with Ubuntu Tweak. Here is a guide:
[http://ubuntuforums.org/showthread.php?t=1587462]("http://ubuntuforums.org/showthread.php?t=1587462")

That will give you a little breathing room, but having said that, 11GB is way too large for a /boot partition to be filled up. It's possible you have other files in their taking up space - perhaps a backup stored to the wrong partition, etc. Here is another link which might help you find out what is taking up your /boot space:
[HOWTO: Recover Lost Disk Space]("http://ubuntuforums.org/showthread.php?t=1122670")

---

### Post by justpoppingin on 2011-01-29
Thank you for your speedy replies.  Unfortunately I can't seem to remove the kernels.

Synaptic Manager output said this:

```
(Reading database ... 360268 files and directories currently installed.)
Removing linux-backports-modules-2.6.20-16-generic ...
update-initramfs: Generating /boot/initrd.img-2.6.20-16-generic
Removing linux-backports-modules-2.6.20-17-generic ...
update-initramfs: Generating /boot/initrd.img-2.6.20-17-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.20-17-generic
dpkg: error processing linux-backports-modules-2.6.20-17-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-backports-modules-2.6.22-16-generic ...
update-initramfs: Generating /boot/initrd.img-2.6.22-16-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.22-16-generic
dpkg: error processing linux-backports-modules-2.6.22-16-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-backports-modules-2.6.20-17-generic
 linux-backports-modules-2.6.22-16-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up initramfs-tools (0.92bubuntu78) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.32-28-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.32-28-generic
dpkg: error processing initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 initramfs-tools

```

Any ideas?

---

### Post by SaintDanBert on 2011-01-30
There is a way to do this using the package manager(s) and the **purge** options -- completely remove package parts. However,
the brute force way does something like this:
```

prompt$  sudo -i    #start a shell as super user
x*x*x*x*

prompt# #..... which kernels do you have?
prompt# ls -lh /boot/vmlinuz*
-rw-r--r-- 1 root root 3.9M 2010-11-24 07:57 vmlinuz-2.6.32-26-generic                                              
-rw-r--r-- 1 root root 4.0M 2010-11-24 08:17 vmlinuz-2.6.32-26-generic-pae                                                
-rw-r--r-- 1 root root 3.9M 2010-12-01 18:48 vmlinuz-2.6.32-27-generic                                                
-rw-r--r-- 1 root root 4.0M 2010-12-01 18:59 vmlinuz-2.6.32-27-generic-pae                                                
-rw-r--r-- 1 root root 3.9M 2011-01-10 19:18 vmlinuz-2.6.32-28-generic                                                
-rw-r--r-- 1 root root 4.0M 2011-01-10 19:36 vmlinuz-2.6.32-28-generic-pae

prompt#..... notice the oldest numbers & remove them
prompt# sudo rm -iv /boot/*32-26*
rm: remove regular file `/boot/abi-2.6.32-26-generic'? 
rm: ...

prompt# #..... now tell grub about the changes
prompt# sudo update-grub

prompt# {ctrl-D}
prompt$ 

```

I usually keep only three kernels -- actually six: 3 with and 3 without -pae.  You are supposed to be able to set parameters in grub that only put N into the menu, but it does not remove files from the /boot folder.

Cheers,
~~~ 0;-Dan

---

### Post by justpoppingin on 2011-01-30
Back after a good night's sleep (it was getting a bit late here!)

So, the attempts I made with Synaptic and Tweak last night must have had some effect as today the sluggishness is gone and all keyboard strokes are registering (which is a beautiful thing!)  However, I still got the message about /boot being full when I logged in.  Disk Usage Analyser was showing ~180MB in /boot. 

I have now followed Dan's instructions (thanks Dan) and, according to DUA, /boot is down to 55.9MB, but still 100% full.  What's the usual capacity for /boot?  56MB doesn't seem like a lot to be filling something up.

Except...  If I run DUA on the whole filesystem, it shows / to be 100% full and /boot to be only 0.6%.  Do the percentages not mean what I thought they meant?  Total filesystem capacity is 52.3GB of which only 9.8GB are now used.

Thanks.

---

### Post by Irony on 2011-01-30
What files/folders do you see in /boot;

```
ls /boot

abi-2.6.32-27-generic
grub
memtest86+.bin
vmcoreinfo-2.6.32-27-generic
config-2.6.32-27-generic
initrd.img-2.6.32-27-generic
System.map-2.6.32-27-generic
vmlinuz-2.6.32-27-generic
```

---

### Post by justpoppingin on 2011-01-30
Since my last post, a warning in update manager told me that updating was broken, and I should run ```
sudo apt-get install -f
``` to fix it.  This generated three new initrd* files.  Full list:
  
```

total 78M
-rw-r--r-- 1 root root 414K 2010-03-24 13:33 abi-2.6.24-27-generic
-rw-r--r-- 1 root root 414K 2010-11-24 13:00 abi-2.6.24-28-generic
-rw-r--r-- 1 root root 637K 2011-01-11 01:18 abi-2.6.32-28-generic
-rw-r--r-- 1 root root  79K 2010-03-24 13:33 config-2.6.24-27-generic
-rw-r--r-- 1 root root  79K 2010-11-24 13:00 config-2.6.24-28-generic
-rw-r--r-- 1 root root 114K 2011-01-11 01:18 config-2.6.32-28-generic
drwxr-xr-x 2 root root 1.0K 2011-01-30 12:43 grub
-rw-r--r-- 1 root root  11M 2011-01-30 13:25 initrd.img-2.6.20-17-generic
-rw-r--r-- 1 root root  11M 2011-01-30 13:26 initrd.img-2.6.22-16-generic
-rw-r--r-- 1 root root 7.6M 2010-04-29 21:09 initrd.img-2.6.24-27-generic
-rw-r--r-- 1 root root 7.6M 2010-03-18 21:30 initrd.img-2.6.24-27-generic.bak
-rw-r--r-- 1 root root 7.4M 2011-01-29 20:34 initrd.img-2.6.24-28-generic
-rw-r--r-- 1 root root 7.6M 2011-01-22 11:46 initrd.img-2.6.24-28-generic.bak
-rw-r--r-- 1 root root  13M 2011-01-30 13:26 initrd.img-2.6.32-28-generic
drwx------ 2 root root  12K 2007-10-19 13:42 lost+found
-rw-r--r-- 1 root root 157K 2010-03-23 09:37 memtest86+.bin
-rw-r--r-- 1 root root 886K 2010-03-24 13:33 System.map-2.6.24-27-generic
-rw-r--r-- 1 root root 886K 2010-11-24 13:00 System.map-2.6.24-28-generic
-rw-r--r-- 1 root root 1.7M 2011-01-11 01:18 System.map-2.6.32-28-generic
-rw-r--r-- 1 root root 1.2K 2011-01-11 01:20 vmcoreinfo-2.6.32-28-generic
-rw-r--r-- 1 root root 1.9M 2010-03-24 13:33 vmlinuz-2.6.24-27-generic
-rw-r--r-- 1 root root 1.9M 2010-11-24 13:00 vmlinuz-2.6.24-28-generic
-rw-r--r-- 1 root root 3.9M 2011-01-11 01:18 vmlinuz-2.6.32-28-generic

```

---

### Post by drs305 on 2011-01-30
It looks like you still have some very old kernels in /boot, such as 2.6.20, 2.6.22, 2.6.24, etc. 

You don't need anything earlier than 2.6.32 if you are using Lucid. Try Ubuntu Tweak again and remove anything less than 2.6.32.

You can also look for earlier kernels with this command:
```
sudo find /boot/*2.6.2*
```
If you have properly removed the unnecessary files that command should not produce any output.

If Ubuntu Tweak is unable to remove them, open a file browser as root and remove the files. The easy way to do that is to install "nautilus-gksu", which then allows the user to right click on any folder and select "Open as administrator".

You also might want to look at your /etc/apt/sources.list file to make sure you don't have any references to earlier Ubuntu releases (edgy, fiesty, hardy, etc)
```
cat /etc/apt/sources.list | grep -v "#"
```

---

### Post by justpoppingin on 2011-01-30
Thanks.  I just ran Tweak again, and it removed the old kernels with no problem this time (presumably because it had more space after I'd taken out the *even older* ones with Dan's method?)  Have re-booted and am no longer getting the warning message after login, so I think it's sorted.

However, I still don't understand the DUA info.  If I use it to scan /boot, it lists "usage" as 100% still (with 19.4MB).  On the other hand, System Monitor lists /boot as 12% used.   Why the inconsistency?

---

### Post by drs305 on 2011-01-30
> **justpoppingin said:**
> However, I still don't understand the DUA info.  If I use it to scan /boot, it lists "usage" as 100% still (with 19.4MB).  On the other hand, System Monitor lists /boot as 12% used.   Why the inconsistency?

DUA can be a bit confusing, so don't feel like it's only you...

The top level of DUA always shows 100%, even if the partition is always empty.

---

### Post by SaintDanBert on 2011-01-30
If you used the desktop to remove files, did you remember to empty the trash?

Take a look at the **du** (disk usage) command line utility.

Also, check out the **baobab** graphical disk usage analyzer.

If you "deleted" files and you don't see freespace ... you have overlooked something. Each vmlinuz is roughly 4 MB and initrd is another 14 MB. With the other little files thing 20 MB per kernel edition.

Good luck,
~~~ 0;-Dan

---

### Post by justpoppingin on 2011-01-30
Thanks for all the advice.  I checked for Trash using [[COLOR=#d40000]**drs305**[/COLOR]]("http://ubuntuforums.org/member.php?u=223945")'s How To page, and didn't find any.  It looks like I'm sorted!

---

### Post by SaintDanBert on 2011-01-30
> **justpoppingin said:**
> 
...

Except...  If I run DUA on the whole filesystem, it shows / to be 100% full and /boot to be only 0.6%.  Do the percentages not mean what I thought they meant?  Total filesystem capacity is 52.3GB of which only 9.8GB are now used.Thanks.

From the "is it plugged in school of fixing things"

On disk, there is a partition. We create a file system on that partitions then We mount that partition and call it "/" (laugh) pronounced "root."

Within this file system is a folder called "/boot"  The contents of this folder might be
[list]
[*]the actual files and folders used during initial startup, [highlight]OR[/highlight]
[*]the mount point of a separate file system -- and that separate file system holds the actual files and folder &c.
[/list]

Remember what we said about /boot? You can say the same things about "/tmp" and "/var" and several other top-level folders. The /tmp folder gets all sorts of log files and other temporary (sic) contents. If these are actual folders within your root file system, then if it gathers cruft, root will get filled and messages gang aglee. Therefore some disk house cleaning, try /tmp/* and  /var/log/messages as starters.

Bonne chance,
~~~ 0;-Dan

---

