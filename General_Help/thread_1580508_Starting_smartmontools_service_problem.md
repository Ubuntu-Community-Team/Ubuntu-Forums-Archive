---
title: "Starting smartmontools service problem"
date: 2010-09-23
forum: General Help
---

### Post by arashi256 on 2010-09-23
Hi all, 

First post :) I'm an Ubuntu newbie (mostly used RedHat-based systems) and am trying to get smartmontools working on my little Samsung N120 Netbook with Ubuntu Netbook Remix. I've not really delved under the hood of Ubuntu, so I've got myself stuck pretty rapidly. I'm running all this as root through "sudo su - root" if it helps...

I'm trying to monitor my drive (/dev/sda) and have edited the following information into /etc/default/smartmontools: -

```

/dev/sda -m root@localhost -M exec /usr/share/smartmontools/smartd-runner

```

This was following the documentation from: [https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)


but when I try and start smartmontools service I get: -

```

root@joshua12:~# /etc/init.d/smartmontools start
/etc/default/smartmontools: 14: /dev/sda: Permission denied

```

I had to use "/dev/sda" instead of DEVICESCAN environment variable (I assume that is what it is anyway), because my system doesn't seem to have it and I'm not entirely sure what it should be.

Doing an "ls -la /dev/sda*" for this drive gives me: -

```

brw-rw----   1 root disk      8,   0 2010-09-23 17:42 sda
brw-rw----   1 root disk      8,   1 2010-09-23 17:42 sda1
brw-rw----   1 root disk      8,   2 2010-09-23 17:42 sda2
brw-rw----   1 root disk      8,   5 2010-09-23 17:42 sda5

```

Huh?! I'm root and have access to the disk (which is fine, btw, system is running peachy). What is this "disk" group all about as well?

Can anyone help please? Thanks.

---

