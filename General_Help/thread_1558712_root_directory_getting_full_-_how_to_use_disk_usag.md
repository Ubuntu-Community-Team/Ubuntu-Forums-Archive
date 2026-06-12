---
title: "root directory getting full - how to use disk usage analyzer to trim it?"
date: 2010-08-22
forum: General Help
---

### Post by finny388 on 2010-08-22
I have root on sda1 and home on sdb1.

I am getting close to full and wanted to analyze what apps or files are taking up the most room.

How do I navigate to sda1 in Disk Usage Analyzer?

"/" says 100% 121.5GB in dua (see attached screenshot)

thanks

```

df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             3.7G  3.2G  317M  92% /
none                  493M  340K  493M   1% /dev
none                  497M  2.5M  495M   1% /dev/shm
none                  497M  492K  497M   1% /var/run
none                  497M     0  497M   0% /var/lock
none                  497M     0  497M   0% /lib/init/rw
/dev/sdb1              14G   12G  2.2G  84% /home
/dev/sdc1             112G   98G   15G  88% /media/120GB
/dev/sdd1              15G   11G  4.6G  70% /media/SD_EEE_16GB
```

---

### Post by ajgreeny on 2010-08-22
I think your / partition was much too small to start with, but nevertheless I agree that the dua is very confusing in the way it shows the file system usage; mine also shows / as 100%, when it is in fact 38% full as shown by System Monitor and the df command.

If you can do so, I think it will be worth using a live CD and enlarging your / partition to about 8 -10GB with gparted, giving plenty of overhead for activities in the root file system.  What else is on the sda disk?   I presume there is some other OS taking up more space and that you can borrow or steal some from that.

I think your screenshot shows the nearest you can get to showing just sda1, which even though your /home is on a separate partition, it is still within the file system as far as linux is concerned, so still shows in dua.

---

### Post by finny388 on 2010-08-22
These aren't partitions. My netbook is an eee-pc with a 4GB SSD + 16GB SSD.

I am pretty stuck with 4GB.

I'm also not dual-booting: just a clean install of Ubuntu 10.04 when it came out.

I guess I can just fish around the / folder and ignore /home as part of the issue.

I'm concentrating on /usr/lib. I'm going to uninstall Open Office - looks like the biggest app.

Is there no tool like in Windows to show the footprint of installed software? That would be so welcome in Synaptic.

---

### Post by drs305 on 2010-08-22
I wrote the following post to help try to find out why free space slowly or suddenly disappears. In your case, I don't think you are really having the most common problems, such as undeleted trash, really large log files or backups made to the wrong partition.

Nevertheless, you might find some commands in the post useful, such as finding large files. There is also a section on Disk Usage Analyzer (and how it can be confusing).
[HOWTO: Recover Lost Disk Space]("http://ubuntuforums.org/showthread.php?t=1122670")

And don't forget to remove downloaded packages, which aren't necessary to keep on your system: "sudo apt-get clean && sudo apt-get autoclean"

---

### Post by Asmodai on 2010-08-22
> That would be so welcome in Synaptic. 	
Synaptic already has that (see screenshot). You can activate the "installed size" column in the settings if it's now shown for you.

---

### Post by manthony121 on 2010-08-22
My favorite way to see where all my disk space is going (from terminal):

$ sudo du /|sort -gr|more

---

### Post by finny388 on 2010-08-23
thanks all

Asmodai, I mistook Ubuntu Software Center for Synaptic.

Now I can see Size. thanks

---

### Post by finny388 on 2010-08-23
> **manthony121 said:**
> My favorite way to see where all my disk space is going (from terminal):

$ sudo du /|sort -gr|more

are you sure that is correct?

I get this:
```
du: cannot access `/home/eeepc/.gvfs': Permission denied
du: cannot access `/proc/19329/task/19329/fd/4': No such file or directory
du: cannot access `/proc/19329/task/19329/fdinfo/4': No such file or directory
du: cannot access `/proc/19329/fd/4': No such file or directory
du: cannot access `/proc/19329/fdinfo/4': No such file or directory
```

---

### Post by manthony121 on 2010-09-02
> **finny388 said:**
> are you sure that is correct?

I get this:
```
du: cannot access `/home/eeepc/.gvfs': Permission denied
du: cannot access `/proc/19329/task/19329/fd/4': No such file or directory
du: cannot access `/proc/19329/task/19329/fdinfo/4': No such file or directory
du: cannot access `/proc/19329/fd/4': No such file or directory
du: cannot access `/proc/19329/fdinfo/4': No such file or directory
```


Yes, it's correct.  Running 'du' on the root directory ('du /') can take a LONG time to read all the directories and sort the output, so after getting the above errors, it should eventually give you the list you want.  You can also run 'du' from the current directory by just using 'du' without the '/', or specify the directory to start in ('du /usr').  If you don't like the error messages, try this:

```

$ sudo du / 2>/dev/null |sort -gr| more
```

---

### Post by Jbike on 2010-09-04
I have the same problem on an eeepc1000. Mine comes with a fast 8G ssd as well as a slower 32G ssd, and I too installed the root on the 8G, and /home  on the 32G. I have uninstalled everything that I could and still I only have 10% free. I will take a look at your references drs305 to see if I can fix this myself. It seems strange to me that I can uninstall LOTS of software and still cannot free-up any space. All of my usage is in  /usr as shown below, with /usr/bin and /usr/lib quite heavy.

jbike3@jbike3-netbook:/usr$ ls -l
total 228
drwxr-xr-x   2 root root 69632 2010-09-04 14:56 bin
drwxr-xr-x   5 root lp    4096 2009-12-12 08:35 Brother
drwxr-xr-x   2 root root  4096 2010-09-04 14:33 games
drwxr-xr-x  66 root root 12288 2010-09-04 14:55 include
drwxr-xr-x 250 root root 94208 2010-09-04 14:55 lib
drwxr-xr-x   3 root root  4096 2010-01-02 10:37 lib64
drwxr-xr-x  11 root root  4096 2010-03-22 18:22 local
drwxr-xr-x   3 root root  4096 2010-03-06 11:39 man
drwxr-xr-x   2 root root 12288 2010-08-27 18:44 sbin
drwxr-xr-x 379 root root 12288 2010-09-04 14:55 share
drwxrwsr-x  18 root src   4096 2010-06-05 05:37 src
jbike3@jbike3-netbook:/usr$ 


Jbike

---

### Post by drs305 on 2010-09-04
Jbike,

Take a look at the guide, and if you don't come up with a solution reply in that thread since this thread 'belongs' to finny388, your post doesn't necessary involve disk usage analyzer specifically, and has been marked "SOLVED" by the OP.
[HOWTO: Recover Lost Disk Space]("http://ubuntuforums.org/showthread.php?t=1122670")

---

### Post by Jbike on 2010-09-04
interesting... gksudu nautilus reports the following for /usr 
343,509 items, totalling 3.5 GB

while sudo du -h --max-depth=1 / | grep '[0-9]G\> reports 4.2G usage for /usr (see below) which one is correct?

jbike3@jbike3-netbook:~$ sudo du -h --max-depth=1 / | grep '[0-9]G\>' 
[sudo] password for jbike3: 
4.2G	/usr
1.7G	/media
du: cannot access `/home/jbike3/.gvfs': Permission denied
1.2G	/home
du: cannot access `/proc/4170/task/4170/fd/4': No such file or directory
du: cannot access `/proc/4170/task/4170/fdinfo/4': No such file or directory
du: cannot access `/proc/4170/fd/4': No such file or directory
du: cannot access `/proc/4170/fdinfo/4': No such file or directory
8.2G	/
jbike3@jbike3-netbook:~$

---

### Post by drs305 on 2010-09-04
> **Jbike said:**
> interesting... gksudu nautilus reports the following for /usr 
343,509 items, totalling 3.5 GB

while sudo du -h --max-depth=1 / | grep '[0-9]G\> reports 4.2G usage for /usr (see below) which one is correct?


I ran the *du* command with the "--apparent-size" option and the results were basically the same as that with "*gksu nautilus*". You can read about the various *du* options by typing "*man du*" in a terminal.

Without the switch, the descrepancy in my results were about the same as yours, although less disk space in each case: 3.0 vs 2.7

---

### Post by dcstar on 2010-09-04
> **finny388 said:**
> I have root on sda1 and home on sdb1.

I am getting close to full and wanted to analyze what apps or files are taking up the most room.

How do I navigate to sda1 in Disk Usage Analyzer?
.......
The Disk Usage Analyzer only runs in user mode, for full access do:
```
gksudo baobab
```

---

