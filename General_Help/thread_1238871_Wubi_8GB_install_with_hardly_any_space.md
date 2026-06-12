---
title: "Wubi 8GB install with hardly any space?"
date: 2009-08-12
forum: General Help
---

### Post by afogl001 on 2009-08-12
I'm somewhat new to Ubuntu but I did mess with 8.04 for awhile some I'm not completely in the dark.  Anyway, I did a fresh Wubi install of 9.04 with 8GB virtual partition but after installing three small games (UT, SShock2, and Blood 2) I had less than a 1GB left.  I don't remember the 8.04 system taking up so much space, but is 9.04 different?  

Also, I used LVPM to expand to 9 GB thinking that would fix some kind of glitch but nope, just added a GB of space, so now I have a whooping 1.5GBs...  Am I missing something?

---

### Post by starcraft.man on 2009-08-12
> **afogl001 said:**
> I'm somewhat new to Ubuntu but I did mess with 8.04 for awhile some I'm not completely in the dark.  Anyway, I did a fresh Wubi install of 9.04 with 8GB virtual partition but after installing three small games (UT, SShock2, and Blood 2) I had less than a 1GB left.  I don't remember the 8.04 system taking up so much space, but is 9.04 different?  

Also, I used LVPM to expand to 9 GB thinking that would fix some kind of glitch but nope, just added a GB of space, so now I have a whooping 1.5GBs...  Am I missing something?

The default 9.04 install is only about 2GB. Something definitely wrong, know how big the game installs are? I don't really wager that covers it, I can't fathom what took all your space. Use the disk space analyzer to figure it out.

Applications > Accessories > Disk Usage Anaylzer. Fiddle around till ya find the places taking all your space. If it's still not apparent, I'd just reinstall.

---

### Post by afogl001 on 2009-08-13
Good to know I'm not crazy.  I'll check it out an post with what I find.

---

### Post by Yvan300 on 2009-08-13
Urban terror is a 700mb game and quickly rises to well over 1gb as you download more maps, why not just check how much space each game consumes so that you will know if they are the cause of the problem.

---

### Post by afogl001 on 2009-08-13
Actually, after thinking about it, I did install quite a few applications from the repository, including a number of games.  I guess I didn't think they took up so much space.  While I was thinking it may have been a bad install (windows crashed in the middle, then I reinstalled over the original) I think it had more to do with me underestimating the size of some of those applications.  

In any case, I just did another clean install, one great thing about Wubi Ubuntu is how easy it is to set up.  I was wondering though, what are some of the standard directories for the Add/Remove application, such as where "Games" and "Sound & Video" are located?  Thanks.

---

### Post by matthewbpt on 2009-08-13
Run 'sudo apt-get clean' to clear the cache of downloaded debs which you dont need anymore, I find this often clears lots of space which I didn't know was being taken up.

---

### Post by Yvan300 on 2009-08-13
What you mean, you just click on the games category so that you will install games only :)

---

### Post by afogl001 on 2009-08-14
Wow, the get-apt clean command cleaned up 500 MB of space, I'll have to remember that one.  Any other good hard drive cleaning tips to get the most out of limited space?

---

### Post by afogl001 on 2009-08-16
Alright, it's happened again.  I increased my wubi size to 10 GB, installed <3 GB of games, and now I have less than .7 GB again. I thought it might have been that Windows was compressing the file but I checked it and neither the partition it's on is compressed nor was it smaller (properties said it was still 10 GB).

 Here is a list of some larger files, maybe I can pinpoint where all this free space is going.

var = 4.1 GB
usr = 1.8 GB
home = .96 GB

These are the three largest folders,  everything else together is 1.8 GB (except "host, which obviously has all my windows folder on the partition which is more than 56GB)  So it looks like it all adds up, but I know I didn't install >6 GB worth of stuff.  So...

Is my "var" folder supposed to be that big?

---

### Post by geirha on 2009-08-16
Try to find out what's taking up so much space in /var, 

```

du -x --max-depth=1 /var/ | sort -n
du -x --max-depth=1 /var/large_dir/ | sort -n
...

```

---

### Post by drs305 on 2009-08-16
afogl001,

Although it is not written specifically for wubi, the "DiskSpace" link in my signature line goes through a list of things to check when free disk space seems to 'disappear'. 

As was mentioned, your /var folder is pretty large and you probably have some very big log files in there that can be removed.

---

### Post by afogl001 on 2009-08-16
Okay, I went through and these are the big ones.  As you can see, they are all in my var/log, which is 3.9GB

/var/log/kern.log = 400mb
 
/var/log/kern.log.0 = 930mb

/var/log/messages = 400mb

/var/log/messages.0 = 930mb

/var/log/syslog = 400mb

/var/log/syslog.0 = 930mb

Can I delete any of this or does ubuntu need it?  Any ideas on why I have copies of the giant files?
Oh, and thank you guys so much for helping!

---

### Post by geirha on 2009-08-18
Those are log files, and if they're that big, then there's probably something wrong somewhere that produces insane ammounts of log messages. Have a look inside and see what the most messages are.

The log files are regularly rotated, that is logfile is renamed to logfile.0, and next logrotation, logfile.0 is gziped and moved to logfile.1.gz, while logfile becomes logfile.0 etc... After 5 (iirc) such rotations the oldest file is removed.

The log files are not vital, so they may be removed. They're only there for the system administrator(s) to be able to see what's going on in the system.

---

### Post by afogl001 on 2009-08-18
Great, thank you.  I deleted them and they haven't gotten nearly that size now, must have been from updating or something.

---

