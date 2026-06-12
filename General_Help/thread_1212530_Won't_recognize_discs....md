---
title: "Won't recognize discs..."
date: 2009-07-13
forum: General Help
---

### Post by Gizenshya on 2009-07-13
It was working fine earlier, now nothing.  I put in music, and nothing.  Movie and nothing.  Blank disc and nothing

I did sudo lshw -C disk and here is what it gave me for the drive:

```
  *-cdrom
       description: DVD reader
       product: DVD-ROM SD-616E
       vendor: SAMSUNG
       physical id: 0.0.0
       bus info: scsi@16:0.0.0
       logical name: /dev/cdrom1
       logical name: /dev/dvd1
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: F503
       capabilities: removable audio dvd
       configuration: status=nodisc

```

note: status=nodisc

tha is incorrect, but I can't seem to fix it.  I have to burn a disc, and the comp is in the middle of something else that's going to take a while, and I can't restart it.

I've had this problem several times.  With this and Flash, Ubuntu does well, but just deteriorates over time until it just stops working with them altogether, then reset and it's all peachy for another day or two.


```
guest@desktop:~$ uptime
 19:36:45 up 2 days,  8:49,  4 users,  load average: 0.37, 0.19, 0.20
```

all the users are me, btw.

Sometimes it gets "stuck."  If I'm watching a movie, when I put another one in later, it won't read the disc, but it has the label of the other DVD.  But right now it just says it's empty.

ls -a of cdrom0 simply gives me ". .."

:(

edit: just noticed.  above in the first code I posted, it calls it cdrom1, among other things.  if I try to cd there, there is no such file or directory.  Is it still cdrom0 or cdrom1?  It used to be cdrom0, and I can cd to cdrom0, and that's where I used the ls -a.  I don't know what all that means, or if it matters, though.

---

### Post by Gizenshya on 2009-07-13
just restarted, and restarting doesn't help.

if I open the try, it shows tha it's open.  When I close it, no matter what's in it, it says no disc.

I've tried two different drives, same thing.

any ideas?

---

