---
title: "Problem with automount cdrom and usb memory sticks after upgrade from 10.10 to 11.04"
date: 2011-04-30
forum: General Help
---

### Post by Kapucha on 2011-04-30
This is serious problem. After upgrade from 10.10 to 11.04 I was suprised that I system can't mount automaticly usb memory sticks or cd rom or any external memory devices.

Is this normal in new ubuntu? Previous version (10.10) version was working exellent and automounting was working good. Is there any way to make automount working in this new version?

---

### Post by jamesjenner on 2011-05-01
Hey,

I've just had similar problems, discovered with duel external (identical) drives that I was setting up for backups.

I had formatted both of them a while back and was using one for file transfers, so the first one I did a backup via deja and then decided to reformat the second one instead of deleting all the info off of it.

I found that after I reformatted and repartitioned that it wouldn't auto mount. I could mount it manually and everything appeared to be okay (I was using Disk Utility), I could transfer files, etc but Unity wouldn't auto mount and as such deja wouldn't see it as a drive to backup to.

After comparing the two I realised what was wrong. The drive that worked had the following info defined in Disk Utility:

Partition Type: HPFS/NTFS (0x07)
Type: FAT (32-bit version)

The drive that didn't work I had formatted as Master Boot Record and then as FAT, I tried formatting the volume (or partition, not sure now) as FAT as well, it kept saying that the type was unknown. I found that if I formated the drive with NTFS and then the partition (or volume, not sure which it was now), then Unity now discovers the drive and it shows the same info as the original.

I'm going to do a little reading up about the formatting of drives with linux, obviously there is two levels, the drive and the partitions (which makes sense but I hadn't really thought about it). Just check out what your's are via Disk Utility and if you see the unknown against the Type under Volumes then maybe that is the cause of your problem.

Cheers,

James.

(I should note, I'm pretty rusty with linux, haven't really used it for years, so apologies if I'm screwing things up in my explanation).

---

### Post by qwazix on 2011-05-01
The same thing here too, on two different Dell Laptops. Anybody got a solution? No usb drive automounts (I am able to mount manually though)

I installed usbmount and then for only one time the flash drive was automounted, but not in the usual way (on /media/usb0 and I had to be root to unmount it). At the same time the 4.0 gb filesystem entry on the left of nautilus appeared along with another one usb0 that had the eject icon. As soon as I unmounted usb0 (sudo umount /media/usb0/) I was able to mount 4.0GB filesystem by clicking on it. That was the only time it worked. Finally I autoremoved usbmount.

---

### Post by qwazix on 2011-05-01
SOLVED

There was an entry in fstab, for a filesystem at sdb1, but sdb1 does not exist, it gets created when you plug in a flash drive. The automounter probably thinks it's already mounted (since it's in fstab) and ignores it.

On the other machine there was an sdc (sdb was the root fs) and that was the problem. Upon installation there was another drive so the fstab was created with sdc.

---

### Post by penguinus on 2011-05-06
I have the same problem, but I've checked /etc/fstab and there are no incorect values

---

### Post by bryanagee on 2011-05-18
> **penguinus said:**
> I have the same problem, but I've checked /etc/fstab and there are no incorect values

+1

I also have a question on AskUbuntu.com here:
[http://askubuntu.com/questions/43699/cd-rom-not-mounting](http://askubuntu.com/questions/43699/cd-rom-not-mounting)

---

### Post by penguinus on 2011-05-18
[http://ubuntuforums.org/showthread.php?t=1745808#8](http://ubuntuforums.org/showthread.php?t=1745808#8)

---

### Post by roshan18 on 2011-05-20
I have been using Ubuntu for many years now and this is the first time Ubuntu has disappointed me, with such a major issue left hanging in a release. I upgraded the distribution from 10.04 to 10.10 and then immediately, from 10.10 to 11.04. I didn't do a clean install since I didn't have sufficient time. I have used distribution upgrade before and haven't faced any issue. But this time I was stuck with a system which is in a barely useable state. I can't fall back to the system which worked. I have to find a workaround/alternative to this automounting issue in the current release. Otherwise, I have to do a clean install, in which case I would have chosen the much stabler 10.04 since I didn't want to find similar issues in a clean install too. In either case, I would have to 'waste' time, which was what I was trying to avoid; the whole point of using distribution upgrade. Disappointed. Frustrated. I have advocated Ubuntu to all my friends for a long time now, but I won't be suggesting 11.04 to anyone. Enough of the rant!

I have searched and searched but haven't found a solution to this automounting issue. After days of tracking, I have found some independent alternatives that resolve the automounting issue to some extent, each with their own pros/cons. You can try one of the following 3 independent alternatives - whichever suits you the best.

**PROBLEM:**
cdrom and USB flash drives don't automount. cdrom doesn't mount even on clicking the cdrom icon in nautilus computer or left side-bar. USB flash drives aren't even listed in nautilus computer or left side-pane. The only way to mount and unmount cdrom and USB flash drives was using specific commands.

**ALTERNATIVE A : halevt**
halevt wasn't installed in my system. On installing halevt, I got a post-installation script error. I found a bug in launchpad which says 'halevt failed to install on distribution upgrade' :
[https://bugs.launchpad.net/ubuntu/+source/halevt/+bug/746949](https://bugs.launchpad.net/ubuntu/+source/halevt/+bug/746949)
A workaround is mentioned in the comments and I tried that out : Install halevt (ignore the error). Comment out the line "invoke-rc.d --quiet hal restart" in /var/lib/dpkg/info/halevt.postinst, Run "dpkg --configure -a", Reboot.
USB flash drive automounts with root permissions. They can't be unmounted without root permissions i.e. they can only be unmounted using specific commands. This issue has been raised in [http://ubuntuforums.org/showthread.php?t=1702452](http://ubuntuforums.org/showthread.php?t=1702452).
cdrom doesn't automount. On clicking the icon in nautilus computer or left side-pane, cdrom mounts. It can be unmounted through the 'Eject' menu option on right-clicking the mounted cdrom.
[B]
ALTERNATIVE B : udisks scripts[/B]
These scripts provide the same behavior as 'Alternative A', but with more customization. The scripts can be found here:
[https://wiki.archlinux.org/index.php/Udev#Auto_mounting_USB_devices](https://wiki.archlinux.org/index.php/Udev#Auto_mounting_USB_devices)
There is an option to 'allow a non-root user to unmount udev-mounted devices. The required username must be hard-coded in the RUN command, so this rule set may not be suitable for multi-user systems.'

**ALTERNATIVE C : devmon (udisks wrapper)**
Install devmon ([http://igurublog.wordpress.com/downloads/script-devmon/](http://igurublog.wordpress.com/downloads/script-devmon/)) following the instructions : [http://igurublog.wordpress.com/downloads/ppa/](http://igurublog.wordpress.com/downloads/ppa/) ; instead of 'pcmanfm-mod', install 'devmon'.
There are options to customize, but I just used the default and launched the devmon as a background process through the command 'devmon &'.
USB flash drive automounts with user permissions. It can be unmounted through the 'Unmount' menu option on right-clicking the mounted USB flash drive. Note: I don't see a 'Safely Remove Drive' option in the menu, which was present in previous releases.
cdrom automounts. It can be unmounted through the 'Eject' menu option on right-clicking the mounted cdrom.
In System->Preferences->Startup Applications, I added the command 'devmon' with name "Devmon" so that the same command will be run automatically for every user session. However, this is restricted to the current user in which I added it. For 'Startup Programs for all current and future users', I found :
[http://ubuntuforums.org/showthread.php?t=1230487](http://ubuntuforums.org/showthread.php?t=1230487)
So I ran this command :
```
sudo mv ~/.config/autostart/devmon.desktop /usr/share/gnome/autostart/
```
Now, everything works as in previous releases, albeit the missing 'Safely Remove Drive' option.

PS: I am writing this document after trying out all alternatives. So I might have skipped some steps unintentionally while documenting. If so, do let me know.

---

### Post by wilmark on 2011-07-09
Had the same problem. Here's the easy fix that worked for me...
goto Settings => Removable Drives and Media => Storage
tick the options you want. It seems during the upgrade, some preferences were lost.

I also posted this at [http://ubuntuforums.org/showthread.php?p=11029718#post11029718](http://ubuntuforums.org/showthread.php?p=11029718#post11029718)

---

### Post by fred321cba on 2011-10-28
I had exactly the same problem as roshan18 when upgrading from 10.10 to 11.04. I used fdisk to "fix partition order" and all automount problems were resolved.

---

