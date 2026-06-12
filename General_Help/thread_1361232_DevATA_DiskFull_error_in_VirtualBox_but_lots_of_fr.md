---
title: "DevATA_DiskFull error in VirtualBox but lots of free space!"
date: 2009-12-21
forum: General Help
---

### Post by MKVCrazy on 2009-12-21
```
root@XXXXX:~# du -hx --max-depth=1 /
68K    /tmp
4.0K    /opt
504M    /var
8.0K    /srv
6.2G    /root
4.0K    /additional
2.8G    /usr
127M    /lib
4.0K    /home
4.0K    /selinux
0    /dev
4.0K    /mnt
36M    /boot
6.0M    /etc
0    /proc
16K    /lost+found
0    /sys
9.5M    /sbin
8.0K    /media
5.7M    /bin
9.6G    /
root@XXXXX:~# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             9.7G  9.7G     0 100% /
none                  2.0G  144K  2.0G   1% /dev
none                  2.0G  116K  2.0G   1% /dev/shm
none                  2.0G  292K  2.0G   1% /var/run
none                  2.0G     0  2.0G   0% /var/lock
none                  2.0G     0  2.0G   0% /lib/init/rw
/dev/sda2             870G  215M  826G   1% /home
/dev/sda4              45G  180M   43G   1% /additional
root@XXXXX:~# 
```

I cannot do anything with my VM anymore. Could I get a little help? :confused:

---

### Post by synapsys on 2009-12-21
> **MKVCrazy said:**
> ```

/dev/sda1             9.7G  9.7G     0 100% /

```

This means your root ( / ) partition is 100% full with **0** free space.

Try this to free up some space:

```
sudo apt-get autoclean
```

---

### Post by MKVCrazy on 2009-12-22
Hi, thanks to you I got the idea of using the terminal to remove the folders because I was logged out of my GUI Remote Client (NoMachineNX) because I had no more space left on device. So I could use only the SSH terminal. And luckily one of my folders was easy to remember and I was able to get myself back to GUI.

Thanks. I just realize that **root** folder is not meant for storing files but the **home** folder is. I am guessing that's for my own security.

---

