---
title: "Trying to speed up firefox in an unorthodox manner caused many unwanted side-effects"
date: 2009-12-19
forum: General Help
---

### Post by Surlent777 on 2009-12-19
Clearly this was a bad idea, but I read in many places that it was possible to speed up Firefox by having it use /tmp as a cache, and this was to be accomplished by editing two files (/etc/fstab and /etc/sysctl.conf) and adding a string to Firefox telling it to use /tmp as the cache. It said to add to fstab "tmpfs /tmp tmpfs noexec,defaults,noatime 0 0"
and "tmpfs /var/tmp tmpfs noexec,defaults,noatime 0 0"; it said to add to sysctl "vm.swappiness=1". I did so, and upon discovering my problems, commented the three of those options out, and of course rebooted (again).

The issues I am now experiencing are as follows:
1. gpm (the thing that makes a mouse cursor and middle-click paste possible in a TTY) appears to not be working.
2. screen does not allow me to open it, giving the error message "Cannot make directory '/var/run/screen': Permission denied". If I manually create the directory, or run screen as sudo first, then it works. A google search led me to a Debian bug listing where someone else had this problem from trying what I did with /tmp so far as I understand, but that it was fixed in Sarge. No other information was given.
3. Apparently, anything requiring access to localhost is given "Access denied" messages. The two apps that I've confirmed this with are irssi/bitlbee (/connect localhost) and tor (noticed when XChat couldn't use its normal proxy to connect to anything).

The only other recent change I've made is to disable IPV6 via GRUB. Reverting this didn't seem to fix anything. And yes, all three of these items were working previously. My version of tor is from their official karmic repo (0.2.1.20-1~karmic+1), my version of gpm is 1.20.4-3.2ubuntu1, from the normal repos. bitlbee, irssi, and XChat are all also from the normal repos and at versions 1.2.4-1, 0.8.14-1ubuntu1, and 2.8.6-4ubuntu2.

Relevant data (clean boot)

$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:300 (300.0 B)  TX bytes:300 (300.0 B)

$cat /etc/network/interfaces
auto lo
iface lo inet loopback

$ netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.0.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG        0 0          0 eth0

$ hostname
cory-desktop

$ ls -al /var/
total 52
drwxr-xr-x 15 root root  4096 2009-10-27 11:10 .
drwxr-xr-x 22 root root  4096 2009-12-05 00:41 ..
drwxr-xr-x  2 root root  4096 2009-12-19 01:23 backups
drwxr-xr-x 21 root root  4096 2009-12-04 14:00 cache
drwxrwxrwt  2 root root  4096 2009-12-13 13:10 crash
drwxr-xr-x  5 root root  4096 2009-12-01 13:16 games
drwxr-xr-x 75 root root  4096 2009-12-18 00:14 lib
drwxrwsr-x  2 root staff 4096 2009-10-19 18:18 local
drwxrwxrwt  2 root root    40 2009-12-19 12:49 lock
drwxr-xr-x 18 root root  4096 2009-12-19 12:49 log
drwxrwsr-x  2 root mail  4096 2009-12-19 01:35 mail
drwxr-xr-x  2 root root  4096 2009-10-27 10:56 opt
drwxr-xr-x 14 root root   600 2009-12-19 12:57 run
drwxr-xr-x  8 root root  4096 2009-11-03 11:46 spool
drwxrwxrwt  5 root root  4096 2009-12-19 12:46 tmp

$ ls -al /var/run
total 60
drwxr-xr-x 14 root       root        600 2009-12-19 12:57 .
drwxr-xr-x 15 root       root       4096 2009-10-27 11:10 ..
srw-rw-rw-  1 root       root          0 2009-12-19 12:48 acpid.socket
-rw-r--r--  1 root       root          5 2009-12-19 12:48 atd.pid
drwxr-xr-x  2 avahi      avahi        80 2009-12-19 12:49 avahi-daemon
drwxr-xr-x  2 root       root         60 2009-12-19 12:49 console
drwxr-xr-x  2 root       root         60 2009-12-19 12:49 ConsoleKit
-rw-r--r--  1 root       root          4 2009-12-19 12:48 console-kit-daemon.pid
-rw-r--r--  1 root       root          5 2009-12-19 12:48 crond.pid
----------  1 root       root          0 2009-12-19 12:48 crond.reboot
drwxr-xr-x  2 messagebus messagebus   80 2009-12-19 12:48 dbus
-rw-r--r--  1 root       root          4 2009-12-19 12:49 dhclient-eth0.pid
drwxrwxr-t  4 root       gdm         100 2009-12-19 12:49 gdm
-rw-r--r--  1 root       root          4 2009-12-19 12:48 gdm.pid
-rw-r--r--  1 root       root        168 2009-12-19 12:49 motd
drwxr-xr-x  2 root       root         60 2009-12-19 12:49 network
-rw-r--r--  1 root       root          3 2009-12-19 12:48 NetworkManager.pid
-rw-r--r--  1 root       root       1777 2009-12-19 12:48 nm-dhclient-eth0.conf
-rw-r--r--  1 root       root          4 2009-12-19 12:49 ntpd.pid
drwxr-xr-x  4 root       root         80 2009-12-19 12:49 pm-utils
drwxrwx---  2 root       polkituser   40 2009-12-19 12:48 PolicyKit
drwxr-xr-x  2 syslog     syslog       60 2009-12-19 12:48 rsyslog
-rw-r--r--  1 root       root          4 2009-12-19 12:48 rsyslogd.pid
-rw-r--r--  1 root       root          0 2009-12-19 12:48 sendsigs.omit
drwxr-xr-x  2 root       root         40 2009-12-19 12:48 sshd
-rw-r--r--  1 root       root          5 2009-12-19 12:48 sshd.pid
drwx------  3 root       cory         60 2009-12-19 12:57 sudo
drwxr-xr-x  2 root       root         60 2009-12-19 12:48 udev-configure-printer
-rw-r--r--  1 root       root          4 2009-12-19 12:48 upstart-udev-bridge.pid
-rw-rw-r--  1 root       utmp       4608 2009-12-19 13:06 utmp

Any help, as well as, if possible, the reasoning behind all of this madness, is very greatly appreciated.

---

### Post by dcstar on 2009-12-19
> **Surlent777 said:**
> Clearly this was a bad idea, but I read in many places that it was possible to speed up Firefox by having it use /tmp as a cache,
......

And what is wrong with simply using one of the many Firefox tweaking tools to just tell it to use a larger Memory Cache and no Disk Cache?

---

### Post by Surlent777 on 2009-12-20
I dunno. I was kind of batch Google searching and doing whatever seemed plausible. I stopped after about four pages, iirc, because they were getting repetitive and I was getting bored. I'm not really all that concerned with the speed issues (the other suggestions on those sites helped quite a bit already); I am far more concerned with getting my system in perfect working order again.

---

### Post by Surlent777 on 2009-12-21
My best guess at this point is that it may have to do with permissions, possibly within /var. Can anyone help me with this?

---

### Post by Surlent777 on 2009-12-25
I think I can now state with confidence that bitlbee, gpm, and tor don't start up at system boot, and these permission errors keep them from starting up at all. Also, screen doesn't make its /var/screen directory on startup either. Any ideas on what might cause all of this, and more importantly, how I might fix it?

---

### Post by bodhi.zazen on 2009-12-25
I do not think your problems are due to the changes you made in your first post.

I have used these exact changes and not had the kinds of problems you describe. In addition you say your reversed the changes and rebooted =)

Is your file system mounted ro ?

boot a live cd and run fsck on your root partition.

---

### Post by Surlent777 on 2009-12-25
I think I can say that my filesystem is most certainly not mounted read only, as I can work normally in all other ways. I have tried running fsck by typing "sudo touch /forcefsck" and rebooting; it completed the scan quickly but reported nothing. =/

---

### Post by bodhi.zazen on 2009-12-25
Well, your system is obviously behaving odd =)

Is there something you are doing that is unusual ? Running 10.04 Alpha ? Running in virtualization ?

Any error messages in your logs (messages, syslog, dmesg) ???

What happens if you boot, then 

```
sudo init 2
```

---

### Post by Surlent777 on 2009-12-25
I'm not doing anything too unusual...it's a normal Karmic x64. Using "sudo init 2" seems to do absolutely nothing. At all. I hit enter, and get the slightest of pauses, and bash is happily awaiting my next command. As for errors, I think one of those logs in /var mentioned several times that gpm needs to be run as root. tor's logs are fairly mundane; it mentions the last time that it was running successfully was right before I restarted after adjusting those files. I skimmed through the suggested log files, but I don't really know if anything in them is abnormal or not...All I know for sure is that gpm error I mentioned, and that it, tor, and screen don't work for some reason. =/

---

### Post by Ex-Opesa on 2009-12-25
I am having the same problem as him, i didn't try to speed up firefox though. All my services didn't start @boot, but when i entered

sudo init 2

All are the services are working fine, but now i have to enter it every time i restart the system. Can't this be done automatically? 
Also 'screen' problem is still there
I think i should make my own thread ^^

Thanks. :)

---

### Post by sdennie on 2009-12-25
What's the output of the following two commands:

```

cat /etc/fstab
mount

```

It's possible you haven't reverted your changes completely.

---

### Post by Surlent777 on 2009-12-25
cory@cory-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=b844896f-c796-4bb8-95e0-7b61bce8791e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=47967b11-e444-4c7c-8533-146c4ee70df3 none            swap    sw              0       0
# tmpfs /tmp tmpfs noexec,defaults,noatime 0 0
# tmpfs /var/tmp tmpfs noexec,defaults,noatime 0 0

cory@cory-desktop:~$ mount
/dev/sda5 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/home/cory/.Private on /home/cory/Private type ecryptfs (ecryptfs_sig=c3733a29ad4b6b0d,ecryptfs_fnek_sig=c7b6cce361961c40,ecryptfs_cipher=aes,ecryptfs_key_bytes=16)
gvfs-fuse-daemon on /home/cory/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=cory)

---

### Post by Surlent777 on 2009-12-29
I must admit I don't know much about these files, but I'm not sure I see anything inherently "wrong" with this setup. I know from further experimentation that bitlbee isn't being started and that the screen folder isn't being created on startup. I can't seem to start bitlbee at all. Tor doesn't seem to be running either. Using "sudo init 2" seems to have no effect. This is really confusing and frustrating. Any other ideas?

---

### Post by Surlent777 on 2009-12-29
Well, I have something that might be a little bit useful, noticed during an update just now. Afterwards, torbutton, instead of taking me to a blank page with an "add exception" button, took me to a page saying that I was trying to connect to a proxy that is refusing connections. This refers to localhost. I don't know if this change will be there when I reboot or not though...

The following packages will be upgraded:
  chromium-browser chromium-browser-inspector 
  chromium-codecs-ffmpeg-nonfree tor tor-geoipdb 
5 packages upgraded, 0 newly installed, 0 to remove.
Need to get 13.4MB of archives. After unpacking 73.7kB will be used.
Do you want to continue? [Y/n/?] y
...
Preparing to replace tor 0.2.1.20-1~karmic+1 (using .../tor_0.2.1.21-1~karmic+1_amd64.deb) ...
Stopping tor daemon: not running (there is no /var/run/tor/tor.pid).
Unpacking replacement tor ...
Preparing to replace tor-geoipdb 0.2.1.20-1~karmic+1 (using .../tor-geoipdb_0.2.1.21-1~karmic+1_all.deb) ...
Unpacking replacement tor-geoipdb ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for desktop-file-utils ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up tor (0.2.1.21-1~karmic+1) ...
Something or somebody made /var/run/tor disappear.
Creating one for you again.
Raising maximum number of filedescriptors (ulimit -n) to 32768.
Starting tor daemon: tor...
Dec 29 16:58:24.764 [notice] Tor v0.2.1.21. This is experimental software. Do not rely on it for strong anonymity. (Running on Linux x86_64)
Dec 29 16:58:24.765 [notice] Initialized libevent version 1.4.11-stable using method epoll. Good.
Dec 29 16:58:24.766 [notice] Opening Socks listener on 127.0.0.1:9050
done.

Setting up tor-geoipdb (0.2.1.21-1~karmic+1) ...
Setting up chromium-codecs-ffmpeg-nonfree (0.5+svn20091210r34297+35231+35323-0ubuntu1~ucd1~karmic) ...
Setting up chromium-browser (4.0.285.0~svn20091229r35334-0ubuntu1~ucd1~karmic) ...

Setting up chromium-browser-inspector (4.0.285.0~svn20091229r35334-0ubuntu1~ucd1~karmic) ...
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

---

### Post by Surlent777 on 2010-01-05
Related to the above, I just now tried reinstalling tor, gpm, screen, and bitlbee using aptitude, and it fixed all but the tor issue (though tor seems to work again with XChat, oddly enough), but after rebooting, I was right back where I started. After reinstalling them with aptitude again, they were relatively fixed again, but this is not adequate. I have previously tried to start bitlbee manually in several ways, from sudo init 2 to using the BUM. None of those worked. Aptitude's forced start of it, however, did work. I also notice that screen's setup is odd. And look at the permissions for screen:

-rwxr-sr-x  1 root   utmp      376032 2009-07-05 22:37 screen

Take a good look at that strange s there. A user in #ubuntu confirmed for me that that s should not be there, and that again, I should have a screen.real. What a mess! On the whole though, it seems clear to me that certain services are not being started normally, and I don't know why. Perhaps this is related to the cases of CUPS suddenly not working (one user mentioned running firefox as root and editing fstab to fix a USB problem before noticing his issue. Not to imply that I ran firefox as root; I didn't, but it is all oddly similar)...and I remember another guy in there a week or so ago complaining that many or perhaps all of his services were not starting...what is going on around here?

---

### Post by Surlent777 on 2010-01-12
I should add that tor works when I include privoxy in the re-installation list. I mean, I could keep just reinstalling every boot, but I would really like a fix that doesn't involve massive backing up/time wasting. Does anyone have any ideas at all?

---

### Post by Surlent777 on 2010-02-01
I did it, finally. I found out from reading the inet config files,
specifically the one for gpm, (building an Arch Linux in virtualbox
gave me the knowledge and idea to try looking around here)
that something I thought unrelated might be the cause, and it was:
I had it set to try and boot using both of my processors like I used
to, by changing /etc/init.d/rc's CONCURRENT=shell line
back to its default of CONCURRENT=none (shell isn't even listed as an
option anymore, so something must have changed anyway, probably making
this tweak useless anymore...indeed I noticed little change in
performance on my reboot...may have actually been faster, I dunno).
Such a simple fix...thank you all for attempting to help me up to this
point though, I really do appreciate it.

---

