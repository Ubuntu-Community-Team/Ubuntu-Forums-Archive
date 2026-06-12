---
title: "error on downloading"
date: 2010-11-01
forum: General Help
---

### Post by arturieto on 2010-11-01
I am used to downloading files like free movies. Latest issue was when the downloading stops using Transmission bittorent. Message is "Error: Unable to save resume file:No space left on device."

I need help on this ! ! !

---

### Post by ajgreeny on 2010-11-01
Show us the output of command ```
df -h
```Perhaps there is not enough room for the downloaded file.

---

### Post by Cdub91 on 2012-02-10
I am having similar problems with qbitorent also with transmission i typed in that command and this is what i got. 
Please help. 
BTW this box has is dual boot win7 and Ubuntu 11.10

Filesystem            Size  Used Avail Use% Mounted on
/dev/loop0             17G   17G  1.7M 100% /
udev                  2.9G  4.0K  2.9G   1% /dev
tmpfs                 1.2G  816K  1.2G   1% /run
none                  5.0M     0  5.0M   0% /run/lock
none                  2.9G  1.4M  2.9G   1% /run/shm
/dev/sda2             684G  156G  528G  23% /host

---

### Post by brpylko on 2012-02-10
Yeah, looks like you are out of disk space(on your primary partition). Delete any unneeded files and uninstall any unneeded programs. Also try running ```
sudo apt-get autoremove
``` in the terminal

---

### Post by Cdub91 on 2012-02-10
How do I make the partition bigger? 
and Unrelated but much worse now Ubuntu wont even boot it says cant write /boot/grub/grubnve.new or something like that any help would  be much appreciated.

---

### Post by pearl298 on 2012-08-10
Transmission defaults to using "/var/lib/transmission-daemon/info/downloads" for ALL downloaded files!

You need to change this to a larger partition (e.g. /home/transmission/... ) then move/delete the downloads in /var/lib/...

I run /home in a separate amd very large partition (1Tb) while my root partition (/) is quite small (20Gb). As a result /var/.. can be filled very quickly!

Once you have filled the root partition then all kinds of things break!

---

