---
title: "Using mkinitramfs for older kernel?"
date: 2010-11-04
forum: General Help
---

### Post by Sarin42 on 2010-11-04
Hi everyone,

I'm currently working on a project that involves running a small version of Ubuntu on an FPGA.

I've already worked out all the kinks for running the 2.6.32 kernel on the machine, but we'd like to use the older, 2.6.22 kernel instead. The only issue, it seems, is building the initramfs for this older kernel.

My problem is as follows:
The "mkinitramfs" command *always* makes initramfs's that are suited for 2.6.32 kernels. For instance, I believe that the "devtmpfs" for mounting /dev in the init script was added for the 2.6.32 kernel, but even if I run "mkinitramfs" for the 2.6.22 kernel, it includes this step.

To illustrate, I have an init script from a 2.6.22 kernel (which we can't use because it doesn't have our upgrades), and its first few lines are:

```
#!/bin/sh

echo "Loading, please wait..."

[ -d /dev ] || mkdir -m 0755 /dev
[ -d /root ] || mkdir --mode=0700 /root
[ -d /sys ] || mkdir /sys
[ -d /proc ] || mkdir /proc
[ -d /tmp ] || mkdir /tmp
mkdir -p /var/lock
mount -t sysfs none /sys -onodev,noexec,nosuid
mount -t proc none /proc -onodev,noexec,nosuid

# Note that this only becomes /dev on the real filesystem if udev's scripts
# are used; which they will be, but it's worth pointing out
mount -t tmpfs -o mode=0755 udev /dev
[ -e /dev/console ] || mknod /dev/console c 5 1
[ -e /dev/null ] || mknod /dev/null c 1 3
> /dev/.initramfs-tools
mkdir /dev/.initramfs
```

Whereas the generated init script, after running "mkinitramfs -o /boot/initrd-img.2.6.22-abacus 2.6.22-abacus", gives:

```
#!/bin/sh

echo "Loading, please wait..."

[ -d /dev ] || mkdir -m 0755 /dev
[ -d /root ] || mkdir -m 0700 /root
[ -d /sys ] || mkdir /sys
[ -d /proc ] || mkdir /proc
[ -d /tmp ] || mkdir /tmp
mkdir -p /var/lock
mount -t sysfs -o nodev,noexec,nosuid none /sys
mount -t proc -o nodev,noexec,nosuid none /proc

# Note that this only becomes /dev on the real filesystem if udev's scripts
# are used; which they will be, but it's worth pointing out
tmpfs_size="10M"
if [ -e /etc/udev/udev.conf ]; then
        . /etc/udev/udev.conf
fi
if ! mount -t devtmpfs -o mode=0755 none /dev; then
        echo "W: devtmpfs not available, falling back to tmpfs for /dev"
        mount -t tmpfs -o size=$tmpfs_size,mode=0755 udev /dev
        [ -e /dev/console ] || mknod -m 0600 /dev/console c 5 1
        [ -e /dev/null ] || mknod /dev/null c 1 3
fi
```


So my question is this:
How can I run "mkinitramfs" to create an initramfs (and init script) more suited to the older kernel, 2.6.22?

Thank you kindly for you support. Feel free to ask any questions.

Regards,
Ben

---

### Post by sandeep048 on 2011-04-25
Hi Ben,

Finally did you manage to get it working. If yes I would like to know the solution.

Thanks & Regards,
Sandeep

---

