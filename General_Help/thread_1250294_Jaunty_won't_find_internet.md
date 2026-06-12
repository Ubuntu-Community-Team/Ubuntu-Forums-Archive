---
title: "Jaunty won't find internet"
date: 2009-08-26
forum: General Help
---

### Post by DougieFresh4U on 2009-08-26
I don't know if there is a related issue.
Multi boot machine, 2 Karmic, 1 Jaunty & a Windows 7 partitions.
All the other partitions find internet. I have tried wireless and ethernet and Jaunty does not see either one.
Any way I can mount the Jaunty partition and some how get it to update or try to find the problem?
Thanks.

---

### Post by Iowan on 2009-08-26
> **DougieFresh4U said:**
> Any way I can mount the Jaunty partition and some how get it to update or try to find the problem?
Thanks.I presume you can select it from grub? Check **ifconfig -a** and **lshw -C network**.

---

### Post by bchurchill on 2009-08-26
You can also boot into a live CD (or even your other operating systems - the instructions are the same) and use this to upgrade/install packages on your Jaunty partition, if that helps at all.  If you know what device your root partition of Jaunty is on, (say /dev/sda__) then you can use

```

mkdir /jaunty
mount /dev/sad__ /jaunty

```

to mount it.  Use "sudo fdisk -l" to list devices if necessary.  If you can't get internet working in the live cd... then you have a weird issue.  Otherwise, get it working and do the following either in a root shell, or using sudo:

(these first two are probably unnecessary unless you did some sort of minimal install) 
```

cp /etc/hosts /jaunty/etc/
cp /etc/network/interfaces /jaunty/etc/network/

```

and then do
```

mount --bind /dev /jaunty/dev
mount -t proc proc /jaunty/proc
mount -t sysfs sysfs /jaunty/sys
chroot /jaunty

```

(the basic idea behind these instructions is here: [http://www.howtoforge.com/minimal-ubuntu-8.04-server-install](http://www.howtoforge.com/minimal-ubuntu-8.04-server-install))

now you're (for all practical purposes) in your Jaunty's shell and connected to the internet so you should (if I got this right) be able to do 

sudo apt-get update
sudo apt-get upgrade

---

### Post by DougieFresh4U on 2009-08-27
> **Iowan said:**
> I presume you can select it from grub? Check **ifconfig -a** and **lshw -C network**.

Had to boot into Jaunty partition and ran your 'codes'. First one didn't work. printed out what the second 'code' spat out. Booted into Karmic partition to type the output of second 'code':
```
WARNING: you should run this program as super-user.
*-network DISABLED
description: Ethernet interface
product: RTL8111/8168B PCI Express Gigabit Ethernet
controller
vendor: Realtek Semiconductor Co., Ltd.
physical id: 0
bus info: pci@0000:02:00.0
logical name: eth0
version: 02
serial: 00:21:97:7a:24:1a
width: 64 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical
configuration: broadcast=yes driver-r8169
driverversion=2.3LK-NAPI latency=0 module=r8169
multicast=yes
*-network
description: Ethernet interface
physical id: 1
logical name: pan0
serial: 46:0c:e8:d2:d1:d8
capabilities: ethernet physical
configuration: broadcast=yes driver=bridge
driverversion=2.3 firmware=N/A multicast=yes
```
that is all the terminal spat out for me
Thanks

---

### Post by DougieFresh4U on 2009-08-27
> **Iowan said:**
> I presume you can select it from grub? Check **ifconfig -a** and **lshw -C network**.

> **bchurchill said:**
> You can also boot into a live CD (or even your other operating systems - the instructions are the same) and use this to upgrade/install packages on your Jaunty partition, if that helps at all.  If you know what device your root partition of Jaunty is on, (say /dev/sda__) then you can use

```

mkdir /jaunty
mount /dev/sad__ /jaunty

```

to mount it.  Use "sudo fdisk -l" to list devices if necessary.  If you can't get internet working in the live cd... then you have a weird issue.  Otherwise, get it working and do the following either in a root shell, or using sudo:

(these first two are probably unnecessary unless you did some sort of minimal install) 
```

cp /etc/hosts /jaunty/etc/
cp /etc/network/interfaces /jaunty/etc/network/

```

and then do
```

mount --bind /dev /jaunty/dev
mount -t proc proc /jaunty/proc
mount -t sysfs sysfs /jaunty/sys
chroot /jaunty

```

(the basic idea behind these instructions is here: [http://www.howtoforge.com/minimal-ubuntu-8.04-server-install](http://www.howtoforge.com/minimal-ubuntu-8.04-server-install))

now you're (for all practical purposes) in your Jaunty's shell and connected to the internet so you should (if I got this right) be able to do 

sudo apt-get update
sudo apt-get upgrade
Internet works for all other partitions.
Not sure how to follow your 'codes' given. I am no guru, so don't know whether I need sudo before pasting etc etc. 
Jaunty is on dev/sda6

---

### Post by DougieFresh4U on 2009-08-28
So, it says network is disabled. How would I enable it.
I have to manually enter internet address info and I click apply but still no internet

---

### Post by bchurchill on 2009-08-28
For just about every command someone writes on these forums, you'll type it into the terminal which you can find at

Applications Menu -> Accessories -> Terminal

You'll need to right-click in terminal to pase; Cntl-V doesn't work.  For all the commands I gave you you'll need to write sudo before the command, howver this is not typically the case, and you should only use sudo when it's needed.

EDIT: my original post was useless... you already tried ifconfig -a.  

What error message did it give you when you typed "ifconfig -a"?  Is there a button on your computer that turns on/off the network?  (This is common with wireless, but it looks like you're wired)

---

### Post by DougieFresh4U on 2009-08-28
> **bchurchill said:**
> For just about every command someone writes on these forums, you'll type it into the terminal which you can find at

Applications Menu -> Accessories -> Terminal

You'll need to right-click in terminal to pase; Cntl-V doesn't work.  For all the commands I gave you you'll need to write sudo before the command, howver this is not typically the case, and you should only use sudo when it's needed.

EDIT: my original post was useless... you already tried ifconfig -a.  

What error message did it give you when you typed "ifconfig -a"?  Is there a button on your computer that turns on/off the network?  (This is common with wireless, but it looks like you're wired)
Thanks for you reply. 
Internet works great for my 3 other partitions. I mostly use wired, but I can also use wireless if I want. Neither will work on Jaunty. 
Don't remember exactly what the one code you provided. Some thing about no network. Will boot into Jaunty in a few, or is there a way to access from my Karmic partition?

---

