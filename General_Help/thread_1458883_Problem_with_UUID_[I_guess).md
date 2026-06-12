---
title: "Problem with UUID [I guess)"
date: 2010-04-20
forum: General Help
---

### Post by dispaired frog on 2010-04-20
I haven\t been able to start Ubuntu on my computer for 10 days. I have tried to get some kind of magic sentence on the internet to fix the problem but what I have found is to complex for me. This is the problem I am confronted to

When I try to start the computer, I can read on the screen boot from (hd 0,0) ext 3 and then f95164c-4d7b-49b9-a90e/3078c81bc429 does not exist.

Pressing on escape I come to an other screen where the following word appears (initramfs)

When I write ls -l /dev/disk/by-uuid

I get the following text

lrwxrwxrwx  1    0    0     10 109845fd-5d83-4a54-86bc-395dd162f9e5    ../../sda 5


I have tried to write this chain of characters which could be the right UUID, beginning by 1098 and ending by f9e5, after /dev/disk/by-uuid but I get permission denied as the only answer.

Does anybody know what I could do to get out of this mess 

Thanks.

---

### Post by duanedesign on 2010-04-20
you need to add that UUID to your fstab file. See [this page]("https://help.ubuntu.com/community/Fstab") for examples.

This will give you the UUID:

```
sudo blkid
```

Unless you have multiple Linux partitions it is the one that says ext3/4

Example:
```
/dev/sda5: UUID="b74d1112-d6c3-43ga-8501-5e81de0edf30" TYPE="ext4" 
```

then open the fstab:

```
sudo /etc/fstab
```

You will see an entry like this (this is just an example yours might be slightly different). This is where you put the UUID:
```
# /dev/sda5
UUID=b74d1112-d6c3-43ga-8501-5e81de0edf30  /  ext3  relatime,errors=remount-ro  0  1
```

save the file and reboot.
-
-
Additional Resources:
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

