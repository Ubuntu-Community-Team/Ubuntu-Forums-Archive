---
title: "Usb"
date: 2010-01-14
forum: General Help
---

### Post by okmijn22 on 2010-01-14
In windows XP, if you want to access a USB drive, then you would go the My Computers, and then under Devices with External Storage, you would find the drive. I am wondering where this same drive can be found in Ubuntu.
Thanks!

---

### Post by howefield on 2010-01-14
On mine, I get an icon on the desktop and also the device appears in the places menu.

Are you not seeing anything when the disk is inserted ?

---

### Post by okmijn22 on 2010-01-14
Yesterday, it was working, today it does not appear.

---

### Post by Leppie on 2010-01-14
and the usb stick works fine in windows?

---

### Post by okmijn22 on 2010-01-14
Yes, because I dual boot. When the same usb boots from windows, it shows.

---

### Post by warfacegod on 2010-01-14
Did you "Safely Remove Hardware" the last time it was in a Windows machine?

---

### Post by okmijn22 on 2010-01-15
Yes, I believe so.

---

### Post by warfacegod on 2010-01-15
Try looking under Places. If it's not there Computer in the Places menu is where it would be.

---

### Post by rcayea on 2010-01-15
Maybe you could double check in the dev folder in the file system. Someone else may better correct me because maybe it should show up in the media folder? One of them. I say click on the file system and click around to be sure it is there.

---

### Post by warfacegod on 2010-01-15
> **rcayea said:**
> Maybe you could double check in the dev folder in the file system. Someone else may better correct me because maybe it should show up in the media folder? One of them. I say click on the file system and click around to be sure it is there.

/dev if it isn't mounted /media if it is.

Assuming, of course, that the device hasn't had it's mount point reassigned.

---

### Post by Leppie on 2010-01-16
could you post your fstab and the output of the following command:
```
groups <yourusername>
```

---

### Post by okmijn22 on 2010-01-16
*** : *** adm dialout cdrom plugdev lpadmin admin sambashare
***@ubuntu:~$ 
Is this what you wanted me to post?
And how do I post fstab.
Sorry I am a neophyte.

---

### Post by blackened on 2010-01-16
fstab probably won't be of any help if it's using hotplug, which we have to assume it is.

If it mounts on Windows, but not on Ubuntu, then it is likely one of two things: an unclean mount of an NTFS volume (you didn't use "Safely Remove Hardware") or the device follows [U3 spec]("http://en.wikipedia.org/wiki/U3") and won't mount automatically.

First, as has already been mentioned, you should check if the drive exists under the "Places" menu or is mounted in /media. You may need to remove the drive, reboot, then replug the drive. Hotplug flakes out pretty easily sometimes.

---

### Post by okmijn22 on 2010-01-16
It is not under Places
and I replugged and rebooted and still nothing. 
Then I think I may not have 'Safely Remove Harddrive,'
Is there any solutions for this?

---

### Post by warfacegod on 2010-01-16
> **okmijn22 said:**
> It is not under Places
and I replugged and rebooted and still nothing. 
Then I think I may not have 'Safely Remove Harddrive,'
Is there any solutions for this?

Yes, plug it into a Window a machine and Safely Remove it.

---

### Post by okmijn22 on 2010-01-16
I just did that and it still does not show?

---

### Post by warfacegod on 2010-01-17
I'm fairly sure you are having the same problem as the guy in this thread. If the problem isn't the same I think the fix we are working on will work for you as well.

[http://ubuntuforums.org/showthread.php?t=1382173]("http://ubuntuforums.org/showthread.php?t=1382173")

---

### Post by okmijn22 on 2010-01-17
I don't think it is the same. I cannot even see the drives.
I must have done something wrong because it worked before, like the day before yesterday.

---

### Post by warfacegod on 2010-01-17
This may not be your fault, don't beat yourself up. It may not be the same problem but I still think they are related.

---

### Post by Leppie on 2010-01-17
> **okmijn22 said:**
> *** : *** adm dialout cdrom plugdev lpadmin admin sambashare
***@ubuntu:~$ 
Is this what you wanted me to post?
And how do I post fstab.
Sorry I am a neophyte.

first of all, you need to put yourself in the fuse group. this group allows you to mount using your permissions, not root's permissions. to add yourself:
```
sudo useradd <youruseraccount> fuse
```

to view your fstab:
```
cat /etc/fstab
```

---

### Post by okmijn22 on 2010-01-17
I'll try that right now.
Now I have experienced another problem.
For exmaple when I boot Ubuntu with the USB mouse in the USB slot, it works.
However, once I boot into the OS and I take the USB mouse out of the slot, and then reinsert it, it would not work anymore.

---

### Post by Leppie on 2010-01-17
> **okmijn22 said:**
> I'll try that right now.
Now I have experienced another problem.
For exmaple when I boot Ubuntu with the USB mouse in the USB slot, it works.
However, once I boot into the OS and I take the USB mouse out of the slot, and then reinsert it, it would not work anymore.
could you boot with your usb mouse plugged in, then once logged in take it out, issue the following command:
```
tail -f /var/log/messages
```
then hit enter a couple of times to mark the start of the connection process and then connect the mouse and post the output.

could you also do the same for the usb drives? i.e. issue the command:
```
tail -f /var/log/messages
```
hit enter a couple of times to mark the start of the connection process, connect a drive and post the output

---

### Post by okmijn22 on 2010-01-17
fstab
***@ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

---

### Post by okmijn22 on 2010-01-17
Mouse
***@ubuntu:~$ tail -f /var/log/messages
Jan 17 15:04:56 ubuntu kernel: [   28.293151] ppdev: user-space parallel port driver
Jan 17 15:05:00 ubuntu kernel: [   32.137635] integrated sync not supported
Jan 17 15:05:00 ubuntu kernel: [   32.281657] integrated sync not supported
Jan 17 15:05:00 ubuntu kernel: [   32.421695] integrated sync not supported
Jan 17 15:05:15 ubuntu kernel: [   47.607493] integrated sync not supported
Jan 17 15:05:15 ubuntu kernel: [   47.750723] integrated sync not supported
Jan 17 15:05:16 ubuntu kernel: [   47.897096] integrated sync not supported
Jan 17 15:05:23 ubuntu kernel: [   55.567047] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Jan 17 15:05:23 ubuntu kernel: [   55.678048] padlock: VIA PadLock not detected.
Jan 17 16:23:49 ubuntu kernel: [ 4761.024180] usb 2-1: USB disconnect, address 2
How do I post output?

---

### Post by okmijn22 on 2010-01-17
USB
***@ubuntu:~$ tail -f /var/log/messages
Jan 17 16:47:00 ubuntu kernel: [   27.880114] integrated sync not supported
Jan 17 16:47:00 ubuntu kernel: [   28.635458] ppdev: user-space parallel port driver
Jan 17 16:47:03 ubuntu kernel: [   31.173634] integrated sync not supported
Jan 17 16:47:03 ubuntu kernel: [   31.313531] integrated sync not supported
Jan 17 16:47:03 ubuntu kernel: [   31.453632] integrated sync not supported
Jan 17 16:47:24 ubuntu kernel: [   52.150863] integrated sync not supported
Jan 17 16:47:24 ubuntu kernel: [   52.298643] integrated sync not supported
Jan 17 16:47:24 ubuntu kernel: [   52.450737] integrated sync not supported
Jan 17 16:47:30 ubuntu kernel: [   57.900661] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Jan 17 16:47:30 ubuntu kernel: [   58.032060] padlock: VIA PadLock not detected.

---

### Post by okmijn22 on 2010-01-18
bump........

---

### Post by Leppie on 2010-01-18
didn't provide much more info. could you also post the output of lsmod?

---

### Post by okmijn22 on 2010-01-18
How do I provide output of Ismod?

---

### Post by blackened on 2010-01-18
> **okmijn22 said:**
> How do I provide output of Ismod?

lsusb would likely be helpful as well. So would a full output of /var/log/messages.

```
lsmod > lsmod.txt
```

Then attach lsmod.txt to your post.

Or you could just enter lsmod into the terminal, then cut and paste the results into your post, preferably wrapped in code tags.

---

### Post by okmijn22 on 2010-01-18
This is very strange. The mouse and the USB suddenly works again... Do you guys still want me to post the Ismod?

---

### Post by Leppie on 2010-01-18
> **okmijn22 said:**
> This is very strange. The mouse and the USB suddenly works again... Do you guys still want me to post the Ismod?
well, if your usb works normally we know that all modules are loaded correctly.
post it when the issue returns.
did you receive some system updates in the meantime?

---

### Post by okmijn22 on 2010-01-19
Yes, there may have been some system updates in between the time it did not work and when it did work.

---

### Post by Leppie on 2010-01-19
> **okmijn22 said:**
> Yes, there may have been some system updates in between the time it did not work and when it did work.
then with a bit of luck, the issue has been resolved by one of the updates. i saw one of the messages you were receiving filed as a bug which seemed to be related to video card drivers (but messing up the whole kernel in some cases).
monitor your system for this behavior

---

### Post by okmijn22 on 2010-01-19
Are there some guides that would teach me some system monitoring techniques?

---

### Post by blackened on 2010-01-19
> **okmijn22 said:**
> Are there some guides that would teach me some system monitoring techniques?

When in doubt, check the logs. Oh, and learn to use grep to sift through the mountains of information contained in the logs. The use of the pipe (|) and stdout redirect (>) are also helpful.

There are myriads of introductory commandline lessons available online. The trick to making the commands stick is to use them in your daily interaction with your machine.

---

### Post by Leppie on 2010-01-19
also dmesg and tail are useful for system monitoring, you can combine a lot of things.
like the following:
```
dmesg | tail
```
will show you the last part of the dmesg log.

---

