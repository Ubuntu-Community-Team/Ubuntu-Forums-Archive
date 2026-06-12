---
title: "Crash help?"
date: 2011-12-01
forum: General Help
---

### Post by jaylc005 on 2011-12-01
Hello guys, firstly thanks for any information you can provide me in helping me resolve my issue.

Im a bit of a linux noob, been playing with it for years but never really exceeded beyond that level.

I am running Ubuntu 10.10 on an acer extensa 5235 laptop, and here is a rough explanation of the problems I am facing and how I may have got there..

I installed ubuntu about 2 weeks ago when I got my new crucial m4 ssd (hissy fit and a slammed lid resulted in previous hdd breaking, silly behaviour I know.)

After that, i played with ahci modes to get screen brightness control working, success.
Took some updates
found out about the need for trim, set it up according to a guide on the net with hdparm etc.. checked trim was operational as best I could, according to site, it was now set up.
played with sources.list to add backtrack repositories to synaptec package manager.
played with aircrack and stuff
done lots of reading aircrack-ng wiki and forums to find solution to -1 channel fix in aircrack-ng, finally found a solution here - [http://blog.macuyiko.com/2010/11/ubuntu-1010-fixed-channel-mon0-1.html](http://blog.macuyiko.com/2010/11/ubuntu-1010-fixed-channel-mon0-1.html), followed it, fixed the -1 channel issue.. 
updates broke, various excuses, restored sources.list and ran apt-cdrom for some reason, this fixed the issue and done a last update.

Thinking about it now I am typing up the events as I vaguely remember them, I feel the problem started when I followed the -1 fix.

The fix was as follows.
```
wget http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2010-10-16.tar.bz2
tar -jxf compat-wireless-2010-10-16.tar.bz2
cd compat-wireless-2010-10-16
wget http://patches.aircrack-ng.org/mac80211.compat08082009.wl_frag+ack_v1.patch
patch -p1 < mac80211.compat08082009.wl_frag+ack_v1.patch
wget http://patches.aircrack-ng.org/channel-negative-one-maxim.patch
patch ./net/wireless/chan.c channel-negative-one-maxim.patch
gedit scripts/update-initramfs
#*** FIND LINE 13: KLIB=/lib/modules/2.6.31-wl/build
#*** REPLACE WITH: KLIB=/lib/modules/$(uname -r)/build
make
sudo make install
sudo make unload
sudo modprobe iwl3945
```The only thing I didnt do was modprobe iwl3945, instead I just restarted and allowed the required module to load itself.

The problem:
The problem is simple, I am using my machine or idle, and sometimes x seems to close, it returns to the text boot screen, showing the last messages before ubuntu loaded the session, the cursor is still visible on top of the black screen but not moving.

How do I start to even diagnose something like this, especially when being slack and not taking note or notice of what I am doing to the system to customize it to my preferences?

last -n 40 gives the output:
```
br0adcas pts/0        :0.0             Thu Dec  1 11:22   still logged in   
br0adcas tty7         :0               Thu Dec  1 10:30   still logged in   
reboot   system boot  2.6.35-31-generi Thu Dec  1 10:30 - 11:22  (00:51)    
br0adcas tty7         :0               Thu Dec  1 10:17 - crash  (00:13)    
reboot   system boot  2.6.35-31-generi Thu Dec  1 10:13 - 11:22  (01:08)    
br0adcas tty7         :0               Thu Dec  1 03:10 - down   (00:30)    
reboot   system boot  2.6.35-31-generi Thu Dec  1 03:10 - 03:41  (00:30)    
br0adcas tty7         :0               Thu Dec  1 03:07 - down   (00:00)    
reboot   system boot  2.6.35-31-generi Thu Dec  1 03:06 - 03:07  (00:00)    
br0adcas pts/2        :0.0             Thu Dec  1 00:55 - 03:06  (02:10)    
br0adcas pts/1        :0.0             Thu Dec  1 00:52 - 00:53  (00:00)    
br0adcas pts/0        :0.0             Thu Dec  1 00:30 - 00:49  (00:18)    
br0adcas tty7         :0               Thu Jan  1 00:03 - down  (1064+03:03)
reboot   system boot  2.6.35-31-generi Thu Jan  1 00:00 - 03:06 (1064+03:06)
br0adcas tty7         :0               Thu Jan  1 09:26 - crash  (-9:-25)   
reboot   system boot  2.6.35-31-generi Thu Jan  1 09:26 - 03:06 (1063+17:40)
br0adcas pts/0        :0.0             Wed Nov 30 23:46 - crash (-1063+-14:-
br0adcas tty7         :0               Thu Jan  1 06:39 - crash  (02:47)    
reboot   system boot  2.6.35-31-generi Thu Jan  1 06:39 - 03:06 (1063+20:27)
br0adcas pts/2        :0.0             Wed Nov 30 19:13 - crash (-1063+-12:-
br0adcas pts/1        :0.0             Wed Nov 30 19:13 - 20:45  (01:32)    
br0adcas pts/0        :0.0             Wed Nov 30 19:13 - crash (-1063+-12:-
br0adcas tty7         :0               Thu Jan  1 04:06 - crash  (02:32)    
reboot   system boot  2.6.35-31-generi Thu Jan  1 04:06 - 03:06 (1063+22:59)
br0adcas tty7         :0               Thu Jan  1 03:15 - crash  (00:51)    
reboot   system boot  2.6.35-31-generi Thu Jan  1 03:14 - 03:06 (1063+23:51)
br0adcas pts/0        :0.0             Wed Nov 30 17:36 - crash (-1063+-14:-
br0adcas tty7         :0               Thu Jan  1 00:00 - crash  (03:14)    
reboot   system boot  2.6.35-31-generi Thu Jan  1 00:00 - 03:06 (1064+03:06)
br0adcas tty7         :0               Wed Nov 30 04:51 - down   (02:20)    
reboot   system boot  2.6.35-31-generi Wed Nov 30 04:51 - 07:12  (02:21)    
br0adcas pts/2        :0.0             Wed Nov 30 04:44 - 04:51  (00:07)    
br0adcas pts/0        :0.0             Wed Nov 30 04:44 - 04:51  (00:06)    
br0adcas pts/1        :0.0             Wed Nov 30 04:23 - 04:43  (00:19)    
br0adcas pts/0        :0.0             Wed Nov 30 04:21 - 04:43  (00:21)    
br0adcas tty7         :0               Wed Nov 30 04:21 - down   (00:30)    
reboot   system boot  2.6.35-31-generi Wed Nov 30 04:20 - 04:51  (00:30)    
root     pts/0        :0.0             Wed Nov 30 03:46 - down   (00:33)    
br0adcas tty7         :0               Wed Nov 30 02:34 - down   (01:46)    
reboot   system boot  2.6.35-31-generi Wed Nov 30 02:34 - 04:20  (01:46)   
```

I know where the logs are, and I know how to read them, but I cant make head or tail of them, partly because I have a duff bios battery, so some things are showing as jan 1st, the logs are a mess at the moment, I will add a new battery, hopefully tonight if I can find one, I have also considered this may be an issue, ubuntu always seems to update the time and date, but still has created logs from jan 1st, which this install never existed.

Can you guys help me in perhaps getting close to my issue, I will reinstall and start again, its good practice, that way i could probably in a reasonable amount of time, figure out where I went wrong, but I would much rather save the install.

Any help would be greatly appriciated, this is my first post to the ubuntu forums, but windows was thrown out a long time ago for me, I really want to get back into the swing of things, so it will be great to get chatting and sharing with you guys.

Peace.
Jay. UK

---

### Post by jaylc005 on 2011-12-01
Just an update to this, I was messing around and opened about ubuntu from the system menu, to my surprise I had upgraded to nutty narwhal 11.04? 

That I dont think was the issue, because im sure the problem was happening before that, but either way I reinstalled, and started from the beginning, the process I followed was :

```


1. ***Set up SSD behaviors.***
(a) gksudo gedit /etc/fstab and add noatime,discard,data=ordered to options for sda1. 
(b) sudo hdparm -W1 /dev/sda to enable writeback.
(c) gksudo gedit /etc/rc.local and add hdparm -W1 /dev/sda to make persistent. 

2. ***Finish SSD behaviors (noop), ACPI (backlight) and boot options.***
(a) gksudo gedit /etc/default/grub and edit GRUB_CMDLINE_LINUX_DEFAULT= to include "quiet", "acpi_osi=Linux" and "elevator=noop" and remove "splash" and "quiet". 
(b) Change boot timeout to 0 sec.
(c) sudo update-grub

3. ***Patch wireless driver for fixed channel mon0: -1" Aircrack Problem.***
(a) wget http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2010-10-16.tar.bz2
(b) tar -jxf compat-wireless-2010-10-16.tar.bz2
(c) cd compat-wireless-2010-10-16
(d) wget http://patches.aircrack-ng.org/mac80211.compat08082009.wl_frag+ack_v1.patch
(e) patch -p1 < mac80211.compat08082009.wl_frag+ack_v1.patch
(f) wget http://patches.aircrack-ng.org/channel-negative-one-maxim.patch
(g) patch ./net/wireless/chan.c channel-negative-one-maxim.patch
(h) gedit scripts/update-initramfs
(i) Find line 13 "KLIB=/lib/modules/2.6.31-wl/build" and replace with "KLIB=/lib/modules/$(uname -r)/build"
(j) make
(k) sudo make install
(l) sudo make unload
(m) sudo reboot


```

I have not run any updates, and so far, so good..

I hope it stays this way, I have not had a crash as of yet, I have saved the above text file with all the edited files for easy setup should I have to reinstall, sure its not fully custom, but it gets my ubuntu 10.10 install to a base level of configuration I require.

I would like to create an installer dvd which installs with all of these settings 'pre-set', like my own custom distro, but that is for another thread. :)

Peace.
Jay

---

### Post by jaylc005 on 2011-12-02
Hi guys, unfortunately the problem still persists.. 

Is there anybody able to shed any light on my issue, the only thing I have done apart from the above actions is install aircrack-ng and docky and turned off updates.

I guess this is a problem with the compat wireless patch?

Any ideas guys, even if its just some ability to be able to pinpoint the roundabout problem?

I have heard that uninstalling the backport modules solves the problem, but it was vague at best, and didnt say which one, nor did it say if it reverted the issue of fixed channel -1 in aircrack.

Thanks
Jay

---

