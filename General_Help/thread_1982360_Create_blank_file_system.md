---
title: "Create blank file system"
date: 2012-05-18
forum: General Help
---

### Post by giveen on 2012-05-18
I'm working on an Android project and need to create a system.img

What I need to do is create a blank ext 4 file system, copy my files into it, and than create that as a ext4 system.img

But I am unsure of what commands to do.


Could you guys help?

---

### Post by giveen on 2012-05-18
Am I in the wrong section to ask this?

---

### Post by giveen on 2012-05-18
Would this work?
"mke2fs -b 2048 -F -L test_system.img -t ext4 -v"

---

### Post by giveen on 2012-05-18
Figured it out

```

[LIST=1]
[*]dd if=/dev/zero of=cm9system.img bs=1MB count=0 seek=350
[*]mke2fs -t ext4 cm9system.img
[*]mkdir /mnt/cm9system
[*]sudo mount -o loop cm9system.img /mnt/cm9system
[*] 
[*] 
[*]cp out/target/product/device_name/system /mnt/cm9system
[*]sudo umount /mnt/cm9system
[/LIST]


```

---

