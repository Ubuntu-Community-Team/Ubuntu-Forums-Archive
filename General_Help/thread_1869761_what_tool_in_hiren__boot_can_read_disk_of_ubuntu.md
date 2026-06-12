---
title: "what tool in hiren  boot can read disk of ubuntu"
date: 2011-10-26
forum: General Help
---

### Post by pedro2011 on 2011-10-26
Hello,

My Ubuntu operation can not start. I want to use disk hiren  boot 10.6 to read disk of ubuntu to take my data. Could you please tell me what tool in hiren  boot can read them?

Thank you in advance.

---

### Post by haqking on 2011-10-26
> **pedro2011 said:**
> Hello,

My Ubuntu operation can not start. I want to use disk hiren  boot 10.6 to read disk of ubuntu to take my data. Could you please tell me what tool in hiren  boot can read them?

Thank you in advance.

Try the hiren page.

[http://www.hiren.info/pages/bootcd](http://www.hiren.info/pages/bootcd)

However you can just boot to a Ubuntu Live CD, you dont need any special tools

---

### Post by haqking on 2011-10-26
Edit. Multiple post, whoops

---

### Post by pedro2011 on 2011-10-27
> **haqking said:**
> Try the hiren page.

[http://www.hiren.info/pages/bootcd](http://www.hiren.info/pages/bootcd)

However you can just boot to a Ubuntu Live CD, you dont need any special tools

I tried to use a Ubuntu Live CD but I can not see my directory. I must do something more to see it? What must I do more?

Thanks.

---

### Post by oldfred on 2011-10-27
Is it that the partition does not mount? Have you tried running filechecks on the partition. I might try that from liveCD.

#From liveCD so everything is unmounted,swap off if necessary, change sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems.
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors:
sudo e2fsck -f -y -v /dev/sdb1

---

