---
title: "Intrepid not seeing external usb hdd, already have ntfs-3g/ntfs-config"
date: 2010-10-16
forum: General Help
---

### Post by b_k_chu on 2010-10-16
got a western digital external usb hdd that my Intrepid system just isn't seeing at all.  when i try
```
sudo fdisk -l
```the only device i see is my main internal hdd.  and i don't know much about mounting devices and all that, but from the way i understand it, i can't even mount the external hdd if fdisk doesn't even show a device name attached to it like /dev/sdb or something.

by the way the external hdd *does* work -- i hooked it up to a windows system and it saw the drive just fine, and also showed it was formatted as NTFS.

not sure what my system is missing here.  i have ntfs-3g already installed, and i ran ntfs-config and checked the box marked "Enable write support for external device".

and before anyone says, "Well, Intrepid is pretty old so just upgrade your Ubuntu and your problem will probably go away" -- that's why i got the external drive in the first place.  i needed somewhere where i can make a backup of all my important files first *before* i attempt an upgrade. :3

---

### Post by Rocket2DMn on 2010-10-16
Can you please disconnect then reconnect the hard drive and post the output of the following commands:
```
sudo fdisk -l
cat /etc/fstab
sudo blkid
mount
lsusb
dmesg
```

---

### Post by b_k_chu on 2010-10-17
done and done.

dmesg output looks suspicious -- i could only include part of the output because it went off screen.  but mostly it was the same thing over and over:

```
[75536.008123] hub 3-0:1.0: over-current change on port 1
[75536.752283] hub 3-0:1.0: over-current change on port 1
[75537.744100] hub 3-0:1.0: over-current change on port 1
[75538.488102] hub 3-0:1.0: over-current change on port 1
[75539.480256] hub 3-0:1.0: over-current change on port 1
[75540.224103] hub 3-0:1.0: over-current change on port 1
[75541.216064] hub 3-0:1.0: over-current change on port 1
[75541.960091] hub 3-0:1.0: over-current change on port 1
[75542.952097] hub 3-0:1.0: over-current change on port 1
[75543.696531] hub 3-0:1.0: over-current change on port 1
[75544.688079] hub 3-0:1.0: over-current change on port 1
[75545.432098] hub 3-0:1.0: over-current change on port 1
[75546.424123] hub 3-0:1.0: over-current change on port 1
[75547.168275] hub 3-0:1.0: over-current change on port 1
[75548.160118] hub 3-0:1.0: over-current change on port 1
[75548.310415] loop: module loaded
[75548.904105] hub 3-0:1.0: over-current change on port 1
[75549.896352] hub 3-0:1.0: over-current change on port 1
[75550.640104] hub 3-0:1.0: over-current change on port 1
[75551.632102] hub 3-0:1.0: over-current change on port 1
[75552.376368] hub 3-0:1.0: over-current change on port 1
[75553.120911] hub 3-0:1.0: over-current change on port 1
[75554.112315] hub 3-0:1.0: over-current change on port 1
[75554.856090] hub 3-0:1.0: over-current change on port 1
[75555.848098] hub 3-0:1.0: over-current change on port 1
[75556.592097] hub 3-0:1.0: over-current change on port 1
[75557.584090] hub 3-0:1.0: over-current change on port 1
[75558.328104] hub 3-0:1.0: over-current change on port 1
[75559.320364] hub 3-0:1.0: over-current change on port 1
[75560.064074] hub 3-0:1.0: over-current change on port 1
[75561.056417] hub 3-0:1.0: over-current change on port 1
[75561.800103] hub 3-0:1.0: over-current change on port 1
[75562.792148] hub 3-0:1.0: over-current change on port 1
[75563.536094] hub 3-0:1.0: over-current change on port 1
[75564.528102] hub 3-0:1.0: over-current change on port 1
[75565.272872] hub 3-0:1.0: over-current change on port 1
[75566.264584] hub 3-0:1.0: over-current change on port 1
[75567.008092] hub 3-0:1.0: over-current change on port 1
[75568.000114] hub 3-0:1.0: over-current change on port 1
[75568.744107] hub 3-0:1.0: over-current change on port 1
[75569.736100] hub 3-0:1.0: over-current change on port 1
[75570.480164] hub 3-0:1.0: over-current change on port 1
[75571.472764] hub 3-0:1.0: over-current change on port 1
[75572.216104] hub 3-0:1.0: over-current change on port 1
[75573.208108] hub 3-0:1.0: over-current change on port 1
[75573.952092] hub 3-0:1.0: over-current change on port 1
[75574.944402] hub 3-0:1.0: over-current change on port 1
[75575.688092] hub 3-0:1.0: over-current change on port 1
[75576.681208] hub 3-0:1.0: over-current change on port 1
[75577.424094] hub 3-0:1.0: over-current change on port 1
[75578.168098] hub 3-0:1.0: over-current change on port 1
[75579.160093] hub 3-0:1.0: over-current change on port 1
[75579.904096] hub 3-0:1.0: over-current change on port 1
[75580.896093] hub 3-0:1.0: over-current change on port 1
[75581.640096] hub 3-0:1.0: over-current change on port 1
[75582.632105] hub 3-0:1.0: over-current change on port 1
[75583.376100] hub 3-0:1.0: over-current change on port 1
[75584.368096] hub 3-0:1.0: over-current change on port 1
[75585.112658] hub 3-0:1.0: over-current change on port 1
[75586.105021] hub 3-0:1.0: over-current change on port 1
[75586.848287] hub 3-0:1.0: over-current change on port 1
[75587.840109] hub 3-0:1.0: over-current change on port 1
[75588.584100] hub 3-0:1.0: over-current change on port 1
[75589.576100] hub 3-0:1.0: over-current change on port 1
[75590.320187] hub 3-0:1.0: over-current change on port 1
[75591.312736] hub 3-0:1.0: over-current change on port 1
[75592.056099] hub 3-0:1.0: over-current change on port 1
[75593.048093] hub 3-0:1.0: over-current change on port 1
[75594.040259] hub 3-0:1.0: over-current change on port 1
[75594.784125] hub 3-0:1.0: over-current change on port 1

```

EDIT: did more playing around with rebooting and dmesg, and discovered that those "over-current" messages only display when the external hdd is plugged in.  when i take it out, the messages go away.  also, i use a usb mouse and do not get any messages at all from that being plugged in.

read a note here that talks about the usb port just not having enough power:
[http://forum.soft32.com/linux/usb-current-ftopict352993.html](http://forum.soft32.com/linux/usb-current-ftopict352993.html)

...and about using a Y-usb cable.  could that be the issue?


output from other commands are below:

```
$ sudo fdisk -l
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0008a31e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14406   115716163+  83  Linux
/dev/sda2           14407       14593     1502077+   5  Extended
/dev/sda5           14407       14593     1502046   82  Linux swap / Solaris


$ cat /etc/fstab
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda1 :
UUID=3021e0c4-f58f-47f3-bf77-faadc24c691e / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=065cf230-99d7-48af-97b8-fbfca58f2121 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0



$ sudo blkid
/dev/ramzswap0: TYPE="swap" 
/dev/sda1: UUID="3021e0c4-f58f-47f3-bf77-faadc24c691e" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="065cf230-99d7-48af-97b8-fbfca58f2121" 



$ mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-17-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/daddy/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=daddy)



$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 045e:0745 Microsoft Corp. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by Rocket2DMn on 2010-10-17
That does seem to indicate that it is trying to draw too much power. Is the hard drive powered by USB (like a 2.5" external) or does it have its own power adapter? You shouldn't need to get a Y cable, it could be that you have too many other USB devices plugged in to that hub.

---

### Post by b_k_chu on 2010-10-17
yup, it's powered by the usb.  the only other usb device i have plugged in is my mouse, and i tried unplugging that already, so that the external hdd was the only thing i had plugged in.  got the same result.

---

### Post by Rocket2DMn on 2010-10-17
Well that's rather strange.  If you have an external USB hub that has its own power supply, you might try that. However, the drive should work normally plugged into the computer's internal USB hub. It also could be a design or other type of failure in the drive. If you're not able to get it to connect, you might consider filing a bug report on Launchpad.

---

### Post by sendblink23 on 2010-10-17
Did you try powering up the computer with the External hard drive plugged in... if it has a button to power on the external hard drive well turn it on before powering up the computer?

I had a similar issue with an external and I did that then it worked for me.. but it was not a western digital HD.

There is another thing you could try...  boot up a LiveCD(doing what i said above with the external) ... and if its detected... try formating it using Gparted to NTFS again... maybe that will make it work for your installed Ubuntu afterwards..

these are just random suggestions to try... if it doesn't work... hopefully someone else provides a solution for you

---

### Post by styLz on 2010-10-17
I'm new to ubuntu and I am having this same problem.

So the interesting thing is when I plugged up my phone it picked up the sd card but when I plug up my WD passport external hard drive nothing shows up. I downloaded mountmanager and it doesn't even show up on the list of mounted devices. 

Greatly appreciate the help.

---

### Post by b_k_chu on 2010-10-23
i tried your suggestion sendblink23, booting up with a livecd....still no luck.  got the same "over-current change" error in dmesg, over and over.  and there is no power button to push....the drive's powered purely by the usb port.

it probably is something with the drive after all, Rocket2DMn....after a while i remembered that i had bought this drive as "recertified".  maybe the person who bought it before me ran into the same problem and returned it as a "bad drive".  though it does work with my windows desktop....just not with my laptop, apparently.

guess i'll be trying the Y cable after all and see if it just needs more power.

---

### Post by b_k_chu on 2010-11-13
y-usb cable did the trick.

marking this as solved.

---

