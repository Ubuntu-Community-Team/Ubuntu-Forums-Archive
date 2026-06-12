---
title: "apt-get and package manager not working"
date: 2011-05-10
forum: General Help
---

### Post by bvargo on 2011-05-10
I'm running 10.10 and cannot seem to figure out why apt-get is not working.

It will generally get to the point where it should be unpacking the replacement, but it just hangs there.  I have looked to find a way around that, but right now, I'm still looking at

```
Unpacking replacement libperl5.10 ...
```

I've had to sudo kill -9 dpkg and apt-get and delete the lock in /var/lib/dpkg/ which may have caused more problems...  It seems like the problem started when I attempted to upgrade my version of Flash.

If anyone could help figure out where to begin, I would appreciate it.

---

### Post by bodhi.zazen on 2011-05-10
Is your disk full ?

---

### Post by bvargo on 2011-05-10
Going into gparted, it does not appear so, but I might be missing something.

---

### Post by bodhi.zazen on 2011-05-10
In a terminal, ```
df -h
```

---

### Post by bvargo on 2011-05-10
```
bvargo@ruth-pc:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             410G  145G  244G  38% /
none                  1.5G  316K  1.5G   1% /dev
none                  1.5G  912K  1.5G   1% /dev/shm
none                  1.5G   80K  1.5G   1% /var/run
none                  1.5G     0  1.5G   0% /var/lock
/dev/sda6             1.1G  912M   73M  93% /usr/local
/dev/sda9             9.7G  1.4G  8.2G  15% /home
/dev/sda7              34G  2.8G   30G   9% /media/ee932142-fb47-4843-b6cb-9d4ca940bfa2

```

---

### Post by bodhi.zazen on 2011-05-10
The only partition that seems remotely full is /usr/local

My only other suggestion is to file a bug report.

---

### Post by bvargo on 2011-05-10
I am not sure how the /usr/local partition got there or if it is even from this version of ubuntu.  I started with 10.10 on this new HDD and when I saw natty was out, I decided to give it a try.  I didn't like it and went back to maverick.  If i cd /usr/local/bvargo/Desktop what I see there is what I expect, i.e. what is on my desktop.

If I go about reinstalling, is there any way I can do it without reformatting?  Of specific concern is not having to reinstall all of my extensions for FF4.  You might have been able to tell that my home directory is on another partition from the main install.

---

### Post by bodhi.zazen on 2011-05-10
The advantage of a separate home partition is that you can easily re install.

Before you do that, boot the live CD and try to install the package, just to make sure it is not a broken package.

---

### Post by bvargo on 2011-05-10
Ok, I'm presently booted from Live 10.10 CD.  I went to terminal and did a sudo apt-get update and then a sudo apt-get upgrade.  It said that it ran out of space.  How do I tell it to do it on /dev/sda1?

---

### Post by bodhi.zazen on 2011-05-11
Reboot the live CD and install the single package, not apt-get upgrade (which installs many many packages, thus you ran out of space).

---

### Post by bvargo on 2011-05-11
It appears that I was able to get apt-get to work by doing the following (and I apologize, there are two variables here and I can't say which fixed the problem):

boot from live CD
sudo apt-get update
sudo apt-get upgrade

then the aforementioned problem with running out of space (which doesn't seem possible given the size of my drive)

boot from live CD
sudo apt-get update
sudo apt-get install libperl5.10
then via FF, install Flash.  It seemed to indicate that it wasn't working, but when I rebooted into the OS and I did the update/upgrade, it went off without a hitch.  Now onto my next problem, networking not restarting when the computer goes into suspend/hibernate.

---

