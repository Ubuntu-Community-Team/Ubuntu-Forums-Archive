---
title: "Unable to properly update ubuntu b/c my cd-rom isnt properly mounted?"
date: 2010-08-19
forum: General Help
---

### Post by PhixionalTruth on 2010-08-19
GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783Failed to fetch cdrom://Ubuntu-Netbook 10.04 _Lucid Lynx_ - Release i386 (20100429.4)/dists/lucid/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom://Ubuntu-Netbook 10.04 _Lucid Lynx_ - Release i386 (20100429.4)/dists/lucid/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.


*****Thats what I get when I run the auto update.
*****apt-cdrom gives me this---->ninja@ninja-laptop:~$ apt-cdrom add
Using CD-ROM mount point /media/apt/
Identifying.. 
E: Unable to stat the mount point /media/apt/ - stat (2: No such file or directory)
W: Failed to mount '/dev/sr0' to '/media/apt/'
E: Unable to change to /media/apt/ - chdir (2: No such file or directory)
ninja@ninja-laptop:~$ 

******every command gives me an error

---

### Post by bukwirm on 2010-08-19
Try commenting out any lines in you /etc/apt/sources.list file that refer to your CD drive.

---

### Post by wojox on 2010-08-19
What does this return

```
cat /etc/fstab
```

---

### Post by PhixionalTruth on 2010-08-19
ninja@ninja-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=742fba88-6a95-44f9-88f3-992a9b15356e none            swap    sw              0       0
ninja@ninja-laptop:~$

---

### Post by wojox on 2010-08-20
What is it exactly your trying to do?

---

### Post by wojox on 2010-08-20
Run these two commands to import the key for medibuntu

```

gpg --keyserver pgpkeys.mit.edu --recv-key  2EBC26B60C5A2783 
gpg -a --export 2EBC26B60C5A2783 | sudo apt-key add -

```

If it still throws an error, use bukwirm's advice and edit your sources.list

```
gksudo gedit /etc/apt/sources.list
```

Comment out at the top about using your cd-rom.

---

### Post by PhixionalTruth on 2010-08-20
i commented out the part about my cdrom and boom no update errors, thanks guys. Why was that such an issue?

---

### Post by stlsaint on 2010-08-20
You were trying to use a cd as a source for updates/upgrades maybe? Either way if issue is resolved please mark as solved.

---

### Post by belowstandard on 2010-08-20
I've spent quite a while looking at various Ubuntu forums trying to find a solution to, or even understanding of, this problem, and have had no luck.

I've done a clean install of Lucid. I DO NOT want the machine connected to a network until it is fully set up. It's a security issue, but that doesn't matter. I should be able to use the repository on the cd to install from.

apt-get install gives the "Failed to fetch cdrom: ..." error. The cdrom appears to be mounted properly, the sources.list file contains the correct reference to the cdrom, and yet I still get this error.

But, the error only occurs if I attempt to install a package which depends on another package. If there is no dependency then the install procedes correctly.

I wanted to install dpgk-dev and was unable. As a work around I installed dependencies one at a time until I reached a point where two packages had a mutual dependency and apt would not get past this error.

I then had to resort to creating a temporary simple repository on the harddrive, copying the .debs from the cd to the harddrive, creating a Packages.gz, adding a line to sources.list to point to the temporary repository, and completing the install.

There may well be something that I have overlooked that is causing the problem but I don't know what it is.

My point in posting this is not so much to get an answer, as it is to metion this kludge of a work around for other people who might find this thread (like I did) while looking for a solution. 

If anyone who really knows what is going on could explain what is causing this problem that would probably be helpful to many people since I have seen 20 or 30 threads in different forums describing this and related problems. If anyone knows a solution, that would be even more useful.

Even if the solution is a simple configuration issue then it seems the distribution managers should look into it since it appears to be fairly common.

Finaly, in almost every thread I've seen someone comes along and says to "uncheck"; some box, or comment out the cdrom line in sources.list. Maybe I need to move from Ubuntu to Debian, but I would have thought there are still people who know how to use a command line -- there are no check boxes on a command line.

Wether using a desktop or a console, removing the cdrom from sources.list is not a solution, nothing has been "solved", it's sweeping a problem under the rug. It is incredibly frustrating trying to find a solution, seeing lots of threads started by someone with the same question, and in almost all cases it devolves into "Why would anyone want to do that?"

I'm glad the OP has a usable work-around, but the problem is not solved.

---

### Post by wojox on 2010-08-21
> **PhixionalTruth said:**
> i commented out the part about my cdrom and boom no update errors, thanks guys. Why was that such an issue?

Because you told it to with

```
apt-cdrom add
```

---

