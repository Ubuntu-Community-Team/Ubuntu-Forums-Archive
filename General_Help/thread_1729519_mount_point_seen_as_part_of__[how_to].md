---
title: "mount point seen as part of / [how to]"
date: 2011-04-15
forum: General Help
---

### Post by achitan on 2011-04-15
Hello, everybody!

Here's the sit. I have a 372 GB hdd. I partitioned it like this:
100 MB boot partition
304 GB / partition for one Ubuntu installation that I don't use :D
66 GB  / partition for the Ubuntu I am using
1 GB   swap partition

Why? Because I thought I would install Windows on that 300 GB partition, but I got sick of Windows.
What do I need? I need to make one folder from the 304 GB partition as part of the / partition in the Ubuntu I am using. That 304 GB partition is mounted in /media (/dev/sda4). So it's kind of a way to resize my 66 GB partition.
Why don't I use KDE Partition Manager or some keen? Because it doesn't let me resize the partition because of the way they are ordered on the hdd (I think - I've attached a picture from KDE PM).
That's about it. Any input will be much appreciated.

Thank a lot,

Adrian Chitan

---

### Post by jerome1232 on 2011-04-15
It won't let you edit the partition because it's mounted, you have to unmount it first.

```
sudo umount /dev/sda4
```

---

### Post by achitan on 2011-04-15
yeah, ok...I think I got it:

1) unmount the big partition
2) resize it (get some unalocated space)
because I can't unmount / I should:
3) go into the other Ubuntu (where the big partition is /)
4) give that unallocated space to the small (66 GB) partition
5) be happy because you've managed to enlarge your Ubuntu partition

OR

1) use a ubuntu livecd to do the tweaks (then you will be able to resize everything, 'coz Ubuntu is on the CD)

That solves the problem of resizing. Now how about what I asked? Is there a way to add (mount, merge, give:))) a folder from a different partition to the /, so the free space, for instance, of the / partition would be the added free spaces?

Thanks for the reply,

Adrian Chitan

---

