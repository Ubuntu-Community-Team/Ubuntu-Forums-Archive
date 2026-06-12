---
title: "General impressions and thing i would like"
date: 2004-10-23
forum: General Help
---

### Post by idioteque on 2004-10-23
Ok fist impression is GREAT ,

fast and debian and desktop is just great. I love Ubuntu

But....

thing I miss of found weird

On first gnome boot a very small SUDO guide 

No smbfs installed, i cant mount SMB's

The apt-get repositor should pop up and  ask automaticlay if I want to select internet sources. Took me 30 min to find out why I only had a cd-rom source

No PPPOE gui of text shortcut with network, again took me 30 min on internet to find this out.

Disk manager, gui partition managrer with mount NTFS and FAT32 support

automount +R NTFS disks would be nice

At install at  DHCP point add PPPOE config so I can download sources during install 

Add root user during  install  say for instance: ubuntu:ubuntu

would like a Mplayer deb  :)

place PPPOE first on boot and then NTP server, Now NTP wont start cause PPPEO has not started yet

For the rest I love the conbination Debian and Gnome :)

---

### Post by butters on 2004-10-23
smbfs is included in the default kernel:

# cat /boot/config-2.6.8.1-3-386 | grep SMB
CONFIG_SMB_FS=m
# CONFIG_SMB_NLS_DEFAULT is not set

you can mount smb shares by using the connect to server feature in nautlius or:

mount -t smbfs <-o username=myuser> //host.domain/share /mnt/point

Its pretty obvious how to use sudo.  Anyone who can figure out how to open a terminal and discover the sudo command can also discover 'man sudo'.  There they can find out about 'sudo -s', which works like su, except using the regular user's password.  For graphical applications that ask for root, they might simply change their dialog to say: 'Enter username's password for /usr/sbin/program', since asking for 'your' password might worry some people who realize that they never set a root passwd.  By the way, you can always do 'sudo passwd root' to set the root password.

GNOME should have a real volume manager.  One tab for removable volumes (i.e. the current gnome-volume-manager), one for mounts (ext, reiser, fat, ntfs, nfs, smb, iso, afs), and another for shares (http, ftp, smb, nfs)

GNOME should extend nautilus-cd-burner to include selectable filters for burning audio CDs from mp3, ogg, mpc, flac, shn, etc.  If it finds any supported audio types in the list of files to burn, then it asks if they should all be filtered to CD audio (and any unsupported files discarded).

Ubuntu should be a release vehicle for GNOME.  Feedback like this generated from Ubuntu users should be passed upstream to the GNOME devs.  The fact of the matter is, GNOME needs better volume management, not just Ubuntu.  Ubuntu is quickly becoming the reference implementation of GNOME 2.8, and I think that in light of problems with distributions packaging GNOME (especially slackware), there is a definite need for such a reference implementation.

Perhaps Synaptic should have a Package Sources button next to Reload to make the idea of (possibly) adding repositories more obvious.  Adding repositories using Settings->Repositories is very straightforward, though.

I think that a major area of improvement for Ubuntu would be documentation.  Check out [http://www.gentoo.org/doc/en/index.xml](http://www.gentoo.org/doc/en/index.xml) to see what a real commitment to thorough documentation looks like.  Something like your introduction to sudo could be included, as well as tips for using debian's package management and init scripts.  I still haven't figured out how to add and remove services from runlevels other than by creating and removing symlinks by hand, and if I can't figure it out, there's no way a novice could.

From a devout Gentoo user since before verion 1.0, and now an Ubuntu user for a week, here is my one line review: Ubuntu is not the easiest distribution available or the most tinker-friendly, but it is by far and away the most power-user-friendly distribution that's ready for work in less than an hour.  The functional state of Ubuntu after a default install would take about 12-20 hours to obtain from a stage3 gentoo install, plus new packages install in a fraction of the time and the whole system is relatively easy to upgrade and maintain.  I could even compile my own tricked-out kernel patchset without breaking any distro-specific stuff.

Ubuntu has stole me away from Gentoo on my laptop, but I'll never let it have my development workstation.

---

### Post by snazbaz on 2004-10-23
[QUOTE=butters]

I still haven't figured out how to add and remove services from runlevels other than by creating and removing symlinks by hand, and if I can't figure it out, there's no way a novice could.

[/QUOTE]

"man update-rc.d"

I had the same problem as you, I was looking for something like rc-update (Gentoo) but it's all the wrong way round :)

---

### Post by butters on 2004-10-23
Well, it does the job, basically

rc-update add foobar default --> update-rc.d fubar defaults
rc-update del foobar --> update-rc.d -f fubar remove

It has a pretend mode using the -n switch, which is nice, although there's no real complex behavior involved here.  There is sadly no analogues for 'rc-update show' and 'rc', although you can look through all the symlinks in /etc/rcN.d and all the scripts in /etc/init.d to get the same info as the former, and you can probably do 'telinit 5' to restart your stopped runlevel services.

---

