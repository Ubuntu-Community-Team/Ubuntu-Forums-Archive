---
title: "please help me, system crashed during karmic upgrade"
date: 2009-11-12
forum: General Help
---

### Post by pgeorge3 on 2009-11-12
Hi all,

             I had a perfectly running jaunty and last night i started an upgrade to karmic when suddenly it crashed during the installation stage. After that it won't boot up. I can see my files are still there but boot it up to get it running. What is the best way to deal with this? I don't mind going back to jaunty but all my teaching and research stuff are in there plus lots of software and other stuff. Please help me. Really appreciate it.

---

### Post by Andreas1 on 2009-11-12
I would boot up a live cd, collect all personal data and copy it to some place save (another partition or an external storage device) and then do a fresh install.

to avoid such a thing i suggest having the operating system and personal data on two different partitions.

---

### Post by pgeorge3 on 2009-11-12
Sorry to ask a stupid question, is there any way to repair the installtion using a CD or something or is a fresh install after backup the only way to go? Thank you

---

### Post by Andreas1 on 2009-11-12
> **pgeorge3 said:**
> Sorry to ask a stupid question, is there any way to repair the installtion using a CD or something or is a fresh install after backup the only way to go? Thank you

i have heard from a lot of people that upgrading to karmic messed up their system and that it is recommended to do a clean install. it depends on how much effort keeping your old system is worth. if you decide you want to repair it you will have to post more details, like what exactly is going wrong if you try to boot, any error messages...

either way, a good idea would be to back up your entire home folder (/home/username) because all of your settings are stored there. you could then use them again after a reinstall. this is what i personally would do, because if you know exactly where your personal data, including settings, is stored, reinstalling is the least effort. but there have been complaints in the forums that telling people to reinstall as a solution to every problem is not acceptable, so you have to decide for yourself.

EDIT:
oh, and also, either way, you might want to consider sticking with jaunty a little longer because karmic has been reported to be unstable even after a clean install. (happened to me)

---

### Post by pgeorge3 on 2009-11-12
Can I use a jaunty live CD and restore my original stuff at this stage? The message I get when I try to boot now is the following

One or more of the mounts listed in /etc/fstab cannot yet be mounted: (ESC for recovery shell)
/: waiting for /dev/disk/by-uuid/2760910c-a3be-49d7-84a3-509a626c9f87
/tmp: waiting for (null)
swap: waiting for UUID=0c648a87-f312-8129-9f2b8b258db2

and it stays there. As a newbie all i sense is that something is terribly wrong. I will be very happy to go back top jaunty and be there for ever if a jaunty live CD will help at this stage. I am already downloading a 9.04 ISO and i will wait for an expert opinion before i do anything. I don't want karmic.

---

### Post by Andreas1 on 2009-11-12
ok, that is also beyond me, but since it crashed *during* upgrade, if i got that right from your first post, i don't think it is (easily) doable to restore it to the state of before the upgrade, [SIZE="4"]but maybe someone more experienced than me can clarify...[/SIZE]

what you can do regardless of that, is, as soon you have that jaunty cd, start a live session, mount your hard drive, and collect your data. about that:
what exactly are you talking about?
documents stored in your home folder? program preferences? (they should also be in your home folder, typically *hidden* folders, e.g. ".mozilla"). installed programs? i always go through the main menu and write all the extra applications i have installed on a note and then reinstall them on the new system all at once (if they were installed via apt/synaptic and not installed manually, that is.)



EDIT: an example:
i use a mail application called sylpheed. if i were to reinstall my sytem i would do the following:

-copy "/home/andreas/.sylpheed" to "/media/data"  (my extra partition for personal data)
-reinstall ubuntu
-reinstall sylpheed using apt or synaptic
-copy ".sylpheed" from "/media/data" to my new "/home/andreas"

---

### Post by pgeorge3 on 2009-11-12
I have 9.04 on a CD and I am trying to back up my files before doing a fresh install. I see all my folders but somehow they have a "read-only" setting which I am unable to change trying to access them as a "guest". Any way around this? Thanks a lot.

---

### Post by 23dornot23d on 2009-11-12
> **Andreas1 said:**
> I would boot up a live cd, collect all personal data and copy it to some place save (another partition or an external storage device) and then do a fresh install.

to avoid such a thing i suggest having the operating system and personal data on two different partitions.


If you are doing exactly what is said above ....

as long as you can read them ..... your should be able to write the files to 

another drive
as long as you have write permissions for that drive ...... 

You should be able to read the files and write them out .......... to something like ..........

An external USB hard drive ...... you never mentioned how much data you have ........

I back all my files up to an external Terra USB hard drive ..... it is a valuable piece of kit to have and gives
reasonably cheap storage .......


Hope that this helps ..... if you do need more permissions run 

sudo thunar

in a terminal window ..... but I do not think you really need to do this ..... to copy your files
to a disk drive ...... that you have write permissions for ........

Just my quick - 2 cents ,,, hope it helps .......

---

### Post by Andreas1 on 2009-11-12
> **23dornot23d said:**
> sudo thunar

um, thunar would be the file manager of *x*ubuntu. in ubuntu it's nautilus.

but basically 23dornot23d is right, if you can read your files you should be able to copy them somewhere else. if you don't seem to have enough permissions you could run the file manager with root permissions, that would be:
```
gksudo nautilus
```
to be correct

---

### Post by Garnett on 2009-11-12
I had the same problem and found a solution on here that worked perfectly. It was a case of working from the console right where it says that stuff about waiting for mounts.

Gimme a minute to find it before trying anything more complicated...

---

### Post by Garnett on 2009-11-12
I think it was this one:

[http://swiss.ubuntuforums.org/showpost.php?p=8171200&postcount=5](http://swiss.ubuntuforums.org/showpost.php?p=8171200&postcount=5)

From this thread:

[http://swiss.ubuntuforums.org/showthread.php?t=1301766](http://swiss.ubuntuforums.org/showthread.php?t=1301766)

I just typed:

*apt-get -f install*

then

*apt-get upgrade*

I'm not an expert so wait until this gets some decent endorsement but it worked for me.

Here's some more possible solutions:

[http://www.google.co.uk/search?hl=en&client=firefox-a&channel=s&rls=org.mozilla%3Aen-GB%3Aofficial&hs=lI1&q=site%3Ahttp%3A%2F%2Fubuntuforums.org+%22One+or+more+of+the+mounts+listed%22&btnG=Search&meta=&aq=f&oq=](http://www.google.co.uk/search?hl=en&client=firefox-a&channel=s&rls=org.mozilla%3Aen-GB%3Aofficial&hs=lI1&q=site%3Ahttp%3A%2F%2Fubuntuforums.org+%22One+or+more+of+the+mounts+listed%22&btnG=Search&meta=&aq=f&oq=)

---

### Post by blueridgedog on 2009-11-12
I can try and walk you through some long shot type of repairs if you like.  It will involve booting off a liveCD and then mounting your existing file system and running some commands on it.  If it fails, you can always copy off your files and re-install, which looks like your current path.

To get things started, I would like a better understanding of the disk(s) and partitions inside your system.

Can you post the output of:

```
sudo fdisk -l
```

and 

```
mount
```

While running the liveCD?

---

### Post by pgeorge3 on 2009-11-12
Here is the output. I just started the slow and tedious task of backuping my files. Not sure how long it will take. there are lots of issues with licensed software, virtualbox etc with new install. So a repair if possible will be great. Below is the o/p for the fdisk and mount



ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6125db67

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14219   114214086   83  Linux
/dev/sda2           14220       14593     3004155    5  Extended
/dev/sda5           14220       14593     3004123+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ mount
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda1 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)
ubuntu@ubuntu:~$

---

### Post by blueridgedog on 2009-11-12
OK.  What we are going to do is mount your existing drive and try and run a package repair command on it.

Your existing / is /dev/sda1 and it is currently mounted on /media/disk.

When you are ALL DONE with your backups (you can't be doing anything else when you do the following), bring up a terminal and try the following:

Bind dev to the dev on the disk in your PC:
```

sudo mount --bind /dev /media/disk/dev
```

Change to the drive in your PC as the root:

```
sudo chroot /media/disk
```

Try and repair the broken packages on your system:

```
sudo dpkg --configure -a
sudo aptitude -f install
sudo aptitude dist-upgrade
```

After that restart and boot on the hard drive, not the LiveCD to see if the error goes away.

If not, then we can try a few other things if you are still interested in recovery.

---

### Post by pgeorge3 on 2009-11-12
Bingo, I stopped the back up and gave it a shot, at first I got the new version without GUI, i logged in and did the same steps you suggested and they somehow repaired themselves. i am not sure whether everything is perfect but atleast i dont have to reinstall a bunch of stuff. thanks a ton. it tells me that there are 208 bad sectors on my hard disk though, how bad is that and what should I do? my VB works fine and wireless is ok. something is wrong with the flashplayer but i can do that slowly tomorrow. again, thank you very much. didnt have any food or sleep since last night coz of this crap. lemme go and have those now.

---

### Post by pgeorge3 on 2009-11-13
Having problems with frozen panel upon reboot. How to solve this? Thanks

---

### Post by blueridgedog on 2009-11-15
> **pgeorge3 said:**
> it tells me that there are 208 bad sectors on my hard disk though, how bad is that and what should I do? my VB works fine and wireless is ok. something is wrong with the flashplayer but i can do that slowly tomorrow. again, thank you very much. didnt have any food or sleep since last night coz of this crap. lemme go and have those now.

I am glad it worked for you (mostly)!  You need replace that disk ASAP and start a regular backup program.

---

### Post by blueridgedog on 2009-11-15
> **pgeorge3 said:**
> Having problems with frozen panel upon reboot. How to solve this? Thanks

I am on the road (have been for a bit), but will try and come up with some ways to debug it.

---

