---
title: "moving files from /usr to /usr/local"
date: 2011-01-28
forum: General Help
---

### Post by rajn on 2011-01-28
Hi,
My ~/usr partition is getting full. However, the usr/local partition is barely used.
Instead of changing the partition size (which looks to me a difficult proposition as the two i.e., usr and usr/local are not contiguous : sdev6 and sdev8), I think the best option is to move some applications from usr to usr/local. Also, I have Mandriva distro as a second boot option and that I have not partitioned. This means Mandriva by default occupies the rest of the hard drive space. Therefore, I am not sure if I can create extra space for another partition and move /usr to that partition.


Instead,
I would like to move applications such as Scilab, Gimp, Gnuplot, Python, OpenOffice etc to usr/local and subsequently change path profile such that whenever I download a new app or update an existing app, it would first look into usr/local and then in usr. Currently, it looks like everything is dumped into usr which is now the cause of my problem.

I will appreciate any suggestions how to do that.
Most of these applications have their files distributed everywhere such as in /bin, /lib, /include etc.
Is there a way to move all associated files together?
Is there any solution other than uninstalling and reinstalling into /usr/bin.
Thanks

---

### Post by vanadium on 2011-01-28
It is the distribution maintainer that decided where to place the application files. Trying to organize the system structure differently is like making your own Linux distribution. Highly technical and highly complicated for most of us.

If I were you, I'd remove my Ubuntu installation and all partitions it uses completely. Then, I'd reinstall, having it use a single partition in the freed space.

It could be possible to move /usr elsewhere and have it replaced by a symbolic link. I think that would work, but I do not know for sure.

---

### Post by srs5694 on 2011-01-28
In the old days, when people walked ten miles through six-foot snow banks to and from school (uphill both ways), using symbolic links to move part of a nearly-full filesystem to a less-full filesystem was common. I wouldn't recommend it today, though, mainly because I don't know how the package management tools would react to such a change. They might do something strange, which could cause much worse problems.

Since /usr/local is intended for locally-compiled software, one possibility (while keeping within the rules) would be to uninstall some software using APT and then compile it from source code locally for installation in /usr/local. This will increase your administrative load, though; you'll have to update the software you compile locally yourself. Furthermore, if some other package relies on what you install, you'll end up in Dependency Hell. Overall, unless you're already familiar with managing software by compiling it locally (and I suspect from your predicament that you're not), this doesn't seem like a good solution to me.

Another option is to clean up your root (/) partition or uninstall unused packages. Try typing "sudo apt-get clean" and see if that frees up any space. If not, you could use Synaptic or some other package manager to peruse your system for packages you might be able to do without. (Keep in mind that some useless-sounding packages are actually vital or may be depended upon by something you actually do need, though. Try uninstalling things one at a time, and if the program tells you it must uninstall something else, abort the operation until you're sure you don't need anything it wants to uninstall.)

You might want to post a screen shot of GParted's view of your hard disk. That'll show us how your partitions are arranged and give us some idea of how full each one is. It could be that a resize/move operation wouldn't be that painful.

---

### Post by vanadium on 2011-01-28
> **srs5694 said:**
> In the old days, when people walked ten miles through six-foot snow banks to and from school (uphill both ways), using symbolic links to move part of a nearly-full filesystem to a less-full filesystem was common. I wouldn't recommend it today, though, mainly because I don't know how the package management tools would react to such a change.
That's my reservation also, although at first sight, I do not see why package management tools would choke on it. It would be a very simple solution, though. The other options given are barely realistic except for real system guru's. Then these probably are having fun with something else than Ubuntu.

Re-installation and avoiding this useless partitioning would be the best option here, in my opinion.

Anyway, let's see what the OP thinks he can handle.

---

### Post by rajn on 2011-01-28
Thanks for many suggestions but looks like I will have to make a new partition after backing up the files. Here is the output of fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00023100

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         244     1951744   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2             244         851     4882432   83  Linux
Partition 2 does not end on cylinder boundary.
/dev/sda3             851        1459     4882432   83  Linux
/dev/sda4            1459        9729    66429562+   5  Extended
/dev/sda5            1459        1520      487424   83  Linux
/dev/sda6            1520        2128     4881408   83  Linux
/dev/sda7            2128        2371     1951744   83  Linux
/dev/sda8            2371        2614     1951744   83  Linux
/dev/sda9            2614        3222     4881408   83  Linux
/dev/sda10           3222        3465     1951744   82  Linux swap / Solaris
/dev/sda11           3466        5032    12586896   83  Linux
/dev/sda12           5033        5541     4088511   82  Linux swap / Solaris
/dev/sda13           5542        9729    33640078+  83  Linux

2 is /
1 is /boot
3 is /home
5 is /tmp
6 is /usr
7 is /var
8 is /opt 
9 is /usr/local

I made this partition as a newbee. I am not sure what did I do and why is sda4 is extended....

and to df -h

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             4.6G 1009M  3.4G  23% /
none                  118M  300K  118M   1% /dev
none                  122M  280K  122M   1% /dev/shm
none                  122M   92K  122M   1% /var/run
none                  122M     0  122M   0% /var/lock
none                  122M     0  122M   0% /lib/init/rw
/dev/sda5             461M   99M  340M  23% /tmp
/dev/sda1             1.9G  165M  1.6G  10% /boot
/dev/sda3             4.6G  1.4G  3.0G  32% /home
/dev/sda6             4.6G  3.6G  851M  81% /usr
/dev/sda7             1.9G  551M  1.3G  31% /var
/dev/sda8             1.9G  180M  1.6G  11% /opt
/dev/sda9             4.6G  267M  4.1G   6% /usr/local

Any suggestions how to go ahead? I do not know how to see the remaining disk space i.e., the one owned by the other Linux system Mandriva which is chain loaded to Ubuntu.

---

### Post by vanadium on 2011-01-29
It makes no sense to have all these different small partitions for a desktop system. This lets you bump into the problems you are now experiences because space is not efficiently used.

I would reinstall it all, and first repartition manually
1) 10 GB for / of Ubuntu installation
2) 10 GB for / of Mandriva installation
3) Remainder - swap for /mnt/data partition
4) One single swap partition (both linux distro's can use that). Caveat: if you want hibernation to work, you need two swaps, one for each distro.

1) and 2) could be primary partitions, 3) and 4) (and optionally second swap 5) can go into an extended partition.

Otherwise, you can attempt a complex repartitioning exercise (eg. join sda1, 2 and 3 to reinstall Ubuntu, join 5, 6, 7, 8 and 9 for a data partition). If this breaks your Mandriva install (not necessary if UUIDS are used rather than device names), you are back to square 1, and you will need to revert to a reinstall of everything.

---

### Post by SeijiSensei on 2011-01-29
Let me make an alternative suggestion as an interim solution. One thing that eats space in /usr is /usr/share/doc, which contains all the various documentation files associated with the applications you've installed.  On my machine that's about one of the four gigabytes my /usr contains.  

Have you ever read any of this documentation?  If not, and if you don't expect to, you can get that gig or so back with "sudo rm -rf /usr/share/doc".

If you someday need to read the README file for an application, you can usually find it through a Google search.

> **rajn said:**
> I made this partition as a newbee. I am not sure what did I do and why is sda4 is extended....

The PC architecture supports up to four "primary" partitions on a hard drive.  One of those partitions can be an "extended" partition that supports "logical" partitions within it.  So to have more than four partitions, one of them has to be an extended partition.

---

### Post by srs5694 on 2011-01-29
As others have suggested, re-partitioning and re-installing is probably the most sensible approach. You *could* consolidate all your tiny partitions, but doing so would almost certainly be more effort than re-installing, and you'd run the risk of damaging things so badly that you'd need to re-install. Be sure to back up /home before proceeding. You can either delete the original partition and restore the backup later or use GParted to move it somewhere sensible for your new partitioning scheme.

---

