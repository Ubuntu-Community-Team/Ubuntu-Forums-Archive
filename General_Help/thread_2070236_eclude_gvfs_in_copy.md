---
title: "eclude gvfs in copy?"
date: 2012-10-12
forum: General Help
---

### Post by qwertyjjj on 2012-10-12
I get the following error when running a backup:
j-media-centre@jmediacentre-A880G:~$ sudo cp -rp /home/j-media-centre /mnt/mynewdrive/home/j-media-centre.backup
cp: cannot stat `/home/j-media-centre/.gvfs': Permission denied


What is gvfs and how can I exclude it in that command?

---

### Post by dcstar on 2012-10-13
> **qwertyjjj said:**
> I get the following error when running a backup:
j-media-centre@jmediacentre-A880G:~$ sudo cp -rp /home/j-media-centre /mnt/mynewdrive/home/j-media-centre.backup
cp: cannot stat `/home/j-media-centre/.gvfs': Permission denied


What is gvfs and how can I exclude it in that command?

If the destination is not a Linux filesystem then issues can arise, also using sudo for copying /home data is not really valid.

---

### Post by steeldriver on 2012-10-13
afaik $HOME/.gvfs is a mount point for remote shares under the Gnome Virtual file System - so the files there aren't really the user's home files

You could try adding the -x or  --one-file-system flag (stay on this file system) to cp or maybe use rsync instead with --exclude

---

### Post by qwertyjjj on 2012-10-15
> **steeldriver said:**
> afaik $HOME/.gvfs is a mount point for remote shares under the Gnome Virtual file System - so the files there aren't really the user's home files

You could try adding the -x or  --one-file-system flag (stay on this file system) to cp or maybe use rsync instead with --exclude

tried deja dup instead and got the following error:
could not backup:

/etc/.pwd.lock
/etc/NetworkManager/system-connections/Wired connection 1
/etc/apparmor.d/cache/lightdm-guest-session
/etc/apparmor.d/cache/sbin.dhclient
/etc/apparmor.d/cache/usr.bin.evince
/etc/apparmor.d/cache/usr.lib.telepathy
/etc/apparmor.d/cache/usr.sbin.cupsd
/etc/apparmor.d/cache/usr.sbin.tcpdump
/etc/apt/trustdb.gpg
/etc/at.deny
/etc/chatscripts
/etc/cups/ssl
/etc/cups/subscriptions.conf
/etc/cups/subscriptions.conf.O
/etc/default/cacerts
/etc/fuse.conf
/etc/group-
/etc/gshadow
/etc/gshadow-
/etc/mtab.fuselock
/etc/passwd-
/etc/ppp/chap-secrets
/etc/ppp/pap-secrets
/etc/ppp/peers
/etc/security/opasswd
/etc/shadow
/etc/shadow-
/etc/ssl/private
/etc/sudoers
/etc/sudoers.d/README
/etc/transmission-daemon/settings.json
/etc/ufw/after.rules
/etc/ufw/after6.rules
/etc/ufw/before.rules
/etc/ufw/before6.rules

---

### Post by shreepads on 2012-10-15
Why are you backing up stuff in /etc? Check the Deja Dup settings...

If you want to backup and are comfotable with command-line use rsync. There is Grsync if you want rsync with a UI...

---

### Post by qwertyjjj on 2012-10-19
> **shreepads said:**
> Why are you backing up stuff in /etc? Check the Deja Dup settings...

If you want to backup and are comfotable with command-line use rsync. There is Grsync if you want rsync with a UI...

in case I have to restore it in future.
backing up /home and /etc

---

