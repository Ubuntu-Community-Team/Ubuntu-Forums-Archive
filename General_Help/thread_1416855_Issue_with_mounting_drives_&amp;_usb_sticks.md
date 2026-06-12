---
title: "Issue with mounting drives &amp; usb sticks"
date: 2010-02-26
forum: General Help
---

### Post by duckytn on 2010-02-26
While I have come to trust webupd8.com for their Ubuntu tips.. the one posted yesterday about installing an updated version of the gnome-disk-utility has really screwed my Ubuntu 9.10 up. Ever since I have installed it my ntfs partitions are no longer visible and when I insert a USB flash drive the system no longer mounts them. I have removed their "updated" version of the gnome-disk-utility and this has not helped. Can anyone provide any direction as to a non-destructive method to restore this capability ?

Cheers & Thanks !

Eric

---

### Post by neoroses on 2010-02-26
heyup.

[https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB) have a look here your automatic mounting may have screwed up for some reason or another, and try install ntfs-config

```
sudo apt-get install ntfs-config
```

im no expert just thought these tips may help out.:KS

---

### Post by duckytn on 2010-02-26
> **neoroses said:**
> heyup.

[https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB) have a look here your automatic mounting may have screwed up for some reason or another, and try install ntfs-config

```
sudo apt-get install ntfs-config
```

im no expert just thought these tips may help out.:KS

Will this help with the USB flash drive with a fat32 fs ?

Thanks!

---

### Post by neoroses on 2010-02-26
no it wont but it might sort out not being able to see your ntfs drives, the link in the post is a good place to start for your fat 32 usb drives

---

### Post by duckytn on 2010-02-26
Thanks for your help!! I will check it out.

---

