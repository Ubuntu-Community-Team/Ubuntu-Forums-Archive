---
title: "Hard disk gets filled!"
date: 2010-07-15
forum: General Help
---

### Post by davoudi on 2010-07-15
I have been recently faced with a strange problem. I received an error that the hard disk is almost full. I have a 500 GB hard disk in which 350 GB of is for Ubuntu. I found a series of folders in proc directory. I don't know why they are created and left there. I am using ubuntu 10.04.

Thanks for your time.

---

### Post by linux18 on 2010-07-15
The proc directory is a special directory for "tasks" all the stuff running through the processor originates in the proc directory. Don't touch it those are necessary for your computer to run and dont acctually take up disk space ( maybe a few KB ). I assume you used du or df and proc sprouted up 100 permission denied errors? if your running out of space on a 350 GB hard drive your /home directory is to blame unless you have an ungodly amount of log files and packages installed. use the disk usage analyzer and scan the filesystem then report back with the size of each entry. example: /var 900 MB


If I know where your "mess" is I can help fix it.

---

### Post by hansdown on 2010-07-15
Hi davoudi.

Don't worry about the  /proc directory.

It's a virtual directory, and doesn't take up hard drive space.

Here's a link, that explains it better.

[http://it.toolbox.com/blogs/locutus/what-does-this-proc-directory-do-17379](http://it.toolbox.com/blogs/locutus/what-does-this-proc-directory-do-17379)

If you want to clean up some old files, do these commands in a terminal.

```
sudo apt-get clean
```

```
sudo apt-get autoclean
```


More info.

[http://forum.eeeuser.com/viewtopic.php?id=64986](http://forum.eeeuser.com/viewtopic.php?id=64986)

---

### Post by linuxman94 on 2010-07-15
Could you post the output of this command, please?

```
df -h
```

---

### Post by davoudi on 2010-07-15
I had to restart my computer since nothing was functional and everything turned to normal after restart. I checked all directory and they were all fine. They only  directory which returned wierd size was /proc 120 TB! That was the second time that I was faced with the same problem. I was running a program under MonoDevelope several times and I am wondering if the problem is due to terminiating the program. It seems to me that this problem starts everytime I use my computer for heavy calculation.

---

### Post by linuxman94 on 2010-07-15
Please read my previous post.

---

### Post by davoudi on 2010-07-15
> **linuxman94 said:**
> Could you post the output of this command, please?

```
df -h
```

Now things are normal, I will post the output of the command next time I have the same problem. Thing are fine now after a restart.

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             301G   16G  270G   6% /
none                  1.9G  324K  1.9G   1% /dev
none                  1.9G  9.4M  1.9G   1% /dev/shm
none                  1.9G  336K  1.9G   1% /var/run
none                  1.9G     0  1.9G   0% /var/lock
none                  1.9G     0  1.9G   0% /lib/init/rw

---

### Post by linuxman94 on 2010-07-15
Yes, everything looks OK.

---

### Post by linux18 on 2010-07-15
You shouldn't be experiencing low disk usage messages....strange.

---

### Post by davoudi on 2010-07-16
I just start working with my computer and there is 10% of extra HD used:

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             301G   42G  244G  15% /
none                  1.9G  324K  1.9G   1% /dev
none                  1.9G  9.1M  1.9G   1% /dev/shm
none                  1.9G  324K  1.9G   1% /var/run
none                  1.9G     0  1.9G   0% /var/lock
none                  1.9G     0  1.9G   0% /lib/init/rw

---

### Post by HermanAB on 2010-07-16
Have a look in /var/log for junk files that are not rotated, then fix /etc/logrotate.conf

---

### Post by davoudi on 2010-07-16
> **HermanAB said:**
> Have a look in /var/log for junk files that are not rotated, then fix /etc/logrotate.conf
The total size of file in /var/log is less than 200 MB.

This is the new output

df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             301G   58G  228G  21% /
none                  1.9G  324K  1.9G   1% /dev
none                  1.9G  9.5M  1.9G   1% /dev/shm
none                  1.9G  324K  1.9G   1% /var/run
none                  1.9G     0  1.9G   0% /var/lock
none                  1.9G     0  1.9G   0% /lib/init/rw

---

### Post by davoudi on 2010-07-16
I found the problem. It was a hidden file called .xsession-errors in my home directory. It seems that there is a problem with davmail, all error in connecting to exchange 2007 are sent to the file leading to a huge file!

---

### Post by davoudi on 2010-07-16
Solved. The upgrate lightning &  thunderbird resolved  the problem of davmail in producing endlist errors. Thanks for your time.

---

### Post by linuxman94 on 2010-07-16
Great! Please mark your thread as solved using Thread Tools at the top of this page

---

### Post by jokes_finder on 2010-07-17
hello, guys!

well, I've the same problem here as davoudi
-I'm new to Ubuntu -
I've installed ubuntu 9.10 on a 10GB partition
Ubuntu doesn't read except 3GB
when I tried "df -h"
here's the output:
"Filesystem            Size  Used Avail Use% Mounted on
/dev/loop0            2.7G  2.2G  350M  87% /
udev                  1.3G  288K  1.3G   1% /dev
none                  1.3G  936K  1.3G   1% /dev/shm
none                  1.3G   96K  1.3G   1% /var/run
none                  1.3G     0  1.3G   0% /var/lock
none                  1.3G     0  1.3G   0% /lib/init/rw
"

when I was upgrading to the newer version of ubuntu, it screamed for more space claiming that I only have about 300 or 500 MB free space - don't remember -:shock:

I found the file .xsession-errors - there's another one called .xsession-errors.old - but don't know what to do with it..:confused:

need help guys
thanks in advance

---

