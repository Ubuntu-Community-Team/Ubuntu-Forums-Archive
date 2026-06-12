---
title: "Grub is messed up"
date: 2010-01-31
forum: General Help
---

### Post by BrutalSpoon on 2010-01-31
Hi guys,

I've run into a major problem, and I've trawled the internet but can't seem to find the exact same issue, so I've made a new thread.

So, I installed Ubuntu onto a 160gb drive. I have other drives in the system, but I disconnected them so that the system drive would be sda. Ubuntu installed perfectly with no issues whatsoever.

I connected the other drives in the system, and again it booted up perfectly (although I can't remember whether the 160gb drive remained as sda or became sdd). Then I attached some extra drives temporarily to do some data shuffling. This moved my system drive to become sdf.

My computer booted fine multiple times like this, but when I was finished with the drives I rebooted and suddenly everything broke. For some reason my ubuntu installation showed up in the GRUB twice, and neither of them booted.

So, I popped in the Live CD (which I'm using to type this post), and decided to update the grub. I chrooted into my system drive and ran update-grub, but it simply returned something like this:

```
grub-probe: error: Cannot find a GRUB drive for /sdd1. Check your device map.

Cannot find list of partitions!
```

This is obviously not working how it should be, so I decide to uninstall GRUB2 and install GRUB. I backed up the GRUB then purged grub2 and grub-pc. Then, when I entered in apt-install grub it seemed to download it and install it just fine. Running update-grub detected my installation just fine. However, when I go to install it to the drive with grub-install /dev/sdd, I get the following error:

```
/dev/sdd does not have any corresponding BIOS drive.
```

As far as I know, this should be a problem since I bound /dev from the live cd to /dev in the chroot.

This is really frustrating, as I had the server working absolutely perfectly and it was ready to go, and now THIS happens. Any ideas?

Thanks in advance (as always),

BrutalSpoon

---

### Post by quixote on 2010-02-02
I would guess that plugging and unplugging the drives terminally confused the poor little grub.  Unplug all the other drives, plug in your ubuntu drive by itself, rebuild grub, and then in future be sure to have your ubuntu drive plugged in first.  Or in whatever order you had it when you rebuilt grub.

Or have you tried all that already?

---

### Post by BrutalSpoon on 2010-02-02
> **quixote said:**
> I would guess that plugging and unplugging the drives terminally confused the poor little grub.  Unplug all the other drives, plug in your ubuntu drive by itself, rebuild grub, and then in future be sure to have your ubuntu drive plugged in first.  Or in whatever order you had it when you rebuilt grub.

Or have you tried all that already?

Yes, I had tried that with no success.

I've given up on it and reinstalled Ubuntu - absolutely no data loss since I had it installed on a 10GB partition. Now, it boots perfectly, and pretty much everything works, but for the life of me I just can't get a drive to mount - no matter what I try I keep getting '/dev/sdb1 is mounted or /media/Sigholt (the mounting point) is busy'.

But that's a problem for another thread, I guess :P

Thanks for the tip, though :)

---

### Post by oldfred on 2010-02-02
I agree that grub was confused with the plugging & unplugging of drives. It has a file device.map that you probably could have updated to fix the issue. (for future reference)

Example, yours was probably missing sdd:
/boot/grub/device.map
(hd0)    /dev/sda
(hd1)    /dev/sdb

sudo dpkg-reconfigure grub-pc
or
If it complains about a device map 
sudo grub-mkdevicemap

On your new problem is the drive already mounted?

---

### Post by BrutalSpoon on 2010-02-02
> **oldfred said:**
> On your new problem is the drive already mounted?

No - when I click on it in 'places' or in the file manager, it tells me that only root can mount it (hence implying that it's not yet mounted). I then enter 'sudo mount /dev/sdb1 /media/Sigholt' and I get the error I mentioned before.

I've tried typing 'umount /dev/sdb1', and that returns that it's not mounted, and I type 'umount /media/Sigholt', which returns that there's nothing mounted there.

Curiously, when I type in 'mount /dev/sdb1 -t ext2 -f /media/Sigholt' I get no error at all, but I go to /media/Sigholt and there's nothing there.

Thanks for your reply... any thoughts?

---

### Post by bumanie on 2010-02-02
It is possible that the drives you are trying to mount are not in /etc/fstab
[Here is a site]("http://www.tuxfiles.org/linuxhelp/fstab.html") that explains fstab and how to add drives to it. If you need help, post back, but also supply the output of terminal command > cat /etc/fstab /etc/fstab may be OK, but that is the first place I would check.

---

### Post by quixote on 2010-02-02
If a drive is not in fstab, it should only need a complete mount command, such as he's giving it, in order to mount.  That said, it can't hurt to try putting it in fstab, rebooting, and seeing if that makes any difference.

One question: why are you using "-f"?  Man says that does the following:> -f  [INDENT]Causes everything to be done except for the actual system call; if it's not obvious, this ``fakes'' mounting the file system.  This option is useful in conjunction with the -v flag to determine what the mount command is  trying  to  do. It can also be used to add entries for devices that were mounted earlier with the -n option. The -f option checks for existing record in /etc/mtab and fails when the record already exists (with  regular  non-fake mount, this check is done by kernel).[/INDENT]


So, if you always use the -f switch, maybe that's the problem?

---

### Post by BrutalSpoon on 2010-02-03
> **quixote said:**
> If a drive is not in fstab, it should only need a complete mount command, such as he's giving it, in order to mount.  That said, it can't hurt to try putting it in fstab, rebooting, and seeing if that makes any difference.

One question: why are you using "-f"?  Man says that does the following:

So, if you always use the -f switch, maybe that's the problem?

Just to clarify:

If I just type in 'sudo mount /dev/sdb1 /media/Sigholt', it tells me that either the drive is mounted or the destination is busy. If I add the -f switch it doesn't error at all, but simply doesn't seem to do anything.

... After checking the mount man, I realise I was getting -f mixed up with '-o force', which I've used to mount NTFS drives previously. Would you recommend using that? Or not? Would it make any difference either way?

Haven't yet gotten around to checking the fstab yet. I'm about to temporarily shift the server back to somewhere I can get a monitor plugged in, otherwise whenever I try to VNC into it I just get a black screen. But I'll worry about that later. One problem at a time :)

Thanks to everybody for their replies and help.

EDIT: Turns out that everything's decided to start working for no apparent reason. Sigholt mounts fine (at least for now), and it turns out my VNC problem was just that I'd forgotten to turn off the local request for remote desktop ](*,)

If I have problems again I'll start up a new thread. Thanks once more for your help, everyone, and a gold star for each of you! :KS

---

