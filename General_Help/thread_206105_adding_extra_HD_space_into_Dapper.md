---
title: "adding extra HD space into Dapper"
date: 2006-06-29
forum: General Help
---

### Post by herot on 2006-06-29
ok, i have Dapper installed and i had my 2 windows partitions intact... i had a 10GB for "C" drive and a 40GB "D" drive where i kept all my data and programs...

i needed more space for my Dapper installation... so i formated my old windows "D" partition to an ext3 filesystem...

now it no longer shows up on my desktop as a drive... AND i have to mount it everytime i reboot... before i formatted it, it showed up as a "drive" icon on my desktop and was easy to get to... 

i don't want to have to mount and then navigate to /media/hdb5 to get access to this partition everytime... is there anyway to make it show as a "drive" again?? (and automount of course)

---

### Post by jonrkc on 2006-06-29
Try putting a line like this into your /etc/fstab file:
```

/dev/hdb5       /media     ext3    defaults,errors=remount-ro 0       1

```
Then issue "sudo mount -a" to remount all devices without having to reboot, and see how it shows up after that.

---

### Post by herot on 2006-06-29
can i make it show up as a drive (like my usb drive and my windows "C" drive)???

---

### Post by herot on 2006-06-30
how can i make a link to my /media/storage filesystem (ext3)??? i tried but it wont let me...

it makes me browse through the filesystem to find it each time...

---

