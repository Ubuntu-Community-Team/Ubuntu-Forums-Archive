---
title: "Where's my disk space?"
date: 2009-07-11
forum: General Help
---

### Post by Nathanael Culver on 2009-07-11
Where's my disk space?

I've seen the thread here: [http://ubuntuforums.org/showthread.php?t=1210322](http://ubuntuforums.org/showthread.php?t=1210322)

but it doesn't help in my case.

I have a 160gb hard drive partitioned into a 4gb swap partition, a 16gb system partition mounted at root (/), and a 138gb partition (sda6) mounted at /home. I currently have only one user account (my /home contains only three dirs -- cj3, .Trash-0 and Lost+Found), and I keep running out of disk space.

```

cj3@cj3-laptop:~$ df -H
Filesystem             Size   Used  Avail Use% Mounted on
/dev/sda5               17G   2.4G    13G  16% /
tmpfs                  1.2G      0   1.2G   0% /lib/init/rw
varrun                 1.2G   111k   1.2G   1% /var/run
varlock                1.2G      0   1.2G   0% /var/lock
udev                   1.2G   148k   1.2G   1% /dev
tmpfs                  1.2G    78k   1.2G   1% /dev/shm
lrm                    1.2G   2.9M   1.1G   1% /lib/modules/2.6.28-11-generic/volatile
/dev/sda6              138G   126G   4.9G  97% /home

```

```

cj3@cj3-laptop:~$ du -sh -c /home/cj3/*
514M	/home/cj3/AMR
67M	/home/cj3/Application Data
4.0K	/home/cj3/blocked_outbound_ip.data
4.0K	/home/cj3/blocked_outbound_ip.data~
8.0K	/home/cj3/BT Headset.txt
6.0M	/home/cj3/Colver-Culver.gdb
661M	/home/cj3/Desktop
4.0K	/home/cj3/dirlist
235M	/home/cj3/Documents
127M	/home/cj3/DosBox
8.0K	/home/cj3/dosbox.conf
1.6G	/home/cj3/Downloads
4.0K	/home/cj3/dvdrip-data
12K	/home/cj3/EBook Maestro
4.0K	/home/cj3/enc
4.0K	/home/cj3/enc.sh
0	/home/cj3/Examples
28M	/home/cj3/firefox
45M	/home/cj3/Games
6.7M	/home/cj3/g_BVoR3b.pdf
1.7G	/home/cj3/Genealogy
3.0M	/home/cj3/help
132K	/home/cj3/iMacros
4.0K	/home/cj3/installthese.txt
4.0K	/home/cj3/iphone screens.txt
113M	/home/cj3/Literature
12K	/home/cj3/mail
4.0K	/home/cj3/MainData.log
325M	/home/cj3/Music
4.0K	/home/cj3/Network Configuration.txt
670M	/home/cj3/Personal Documents
4.0K	/home/cj3/pgp_key.txt
2.1G	/home/cj3/Pictures
2.9G	/home/cj3/PortableApps
15G	/home/cj3/Projects
4.0K	/home/cj3/Public
4.0K	/home/cj3/Reset Compiz to all defaults.txt
4.0K	/home/cj3/Templates
884K	/home/cj3/Themes
4.0K	/home/cj3/TryMe
36K	/home/cj3/virtual-drives
20G	/home/cj3/Virtualization
76K	/home/cj3/winetricks
45G	total

```

However, the du command doesn't include dotted directories, of which I have 82, totaling about 19gb.

Disk Usage Analyzer's summary reports total capacity 143gb, used 119.1gb available 23.8gb, but shows my home directory (/home/cj3) using only 64.4gb.

/home/cj3 has no .Trash, but /home has both a .Trash and a Lost+Found; currently they combine for 2mb.

So from what I can tell, I'm currently using about 65gb on a ca. 140gb partition; yet I only have about 5gb available. Where's my other 70gb?

NathanaelCulver

---

### Post by michy99 on 2009-07-11
You say /home/cj3 has no .Trash, but there should be a Trash at /home/cj3/.local/share/Trash. You might want to have a peek in there.

---

### Post by niteshifter on 2009-07-11
Hi,

Try using du like this:
```
du -sh /home/cj3
```

There's a big difference between the above and:
> du -sh -c /home/cj3/*

The first has du looking at all of folder cj3. In the second, shell expansion of * is doing you in (with the -s switch).

And +1 what michy99 said ;) Either that or there's way to much space reserved on the volume for root.

---

### Post by ibuclaw on 2009-07-11
```
sudo du --max-depth=1 -h -c /home/cj3 | grep G
```

Regards
Iain

---

### Post by Nathanael Culver on 2009-07-11
> **michy99 said:**
> there should be a Trash at /home/cj3/.local/share/Trash.

Ah, THAT's where that thing is -- I can never remember.

Thanks also to Niteshifter for replying, but this one gets filed under DOH! Turns out in checking the contents of /home/.Trash-0 (in Nautilus) I neglected to unhide the hidden stuff. Lo and behold -- 52gb worth.

```

cj3@cj3-laptop:~$ du -sh /home/cj3
65G	/home/cj3
cj3@cj3-laptop:~$ df -H
Filesystem             Size   Used  Avail Use% Mounted on
/dev/sda5               17G   2.4G    13G  16% /
...
/dev/sda6              138G    70G    62G  54% /home

```

Puts me right about where I should be (except I don't understand why 70 + 62 = 138 :-) ).

Sorry to have bothered y'all.

NathanaelCulver

---

