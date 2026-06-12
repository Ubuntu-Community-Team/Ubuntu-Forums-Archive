---
title: "Unable to boot into 11.04 partition"
date: 2011-03-21
forum: General Help
---

### Post by Grantbourque on 2011-03-21
Hello, I am trying to test out Ubuntu 11.04. I had Windows 7 and Ubuntu 10.10 already installed. I installed 11.04 from disc and everything was successful, but in grub all of the Ubuntu, Linux 2.6-x boot into 10.10.


How do I get my 11.04 partion (/dev/sda7) on the grub menu?

---

### Post by idoitprone on 2011-03-21
```
sudo update-grub 
```

hope that helps?

---

