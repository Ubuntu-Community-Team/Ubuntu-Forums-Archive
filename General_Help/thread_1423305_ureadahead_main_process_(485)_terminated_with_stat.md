---
title: "ureadahead main process (485) terminated with status 5"
date: 2010-03-06
forum: General Help
---

### Post by Matti L on 2010-03-06
When booting I see that after the white ubuntu logo before gdm. Everything seems to work fine but is that bad? How to fix? Should I try reinstalling Ubuntu for it to go away?

---

### Post by octavio.rdz on 2010-05-03
Hi I just installed ubuntu 10.04 the release and I have the same message just with different process (number), so I would like to know if there is something you did to avoid getting the message.

is there anything wrong with the installation that I get this message?

thanks in advance.

---

### Post by john newbuntu on 2010-05-03
Please read this interesting post by a developer - kabuk.  It says to check your /etc/fstab file and see if something fails to get mounted at boot time.
[http://ubuntuforums.org/showthread.php?t=1434502](http://ubuntuforums.org/showthread.php?t=1434502)

---

### Post by Matti L on 2010-05-04
I fixed the problem by reinstalling Ubuntu 9.10 (or actually installed Linux Mint first but didn't like it so went back to Ubuntu). I think I got the message cause I had resized and moved partitions after installing Ubuntu so maybe the UUIDs weren't right because of that, though they did show up the same as in my fstab with "blkid" and "ls -l /dev/disk/by-uuid" commands.

So my fix is to resinstall Ubuntu but for that it's good to have a separate /home. Or maybe regenerate UUIDs somehow or something, I dunno.

---

### Post by tlinuxx on 2010-05-09
/dev/disk/by-uuid is the same with /etc/fstab, It seems no problem found,but the problem is that ureadahead still terminated with status 5

---

### Post by piedro on 2010-05-11
Exactly the same for me! the UUIDs are the same like in /etc/fstab ... 

And: "/var/lib/ureadahead/pack" doesn't exist ... 

I renamed "/etc/init/ureadahead.conf" to "/etc/init/ureadahead.conf.disabled" but it will not be rewritten even after reinstalling ureadahead ... 

I don't understand what's wrong. 

plz help, 
thx, 
piedro

---

### Post by Matti L on 2010-05-11
If you get the message "ureadahead-other main process terminated with status (some number)" then AFAIK removing extra file systems (like ntfs/windows partitions) from fstab works.
[http://tech--help.blogspot.com/2009/12/ubuntu-solved-ureadahead-other-main.html](http://tech--help.blogspot.com/2009/12/ubuntu-solved-ureadahead-other-main.html)

But my problem was that I had ureadahead and ureadahead-other terminating and fixing the latter didn't fix the former.

But I had that problem two or three months ago and fixed it with a fresh install.

---

### Post by piedro on 2010-05-11
Seems to be a buggy "ureadahead"-package. 

I found this bug on launchpad: 

[https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/523484](https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/523484) 

I have /var on a separate partition. 

Well, now that's it for the moment it seems ... 

cu,  
piedro

---

### Post by webstandardcss on 2010-05-15
> **piedro said:**
> Seems to be a buggy "ureadahead"-package. 

I found this bug on launchpad: 

[https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/523484](https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/523484) 

I have /var on a separate partition. 

Well, now that's it for the moment it seems ... 

cu,  
piedro


[SOLVED] OK, so you thought you were smart and installed Ubuntu with /var on its own partition  so that way runaway log files can't take down your whole system. (wasn't this theory valid back when hard drives we measured in Megabytes?)

Well I am that smart guy and I got the readahead error.

Here is what I did to fix it.  (it worked for me YMMV)

Boot to Ubuntu live CD

Mount /var partition and root partition from the Hard drive. (Just click the drive in Places to see the disks.)

Edit /etc/fstab on the hard drive root filesystem and comment out the line containing /var

Enter the /var partition on the root filesystem and rename the three existing directories appending ".old" (without quotes) to the end of the filename.

Copy the contents of the var partition to the /var folder of the root partition

Copy the contents of the three ".old" directories to their respective directories inside /var on the root partition.

Reboot.

Now in places you should see an unmounted disk which used to be the /var/ partition

Also you should not see the unreadahead error any more.

---

### Post by Matti L on 2010-05-15
> **webstandardcss said:**
> [SOLVED] OK, so you thought you were smart and installed Ubuntu with /var on its own partition  so that way runaway log files can't take down your whole system. (wasn't this theory valid back when hard drives we measured in Megabytes?)

Well I am that smart guy and I got the readahead error.

Here is what I did to fix it.  (it worked for me YMMV)

Boot to Ubuntu live CD

Mount /var partition and root partition from the Hard drive. (Just click the drive in Places to see the disks.)

Edit /etc/fstab on the hard drive root filesystem and comment out the line containing /var

Enter the /var partition on the root filesystem and rename the three existing directories appending ".old" (without quotes) to the end of the filename.

Copy the contents of the var partition to the /var folder of the root partition

Copy the contents of the three ".old" directories to their respective directories inside /var on the root partition.

Reboot.

Now in places you should see an unmounted disk which used to be the /var/ partition

Also you should not see the unreadahead error any more.

Marked this thread as solved \\:D/

---

### Post by piedro on 2010-05-15
thx webstandardcss! 

Actually I did have /var on an extra partition to make it easy to update the system with a clean installation without the necessity for a complete databases and webserver backup ... (but that's not too much trouble to be honest ...)

But anyway - your workaround works. So I don't get any errors during boot now anymore. 

Thx for your help, 
piedro

---

### Post by bigbaraboom on 2010-05-21
> Now in places you should see an unmounted disk which used to be the /var/ partition

What is the purpose of an unmounted /var partition after this workaround?

---

### Post by piedro on 2010-05-22
No purpose! 

Delete it and resize your / partition to reclaim the otherwise wasted space ... 

cya, 
p.

---

### Post by SoFl W on 2010-06-25
So the fix is to remove the separate /var partition?  I have /var on a separate drive for web development and because the root drive is small.  I also have /home on that second drive as a separate partition.  The problem is because of the /var partition being separate?

---

### Post by piedro on 2010-06-25
Yes! 

No separate /var solves the problem, sry, works around it. 

If you're root partition is small, you can make a folder (I called it "system" on your home partition, add those folders for webdevelopment, servers, databases and maybe caches or even logs to this "system" folder and finally symlink those folders to their expected locations in the /var folder. 

It's easy to do and you accomplish two things: 
- control the size of your root partition 
- and have all your important data within your /home partition 

But I hope the ureadahead stuff will be fixed for separate partitions in the future - at least it seems like a conceptional flaw to me.   

thx for reading, 
piedro

---

### Post by SoFl W on 2010-06-25
Thank you for your help.  I was wondering if a symbolic link from /var/www to a folder on my second drive would work and eliminate the error.  If I get the courage and the time I will give it a try.  Right now the /var/www space is small and I have other servers to use but I wanted server practice.  I set these things up and forget how I did everything.
I learn again, and learn a lot of new things.

Thanks again for your help, I will let you know how things work.

---

### Post by Gianluca Tedone on 2010-07-31
Hi. I'm facing the same "ureadahead main process (xyz) terminated with status 5" problem each time I boot with my "2.6.35-020635rc6-generic" kernel, but I've no /var separate partition. 

However some symptoms are the same of above users:

bluespirit@lupin3:~$ status ureadahead
ureadahead stop/waiting

bluespirit@lupin3:~$ cat /proc/self/mountinfo
13 17 0:13 / /sys rw,nosuid,nodev,noexec,relatime - sysfs none rw
14 17 0:3 / /proc rw,nosuid,nodev,noexec,relatime - proc none rw
15 17 0:5 / /dev rw,relatime - devtmpfs none rw,size=1009108k,nr_inodes=216072,mode=755
16 15 0:10 / /dev/pts rw,nosuid,noexec,relatime - devpts none rw,gid=5,mode=620,ptmxmode=000
17 1 8:7 / / rw,relatime - ext3 /dev/disk/by-uuid/4e7c0d18-1de9-4f5a-80f8-5fcb4cb0efd7 rw,errors=remount-ro,barrier=0,data=ordered
18 13 0:14 / /sys/fs/fuse/connections rw,relatime - fusectl none rw
19 13 0:7 / /sys/kernel/debug rw,relatime - debugfs none rw
20 13 0:15 / /sys/kernel/security rw,relatime - securityfs none rw
21 15 0:16 / /dev/shm rw,nosuid,nodev,relatime - tmpfs none rw
22 17 0:17 / /var/run rw,nosuid,relatime - tmpfs none rw,mode=755
23 17 0:18 / /var/lock rw,nosuid,nodev,noexec,relatime - tmpfs none rw
24 17 0:19 / /lib/init/rw rw,nosuid,relatime - tmpfs none rw,mode=755
25 17 8:5 / /data_exc rw,nosuid,nodev,relatime - fuseblk /dev/sda5 rw,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096
26 17 8:1 / /windows rw,nosuid,nodev,relatime - fuseblk /dev/sda1 rw,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096
27 17 8:6 / /boot rw,relatime - ext3 /dev/sda6 rw,errors=continue,barrier=0,data=ordered
28 17 8:8 / /home rw,relatime - ext3 /dev/sda8 rw,errors=continue,barrier=0,data=ordered
29 14 0:20 / /proc/sys/fs/binfmt_misc rw,nosuid,nodev,noexec,relatime - binfmt_misc binfmt_misc rw
32 28 0:22 / /home/bluespirit/.gvfs rw,nosuid,nodev,relatime - fuse.gvfs-fuse-daemon gvfs-fuse-daemon rw,user_id=1000,group_id=1000

bluespirit@lupin3:~$ df -H
File system             Dimens. Usati Disp. Uso% Montato su
/dev/sda7               21G   4,9G    15G  26% /
none                   1,1G   271k   1,1G   1% /dev
none                   1,1G   562k   1,1G   1% /dev/shm
none                   1,1G    82k   1,1G   1% /var/run
none                   1,1G      0   1,1G   0% /var/lock
none                   1,1G      0   1,1G   0% /lib/init/rw
/dev/sda5               21G   8,5G    13G  41% /data_exc
/dev/sda1               32G    12G    21G  36% /windows
/dev/sda6              239M    72M   155M  32% /boot
/dev/sda8               63G    31G    30G  52% /home
 
bluespirit@lupin3:~$ grep debugfs /etc/mtab 
none /sys/kernel/debug debugfs rw 0 0

Furthermore, if I try to make a "ureadahead --dump", I obtain:

ureadahead:/var/lib/ureadahead/pack: Nessun file o directory.

Any help is appreciated.

---

### Post by kipelovets on 2010-09-16
i have the same issue with "ureadahead terminated ...". but my system is not booting after that
i also had /var on a separate partition, but editing fstab hadn't helped

i have ubuntu 10.10 maverick installed. it worked fine with that /var on separate partition until today. and i believe that the last update from repositories that i installed today had broken the system (i launched sudo apt-get update && sudo apt-get upgrade, although i know that is a bad practice, as i believed that maverick is stable enough for that)

edit: that was not connected with ureadahead, it was really an nvidia driver issue

---

### Post by hedge.hog on 2010-10-30
This very simple fix worked for me:

[**sentinella86**]("http://ubuntuforums.org/showpost.php?p=9555086&postcount=9")

and if you want to track a bug report:

[**boot fails [...] ureadahead [...] terminated with status 5**]("https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/542334")

HTH?

---

### Post by AndreaZauli on 2011-03-21
For a better solution (with respect to the /var relocation) try this:
[http://ubuntuforums.org/showthread.php?t=1518110&page=2](http://ubuntuforums.org/showthread.php?t=1518110&page=2)

essentially you have to modify ureadahead.conf

sudo sed -i 's+^start on starting mountall+start on mounted MOUNTPOINT=/var+' /etc/init/ureadahead.conf

...to make "starting" depends on mounted /var instead on 
a generic mountall command.

Maybe this solution will solve the problem also for users with a /var 
located in the root fs....

---

### Post by FizzerJE on 2011-06-19
> **AndreaZauli said:**
> For a better solution (with respect to the /var relocation) try this:
[http://ubuntuforums.org/showthread.php?t=1518110&page=2](http://ubuntuforums.org/showthread.php?t=1518110&page=2)


And thank you for a sane approach.  :)  Worked for me, a simple code paste.

Now I can still be a 'Smart Guy' and keep my /var on a seperate partion.
For reasons other than the old Megabytes.. ;)

---

### Post by Ram Pangeni on 2011-06-23
I am working in the  filed of Cloud Computing and Virtulization. I am using XEN in my system. But, when I tried to install Ubuntu 10.04 as Dom-U in my machine, I am facing a problem. The boot screen shows error:
"ureadahead main process (130) terminated with status 5" . I am unable to boot into the system., although the command "$sudo xm list" shows that the system is up. Help me out?

---

### Post by mylittletom on 2011-08-17
I had the message "... *main process (..) terminated with status 5 *"  after recompiling linux kernel 3.1-RC2.


***sudo sed -i 's+^start on starting mountall+start on mounted MOUNTPOINT=/var+' /etc/init/ureadahead.conf***

That command works for me !

Many thanks to "Ubunteers" :popcorn::KS

---

