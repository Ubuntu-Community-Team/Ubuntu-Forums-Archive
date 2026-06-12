---
title: "Ubuntu 10.04 update fail"
date: 2010-12-02
forum: General Help
---

### Post by raydar on 2010-12-02
On a machine running Ubuntu 10.04, I see updates listed in the Update Manager, but when I proceed to try downloading and installing them, I get "You are about to install software that can't be authenticated" warning for linux-image-2.6.32-26-generic, gwibber, and related packages, followed by "some of the packages could not be retrieved from the server" and the messages quoted below when I choose to go ahead and install anyway. 

This was a standard install of 9.10, upgraded to 10.04, and I haven't done any tweaks that I can think of as crazy except setting up XRDP remote desktop recently. Can anyone clue me in to the nature of the problem?

> W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.32-26-generic_2.6.32-26.47_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.32-26-generic_2.6.32-26.47_i386.deb)
  404  Not Found [IP: 91.189.88.30 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.32-26_2.6.32-26.47_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.32-26_2.6.32-26.47_all.deb)
  404  Not Found [IP: 91.189.88.30 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.32-26-generic_2.6.32-26.47_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.32-26-generic_2.6.32-26.47_i386.deb)
  404  Not Found [IP: 91.189.88.30 80]


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_2.6.32-26.47_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_2.6.32-26.47_i386.deb)
  404  Not Found [IP: 91.189.88.30 80]




---

### Post by zvacet on 2010-12-02
In terminal

```
cat /etc/apt/sources.list
```


and post output here.

---

### Post by Hippytaff on 2010-12-02
Also are you able to ping this ip 91.189.88.30 80

---

### Post by raydar on 2010-12-03
It mysteriously began working again--I was surprised that a url having to do with the linux kernel was unreachable, but I guess I shouldn't have been too suspicious; any connection can go down for a while.

Thanks for your help!

---

