---
title: "How to partition / format a usb hard drive?"
date: 2006-03-27
forum: General Help
---

### Post by UeB on 2006-03-27
I bourght a hard drive and an icy box portalbe hard drive case today.
the hard drive is unpartitioned and unformated
ubuntu found the drive automaticaly (i can see it when i type lsusb in console )
i can even see the drive with the right size and brandname (samsung) in the gnome disks manager but i cant use the disks manager to create a partition. the button "(+) create" is not clickable (grey).
anybody know what to do to get the hard disks formatted with fat32?

---

### Post by scpike on 2006-03-27
make sure the drive is not mounted and then try using gparted

---

### Post by UeB on 2006-03-27
gparted seemed to work fine i created a fat32 partition created a small text file on it.
But my windows machines (xp and 2000) do not recognise the partition ( no drive is automounted in the explorer after switching the drive on) athough the manual promised that there is no need for a extra driver but they do recongnise the the hard drive itsself. i can see the drive in the device manager with the right maufacure name and i can "safly turn off" the usb drive in the task bar.
anybody any ideas whats wrong?
by the way i thourght you need to format a partition after creating it but i think gparted did not do that becouse creating the partition was very fast.

thanks!

---

### Post by plors on 2006-03-28
Hi,

Creating a new fat32 filesystem using the dosfstools (which are used by gparted) is _very_ fast. I guess the reason win2000 doesn't reckognice the filesystem is because you are using an old version of gparted which doesn't set the filesystemtype correctly.
If you are using a pre-0.2 gparted you should upgrade to the latest version. It's advisable to use the [gparted livecd]("http://gparted.sourceforge.net/livecd.php")

good luck

---

### Post by UeB on 2006-03-28
the problem is solved
it was NOT the filesystem or the version of gparted
it was the type of partition which was a linux type 
with fdisk i could change it to windows type (type "c" in fdisk ) without loosing any data and now it works with windows.

---

### Post by plors on 2006-03-28
[QUOTE=UeB]the problem is solved
it was NOT the filesystem or the version of gparted
it was the type of partition which was a linux type 
with fdisk i could change it to windows type (type "c" in fdisk ) without loosing any data and now it works with windows.[/QUOTE]

thats what i said in my previous post. Later versions of gparted set the partitiontype correctly. The gparted on the ubuntu livecd is simply too old.

Anyway, i'm glad your problem is solved :D

---

