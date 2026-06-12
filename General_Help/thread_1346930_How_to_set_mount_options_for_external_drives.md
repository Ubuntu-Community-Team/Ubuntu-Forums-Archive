---
title: "How to set mount options for external drives?"
date: 2009-12-05
forum: General Help
---

### Post by eekhoorn13 on 2009-12-05
Hi,

I believe this is my first post here. Jeej \o/

Anyway. I have problems with setting default and partition specific mount options for external drives. To be clear: I'm running Ubuntu 9.10, but upgraded from 9.04 (which was a clean install if I remember well). There are two situations:

[LIST=1]
[*]I want external drives with an NTFS (or FAT or that matter) filesystem to be mounted with some specific mount options (most important 'noexec'). For my internal drives fstab works great, but for obvious (?) reasons, I need another solution.
[*]At one specific external drive I have 2 partitions for backups. But one partition never needs to be mounted at this computer (because it contains the backups of another computer). I don't need/want it to be impossible to mount it, but just don't want to auto-mount it. Of course I can add an fstab entry, but that would result in an error message every time I attach the drive.
[/LIST]

I've looked into documentation about HAL, gnome-mount and udev, but HAL seems to be deprecated (?), gnome-mount doesn't seem to be installed and about udev I'm not sure how to recognize external NTFS filesystems in general or my specific not-to-be-mounted partition (no uuid sort of thing?).

Probably I should know how to do it by now, but in that case I just have pumped to much information in my head to get to the answer. Anyway, although looking through documentations and learning how the system works is great study-avoiding-behavior, I'd like to get thing working by now. Anyone has an idea?

---

### Post by hal10000 on 2009-12-05
Mount-options for external drives are exactly the same as for internal drives. So, an option which works for an internal drive will also work for an external.

The options you can use depend only on the type of the file system you are going to mount. There is a brief description of the options you can use in the manpage of the mount command.

If you don't want a partition to be mounted (no matter wether on an external or internal drive), just don't put it into your fstab or comment it out. You can always mount a partition manually with the mount command, even if it has no fstab or mtab entry. You can also use the **noauto **option to prevent it from being mounted at boottime.

As long as your external drive is recognized by ubuntu don't mess around with hal or udev, they have nothing to do with your case.

---

### Post by eekhoorn13 on 2009-12-05
Thanks for your reply. But I'm probably not completely clear on the problem. I understand and already knew what you are saying. The problem is that, unlike the internal drives, I don't have my external drives connected at all times. So I'm not talking about automounting at boot time, but at the moment I plug it in.

As I understand it, at the moment I plug in my external drive, udev creates an device node in /dev and then gnome/nautilus mounts the drive under /media/{label}. And hal is in between them (but will be replaced entirely by udev (or something else?) in the near future?). On some fora I found information about gnome using gnome-mount for this and some clear instructions on how to set mount options using gconf (see also gnome-mount man pages). But gnome-mount isn't installed and so this doesn't work for me. Other fora mentioned something about hal being able to 'advice' processes (ie mount software) on how to handle certain hardware. So I should be able to set up certain policies among which the mount options to be used ([http://webcvs.freedesktop.org/hal/hal/doc/spec/hal-spec.html?view=co&pathrev=HEAD#device-properties-storage-policy](http://webcvs.freedesktop.org/hal/hal/doc/spec/hal-spec.html?view=co&pathrev=HEAD#device-properties-storage-policy)). I can set the policy attributes this way, but it isn't looked at (and seems to be an old way of doing things as I read somewhere that HAL is being kicked out). So that doesn't work either. Last thing I got was that the only option was to write an udev rule which would start a shell script after the device node was made and that script would mount the filesystem with all the desired options.

I just don't know whether this is indeed the right way to go and, if so, how to recognize either 'any ntfs/fat filesystem inserted' or the specific partition not to be mounted.

Hopefully this makes my problem a bit more clear.

---

