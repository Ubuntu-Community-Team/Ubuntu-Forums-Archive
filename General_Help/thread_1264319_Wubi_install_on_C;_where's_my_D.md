---
title: "Wubi install on C:; where's my D:?"
date: 2009-09-12
forum: General Help
---

### Post by soksniffer on 2009-09-12
I installed kubuntu onto my Windows XP-laden C: via wubi.  I can't find any files that are on my 2nd hard drive (D: ).

The only suggestions about it in these forums or anywhere talk about "mounting" and typing in a bunch of goofy-looking MS-DOSesque command strings.  Uh, no thanks.  I'm not interested in learning to program an O/S.  I just want to get to the files I already have on the second hard drive that's already installed.

What do I -CLICK- on to find them?

---

### Post by oboedad55 on 2009-09-12
> **soksniffer said:**
> I installed kubuntu onto my Windows XP-laden C: via wubi.  I can't find any files that are on my 2nd hard drive (D: ).

The only suggestions about it in these forums or anywhere talk about "mounting" and typing in a bunch of goofy-looking MS-DOSesque command strings.  Uh, no thanks.  I'm not interested in learning to program an O/S.  I just want to get to the files I already have on the second hard drive that's already installed.

What do I -CLICK- on to find them?

Not clear. Is it Ubuntu you can't find your second drive/partition or in Windows or both?

---

### Post by P4man on 2009-09-12
> **soksniffer said:**
> 

What do I -CLICK- on to find them?

I don't quite understand the question either, so Ill wait for more info before trying to reply to your actual question, but realize one thing: we usually give terminal commands to do stuff, because it is easier for *us* and for you. 

Its much shorter to type in command like "sudo apt-get install somestuff" than having to describe all the GUI steps to do the same through synaptic package manager. We do it because it works on any ubuntu version (or even other linuxes) in any language and with any desktop manager. We dont have to guess or ask if you're using gnome or kde, if you got an English, french or japanese install. if you are using the netbook remix or a regular desktop install.

Its also easier for you, you just have to copy paste a line in a terminal. It doesn't get faster then that. 

This doesn't mean these things can't be done through a GUI, but usually its a lot easier and faster for everyone on this forum if we give you commands and you can copy/paste any error messages from such commands.

---

### Post by soksniffer on 2009-09-12
I can't find it in kubuntu.  Everything in Windows works as it always did.  I looked in /media, I looked in /dev, I looked under "places" but none of those lead to my 2nd hdd.

As for having gnome, kde, whatever, even if someone asked I couldn't tell 'em.  I have whatever it installed....

---

### Post by ankspo71 on 2009-09-12
Hi,

I don't have Kubuntu installed right now, but if I remember right, the only way that I was able to access another hard drive was inside of the Konquerer web browser (it doubles as a file browser in Kde).
James

---

### Post by NoaHall on 2009-09-12
You know it won't be called D: right? It'll be called something like /media/disk or /dev/sda1 before given a place in /media/

---

### Post by P4man on 2009-09-12
You can ignore this message if you want, but I can't give you GUI instructions for the simple reason I do not have KDE (which comes with Kubuntu, I use gnome, ubuntu, which looks quite different). So here come the terminal commands :)

Open a terminal (i assume its in accessories somewhere, and if memory serves its called Konsole).

There type in the following commands:

```
sudo fdisk -l
```

and

```
mount
```

Copy/paste the output here and we'll know a whole lot more.
Konsole won't bite you :)

---

### Post by soksniffer on 2009-09-12
Well, thanks for the suggestions, everyone --I was hopeful about that Konquerer tip, but all I can find is something called "Gigolo" and the one drive it displays returns an error message when I try to open it ("You are not supposed to show G_IO_ERROR_FAILED_HANDLED in the UI").  Anyway, below are the results of the terminal commands.  Looks mostly like gobbledygook to me.  I can see the 2nd drive there, but that /dev/sdb location doesn't exist in the "file system" window.

This is way more complicated an alternative to windows than I was hoping for.  I commend you folks for developing a new system, but to really take a bite out of microsoft, the next iteration might do well to be designed for the lowest common denominator; i.e., dopes like me.  No terminal commands, no weird-*** naming schemes, just some big dumb icons a la *Idiocracy*.  

Also, security is wonderful, but typing in a password every time I want to fart gets kinda old.  Maybe ditch that feature, as well.

Thanks again for all of your hard work.

-----------------------------------------------------
administrator@ubuntu:~$ sudo fdisk -l
[sudo] password for administrator: 

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000675f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4864    39070048+   7  HPFS/NTFS

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc00237f9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       14593   117218241    c  W95 FAT32 (LBA)
administrator@ubuntu:~$ mount
/host/ubuntu/disks/root.disk on / type ext3 (rw,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
/dev/sda1 on /host type fuseblk (rw,nosuid,nodev,user_id=0,group_id=0,allow_other,blksize=4096)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=755)
/host/ubuntu/disks/boot on /boot type none (rw,bind)
securityfs on /sys/kernel/security type securityfs (rw)

---

### Post by NoaHall on 2009-09-12
I'm going to guess "/dev/sdb1" is what you're looking for. So run "mount /dev/sdb1 /media/disk" and see if it's there. If not, what format/size are your HD's?

---

### Post by P4man on 2009-09-12
> **soksniffer said:**
> Well, thanks for the suggestions, everyone --I was hopeful about that Konquerer tip, but all I can find is something called "Gigolo" and the one drive it displays returns an error message when I try to open it ("You are not supposed to show G_IO_ERROR_FAILED_HANDLED in the UI").  Anyway, below are the results of the terminal commands.  Looks mostly like gobbledygook to me.  I can see the 2nd drive there, but that /dev/sdb location doesn't exist in the "file system" window.

No, /dev/sdb/ is the device (the disk), you have to mount it before you can see any files. In linux you can mount to any folder, so for instance /media/disk could be where could find the files of sdb (your second drive) after you mounted it. Just like you can find the contents of /dev/sda1 in "/host". Its confusing only if you have been used to naming your harddisks c: and d: all your life :)


> This is way more complicated an alternative to windows than I was hoping for.  I commend you folks for developing a new system, but to really take a bite out of microsoft, the next iteration might do well to be designed for the lowest common denominator; i.e., dopes like me.  No terminal commands, no weird-*** naming schemes, just some big dumb icons a la *Idiocracy*.  

Well, linux isn't windows, and doesn't want to become windows. Its different. Its only more difficult initially if you've spent your life using windows. Some things are more complicated perhaps, especially if they don't work right away, but most things DO work right away, and there is plenty thats a lot easier. Finding and installing software and drivers, keeping your PC up to date, avoiding spyware, crapware and virusses to name just a few. It takes an untrained windows users a lot longer to learn that :)

> Also, security is wonderful, but typing in a password every time I want to fart gets kinda old.  Maybe ditch that feature, as well.

You only have to type it once every 10 or 15 minutes. Aint that bad. Once your system is setup, you'll pretty much never need it anymore, other than for logging in.

Anyway, so much for the lecture. Im surprised the second harddrive isn't mounted. Its a FAT32, so there shouldn't be much problems. again, ill have to give you terminal commands, perhaps you'll get used to it :)

First lets see if we can mount it manually. Lets make a mountpoint:

```
sudo mkdir /media/d_drive
```

That is just an empty folder we are making, and  that will become the location where you can find your files on drive D: after mounting.

Then mount the partition in such a way everyone can read and write to it:

```
sudo mount /dev/sdb1 /media/d_drive -t vfat -o umask=0000
```

If that gives no error, use Konquerer or whatever and see if you can find your stuff in /media/d_drive

If so, we can make it permanent, as it is, kubuntu will forget about the mount next boot.

If it fails, post the error message.

BTW, not to start a windows vs linux flamewar, but how well is windows reading your ubuntu disk ? :)

---

### Post by soksniffer on 2009-09-15
That worked -- thanks!  But it's gone after a reboot, as you predicted.  I tried some stuff from this:
[https://answers.launchpad.net/ubuntu/+question/14652](https://answers.launchpad.net/ubuntu/+question/14652)
And the d: (or d_drive) shows up in file manager, but it's empty.

You won't start a linus vs. windows war with me; I think a home computer should be waiting and working for its user, not the other way around, yet so far all pc o/s's I've used have been horrible time-sinks for a regular jerk like me.  I'd probably like a mac better, but they're too expensive and kind of snobby anyway (I never hear anyone gloat about how much better their ball-peen hammer is than someone else's, so why do mac owners lord over people?  It's just a tool!).

---

### Post by P4man on 2009-09-15
To make the change permanent, edit a file called "fstab", which defines mount points. Im pretty sure there is a GUI to let you do it, but since im not kubuntu, I'll give you the more universal way. First open fstab in a text editor (kate) as super user:

```
kdesu kate /etc/fstab
```

Add the following lines:

```
# "D: drive"
/dev/sdb1 /media/d_drive vfat umask=0000 0 0
```

save, and reboot, and cross fingers :)

---

