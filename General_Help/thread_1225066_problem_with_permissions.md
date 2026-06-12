---
title: "problem with permissions"
date: 2009-07-28
forum: General Help
---

### Post by kolbiel on 2009-07-28
OK, this is what happened last night:

i installed few new themes following this link: [http://francois.vogelweith.com/?page_id=28&lang=en]("http://francois.vogelweith.com/?page_id=28&lang=en"), all the themes were fine, but when i tried to fire up synaptic an error poped out saying there's not enough free space.... that was weird.. so i tried to open update manager - same error.  after restarting ubuntu something strange happened - ubuntu's default theme was on, it didn't remember my wireless' WPA key, all the bookmarks from firefox were gone (never got to backing them up - that's a lesson learnt hard way), and (i think) something's wrong with my permissions - when i opened thunderbird it got connected to my accounts BUT it didn't download any emails 'cause i didn't have permission to access/write thunderbird inbox.... the same thing happens in other applications....

i need some help fast... anyone?

---

### Post by nikhilk on 2009-07-28
> **kolbiel said:**
> OK, this is what happened last night:

i installed few new themes following this link: [http://francois.vogelweith.com/?page_id=28&lang=en]("http://francois.vogelweith.com/?page_id=28&lang=en"), all the themes were fine, but when i tried to fire up synaptic an error poped out saying there's not enough free space.... that was weird.. so i tried to open update manager - same error.

Are you sure that you are really not out of disk space?

Check output of
```
df -H
```

---

### Post by kolbiel on 2009-07-28
yeah, i'm sure there's at least 2-3 gb of free space...

---

### Post by nikhilk on 2009-07-28
> **kolbiel said:**
> yeah, i'm sure there's at least 2-3 gb of free space...

OK, to be more precise, is your "/home" on a separate partition? If yes, is there disk space on your "/home" partition, regardless of space on "/" partition?

---

### Post by kolbiel on 2009-07-28
no, it's all on one partition, mate

---

### Post by nikhilk on 2009-07-28
> **kolbiel said:**
> no, it's all on one partition, mate

So, that rules out a disk space problem.

Could you check and post back the permissions of your home folder
```
ls -l /home
ls -l /home/<your username>
```

---

### Post by kolbiel on 2009-07-28
sure, as soon as i'm back home from work ;)

edit:

ok, this is what came out:

[IMG]http://i32.tinypic.com/2aeqxck.jpg[/IMG]

i also checked df -H, and there are some strange things shown there:
Filesystem             Size   Used  Avail Use% Mounted on
/host/ubuntu/disks/root.disk
                       6.4G   6.0G    82M  99% /
tmpfs                  1.9G      0   1.9G   0% /lib/init/rw
varrun                 1.9G   222k   1.9G   1% /var/run
varlock                1.9G      0   1.9G   0% /var/lock
udev                   1.9G   181k   1.9G   1% /dev
tmpfs                  1.9G    78k   1.9G   1% /dev/shm
/dev/sda2               11G   8.9G   2.0G  83% /host
lrm                    1.9G   2.3M   1.9G   1% /lib/modules/2.6.28-13-generic/volatile
/dev/sda3              107G    67G    41G  63% /media/SYSTEM
overflow               1.1M    29k   1.1M   3% /tmp
/dev/sda5              2.7G   2.2G   525M  81% /media/MEDIADIRECT



what the hell is dev/sda2 (8.9G) and dev/sda3 (67G)?? i tried to browse to those folders, but they do't seem to be that big... whole /dev folder is just 1.7G.....

i seriously need some help now... or i'm doomed to go back do vista..... :/

edit2: ok, i know what sda3 is - that's the bloody vista, but still no idea what the sda2 is.... ALSO, i've noticed that ubuntu forgot/lost ALL of my settings/prefrences in all aplications - some of the aplications are lost as well.... think only thunderbird and pigeon have all they're settings, apart from that is like brand new system..... bloody hell.....

edit3: just started off thunderbird and it started downloading all messages from january 2008! means it's not good either....

---

### Post by kolbiel on 2009-07-28
anyone?

---

### Post by NoOne121 on 2009-07-28
did you use wubi install method?

---

### Post by kolbiel on 2009-07-28
> **NoOne121 said:**
> did you use wubi install method?

yes

---

