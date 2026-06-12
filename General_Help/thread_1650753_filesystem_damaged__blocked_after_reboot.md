---
title: "filesystem damaged / blocked after reboot"
date: 2010-12-22
forum: General Help
---

### Post by Tarpoon on 2010-12-22
Hello everybody,

I am having quite a serious problem with Ubuntu on 2 different notebooks (Dell Mini 10 and Samsung NC20) so far.
What happens is that the filesystem (ext4 on both computers) gets damaged or blocked completely after a reboot.
This is happening completely randomly, but I believe it may be related to installing updates.
I already filed a bug launchpad ([Link]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/692623")), but as nobody reacted there so far I am trying myself now to get my Dell to run again.

What happens is that when I try to start ubuntu I end up in the busybox. (see screenshots attached to this posting)

What I have tried so far is booting ubuntu from an usb stick and doing fsck on the blocked partition, but it gives me an
```
device or resource busy while trying to open
```
error.

I then reboot the USB-Ubuntu, however it gets stick while shutting down, so I have to do Alt + S-Abf + B.

The next thing I tried is to mount the partition, however
```
sudo mount /dev/sda1 /media/laufwerk
```
results in endless waiting on the console and nothing happens at all.
I cannot even cancel the mounting process without resetting the computer.


Has anyone an idea what I can do to get the to respond again?

---

### Post by Rubi1200 on 2010-12-22
Hi and welcome to the forums :)

To give us a better overview of your setup use a LiveCD/USB to boot the computers.

At the live desktop, download and run the boot info script linked at the bottom of my post (instructions included).

Post the results back here for one or both machines.

Also, post the full specifications for the machines in question.

Thanks.

---

