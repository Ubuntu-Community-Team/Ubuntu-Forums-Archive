---
title: "Low Disk Space error"
date: 2010-08-26
forum: General Help
---

### Post by Crazy K on 2010-08-26
So I recently got an error message about there being low disk space. Well I checked to make sure it was true. Went to Computer and right clicked on "File System" and clicked properties. It said I had 0 bytes. I restarted and got the same Low Disk Space error, this time saying I have 258.5MB of space left. So, what could the problem be? I remember having 11GB of space left. Could this be a problem with my HD since it's pretty old? Well not too old, I think I've had it since like 2003. Help!

If this is in the wrong area, than please do move it to the right location. Oh and here's a pic of what I mean: 

[[IMG]http://imgur.com/mpHqml.jpg[/IMG]](http://imgur.com/mpHqm.jpg)

I should add, that I'm not having any problems surfing the web or anything. It's not going slow at all. 

Oh, and I installed a deb. file for google talk, could that be messing with my computer?

I just noticed that when I check the file system, the free space is always different. I just checked a second ago and it's at 248MB or so. So yeah, I have no idea what's wrong.

---

### Post by sikander3786 on 2010-08-26
Go to Applications >>> Accessories >>> Disk Usage Analyzer and see how much actual space you have and tell if the message is correct or a bug?

---

### Post by Crazy K on 2010-08-26
I went to Disk Usage Anaylzer and this is what came up immediately.
[[IMG]http://imgur.com/p6sJ1l.jpg[/IMG]](http://imgur.com/p6sJ1.png)
It seems to list my External HD (500GB) but not my main HD (40GB) 

I clicked on "Scan File System" so I'll post what comes up after the scan is done. 

Should I un-plug my External HD to do this?

Actually, yeah I'm going to do the scan with my ex HD disconnected. It's going slow since it seems to scan my ex hd first.

---

### Post by Crazy K on 2010-08-26
Sorry about the double post. 

Anyways disconnected my ex hd and here's what I got: 

[[IMG]http://imgur.com/RkcUcl.jpg[/IMG]](http://imgur.com/RkcUc.png)

So it seems like it's legit, and not an error. I already used BleachIt to free up some space. Which got me back 1GB or so and I also deleted programs I'm not using anymore. But I still don't see how so much space is being used. My brother has his music on the main HD, but I doubt it's close to even 1 or 2GB. At the moment I have 2GB or so of space. From the looks of it, I should have 4GB or so. 

I'm currently scanning the file system, but it's taking a while. Is that normal?

Scan is done, here's what I got:
[[IMG]http://imgur.com/vYjH9l.jpg[/IMG]](http://imgur.com/vYjH9.png)

Anyways, what should I do?

---

### Post by -kg- on 2010-08-26
Something that concerns me is the size of your "/var" directory.  I've run a similar scan on my computer, and my "/var" directory is sitting at approximately 547 MB.  Yours is 12 GB!

The following is a list of my /var directory:

> ~$ ls /var
backups  cache  crash  games  lib  local  lock  log  mail  opt  run  spool  tmp

As you can see, you have various subdirectories, including ones for temporary files, cache, log files, backups, and the like.  Apparently, one or more of these are filling up fast with extraneous data.

I have something for you to try. Open whatever text editor you are comfortable with and copy and paste the following into it:

```
#!/bin/bash

sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
sudo apt-get autoremove

sudo -k
```

Save the file to your desktop as: Disk-Cleanup-Script.sh

I shouldn't need to tell you to check any code you get off of the Internet before you run it.  See the "Malicious Commands" thread at the top of the forum.

Once you have saved the file, click on it and select "Run in terminal" from the window.  This will definitively clear out any unused or unneeded files and so forth from your system.

If that doesn't clean up sufficient space, you might want to see what you can eliminate as far as log files.  Many programs and software will append to (meaning "add to the bottom of") their associated log files.  Some of them will become quite large.  Sometimes, eliminating some of these will gain you quite a bit of space.

One thing I can tell you is your "/var" directory contains a massive amount of data, compared to mine.  That would be the first place I would make an attempt to pare down some files to make space on your hard drive.

<Edit>  I've just thought of something:

In order to find out which subdirectory in your "/var" directory is filled with massive amounts of data, you can launch Nautilus, navigate to your "/var" directory, and pull up "Properties" on each directory in "/var" to see how much data it contains.  Any directory that contains an inordinate amount of data needs to be looked at and cleaned, if such is possible.

<Edit2>  Looking at Disk Analyzer, you might be able to do the above using the "Scan Folder" option at the top.

---

### Post by Crazy K on 2010-08-26
I can't seem to get this part to work. 
> Once you have saved the file, click on it and select "Run in terminal" from the window. This will definitively clear out any unused or unneeded files and so forth from your system.

I can't seem to click on it. It wont bring up the prompt that gives you the option to run in the terminal or other options. Nothing comes up. I used Gedit text editor, if there's a better text editor, please do tell. 

Anyways I did what you said below and here are the folders that seem to be holding a lot of file space:

lib holds 293.7MB
log holds 11.4 GB (so that's the one)

The rest of the folders don't hold much at all. 

Also for each of those folders it says I need root access under the properties, so I'm guessing I'll have to sign into root if I need to do anything with these folders.

---

### Post by TwoEars on 2010-08-26
Stop. Whatever you do, do NOT delete anything inside your /var/log folder. This is a classic mistake people make - the log files are there for a reason, to go around deleting them before checking what they say would be insane.

Could you post the output of ```
sudo ls -la /var/log/
``` please?


Also, if you're having issues running the above script, open a terminal and run ```
cd $HOME/Desktop && ./Disk-Cleanup-Script.sh
```

---

### Post by Crazy K on 2010-08-26
Oh haha I had no plan to delete anything in the folder unless I was told to do so. 

But yeah here's what the output of what you said to do: 

```
total 11979164
drwxr-xr-x 21 root              root              4096 2010-08-26 19:18 .
drwxr-xr-x 15 root              root              4096 2008-04-22 14:07 ..
-rw-r-----  1 root              adm                  0 2010-05-02 11:11 acpid
-rw-r-----  1 root              adm                  0 2010-04-25 10:27 acpid.1
-rw-r-----  1 root              adm               1424 2009-12-20 13:32 acpid.5.gz
drwxr-xr-x  2 root              root              4096 2008-04-07 17:39 apparmor
drwxr-xr-x  2 root              root              4096 2010-08-01 10:07 apt
-rw-r--r--  1 root              root                 0 2009-04-12 09:12 aptitude
-rw-r--r--  1 root              root               412 2009-04-11 16:49 aptitude.1.gz
-rw-r-----  1 syslog            adm              45939 2010-08-26 20:48 auth.log
-rw-r-----  1 syslog            adm              60368 2010-08-22 01:31 auth.log.1
-rw-r-----  1 syslog            adm               8990 2010-08-15 08:38 auth.log.2.gz
-rw-r-----  1 syslog            adm               7521 2010-08-08 03:49 auth.log.3.gz
-rw-r-----  1 syslog            adm               6397 2010-08-01 09:55 auth.log.4.gz
drwxr-xr-x  2 root              root              4096 2008-04-08 09:46 bittorrent
-rw-r-----  1 root              adm                 31 2008-04-22 13:49 boot
-rw-r--r--  1 root              root             15923 2010-08-26 19:18 boot.log
-rw-r--r--  1 root              root             40690 2008-04-22 13:49 bootstrap.log
-rw-rw----  1 root              utmp                 0 2010-08-01 10:08 btmp
-rw-rw----  1 root              utmp                20 2010-07-01 09:19 btmp.1.gz
drwxr-xr-x  2 clamav            clamav            4096 2010-08-22 01:46 clamav
drwxr-xr-x  2 root              root              4096 2010-08-01 10:07 ConsoleKit
drwxr-xr-x  2 root              lpadmin           4096 2010-08-26 07:57 cups
-rw-r-----  1 syslog            adm             260369 2010-08-26 19:25 daemon.log
-rw-r-----  1 syslog            adm             282529 2010-08-22 01:35 daemon.log.1
-rw-r-----  1 syslog            adm              21900 2010-08-15 08:39 daemon.log.2.gz
-rw-r-----  1 syslog            adm              18503 2010-08-08 03:54 daemon.log.3.gz
-rw-r-----  1 syslog            adm              13785 2010-08-01 10:00 daemon.log.4.gz
-rw-r-----  1 syslog            adm             154505 2010-08-26 19:19 debug
-rw-r-----  1 syslog            adm             169922 2010-08-22 01:29 debug.1
-rw-r-----  1 syslog            adm              17007 2010-08-15 08:34 debug.2.gz
-rw-r-----  1 syslog            adm              12089 2010-08-08 03:47 debug.3.gz
-rw-r-----  1 syslog            adm               8805 2010-08-01 09:55 debug.4.gz
drwxr-xr-x  3 root              root              4096 2010-05-05 20:50 dist-upgrade
-rw-r-----  1 root              adm              31469 2010-08-26 19:18 dmesg
-rw-r-----  1 root              adm              31468 2010-08-26 15:05 dmesg.0
-rw-r-----  1 root              adm               9939 2010-08-26 14:17 dmesg.1.gz
-rw-r-----  1 root              adm              10216 2010-08-26 12:12 dmesg.2.gz
-rw-r-----  1 root              adm              10160 2010-08-26 07:51 dmesg.3.gz
-rw-r-----  1 root              adm              10104 2010-08-25 15:38 dmesg.4.gz
-rw-r--r--  1 root              root            187058 2010-08-26 19:36 dpkg.log
-rw-r--r--  1 root              root            184200 2010-07-27 09:08 dpkg.log.1
-rw-r-----  1 root              adm               1340 2009-11-29 17:39 dpkg.log.10.gz
-rw-r-----  1 root              adm               2581 2009-10-31 07:33 dpkg.log.11.gz
-rw-r-----  1 root              adm               4339 2009-10-02 09:29 dpkg.log.12.gz
-rw-r--r--  1 root              root             18821 2010-06-30 20:50 dpkg.log.2.gz
-rw-r--r--  1 root              root            201434 2010-05-31 18:24 dpkg.log.3.gz
-rw-r-----  1 root              adm               3726 2010-04-30 08:36 dpkg.log.4.gz
-rw-r-----  1 root              adm               2826 2010-03-26 20:20 dpkg.log.5.gz
-rw-r-----  1 root              adm               1797 2010-03-11 11:16 dpkg.log.6.gz
-rw-r-----  1 root              adm               3462 2010-02-27 13:57 dpkg.log.7.gz
-rw-r-----  1 root              adm                973 2010-02-05 07:01 dpkg.log.8.gz
-rw-r-----  1 root              adm               5902 2010-01-30 20:06 dpkg.log.9.gz
drwxr-s---  2 Debian-exim       adm               4096 2010-08-26 07:57 exim4
-rw-r--r--  1 root              root             24048 2010-05-05 20:02 faillog
-rw-r--r--  1 root              root              3138 2010-07-22 16:24 fontconfig.log
drwxr-xr-x  2 root              root              4096 2008-04-22 13:49 fsck
drwxrwx--T  2 root              gdm               4096 2010-08-26 19:18 gdm
drwxr-xr-x  2 root              root              4096 2010-05-05 19:36 installer
-rw-r-----  1 syslog            adm         4066156177 2010-08-26 20:46 kern.log
-rw-r-----  1 syslog            adm           17436811 2010-08-22 01:43 kern.log.1
-rw-r-----  1 syslog            adm             283414 2010-08-15 08:33 kern.log.2.gz
-rw-r-----  1 syslog            adm            5089215 2010-08-08 04:01 kern.log.3.gz
-rw-r-----  1 syslog            adm            7788391 2010-08-01 09:54 kern.log.4.gz
-rw-r-----  1 syslog            adm              42022 2009-11-18 08:21 kern.log.6.gz
-rw-r-----  1 syslog            adm             234800 2009-11-17 07:43 kern.log.7.gz
drwxr-xr-x  2 landscape         root              4096 2010-04-23 08:58 landscape
drwxrwsr-x  2 lastfm            lastfm            4096 2010-08-22 01:47 lastfm
drwxr-xr-x  2 lastfmproxy       lastfmproxy       4096 2007-05-02 17:46 lastfmproxy
-rw-rw-r--  1 root              utmp            292584 2010-05-05 20:02 lastlog
-rw-r-----  1 syslog            adm                  0 2010-07-23 08:52 lpr.log
-rw-r-----  1 syslog            adm                146 2010-07-23 08:22 lpr.log.1
-rw-r-----  1 syslog            adm               1170 2010-07-14 17:24 lpr.log.2.gz
-rw-r-----  1 syslog            adm                165 2010-06-29 16:57 lpr.log.3.gz
-rw-r-----  1 syslog            adm                235 2010-06-27 00:44 lpr.log.4.gz
-rw-r-----  1 syslog            adm                  0 2008-04-22 13:49 mail.err
-rw-r-----  1 syslog            adm                  0 2008-04-22 13:49 mail.info
-rw-r-----  1 syslog            adm                  0 2008-04-22 13:49 mail.log
-rw-r-----  1 syslog            adm                  0 2008-04-22 13:49 mail.warn
-rw-r-----  1 syslog            adm         4066024953 2010-08-26 20:48 messages
-rw-r-----  1 syslog            adm           17298888 2010-08-22 01:47 messages.1
-rw-r-----  1 syslog            adm             262889 2010-08-15 08:45 messages.2.gz
-rw-r-----  1 syslog            adm            5074239 2010-08-08 04:01 messages.3.gz
-rw-r-----  1 syslog            adm            7769680 2010-08-01 10:08 messages.4.gz
-rw-r-----  1 syslog            adm             260666 2009-11-11 11:43 messages.6.gz
-rw-r-----  1 syslog            adm             145303 2009-10-31 07:31 messages.7.gz
drwxr-sr-x  2 news              news              4096 2008-06-27 22:36 news
drwxr-xr-x  2 ntp               ntp               4096 2008-03-07 15:24 ntpstats
-rw-r--r--  1 root              root             39353 2010-08-26 19:19 pm-powersave.log
-rw-r--r--  1 root              root             38364 2010-08-01 09:54 pm-powersave.log.1
-rw-r--r--  1 root              root               510 2010-07-01 08:53 pm-powersave.log.2.gz
-rw-r--r--  1 root              root               645 2010-06-01 08:47 pm-powersave.log.3.gz
-rw-r--r--  1 root              root                 0 2010-06-01 09:26 pm-suspend.log
-rw-r--r--  1 root              root              2434 2009-06-01 07:57 pm-suspend.log.1
-rw-r--r--  1 root              root               975 2010-05-05 20:50 pycentral.log
drwxr-x---  3 root              adm               4096 2010-08-22 01:47 samba
-rw-r--r--  1 root              root                 0 2010-08-22 01:47 scrollkeeper.log
-rw-r--r--  1 root              root                 0 2010-08-15 08:45 scrollkeeper.log.1
-rw-r--r--  1 root              root                 0 2010-08-08 04:01 scrollkeeper.log.2
drwxr-xr-x  2 speech-dispatcher root              4096 2010-04-15 09:04 speech-dispatcher
-rw-r-----  1 syslog            adm         4045028968 2010-08-26 20:48 syslog
-rw-r-----  1 syslog            adm           11033075 2010-08-26 07:57 syslog.1
-rw-r-----  1 syslog            adm             643767 2010-08-25 10:05 syslog.2.gz
-rw-r-----  1 syslog            adm              73203 2010-08-22 01:43 syslog.3.gz
-rw-r-----  1 syslog            adm             718999 2010-08-21 01:03 syslog.4.gz
-rw-r-----  1 syslog            adm              41648 2010-08-19 09:24 syslog.5.gz
-rw-r-----  1 syslog            adm              23669 2010-08-18 10:21 syslog.6.gz
-rw-r-----  1 syslog            adm              42229 2010-08-17 09:22 syslog.7.gz
-rw-r--r--  1 root              root            153863 2010-08-26 19:18 udev
-rw-r-----  1 syslog            adm                  0 2010-05-05 19:31 ufw.log
drwxr-xr-x  2 root              root              4096 2010-08-25 10:10 unattended-upgrades
-rw-r-----  1 syslog            adm              40984 2010-08-26 20:48 user.log
-rw-r-----  1 syslog            adm              57241 2010-08-22 01:28 user.log.1
-rw-r-----  1 syslog            adm               3113 2010-08-15 08:33 user.log.2.gz
-rw-r-----  1 syslog            adm               2282 2010-08-08 03:46 user.log.3.gz
-rw-r-----  1 syslog            adm               1566 2010-08-01 09:54 user.log.4.gz
-rw-rw-r--  1 root              utmp            306432 2010-08-26 20:48 wtmp
-rw-rw-r--  1 root              utmp              7965 2010-08-01 09:54 wtmp.1.gz
-rw-r--r--  1 root              root               740 2010-05-05 19:36 wvdialconf.log
-rw-r--r--  1 root              root             26698 2010-08-26 19:24 Xorg.0.log
-rw-r--r--  1 root              root             26858 2010-08-26 19:17 Xorg.0.log.old
-rw-r--r--  1 root              root             21632 2010-05-05 21:37 Xorg.1.log
-rw-r--r--  1 root              root              4761 2010-05-05 20:53 Xorg.1.log.old
-rw-r--r--  1 root              root             48858 2008-07-05 14:59 Xorg.20.log
-rw-r--r--  1 root              root              4761 2010-05-05 20:53 Xorg.2.log
-rw-r--r--  1 root              root              4761 2010-05-05 20:53 Xorg.3.log
-rw-r--r--  1 root              root              4761 2010-05-05 20:53 Xorg.4.log
-rw-r--r--  1 root              root              4761 2010-05-05 20:53 Xorg.5.log
-rw-r--r--  1 root              root             47672 2008-10-18 21:13 Xorg.9.log
-rw-r--r--  1 root              root             21551 2010-05-05 21:37 Xorg.failsafe.log
```

I'm hoping this is safe to post. Sorry, just a bit paranoid.

Also, just tried the command for the Disk-Cleanup-Skript.sh and it said permission denied. So I'm guessing I need to be in root or admin mode to do so.

Just tried again as root (typed: su to sign into root) and this time it says No such file or directory.

---

### Post by Miljet on 2010-08-26
The reason that the script file will not run is that it has to be made executable!
Instead of fooling with a script, just run each of the commands in a terminal, one at a time. So much simpler.

---

### Post by linux18 on 2010-08-26
bleachbit is easier
sudo apt-get bleachbit
then get deborphan and localepurge

---

### Post by Crazy K on 2010-08-26
> **linux18 said:**
> bleachbit is easier
sudo apt-get bleachbit
then get deborphan and localepurge

Already have BleachBit, I'll also install the other two soon.

---

### Post by Crazy K on 2010-08-26
> **linux18 said:**
> bleachbit is easier
sudo apt-get bleachbit
then get deborphan and localepurge

Already have BleachBit, I'll also install the other two soon.


> **Miljet said:**
> The reason that the script file will not run is that it has to be made executable!
Instead of fooling with a script, just run each of the commands in a terminal, one at a time. So much simpler.

I should of thought of that. :( Oh well, doing it now, so hopefully it works. 

I'll update you guys if this works out. 

Ok, so I did this one by one:
```
#!/bin/bash

sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
sudo apt-get autoremove

sudo -k
```

And it did free up some space. I now have 3GB of space left on my computer. So, what should I do next?

Anyways, installed localepurge and deborphan. Going to use BleachBit again though.

---

### Post by linux18 on 2010-08-26
to use deborphan:
sudo apt-get purge $(deborphan)

run 3-4 times for best effect

---

### Post by Crazy K on 2010-08-26
Alright, doing that now. 

Also, is it normal for BleachBit to slow the computer down? Also it seems to take up file space while it's working. Is that normal? After I exit BleachBit before it deletes all the files, the file space goes back to normal, which is now 3.4GB, but when I run BleachBit and check "Free Disck Space" under the system area, it says "This option is very slow". So will that cause my space to fluctuate or in this case, go down?

---

### Post by linux18 on 2010-08-27
when bleachbit scans for files in the system area, it is very slow and won't save much space, I suggest only using the default options every once in a while.

---

### Post by Crazy K on 2010-08-27
Ok, so I had 3.5GB, but now it's at 679 MB or so. Was just 800MB or so not too long ago. What could be doing this?

It seems as if something is being downloaded in the background. File space keeps going down. Now it's around 300MB.

Now I have 81MB or space left and it keeps going down. 

Anyways, did a scan of the var folder and here's what I got:
[[IMG]http://imgur.com/Pn1FZl.jpg[/IMG]](http://imgur.com/Pn1FZ.png)

Did a scan of just the log folder as well and here's what I got:
Actually can't save the image because there's no space. **** this is annoying!

I just have 84 KB now. Can anyone guess what could be going wrong?

---

### Post by linux18 on 2010-08-27
post the output of:

du -hs $(find /var/log -print -type f) | grep "M"  
and 
du -hs $(find /var/log -print -type f) | grep "G"

---

### Post by Crazy K on 2010-08-27
First one I got this:
```
find: `/var/log/gdm': Permission denied
find: `/var/log/samba/cores': Permission denied
du: cannot read directory `/var/log/gdm': Permission denied
du: cannot read directory `/var/log/samba/cores': Permission denied
17M	/var/log/messages.1
7.5M	/var/log/kern.log.4.gz
7.5M	/var/log/messages.4.gz
2.4M	/var/log/dist-upgrade
1.3M	/var/log/dist-upgrade/apt-term.log
4.9M	/var/log/kern.log.3.gz
17M	/var/log/kern.log.1
du: cannot read directory `/var/log/gdm': Permission denied
du: cannot read directory `/var/log/samba/cores': Permission denied
du: cannot read directory `/var/log/samba/cores': Permission denied
4.9M	/var/log/messages.3.gz

```
Second one I got this:
```
find: `/var/log/gdm': Permission denied
find: `/var/log/samba/cores': Permission denied
du: cannot read directory `/var/log/gdm': Permission denied
du: cannot read directory `/var/log/samba/cores': Permission denied
du: cannot read directory `/var/log/gdm': Permission denied
du: cannot read directory `/var/log/samba/cores': Permission denied
du: cannot read directory `/var/log/samba/cores': Permission denied
15G	/var/log
1.2G	/var/log/syslog
5.0G	/var/log/messages
3.8G	/var/log/syslog.1
5.0G	/var/log/kern.log

```

Anyways before I did both of those I went through the var/log folder and checked to see which files were the biggers and here's what I got. Seems to be correct with the second script you told me to run.

kern.log - 5GB
kern.log.1 - 16.6MB (posting it because of the big difference)
messages - 5GB
messages.1 - 16.5MB (similar to what I said above)
syslog - 1.2GB
syslog.1 - 3.2GB

total these take up are: 14.4GB (not counting the two 16MB files)

---

### Post by linux18 on 2010-08-27
> **Crazy K said:**
> First one I got this:
```
find: `/var/log/gdm': Permission denied
find: `/var/log/samba/cores': Permission denied
du: cannot read directory `/var/log/gdm': Permission denied
du: cannot read directory `/var/log/samba/cores': Permission denied
17M	/var/log/messages.1
7.5M	/var/log/kern.log.4.gz
7.5M	/var/log/messages.4.gz
2.4M	/var/log/dist-upgrade
1.3M	/var/log/dist-upgrade/apt-term.log
4.9M	/var/log/kern.log.3.gz
17M	/var/log/kern.log.1
du: cannot read directory `/var/log/gdm': Permission denied
du: cannot read directory `/var/log/samba/cores': Permission denied
du: cannot read directory `/var/log/samba/cores': Permission denied
4.9M	/var/log/messages.3.gz

```
Second one I got this:
```
find: `/var/log/gdm': Permission denied
find: `/var/log/samba/cores': Permission denied
du: cannot read directory `/var/log/gdm': Permission denied
du: cannot read directory `/var/log/samba/cores': Permission denied
du: cannot read directory `/var/log/gdm': Permission denied
du: cannot read directory `/var/log/samba/cores': Permission denied
du: cannot read directory `/var/log/samba/cores': Permission denied
15G	/var/log
1.2G	/var/log/syslog
5.0G	/var/log/messages
3.8G	/var/log/syslog.1
5.0G	/var/log/kern.log

```

Anyways before I did both of those I went through the var/log folder and checked to see which files were the biggers and here's what I got. Seems to be correct with the second script you told me to run.

kern.log - 5GB
kern.log.1 - 16.6MB (posting it because of the big difference)
messages - 5GB
messages.1 - 16.5MB (similar to what I said above)
syslog - 1.2GB
syslog.1 - 3.2GB

total these take up are: 14.4GB (not counting the two 16MB files)
post the output of: 

tail -c 4096 /var/log/kern.log 
tail -c 4096 /var/log/syslog
tail -c 4096 /var/log/messages

then:

 sudo rm /var/log/kern.log && sudo rm /var/log/syslog && sudo rm /var/log/messages

---

### Post by Crazy K on 2010-08-27
```
etfilter.nf_conntrack_acct=1 to enable it.
Aug 27 14:37:59 crazyk-desktop kernel: [   37.961397] type=1505 audit(1282934279.684:10):  operation="profile_load" pid=636 name="/usr/bin/evince"
Aug 27 14:37:59 crazyk-desktop kernel: [   37.981799] type=1505 audit(1282934279.704:11):  operation="profile_load" pid=636 name="/usr/bin/evince-previewer"
Aug 27 14:38:00 crazyk-desktop kernel: [   38.456929] eth2:  setting full-duplex.
Aug 27 14:38:00 crazyk-desktop kernel: [   38.883520] EMU10K1_Audigy 0000:00:12.0: PCI->APIC IRQ transform: INT A -> IRQ 18
Aug 27 14:38:00 crazyk-desktop kernel: [   38.889289] interrupt: PCI error
Aug 27 14:38:00 crazyk-desktop kernel: [   38.894695] AC'97 0 access is not valid [0x0], removing mixer.
Aug 27 14:38:00 crazyk-desktop kernel: [   38.898026] EMU10K1_Audigy: probe of 0000:00:12.0 failed with error -5
Aug 27 14:38:02 crazyk-desktop kernel: [   40.320899] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Aug 27 14:38:02 crazyk-desktop kernel: [   40.320912] apm: disabled - APM is not SMP safe.
Aug 27 14:38:03 crazyk-desktop kernel: [   41.416871] [drm] nouveau 0000:01:00.0: Allocating FIFO number 1
Aug 27 14:38:03 crazyk-desktop kernel: [   41.422348] [drm] nouveau 0000:01:00.0: nouveau_channel_alloc: initialised FIFO 1
Aug 27 14:38:10 crazyk-desktop kernel: [   48.868734] eth2: no IPv6 routers present
Aug 27 14:38:15 crazyk-desktop kernel: [   52.974713] ppdev: user-space parallel port driver
Aug 27 14:38:16 crazyk-desktop kernel: [   53.702826] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on vga encoder (output 0)
Aug 27 14:38:16 crazyk-desktop kernel: [   53.723004] [drm] nouveau 0000:01:00.0: Setting dpms mode 0 on vga encoder (output 0)
Aug 27 14:38:16 crazyk-desktop kernel: [   53.723018] [drm] nouveau 0000:01:00.0: Output VGA-1 is running on CRTC 0 using output A
Aug 27 14:38:16 crazyk-desktop kernel: [   53.941071] Inbound IN=eth2 OUT= MAC= SRC=192.168.0.100 DST=239.255.255.250 LEN=368 TOS=0x00 PREC=0x00 TTL=4 ID=0 DF PROTO=UDP SPT=40300 DPT=1900 LEN=348 
Aug 27 14:38:16 crazyk-desktop kernel: [   54.134573] Inbound IN=eth2 OUT= MAC= SRC=192.168.0.100 DST=239.255.255.250 LEN=377 TOS=0x00 PREC=0x00 TTL=4 ID=0 DF PROTO=UDP SPT=40300 DPT=1900 LEN=357 
Aug 27 14:38:16 crazyk-desktop kernel: [   54.237365] Inbound IN=eth2 OUT= MAC= SRC=192.168.0.100 DST=239.255.255.250 LEN=420 TOS=0x00 PREC=0x00 TTL=4 ID=0 DF PROTO=UDP SPT=40300 DPT=1900 LEN=400 
Aug 27 14:38:16 crazyk-desktop kernel: [   54.341706] Inbound IN=eth2 OUT= MAC= SRC=192.168.0.100 DST=239.255.255.250 LEN=434 TOS=0x00 PREC=0x00 TTL=4 ID=0 DF PROTO=UDP SPT=52712 DPT=1900 LEN=414 
Aug 27 14:38:17 crazyk-desktop kernel: [   54.445720] Inbound IN=eth2 OUT= MAC= SRC=192.168.0.100 DST=239.255.255.250 LEN=432 TOS=0x00 PREC=0x00 TTL=4 ID=0 DF PROTO=UDP SPT=46025 DPT=1900 LEN=412 
Aug 27 14:38:17 crazyk-desktop kernel: [   54.549896] Inbound IN=eth2 OUT= MAC= SRC=192.168.0.100 DST=239.255.255.250 LEN=448 TOS=0x00 PREC=0x00 TTL=4 ID=0 DF PROTO=UDP SPT=36640 DPT=1900 LEN=428 
Aug 27 14:38:17 crazyk-desktop kernel: [   54.655787] Inbound IN=eth2 OUT= MAC= SRC=192.168.0.100 DST=239.255.255.250 LEN=367 TOS=0x00 PREC=0x00 TTL=4 ID=0 DF PROTO=UDP SPT=52728 DPT=1900 LEN=347 
Aug 27 14:38:17 crazyk-desktop kernel: [   54.757925] Inbound IN=eth2 OUT= MAC= SRC=192.168.0.100 DST=239.255.255.250 LEN=376 TOS=0x00 PREC=0x00 TTL=4 ID=0 DF PROTO=UDP SPT=52728 DPT=1900 LEN=356 
Aug 27 14:38:17 crazyk-desktop kernel: [   54.861407] Inbound IN=eth2 OUT= MAC= SRC=192.168.0.100 DST=239.255.255.250 LEN=419 TOS=0x00 PREC=0x00 TTL=4 ID=0 DF PROTO=UDP SPT=52728 DPT=1900 LEN=399 
Aug 27 14:38:17 crazyk-desktop kernel: [   54.965843] Inbound IN=eth2 OUT= MAC= SRC=192.168.0.100 DST=239.255.255.250 LEN=433 TOS=0x00 PREC=0x00 TTL=4 ID=0 DF PROTO=UDP SPT=54501 DPT=1900 LEN=413 
Aug 27 14:38:17 crazyk-desktop kernel: [   55.173611] Inbound IN=eth2 OUT= MAC= SRC=192.168.0.100 DST=239.255.255.250 LEN=447 TOS=0x00 PREC=0x00 TTL=4 ID=0 DF PROTO=UDP SPT=42081 DPT=1900 LEN=427 
Aug 27 14:38:46 crazyk-desktop kernel: [   83.816882] lo: Disabled Privacy Extensions
```

```
549896] Inbound IN=eth2 OUT= MAC= SRC=192.168.0.100 DST=239.255.255.250 LEN=448 TOS=0x00 PREC=0x00 TTL=4 ID=0 DF PROTO=UDP SPT=36640 DPT=1900 LEN=428 
Aug 27 14:38:17 crazyk-desktop kernel: [   54.655787] Inbound IN=eth2 OUT= MAC= SRC=192.168.0.100 DST=239.255.255.250 LEN=367 TOS=0x00 PREC=0x00 TTL=4 ID=0 DF PROTO=UDP SPT=52728 DPT=1900 LEN=347 
Aug 27 14:38:17 crazyk-desktop anacron[1840]: Anacron 2.3 started on 2010-08-27
Aug 27 14:38:17 crazyk-desktop anacron[1840]: Normal exit (0 jobs run)
Aug 27 14:38:17 crazyk-desktop kernel: [   54.757925] Inbound IN=eth2 OUT= MAC= SRC=192.168.0.100 DST=239.255.255.250 LEN=376 TOS=0x00 PREC=0x00 TTL=4 ID=0 DF PROTO=UDP SPT=52728 DPT=1900 LEN=356 
Aug 27 14:38:17 crazyk-desktop gnome-session[1386]: WARNING: Could not launch application 'gnome-volume-manager.desktop': Unable to start application: Failed to execute child process "/usr/lib/gnome-volume-manager/gnome-volume-manager" (No such file or directory)
Aug 27 14:38:17 crazyk-desktop kernel: [   54.861407] Inbound IN=eth2 OUT= MAC= SRC=192.168.0.100 DST=239.255.255.250 LEN=419 TOS=0x00 PREC=0x00 TTL=4 ID=0 DF PROTO=UDP SPT=52728 DPT=1900 LEN=399 
Aug 27 14:38:17 crazyk-desktop kernel: [   54.965843] Inbound IN=eth2 OUT= MAC= SRC=192.168.0.100 DST=239.255.255.250 LEN=433 TOS=0x00 PREC=0x00 TTL=4 ID=0 DF PROTO=UDP SPT=54501 DPT=1900 LEN=413 
Aug 27 14:38:17 crazyk-desktop rtkit-daemon[1861]: Sucessfully called chroot.
Aug 27 14:38:17 crazyk-desktop rtkit-daemon[1861]: Sucessfully dropped privileges.
Aug 27 14:38:17 crazyk-desktop rtkit-daemon[1861]: Sucessfully limited resources.
Aug 27 14:38:17 crazyk-desktop rtkit-daemon[1861]: Running.
Aug 27 14:38:17 crazyk-desktop kernel: [   55.173611] Inbound IN=eth2 OUT= MAC= SRC=192.168.0.100 DST=239.255.255.250 LEN=447 TOS=0x00 PREC=0x00 TTL=4 ID=0 DF PROTO=UDP SPT=42081 DPT=1900 LEN=427 
Aug 27 14:38:17 crazyk-desktop rtkit-daemon[1861]: Watchdog thread running.
Aug 27 14:38:17 crazyk-desktop rtkit-daemon[1861]: Canary thread running.
Aug 27 14:38:18 crazyk-desktop polkitd[1877]: started daemon version 0.96 using authority implementation `local' version `0.96'
Aug 27 14:38:18 crazyk-desktop init: plymouth-stop pre-start process (1931) terminated with status 1
Aug 27 14:38:19 crazyk-desktop rtkit-daemon[1861]: Sucessfully made thread 1855 of process 1855 (n/a) owned by '1000' high priority at nice level -11.
Aug 27 14:38:19 crazyk-desktop rtkit-daemon[1861]: Supervising 1 threads of 1 processes of 1 users.
Aug 27 14:38:19 crazyk-desktop anacron[1963]: Anacron 2.3 started on 2010-08-27
Aug 27 14:38:19 crazyk-desktop anacron[1963]: Normal exit (0 jobs run)
Aug 27 14:38:19 crazyk-desktop rtkit-daemon[1861]: Sucessfully made thread 1969 of process 1969 (n/a) owned by '1000' high priority at nice level -11.
Aug 27 14:38:19 crazyk-desktop rtkit-daemon[1861]: Supervising 2 threads of 2 processes of 1 users.
Aug 27 14:38:19 crazyk-desktop pulseaudio[1969]: pid.c: Daemon already running.
Aug 27 14:38:20 crazyk-desktop pulseaudio[1970]: core-util.c: Home directory /etc/timidity not ours.
Aug 27 14:38:20 crazyk-desktop pulseaudio[1970]: lock-autospawn.c: Cannot access autospawn lock.
Aug 27 14:38:20 crazyk-desktop pulseaudio[1970]: main.c: Failed to acquire autospawn lock
Aug 27 14:38:21 crazyk-desktop rtkit-daemon[1861]: Sucessfully made thread 2003 of process 2003 (n/a) owned by '1000' high priority at nice level -11.
Aug 27 14:38:21 crazyk-desktop rtkit-daemon[1861]: Supervising 2 threads of 2 processes of 1 users.
Aug 27 14:38:21 crazyk-desktop pulseaudio[2003]: pid.c: Daemon already running.
Aug 27 14:38:25 crazyk-desktop pulseaudio[1855]: module-x11-xsmp.c: module-x11-xsmp may no be loaded twice.
Aug 27 14:38:25 crazyk-desktop pulseaudio[1855]: module.c: Failed to load  module "module-x11-xsmp" (argument: "display=:0.0 session_manager=local/crazyk-desktop:@/tmp/.ICE-unix/1386,unix/crazyk-desktop:/tmp/.ICE-unix/1386"): initialization failed.
Aug 27 14:38:46 crazyk-desktop kernel: [   83.816882] lo: Disabled Privacy Extensions
Aug 27 14:39:33 crazyk-desktop AptDaemon: INFO: Initializing daemon

```

```
op kernel: [   37.625670] nf_conntrack.acct=1 kernel parameter, acct=1 nf_conntrack module option or
Aug 27 14:37:59 crazyk-desktop kernel: [   37.625678] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
Aug 27 14:37:59 crazyk-desktop kernel: [   37.961397] type=1505 audit(1282934279.684:10):  operation="profile_load" pid=636 name="/usr/bin/evince"
Aug 27 14:37:59 crazyk-desktop kernel: [   37.981799] type=1505 audit(1282934279.704:11):  operation="profile_load" pid=636 name="/usr/bin/evince-previewer"
Aug 27 14:38:00 crazyk-desktop kernel: [   38.456929] eth2:  setting full-duplex.
Aug 27 14:38:00 crazyk-desktop kernel: [   38.883520] EMU10K1_Audigy 0000:00:12.0: PCI->APIC IRQ transform: INT A -> IRQ 18
Aug 27 14:38:00 crazyk-desktop kernel: [   38.898026] EMU10K1_Audigy: probe of 0000:00:12.0 failed with error -5
Aug 27 14:38:02 crazyk-desktop kernel: [   40.320899] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Aug 27 14:38:02 crazyk-desktop kernel: [   40.320912] apm: disabled - APM is not SMP safe.
Aug 27 14:38:03 crazyk-desktop kernel: [   41.416871] [drm] nouveau 0000:01:00.0: Allocating FIFO number 1
Aug 27 14:38:03 crazyk-desktop kernel: [   41.422348] [drm] nouveau 0000:01:00.0: nouveau_channel_alloc: initialised FIFO 1
Aug 27 14:38:15 crazyk-desktop kernel: [   52.974713] ppdev: user-space parallel port driver
Aug 27 14:38:16 crazyk-desktop kernel: [   53.702826] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on vga encoder (output 0)
Aug 27 14:38:16 crazyk-desktop kernel: [   53.723004] [drm] nouveau 0000:01:00.0: Setting dpms mode 0 on vga encoder (output 0)
Aug 27 14:38:16 crazyk-desktop kernel: [   53.723018] [drm] nouveau 0000:01:00.0: Output VGA-1 is running on CRTC 0 using output A
Aug 27 14:38:16 crazyk-desktop kernel: [   53.941071] Inbound IN=eth2 OUT= MAC= SRC=192.168.0.100 DST=239.255.255.250 LEN=368 TOS=0x00 PREC=0x00 TTL=4 ID=0 DF PROTO=UDP SPT=40300 DPT=1900 LEN=348 
Aug 27 14:38:16 crazyk-desktop kernel: [   54.134573] Inbound IN=eth2 OUT= MAC= SRC=192.168.0.100 DST=239.255.255.250 LEN=377 TOS=0x00 PREC=0x00 TTL=4 ID=0 DF PROTO=UDP SPT=40300 DPT=1900 LEN=357 
Aug 27 14:38:16 crazyk-desktop kernel: [   54.237365] Inbound IN=eth2 OUT= MAC= SRC=192.168.0.100 DST=239.255.255.250 LEN=420 TOS=0x00 PREC=0x00 TTL=4 ID=0 DF PROTO=UDP SPT=40300 DPT=1900 LEN=400 
Aug 27 14:38:16 crazyk-desktop kernel: [   54.341706] Inbound IN=eth2 OUT= MAC= SRC=192.168.0.100 DST=239.255.255.250 LEN=434 TOS=0x00 PREC=0x00 TTL=4 ID=0 DF PROTO=UDP SPT=52712 DPT=1900 LEN=414 
Aug 27 14:38:17 crazyk-desktop kernel: [   54.445720] Inbound IN=eth2 OUT= MAC= SRC=192.168.0.100 DST=239.255.255.250 LEN=432 TOS=0x00 PREC=0x00 TTL=4 ID=0 DF PROTO=UDP SPT=46025 DPT=1900 LEN=412 
Aug 27 14:38:17 crazyk-desktop kernel: [   54.549896] Inbound IN=eth2 OUT= MAC= SRC=192.168.0.100 DST=239.255.255.250 LEN=448 TOS=0x00 PREC=0x00 TTL=4 ID=0 DF PROTO=UDP SPT=36640 DPT=1900 LEN=428 
Aug 27 14:38:17 crazyk-desktop kernel: [   54.655787] Inbound IN=eth2 OUT= MAC= SRC=192.168.0.100 DST=239.255.255.250 LEN=367 TOS=0x00 PREC=0x00 TTL=4 ID=0 DF PROTO=UDP SPT=52728 DPT=1900 LEN=347 
Aug 27 14:38:17 crazyk-desktop kernel: [   54.757925] Inbound IN=eth2 OUT= MAC= SRC=192.168.0.100 DST=239.255.255.250 LEN=376 TOS=0x00 PREC=0x00 TTL=4 ID=0 DF PROTO=UDP SPT=52728 DPT=1900 LEN=356 
Aug 27 14:38:17 crazyk-desktop kernel: [   54.861407] Inbound IN=eth2 OUT= MAC= SRC=192.168.0.100 DST=239.255.255.250 LEN=419 TOS=0x00 PREC=0x00 TTL=4 ID=0 DF PROTO=UDP SPT=52728 DPT=1900 LEN=399 
Aug 27 14:38:17 crazyk-desktop kernel: [   54.965843] Inbound IN=eth2 OUT= MAC= SRC=192.168.0.100 DST=239.255.255.250 LEN=433 TOS=0x00 PREC=0x00 TTL=4 ID=0 DF PROTO=UDP SPT=54501 DPT=1900 LEN=413 
Aug 27 14:38:17 crazyk-desktop kernel: [   55.173611] Inbound IN=eth2 OUT= MAC= SRC=192.168.0.100 DST=239.255.255.250 LEN=447 TOS=0x00 PREC=0x00 TTL=4 ID=0 DF PROTO=UDP SPT=42081 DPT=1900 LEN=427 
Aug 27 14:38:20 crazyk-desktop pulseaudio[1970]: lock-autospawn.c: Cannot access autospawn lock.
Aug 27 14:38:46 crazyk-desktop kernel: [   83.816882] lo: Disabled Privacy Extensions

```

```
rm: cannot remove `/var/log/kern.log': No such file or directory

```

The last one, after putting my password in, didn't do anything. Put the command in again and I got that above.

---

### Post by linux18 on 2010-08-27
can you delete that last one through the file browser: 
gksudo nautilus

---

### Post by Crazy K on 2010-08-27
> **linux18 said:**
> can you delete that last one through the file browser: 
gksudo nautilus

Where would that be located?

---

### Post by linux18 on 2010-08-27
type gksudo nautilus then navigate to /var/log and delete kern.log

---

### Post by Crazy K on 2010-08-27
Do I do that in the terminal?

Or do you want me to go into the var/log folder and delete the kern.log file?

---

### Post by linux18 on 2010-08-27
type gksudo nautilus in the terminal, then a root version of the file manager will pop up allowing you to delete files in /var

---

### Post by Crazy K on 2010-08-27
Alright, so I did that, and so far this is what I got:

```
Initializing nautilus-gdu extension
sys:1: GtkWarning: Reset to Defaults: missing action Reset to Defaults
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.
```

Anyways it doesn't seem to be done though. It has stopped at "please ask your system administrator to enable user sharing."

---

### Post by Crazy K on 2010-08-27
I need some help badly. Whenever I turned my computer on, It never would load up. Stays at the Ubuntu loading screen. I put an old 20GB HD as master and I now have 11GB of space, but I don't know how long it'll last.

Also, signed in as root in the terminal and ran gksudo nautilus and noticed that the kern.log is now 52.0KB. So the HD I added lowered the space, and I also checked the log folder as a whole, and it's 3.8GB only. 

I did the disk usage analyzer and here's what I got:

[http://imgur.com/w5oOMl.jpg](http://imgur.com/w5oOMl.jpg)

and

[[IMG]http://imgur.com/Maia2l.jpg[/IMG]](http://imgur.com/Maia2.png)

So to me, it sounds like the HD I had in my comp is actually the problem, or so I think. But still it shouldn't even be 3GB.

Btw, syslog.1 is the file that's taking up the 3.8GB of space.

Alright, just took the HD out (one I put in that got my computer running again) and I couldn't start the computer. It was stuck at the Ubuntu loading screen.

---

### Post by Crazy K on 2010-08-27
I need help as soon as possible. I'm scared to shut the computer down because I'm afraid it'll do the same thing. Someone has to know what to do.

Anyways, I deleted kern.log by following what you said.

Also, I have a question. I haven't ran update manager in a while (since I don't get the sign on the menu bar above telling me I have updates). Anyways could that be the problem? Should I run the update manager?

---

### Post by linux18 on 2010-08-27
upgrade the computer:

sudo chmod 755 /usr/bin/dpkg && sudo apt-get upgrade dpkg
sudo dpkg --purge $(dpkg -l |grep  ^rc |awk '{print $2}' | tr '\012' ' ') 
sudo apt-get -f install && sudo apt-get clean && sudo apt-get autoclean 
sudo apt-get autoremove && sudo apt-get update && sudo apt-get --fix-broken upgrade

---

### Post by Crazy K on 2010-08-27
Doing that now, I'll update you on any problems.

---

### Post by Crazy K on 2010-08-27
Ok, the file space is the same at 11.1GB (with the extra HD added btw) so what do I do next?

---

### Post by linux18 on 2010-08-27
reboot a few times to test it

---

### Post by Crazy K on 2010-08-27
rebooted a few times, but it's still at 11.1GB 

But yeah, like I said before, I put another HD I had (has windows xp and a ton of old files) and I put it as master (main HD is still master as well). It's the only way I can boot the computer now.

---

### Post by linux18 on 2010-08-27
inserting another hard drive shouldn't do anything in the linux install, remove it and reboot, it could be a coincidence

---

### Post by Crazy K on 2010-08-27
haha, oh man I feel like an idiot. It's good now. The main HD was the HD with 11.1GB of space. 

Anyways, sorry for making this problem go on longer than it actually needed. And thanks a ton for all the help.

---

### Post by Andrew.Z on 2010-09-26
> **Crazy K said:**
> Alright, doing that now. 

Also, is it normal for BleachBit to slow the computer down? Also it seems to take up file space while it's working. Is that normal? After I exit BleachBit before it deletes all the files, the file space goes back to normal, which is now 3.4GB, but when I run BleachBit and check "Free Disck Space" under the system area, it says "This option is very slow". So will that cause my space to fluctuate or in this case, go down?

The "free disk space" option will slow down your computer (because it heavily access the hard drive), consume disk space while it works (which will be freed when it is done), and takes a long time (more or less 30-60 minutes).  You may want to leave this option off most of the time. What it does is securely wipe deleted files, but some people think it frees disk space.  (You will end up with the same amount of free disk space.)


> **linux18 said:**
> when bleachbit scans for files in the system area, it is very slow and won't save much space, I suggest only using the default options every once in a while.

The "localizations" option in the system area frees up disk space (sometimes a few hundred MB, especially the first time), but you don't need to run it often.  This URL explains the "localizations" option:
[http://bleachbit.blogspot.com/2009/07/free-disk-space-localepurge.html](http://bleachbit.blogspot.com/2009/07/free-disk-space-localepurge.html)

In the system section, to free disk space quickly, I generally recommend turning on cache, localizations, rotated logs, temporary files, and trash.  Disable "free disk space" and "memory."

---

