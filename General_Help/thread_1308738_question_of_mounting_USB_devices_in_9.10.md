---
title: "question of mounting USB devices in 9.10"
date: 2009-10-31
forum: General Help
---

### Post by chaopoch on 2009-10-31
After upgrading from 9.04 to 9.10, I find something different while mounting USB device, in 9.04 and earlier version, the USB device will be mounted to **/media/disk** or **/media/disk-1** etc., but now, it is mounted to **/media/a62c9816-a2b4-452e-a267-17851f74d6bf**.

Every time I boot up the computer, there is always a message **[udev] specified group "plugdev" unknown**, so I think maybe that is what causes the problem, then I try to add the user to the group "plugdev", but "plugdev" does not exist,

[COLOR="Blue"]$ sudo useradd -G plugdev chaopoch
useradd: group 'plugdev' does not exist[/COLOR]

I add the group 'plugdev', and add the user again,

[COLOR="Blue"]$ sudo groupadd plugdev
$ sudo useradd -G plugdev chaopoch
useradd: user 'chaopoch' already exists[/COLOR]

Then I plug the USB device, but it is still mounted to **/media/a62c9816-a2b4-452e-a267-17851f74d6bf**, I don't want to add the UUIDs of USB devices respectively in the /etc/fstab, so how can I solve this problem? thanks.

---

### Post by chaopoch on 2009-11-02
no one has this problem?

---

### Post by cariboo on 2009-11-02
The easiest way to add a user to a group is to use gpasswd eg:

```
gpasswd -a <user> plugdev
```

---

### Post by chaopoch on 2009-11-10
> **cariboo907 said:**
> The easiest way to add a user to a group is to use gpasswd eg:

```
gpasswd -a <user> plugdev
```

I have run the command above and reboot, but the problem persists, any other solution? thanks.

---

