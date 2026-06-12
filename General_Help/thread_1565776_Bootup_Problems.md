---
title: "Bootup Problems"
date: 2010-09-01
forum: General Help
---

### Post by cturnes on 2010-09-01
I'll try to include as much detail as possible but if there's something I forget, I'll mtry tio supply it.

I recently upgraded to 10.04 after a slew of problems caused by accidentally uninstalling important packages from my 8.04 installation.  After a lot of difficulty and some very late nights, I managed to get 10.04 up and running, but it has always seemed to have boot problems that 8.04 never had.

At the moment, it has stopped booting altogether.  If I try a normal Ubuntu boot, the screen just hangs at "Starting Up...".  If I try to boot to recovery mode, in the middle of loading the various HDDs, it will simply stop, though the hard drive makes so much noise you'd think it was doing something... I tried unplugging all USB devices, since someone else said that fixed the problem for them, but my problem remains, though this time, it manages to load all the way up to the network drivers.

Now, clearly the HDD with Ubuntu on it has the OS and it's detected during boot, since the normal boot procedures start.  However, when I boot to the Live CD and try to mount the hard drive, run fsck, etc., it complains about the drive and won't mount it.  

The answer that I'm sure people will want to give first is that the drive is dead, but I very much doubt that is true.  Whether it is true or not, I'm too stubborn to simply relegate it to that and give up, especially since there are files on that drive I'd very much like to have back...

Can anyone think of how to fix this, or what might be the problem?  None of these boot issues started until the upgrade to 10.04.

---

### Post by tt33l3r on 2010-09-01
Sounds like you drive is dead to me.

---

### Post by oldfred on 2010-09-01
Have you tried the extended file checks:

From liveCD so everything is unmounted, change to your drive, partition
sudo e2fsck -C0 -p -f -v /dev/sdb1
if errors:
sudo e2fsck -f -y -v /dev/sdb1

What errors do you get when trying to mount it?

---

### Post by techunit on 2010-09-01
There was a warning  about upgrading from 8.04 to 10.04. A back-up and clean install is your best bet.

---

