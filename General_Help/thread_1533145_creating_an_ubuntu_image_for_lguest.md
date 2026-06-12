---
title: "creating an ubuntu image for lguest"
date: 2010-07-17
forum: General Help
---

### Post by eviatarkhen on 2010-07-17
Hi
I'm doing a project on lguest, but all the images I tried are not working, so I tried to create it with myself using the following code. The problem is that it doesn't create an initrd.img file(at /boot). Can anyone recognize the problem, or more simply, anyone could refer me to a lguest image that works properly.

Thank you and best regards,

Eviatar Khen

#!/bin/sh
# Copyright 2009 Franklin Piat ; License BSD 2 clauses.
set -x
set -e
MIRROR=http://archive.ubuntu.com/ubuntu

name=$1
size=$2
[ ! "$size" ] && size=1024
[ $USER != "root" ] && (echo 'You are not root, bye!' ; false)

DIST='lucid'
# Create working directory
[ "$name" ] || name=$DIST
mkdir -p $name
cd $name

if [ -f "$name.raw" ]; then
    echo 'The disk image already exists... not wiping it!'
else
    dd if=/dev/zero of=$name.raw bs=1024 seek=$(($size * 1024)) count=1
    mke2fs -F $name.raw
fi
mkdir -p mnt$name
mount $name.raw mnt$name -o loop
trap "umount $PWD/mnt$name" 0 1 2 3 7 13 15
# Avoid error on host running libpam-tmpdir
unset TMP
unset TMPDIR
debootstrap --verbose $DIST ./mnt$name/ $MIRROR 

cat > mnt$name/root/customise_guest <<RUN_IN_GUEST
#!/bin/sh
#trap "kill $PPID" 0 1 2 3 7 13 15

export LANG=C
mount -t devpts none /dev/pts
mount -t proc   none /proc

cd /dev
mknod ubd0 b 98 0

#Ubuntu Repositories
echo "deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid main restricted" >> /etc/apt/sources.list
echo "deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates main restricted universe" >> /etc/apt/sources.list
echo "deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security main restricted" >> /etc/apt/sources.list
echo "deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid universe multiverse" >> /etc/apt/sources.list
echo "deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security universe multiverse" /etc/apt/sources.list

apt-get update && apt-get -y dist-upgrade
echo lguest-$DIST > /etc/hostname
echo "localhost        127.0.0.1" > /etc/hosts

echo "/dev/ubd0        /    ext3    defaults    0    1" >> /etc/fstab
echo "proc        /proc    proc    defaults    0    0" >> /etc/fstab
echo "tmpfs        /tmp    tmpfs    defaults    0    0" >> /etc/fstab
echo "none        /host    hostfs    defaults,noauto 0    0" >> /etc/fstab

mkdir -p /host

# We always want the loopback interface
echo "auto lo" >> /etc/network/interfaces
echo "iface lo inet loopback" >> /etc/network/interfaces
echo "" >> /etc/network/interfaces
echo "auto eth0" >> /etc/network/interfaces
echo "iface eth0 inet dhcp" >> /etc/network/interfaces

sed -i /'ACTIVE_CONSOLES/s/.-./1-2/' /etc/default/console-setup
for i in /etc/init/tty[3-6].conf
do
    sed -i '/^[a-z]/s/^/#/' ${i}
done

ln -sf /usr/share/zoneinfo/Asia/Tel_Aviv /etc/localtime

apt-get -y install less locales console-data
update-locale LANG=C

apt-get -y install ssh tcpdump telnet

umount /dev/pts
umount /proc
exit
RUN_IN_GUEST

# Jump in the new system
chroot $PWD/mnt$name /bin/sh ./root/customise_guest

---

