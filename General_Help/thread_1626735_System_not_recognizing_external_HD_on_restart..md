---
title: "System not recognizing external HD on restart."
date: 2010-11-20
forum: General Help
---

### Post by nlambert on 2010-11-20
Hello!

My system doesn't recognize my external HD when I restart. I have to unlug and replug it in every time. Is there a command I could add to startup apps that would do this for me?

Thanks,
Nathan

---

### Post by nlambert on 2010-11-20
After some more searching, I found out about the storage device manager (pysdm) and about editing fstab manually. Still, I cannot get the external to mount automatically on startup.

When I reboot I get this during startup:

*The disk drive for /media/myexternalhd is not ready yet or not present*

and when I try to open pysdm, it doesn't respond unless I unplug and replug in my external. I don't even see it listed when I type in *ls -l /dev/disk/by-uuid*

From what I can tell, it does no good to edit fstab or use pysdm because the computer doesn't recognize the external until I have unplugged/replugged it.


.... any ideas, guys?

---

### Post by dcstar on 2010-11-20
> **nlambert said:**
> Hello!

My system doesn't recognize my external HD when I restart. I have to unlug and replug it in every time. Is there a command I could add to startup apps that would do this for me?

Thanks,
Nathan

```
partprobe
```

---

### Post by nlambert on 2010-11-20
I looked into partprobe, and it doesn't look like it will help me with my problem. I can't do anything like:

partprobe /dev/sdb1

because my system doesn't even recognize sdb1 or the device's UUID as being there until I unplug/replug my HD.

It is listed when I use *lsusb *whenever it is plugged in, regardless of whether I unplugged/replugged it or not.

---

### Post by dcstar on 2010-11-20
> **nlambert said:**
> I looked into partprobe, and it doesn't look like it will help me with my problem. I can't do anything like:

partprobe /dev/sdb1

because my system doesn't even recognize sdb1 or the device's UUID as being there until I unplug/replug my HD.

It is listed when I use *lsusb *whenever it is plugged in, regardless of whether I unplugged/replugged it or not.
[B]
sudo partprobe[/B] looks for all partitions - do **not** put anything after it.

---

### Post by nlambert on 2010-11-21
thanks for the replies dcstar.

i did** sudo partprobe** and it just hung for 2-3 minutes, and went back to prompt- no output.

i wonder if all of this has something to do with a power-saving feature of the drive (it's a seagate freeagent HD):

[http://www.theinquirer.net/inquirer/news/1021483/seagate-releases-workaround-linux-users](http://www.theinquirer.net/inquirer/news/1021483/seagate-releases-workaround-linux-users)

i connected it to my windows machine, and disabled the power-saving mode. also, i got sdparm and ran [B]sudo sdparm --clear STANDBY -S /dev/sdb

[/B]starting to think that there is no solution. :(

---

### Post by nlambert on 2010-11-21
I know this might be sloppy, but is there a command I could run on startup that would simulate unplugging/replugging in my HD?

It is listed under lsusb as:

Bus 001 Device 005: ID 0bc2:2300 Seagate RSS LLC

Thanks.

---

### Post by dcstar on 2010-11-22
> **nlambert said:**
> thanks for the replies dcstar.

i did** sudo partprobe** and it just hung for 2-3 minutes, and went back to prompt- no output.
.........

There is no output, this shows a summary of detected partitions:

```
sudo partprobe -s
```

---

