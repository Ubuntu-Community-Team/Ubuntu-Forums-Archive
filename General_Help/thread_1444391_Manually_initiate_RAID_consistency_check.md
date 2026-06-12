---
title: "Manually initiate RAID consistency check?"
date: 2010-04-01
forum: General Help
---

### Post by danielcheng on 2010-04-01
Hi,
I have a mdadm RAID5 configuration on my Ubuntu Server (64-bit). In the first week after I configured the RAID, mdadm itself initiated a consistency check automatically. But after that, it won't check the RAID anymore. (the server isn't on 24/7, normally a few hours a day)

I've read a post for manually initiating consistency check with these commands
```
sudo su -
echo check >> /sys/block/md0/sync_action
```but under that directory /sys/block/md0/
there are only 
```
alignment_offset  holders/          removable         subsystem/
bdi/              md/               ro                trace/
capability        power/            size              uevent
dev               queue/            slaves/
ext_range         range             stat

```but no "sync_action"

can anyone help? thanks...

---

### Post by pluvoj on 2010-10-04
Hi!

I found your thread via google and i got an answer for you. Try:
```
echo check > /sys/block/md0/md/sync_action
```

I hope it works :)

Or you can use this tool:
```
/usr/share/mdadm/checkarray --idle md0
```

```
/usr/share/mdadm/checkarray --help
```

---

### Post by danielcheng on 2010-10-05
the first one works perfectly, thanks a lot
it is really out of my expectation to receive the notification from the forum that i have a new reply to my inquiry :)

---

### Post by pedricus on 2011-04-21
Thanks for the command! took me a bit to find the right wording in Google for it :)

does anyone know if there is a command to manually stop the disk check, instead of just killing the process?

---

