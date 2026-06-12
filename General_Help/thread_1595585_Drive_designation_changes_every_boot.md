---
title: "Drive designation changes every boot"
date: 2010-10-13
forum: General Help
---

### Post by sibutt on 2010-10-13
I have a line in fstab to auto mount a drive partitian

/dev/sdb1                    /media/Data    ext4        defaults    0    2

This worked fine until I upgraded to 10.10.

Now every boot I get  the following message on the purple boot splash screen;

                /media/Data is not ready yet or not present

                S to Skip M manual etc

When I looked at gparted the drive had changed from sdb to sdf.  I changed fstab and then ran 
sudo mount -a
I then access /media/Data  as expected, that is until I reboot then I get the same message and find that the drive has swapped to sdb again.

This happens every boot, If it was sdb on the last boot it becomes sdf on this boot and vice-versa.

Thanks in advance
Unbuntu 10.10 upgraded from 10.04  (64 bit)

---

### Post by stinkeye on 2010-10-13
Try changing your fstab entry to use the uuid.
In the terminal, to get your uuid.
```
sudo blkid
```

eg
my old entry
```
/dev/sda5 /media/UBUP ext3 auto,defaults,rw  0   0
```


new fstab entry using uuid
```
UUID=9c04ea8b-889a-4b40-989a-dcb51cba0db7 /media/UBUP  ext3 auto,defaults,rw  0   0 
```

When I upgraded I had my mp3 player plugged in which stuffed things around a bit.

Even now for some reason I'm getting 2 occurrences of UBUP in the nautilus side pane.
Edit: Ha, I've now got 3 occurrences. They're breeding.:o:shock:

---

### Post by sibutt on 2010-10-14
Thanks, worked a treat, don't know why I didn't think of it myself.  It also stopped the drive from swapping designation every boot.:)

---

