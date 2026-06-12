---
title: "Why is root running out of space with 64 GB free?"
date: 2010-03-07
forum: General Help
---

### Post by blackSP on 2010-03-07
I'm puzzled, if there's anybody with an idea please help. I've been searching the web on this, followed up hints and tips (e.g. [http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)) but with no results.

I'm running Ubuntu 9.10 on 3 disk configuration:
1: 80GB SSD running root with /home mounted to the next disk
2: 250GB HDD where /home lives
3: 250GB backup of disk 2

My system is complaining since just now with:
The volume "file system root' has only 640MB od disk space left

However, there's plenty, see below:

blacksp@blacksp-desktop:~$ df -Th | sort
/dev/sda1     ext4     71G  3.0G   64G   5% /
/dev/sdb1     ext4    230G  124G   94G  57% /home
/dev/sdc1     ext4    230G  125G   94G  58% /media/backupdisk
Filesystem    Type    Size  Used Avail Use% Mounted on
none         tmpfs    2.0G     0  2.0G   0% /lib/init/rw
none         tmpfs    2.0G     0  2.0G   0% /var/lock
none         tmpfs    2.0G  196K  2.0G   1% /var/run
tmpfs        tmpfs    2.0G     0  2.0G   0% /dev/shm
udev         tmpfs    2.0G  304K  2.0G   1% /dev

And all my bins are empty:
blacksp@blacksp-desktop:~$ sudo find / -type d -name *Trash* 
/home/blacksp/.local/share/Trash
/home/.Trash-0
/media/backupdisk/home/blacksp/.local/share/Trash


Any ideas?

---

### Post by walter_j on 2010-03-07
Filesystem    Type    Size  Used Avail Use% Mounted on
none         tmpfs    2.0G     0  2.0G   0% /lib/init/rw
none         tmpfs    2.0G     0  2.0G   0% /var/lock
none         tmpfs    2.0G  196K  2.0G   1% /var/run
tmpfs        tmpfs    2.0G     0  2.0G   0% /dev/shm
udev         tmpfs    2.0G  304K  2.0G   1% /dev

looks like the swap drive is full. Restart and see if that fixes the problem. start system monitor and look at processes running to see if there's a whole bunch of zombies running.

---

### Post by blackSP on 2010-03-08
Thanks for the reply!

How can the swap drive be full?

I see utilisation ratios of =< 1%
How does that work?

In the mean time I doubled the swap drive space with gparted.

---

### Post by walter_j on 2010-03-08
Sorry. I had this problem before, and my solution was for you is totally wrong. I'll try to remember how I solved it...

---

### Post by tomcheng76 on 2010-03-08
ext2/ext3 default reserve 5% space for system usage. to lower it to 1%
```
sudo tune2fs -m 1 /dev/sda1
```

---

### Post by drs305 on 2010-03-08
Often this is caused by backups made to the wrong partition (e.g. to / instead of the backup partition), undeleted trash, and large log files. Your *user* trash is empty, but did you check the *root* trash? This also must be emptied - it resides at /root/.local/share/Trash/files in later versions of Ubuntu.

Here is a link to a guide I wrote on how to find out what is taking up free disk space:
[HOWTO: Recover Lost Disk Space ]("http://ubuntuforums.org/showthread.php?t=1122670")

I"m not sure where the problem lies, but running the commands might reveal something.  Added: The command you ran looking for *Trash* should have found any *root* trash bins.

---

### Post by blackSP on 2010-03-08
Hi, I totally don't get it.

All trash bins are empty, including root.
There are only a few small logs, no backups, I followed your guide.

How do you see the  / drive is getting pretty full?
I have a pretty much empty SDD,  my /home lives on another drive.

And by looking at all the         tmpfs's, they're all about empty.

I have no partitions on the ssd other than extended/linux-swap @6.2gb

---

### Post by lykwydchykyn on 2010-03-08
Where exactly are you seeing the message that your disk is full?  Is this coming from a particular program?

I've had problems in the past where a program says "your / drive is full" when in fact it was some other directory that was mounted to a different drive that was full.

Since your root drive clearly is not full or anywhere close, the problem most likely is with whatever software is generating the error.

---

### Post by blackSP on 2010-03-08
It's a system generated message that pops up right after boot with no manually started progs. And I can't think of any drives being full since my machine has three:
SDD:  /dev/sda1     ext4     68G  3.0G   61G   5% /
HDD1: /dev/sdb1     ext4    230G  126G   92G  58% /home
HDD2: /dev/sdc1     ext4    230G  128G   91G  59% /media/backupdisk

With the available disk space this should be no problem:
blacksp@blacksp-desktop:~$ sudo du -h --max-depth=1 / | grep '[0-9]G\>'
126G    /home
128G    /media
2.3G    /usr

I have no Windows partitions or other windows crap installed that would than obviously be the cause of this problem :)

Some more info:
blacksp@blacksp-desktop:~$ du -h /var/cache/apt/
4.0K    /var/cache/apt/archives/partial
4.8M    /var/cache/apt/archives
32M    /var/cache/apt/

blacksp@blacksp-desktop:~$ sudo du -h /var/log
4.0K    /var/log/news
52K    /var/log/ConsoleKit
220K    /var/log/apt
4.0K    /var/log/samba/cores/winbindd
8.0K    /var/log/samba/cores
24K    /var/log/samba
4.0K    /var/log/apparmor
4.0K    /var/log/dist-upgrade
4.0K    /var/log/speech-dispatcher
12K    /var/log/fsck
32K    /var/log/cups
4.0K    /var/log/unattended-upgrades
108K    /var/log/gdm
1.2M    /var/log/installer
28K    /var/log/exim4
17M    /var/log

blacksp@blacksp-desktop:~$ sudo find / -name "lost+found" | sudo xargs du -h
4.0K    /lost+found

blacksp@blacksp-desktop:~$ sudo find / -type d -name '*Trash*' | sudo xargs du -h | sort 
16K    /home/blacksp/.local/share/Trash
16K    /media/backupdisk/home/blacksp/.local/share/Trash
4.0K    /home/blacksp/.local/share/Trash/expunged
4.0K    /home/blacksp/.local/share/Trash/files
4.0K    /home/blacksp/.local/share/Trash/info
4.0K    /media/backupdisk/home/blacksp/.local/share/Trash/expunged
4.0K    /media/backupdisk/home/blacksp/.local/share/Trash/files
4.0K    /media/backupdisk/home/blacksp/.local/share/Trash/info

---

### Post by lykwydchykyn on 2010-03-08
> **blackSP said:**
> It's a system generated message that pops up right after boot with no manually started progs. And I can't think of any drives being full since my machine has three:
SDD:  /dev/sda1     ext4     68G  3.0G   61G   5% /
HDD1: /dev/sdb1     ext4    230G  126G   92G  58% /home
HDD2: /dev/sdc1     ext4    230G  128G   91G  59% /media/backupdisk

Is it a console error or some kind of dialog at the login screen?

You might want to look at the output of dmesg to see if there's a record of the error there.

---

### Post by blackSP on 2010-03-08
It's a standard dialog box with OK button right after login.
dmesg lists nothing related to 'root running out of space'

Could this be an original new Linux or Ubuntu bug?

---

### Post by lykwydchykyn on 2010-03-08
> **blackSP said:**
> It's a standard dialog box with OK button right after login.
dmesg lists nothing related to 'root running out of space'

If it's after login that's different.  That implies it's something related to desktop environment or software you're running in your session, not a system service or kernel error.

In that case, I'd check /var/log/syslog or ~/.xsession-errors for more information.


> 
Could this be an original new Linux or Ubuntu bug?

It's too early to say.  I would certainly recommend reporting to launchpad, where a triager might help you find exactly where to look for more information.

---

### Post by blackSP on 2010-03-08
/var/log/syslog nothing related
~/.xsession-errors same!

I'll  report it to launchpad tonight.

Thanks for now, if you think of anything else...

---

### Post by walter_j on 2010-03-08
Ok, your root folder is listing 64 GB available. Totally different than my case, where i mounted a drive wrong and backed up to root folder. I'm out of ideas. You run fschk at boot?

---

### Post by blackSP on 2010-03-08
fsck found a few block count errors on /dev/sdb1 which is the other HDD where my home sits.
I'll run a sudo touch /forcefsck now and boot and see what the result is.
Be back in a minute (I hope...)

Update: fixed some errors running gparted live cd.
No more errors now. I'll wait until the root space thing comes back, make a screen print, run diagnostic checks and report it on launchpad.

---

### Post by blackSP on 2010-03-09
OK, I thought it was a one time glitch but here's the message. This time it popped up while doing a backup to my backup drive. Actually I was also trimming my SDD, not sure what exactly triggered this but it sure must be something!

Now how do I get to the root of this problem???
Edit: I double checked but all disks have loads of free space, trash empty, cache, logs, nothing I notice to be odd.

[IMG]http://www.lostsummit.net/files/images/Screenshot-Low%20Disk%20Space.png[/IMG]

---

### Post by DaithiF on 2010-03-09
sounds like this bug:
[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/408842](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/408842)

---

### Post by blackSP on 2010-03-10
Alright, seems exactly the same but it is reported to be fixed upstream. I assume the gnome-settings-daemon is fixed in Karmic?

Not sure what to do with this.

---

