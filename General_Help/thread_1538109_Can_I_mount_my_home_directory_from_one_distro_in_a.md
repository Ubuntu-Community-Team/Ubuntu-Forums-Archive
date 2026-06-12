---
title: "Can I mount my home directory from one distro in another?"
date: 2010-07-24
forum: General Help
---

### Post by x-shaney-x on 2010-07-24
I have never shared a home directory between distros, nor had one on a separate partition.
Mainly because if I have different distros I tend to have them set up differently.

However, I am planning to install a secondary, lightweight distro for use when travelling to get the most out of my battery etc.

So I'm wondering if I could mount my own home directory in the secondary?

For example, would this work in fstab? ```
UUID=900f1ef9-9118-457a-baf0-74c0f7a0b1a8/home/me     /home/me    ext3    defaults        0       1
```
Or am I not able to specify actual directories on the UUID (or /dev/sdx/home/me)
If it is possible, what would I need in the options bit?

And finally, what if the home partition in my main distro was ext4 and the secondary distro was ext3?

---

### Post by Miki800 on 2010-07-24
> **x-shaney-x said:**
> I have never shared a home directory between distros, nor had one on a separate partition.
Mainly because if I have different distros I tend to have them set up differently.

However, I am planning to install a secondary, lightweight distro for use when travelling to get the most out of my battery etc.

So I'm wondering if I could mount my own home directory in the secondary?

For example, would this work in fstab? ```
UUID=900f1ef9-9118-457a-baf0-74c0f7a0b1a8/home/me     /home/me    ext3    defaults        0       1
```
Or am I not able to specify actual directories on the UUID (or /dev/sdx/home/me)
If it is possible, what would I need in the options bit?

And finally, what if the home partition in my main distro was ext4 and the secondary distro was ext3?
for mountings based on your HD's uuid, use the following fstab syntax:

# this would be one of your /etc/fstab lines:
```

/dev/disk/by-uuid/900f1ef9-9118-457a-baf0-74c0f7a0b1a8   /mnt/OLD_LINUX_ROOT  ext3   defaults  0  1

```

then you would like to do the following

```

ln -s /mnt/OLD_LINUX_ROOT/home/me /home/me

```

or you could just do this:

```

sudo chroot /mnt/OLD_LINUX_ROOT

```
to have an environment just like your old linux


anyways, what I would really suggest is for your to move your home dir to a portable flash-drive
and do the mounts ON THAT DRIVE and not the other way around - [COLOR="Red"]take with you the entire root[/COLOR] ('/' - slash path) <-- don't do that.


that way you can take with you your home dir, mount it on any linux on /home/me and it should just work.

---

### Post by x-shaney-x on 2010-07-24
Thankyou, very helpful

---

