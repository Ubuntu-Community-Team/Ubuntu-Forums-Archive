---
title: "the volume &quot;Filesystem root&quot; has only x Mb disk space remaining"
date: 2011-09-18
forum: General Help
---

### Post by hardisty on 2011-09-18
Hey all,

I'm a new Linux user and have recently encountered a series of notifications informing me about my rapidly decreasing filesystem root. Google gave me some ideas, but I've yet to find a single SOLVED case. 

If it helps, my "df -h" output is:


Filesystem            Size  Used Avail Use% Mounted on
/dev/sda7             8.1G  7.6G   85M  99% /
udev                  2.9G  4.0K  2.9G   1% /dev
tmpfs                 1.2G  832K  1.2G   1% /run
none                  5.0M     0  5.0M   0% /run/lock
none                  2.9G  1.1M  2.9G   1% /run/shm
/dev/sda6             547G  2.5G  517G   1% /home


Any help would be greatly appreciated!

---

### Post by WorMzy on 2011-09-18
Yep, that's a pretty full / partition. Could be due to natural causes (installing too many applications), or it could be the product of a run-away log file.

Open a terminal and run this command, and it will give us a much better picture of what's been happening:

```
sudo du -hx --max-depth=1 / | sort -h
```

---

### Post by drs305 on 2011-09-18
This thread on finding out why a partition is filling up may be helpful to you:
[http://ubuntuforums.org/showthread.php?t=1122670]("http://ubuntuforums.org/showthread.php?t=1122670")

---

### Post by hardisty on 2011-09-18
> **WorMzy said:**
> Yep, that's a pretty full / partition. Could be due to natural causes (installing too many applications), or it could be the product of a run-away log file.

Open a terminal and run this command, and it will give us a much better picture of what's been happening:

```
sudo du -hx --max-depth=1 / | sort -h
```

Running that now! Thanks for the speedy response, this stuff can get me pretty mentally exhausted

---

### Post by hardisty on 2011-09-18
> **WorMzy said:**
> Yep, that's a pretty full / partition. Could be due to natural causes (installing too many applications), or it could be the product of a run-away log file.

Open a terminal and run this command, and it will give us a much better picture of what's been happening:

```
sudo du -hx --max-depth=1 / | sort -h
```


0	/dev
0	/proc
0	/run
0	/sys
4.0K	/cdrom
4.0K	/home
4.0K	/media
4.0K	/mnt
4.0K	/opt
4.0K	/selinux
4.0K	/srv
16K	/lost+found
32K	/root
56K	/tmp
8.3M	/bin
9.0M	/sbin
14M	/etc
66M	/boot
374M	/lib
1016M	/var
2.6G	/usr
4.0G	/

---

### Post by WorMzy on 2011-09-18
Hm. Well that's odd. There's a 3.6Gb discrepancy between the output of df, and the output of du.

As it stands, du's output suggests to me that your OS partition is perfectly fine: /var is averagely sized (that's where logs are kept), /usr is fine (that's where most applications and their related files are stored). The only thing that looks odd to me, is /lib, but at 374M, it's hardly breaking the bank.

I must admit, this has me stumped.

It may be worth working your way through drs305's thread, and seeing if that turns up anything suspect.

---

### Post by hardisty on 2011-09-18
> **WorMzy said:**
> Hm. Well that's odd. There's a 3.6Gb discrepancy between the output of df, and the output of du.

As it stands, du's output suggests to me that your OS partition is perfectly fine: /var is averagely sized (that's where logs are kept), /usr is fine (that's where most applications and their related files are stored). The only thing that looks odd to me, is /lib, but at 374M, it's hardly breaking the bank.

I must admit, this has me stumped.

It may be worth working your way through drs305's thread, and seeing if that turns up anything suspect.

Thanks for looking it over, is it possible that it's just a matter of too many applications? I haven't downloaded many and I thought that 8GB was way more than enough

---

### Post by WorMzy on 2011-09-18
No. According to the du output, you should still have 4Gb of free space. 8GB is more than enough space for most Linux distributions, especially if you have a separate /home partition like you do.

But yeah, that other unaccounted for 3.9Gb is what's worrying. df says that you're low on space, but du disagrees, so I don't know what to believe.

---

### Post by hardisty on 2011-09-18
> **WorMzy said:**
> No. According to the du output, you should still have 4Gb of free space. 8GB is more than enough space for most Linux distributions, especially if you have a separate /home partition like you do.

I see what you mean now. That's really confusing. I have zero idea what to do now.

---

### Post by JKyleOKC on 2011-09-18
I don't see that discrepancy between the du and df reports. The df report says he's using 7.6G while the last 3 entries in the du report total 7.6 also. Are you overlooking that final entry in the du report that shows 4.0G in "/" -- that's an awful lot of stuff to be in the root since the level was set to 1, so that's the place I would be looking for something runaway (or maybe 100 versions of the kernel images)...

---

### Post by hardisty on 2011-09-18
> **JKyleOKC said:**
> I don't see that discrepancy between the du and df reports. The df report says he's using 7.6G while the last 3 entries in the du report total 7.6 also. Are you overlooking that final entry in the du report that shows 4.0G in "/" -- that's an awful lot of stuff to be in the root since the level was set to 1, so that's the place I would be looking for something runaway (or maybe 100 versions of the kernel images)...

I have very little idea what that means, but I'll see what I can find in that other thread. Thanks!

---

### Post by WorMzy on 2011-09-18
> **JKyleOKC said:**
> I don't see that discrepancy between the du and df reports. The df report says he's using 7.6G while the last 3 entries in the du report total 7.6 also. Are you overlooking that final entry in the du report that shows 4.0G in "/" -- that's an awful lot of stuff to be in the root since the level was set to 1, so that's the place I would be looking for something runaway (or maybe 100 versions of the kernel images)...

The final entry is the sum of all the other entries. It's basically saying that everything on / amounts to 4.0Gb.

---

### Post by hardisty on 2011-09-18
> **WorMzy said:**
> The final entry is the sum of all the other entries. It's basically saying that everything on / amounts to 4.0Gb.

back to not knowing anything, haha. maybe I'll just partition it another 4gb and call it even.

---

### Post by JKyleOKC on 2011-09-18
> **WorMzy said:**
> The final entry is the sum of all the other entries. It's basically saying that everything on / amounts to 4.0Gb.I learn something new every day.

Incidentally I ran the same du command on my 10.04.3 system; it didn't like the -h option to sort, so I used -g. It showed me 3.5G for the total on "/" so he does have half a gigabyte more space being used. My "/var" was just 510M, again about half of his usage -- and my logs go a long way back. 

His /bin, /sbin, and /etc are all significantly larger than mine, but not enough to account for 3.6G unless there are some really huge subdirectories in them that aren't contributing to the total, which I doubt...

---

### Post by hardisty on 2011-09-19
I uninstalled a program, which freed up roughly 120mb, but now every startup gets a new notification with an ever shrinking number.

I'm pretty sure this is unrelated, but I'm also stuck using only Ubuntu 2D for my main account. Signing in as a guest works fine, but Non-2D version of my admin account gives me no taskbar options like mail, wifi, power options, etc. Only the options of "File, Edit, View, Go, Bookmarks, Help"

---

### Post by foureyesboy on 2011-09-19
Well, you do not have /var or /usr separated, they all go to root (/).  So any addition packages you add will take up root.  And IMHO, 8 GB is a bit too small for root, unless you don't add any additional packages or software at all after installation.

Of course it depends on usage (like if you run KVM, which has the VM stored under /var/lib by default), but my root is over 10 GB.  So I guess the ultimate solution for you is to use gparted to shrink your /home a bit and give the space to root.  Remember to backup beforehand.

---

### Post by JKyleOKC on 2011-09-19
> **hardisty said:**
> I uninstalled a program, which freed up roughly 120mb, but now every startup gets a new notification with an ever shrinking number.Take a close look at your /var/log directory, preferably after each startup. Each time you start the system, the "syslog" file will get quite a bit of information added to it, as will a number of other log files. Unless your "logrotate" configuration keeps this data trimmed down it can eat space in a hurry. That's what's meant by a "runaway log" situation.

It's best to keep several days' worth of log data, possibly up to a month's worth, to help trace things back whenever anything goes wrong. However the *nix-based systems were never meant to be shut down and restarted on a daily basis. Many folk leave them powered up for months on end; the machine I'm using to post this was last booted just a few minutes less than 18 days ago. The only reason I restarted it then was that a security update made the reboot necessary.

---

### Post by mcduck on 2011-09-19
Was the home partition created during install or did you set it up manually afterwards?

...just thinking, because the difference between df and du outputs is strange, and the only reason I can think of that would cause such thing is mounting something to a directory which already contains data. In that case the old data would still exist on the drive, taking space and counting as used in df, while du wouldn't see it and would count the mounted filesystem instead.

(for example if you had 3GB of data on your home directory, and then you created a new partition and mounted it as /home, the 3GB of files would still exist but wouldn't show anywhere as long as the partition is mounted)

---

### Post by WorMzy on 2011-09-19
> **mcduck said:**
> Was the home partition created during install or did you set it up manually afterwards?

...just thinking, because the difference between df and du outputs is strange, and the only reason I can think of that would cause such thing is mounting something to a directory which already contains data. In that case the old data would still exist on the drive, taking space and counting as used in df, while du wouldn't see it and would count the mounted filesystem instead.

(for example if you had 3GB of data on your home directory, and then you created a new partition and mounted it as /home, the 3GB of files would still exist but wouldn't show anywhere as long as the partition is mounted)

I think you might be on to something there. It'd certainly explain the discrepancy.

In that case, I think the easiest thing to do would be to reboot into a LiveCD/USB, mount the root partition, and then delete the contents of the "old" /home folder (but leave the folder itself)

e.g.
```
sudo rm -r /media/Ubuntu/home/*
```

Obviously make sure that you don't want to keep the old data before you delete it.

---

### Post by hardisty on 2011-09-19
> **mcduck said:**
> Was the home partition created during install or did you set it up manually afterwards?

...just thinking, because the difference between df and du outputs is strange, and the only reason I can think of that would cause such thing is mounting something to a directory which already contains data. In that case the old data would still exist on the drive, taking space and counting as used in df, while du wouldn't see it and would count the mounted filesystem instead.

(for example if you had 3GB of data on your home directory, and then you created a new partition and mounted it as /home, the 3GB of files would still exist but wouldn't show anywhere as long as the partition is mounted)

I actually did set up /home after, but I had to do a full reinstall, though I think it kept some stuff

---

### Post by mcduck on 2011-09-19
Then you might want to check if there are any files left on the /home. Like WorMzy suggested, booting with a live-CD would be an easy way to check the contents of /home directory of your Linux root partition while the separate home partition isn't mounted.

---

### Post by hardisty on 2011-09-19
> **JKyleOKC said:**
> Take a close look at your /var/log directory, preferably after each startup. Each time you start the system, the "syslog" file will get quite a bit of information added to it, as will a number of other log files. Unless your "logrotate" configuration keeps this data trimmed down it can eat space in a hurry. That's what's meant by a "runaway log" situation.

It's best to keep several days' worth of log data, possibly up to a month's worth, to help trace things back whenever anything goes wrong. However the *nix-based systems were never meant to be shut down and restarted on a daily basis. Many folk leave them powered up for months on end; the machine I'm using to post this was last booted just a few minutes less than 18 days ago. The only reason I restarted it then was that a security update made the reboot necessary.

you're definitely onto something here. The folder keeps growing in size. I'll try some googling.

---

### Post by hardisty on 2011-09-19
I ran "sudo du -x --max-depth=1 /var |sort -n", took a screenshot, waited, rebooted, and did it again. 

/var/log went from 57524 to 57836
/var/lib went from 147408 to 147420

---

### Post by hardisty on 2011-09-19
This is where I would welcome advice.

I ran "ls -x -o |sort -n" (I'm sure there's a better way to do that, but I'm still learning)

and got > drwx------ 2 speech-dispatcher    4096 2011-06-05 22:29 speech-dispatcher 
drwxr-xr-x 2 root                 4096 2011-07-19 10:51 unattended-upgrades 
drwxr-xr-x 2 root                 4096 2011-08-11 13:57 samba 
drwxr-xr-x 2 root                 4096 2011-08-25 12:02 dist-upgrade 
drwxr-xr-x 2 root                 4096 2011-08-31 21:30 fsck 
drwxr-xr-x 2 root                 4096 2011-09-17 17:36 apt 
drwxr-xr-x 2 root                 4096 2011-09-17 18:06 ConsoleKit 
drwxr-xr-x 2 root                 4096 2011-09-17 18:06 lightdm 
drwxr-xr-x 2 root                 4096 2011-09-17 18:06 news 
drwxr-xr-x 2 root                 4096 2011-09-18 01:29 cups 
drwxr-xr-x 3 root                 4096 2011-09-17 18:05 installer 
-rw-r----- 1 root                14691 2011-09-19 17:17 dmesg.1.gz 
-rw-r----- 1 root                14701 2011-09-19 12:59 dmesg.3.gz 
-rw-r----- 1 root                14739 2011-09-19 11:51 dmesg.4.gz 
-rw-r----- 1 root                14796 2011-09-19 14:25 dmesg.2.gz 
-rw-r----- 1 root                   31 2011-08-31 21:30 boot 
-rw-r----- 1 root                 3384 2011-09-19 16:17 apport.log 
-rw-r----- 1 root                57324 2011-09-19 17:27 dmesg.0 
-rw-r----- 1 root                65659 2011-09-19 17:56 dmesg 
-rw-r----- 1 syslog                  0 2011-09-17 18:06 mail.err 
-rw-r----- 1 syslog                  0 2011-09-17 18:06 mail.log 
-rw-r----- 1 syslog                  0 2011-09-17 18:06 ufw.log 
-rw-r----- 1 syslog             122020 2011-09-18 01:16 kern.log.1 
-rw-r----- 1 syslog             124199 2011-09-19 17:59 auth.log 
-rw-r----- 1 syslog             158212 2011-09-18 01:20 syslog.1 
-rw-r----- 1 syslog            2710135 2011-09-19 17:56 kern.log 
-rw-r----- 1 syslog            3461930 2011-09-19 18:02 syslog 
-rw-r----- 1 syslog               8678 2011-09-18 01:17 auth.log.1 
-rw-r--r-- 1 root                    0 2011-09-17 18:05 pycentral.log 
-rw-r--r-- 1 root                    0 2011-09-18 01:29 jockey.log 
-rw-r--r-- 1 root              1318498 2011-09-18 20:55 dpkg.log 
-rw-r--r-- 1 root               134599 2011-09-19 17:56 pm-powersave.log 
-rw-r--r-- 1 root                24024 2011-09-19 11:20 faillog 
-rw-r--r-- 1 root                 2483 2011-09-18 20:01 fontconfig.log 
-rw-r--r-- 1 root               292497 2011-09-19 17:56 udev 
-rw-r--r-- 1 root                31363 2011-09-19 17:56 Xorg.0.log 
-rw-r--r-- 1 root                32173 2011-09-19 17:55 Xorg.0.log.old 
-rw-r--r-- 1 root                32975 2011-09-17 18:05 alternatives.log 
-rw-r--r-- 1 root                41158 2011-09-18 01:29 jockey.log.1 
-rw-r--r-- 1 root                  450 2011-09-19 17:56 boot.log 
-rw-r--r-- 1 root                48583 2011-08-31 21:31 bootstrap.log 
-rw-r--r-- 1 root                70064 2011-09-19 15:54 pm-suspend.log 
-rw-rw---- 1 root                  384 2011-09-19 09:13 btmp 
-rw-rw-r-- 1 root               155904 2011-09-19 17:57 wtmp 
-rw-rw-r-- 1 root               292292 2011-09-19 11:20 lastlog 

then rebooted and ran again to get

> drwx------ 2 speech-dispatcher    4096 2011-06-05 22:29 speech-dispatcher
drwxr-xr-x 2 root                 4096 2011-07-19 10:51 unattended-upgrades
drwxr-xr-x 2 root                 4096 2011-08-11 13:57 samba
drwxr-xr-x 2 root                 4096 2011-08-25 12:02 dist-upgrade
drwxr-xr-x 2 root                 4096 2011-08-31 21:30 fsck
drwxr-xr-x 2 root                 4096 2011-09-17 17:36 apt
drwxr-xr-x 2 root                 4096 2011-09-17 18:06 ConsoleKit
drwxr-xr-x 2 root                 4096 2011-09-17 18:06 lightdm
drwxr-xr-x 2 root                 4096 2011-09-17 18:06 news
drwxr-xr-x 2 root                 4096 2011-09-18 01:29 cups
drwxr-xr-x 3 root                 4096 2011-09-17 18:05 installer
-rw-r----- 1 root                14691 2011-09-19 17:17 dmesg.2.gz
-rw-r----- 1 root                14701 2011-09-19 12:59 dmesg.4.gz
-rw-r----- 1 root                14768 2011-09-19 17:27 dmesg.1.gz
-rw-r----- 1 root                14796 2011-09-19 14:25 dmesg.3.gz
-rw-r----- 1 root                   31 2011-08-31 21:30 boot
-rw-r----- 1 root                 3695 2011-09-19 18:06 apport.log
-rw-r----- 1 root                57415 2011-09-19 18:07 dmesg
-rw-r----- 1 root                65659 2011-09-19 17:56 dmesg.0
-rw-r----- 1 syslog                  0 2011-09-17 18:06 mail.err
-rw-r----- 1 syslog                  0 2011-09-17 18:06 mail.log
-rw-r----- 1 syslog                  0 2011-09-17 18:06 ufw.log
-rw-r----- 1 syslog             122020 2011-09-18 01:16 kern.log.1
-rw-r----- 1 syslog             127167 2011-09-19 18:08 auth.log
-rw-r----- 1 syslog             158212 2011-09-18 01:20 syslog.1
-rw-r----- 1 syslog            2817609 2011-09-19 18:07 kern.log
-rw-r----- 1 syslog            3593036 2011-09-19 18:08 syslog
-rw-r----- 1 syslog               8678 2011-09-18 01:17 auth.log.1
-rw-r--r-- 1 root                    0 2011-09-17 18:05 pycentral.log
-rw-r--r-- 1 root                    0 2011-09-18 01:29 jockey.log
-rw-r--r-- 1 root              1318498 2011-09-18 20:55 dpkg.log
-rw-r--r-- 1 root               138794 2011-09-19 18:07 pm-powersave.log
-rw-r--r-- 1 root                24024 2011-09-19 11:20 faillog
-rw-r--r-- 1 root                 2483 2011-09-18 20:01 fontconfig.log
-rw-r--r-- 1 root               289749 2011-09-19 18:07 udev
-rw-r--r-- 1 root                31465 2011-09-19 18:08 Xorg.0.log
-rw-r--r-- 1 root                32275 2011-09-19 18:06 Xorg.0.log.old
-rw-r--r-- 1 root                32975 2011-09-17 18:05 alternatives.log
-rw-r--r-- 1 root                41158 2011-09-18 01:29 jockey.log.1
-rw-r--r-- 1 root                48583 2011-08-31 21:31 bootstrap.log
-rw-r--r-- 1 root                70064 2011-09-19 15:54 pm-suspend.log
-rw-r--r-- 1 root                  725 2011-09-19 18:07 boot.log
-rw-rw---- 1 root                  384 2011-09-19 09:13 btmp
-rw-rw-r-- 1 root               162816 2011-09-19 18:08 wtmp
-rw-rw-r-- 1 root               292292 2011-09-19 11:20 lastlog


---

### Post by WorMzy on 2011-09-19
That's relatively normal. An couple of extra lines in a couple of log files would easily amount to 312 bytes (78 characters). What you need to worry about is when a log files starts taking up hundreds of *megabytes*.

I really think that you should investigate this /home theory.

---

### Post by hardisty on 2011-09-19
> **WorMzy said:**
> That's relatively normal. An couple of extra lines in a couple of log files would easily amount to 312 bytes (78 characters). What you need to worry about is when a log files starts taking up hundreds of *megabytes*.

I really think that you should investigate this /home theory.

I am going to, but the part that is growing is costing me about 100mb a day. I don't want that to snowball.

---

### Post by JKyleOKC on 2011-09-19
> **hardisty said:**
> I am going to, but the part that is growing is costing me about 100mb a day. I don't want that to snowball.In your /var/log directory, try "ls -l syslog*" which should give you several lines of output. All but the most recent will have a number as part of the file name. What is the highest number you see? Any listed file with a number greater than 7 can easily be deleted to get more space. If everything else is going well, you could get by with only the most recent 4 or 5 such files.

Here's what happens: Each time "logrotate" does its thing with syslog, the highest-numbered of these files gets deleted. Then the rest are renamed, with numbers one greater than they had before. The current unnumbered file gets renamed to "syslog.1" and a new, empty, "syslog" file is created.

Similar things happen for each of the log files. If your situation gets critical, you could get rid of ALL of the numbered log files to make enough disk space available to keep going, but you would lose the detailed history that they provide. The default settings for "logrotate" usually keep the logs pretty much under control, but your log directory is twice as large as mine and that's got me suspicious that something is writing more than it needs to into that area...

EDIT: I agree with WorMzy that you should investigate the /home directory that may still be in the "/" filesystem. Your 3.5-GB discrepancy is far too large to be accounted for by /var/log. My suggestions here are simply to help you keep the situation under control so that you don't run totally out of disk space.

---

