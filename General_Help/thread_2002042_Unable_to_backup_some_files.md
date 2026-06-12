---
title: "Unable to backup some files?"
date: 2012-06-12
forum: General Help
---

### Post by alexpalka23 on 2012-06-12
EDIT: Well, i couldn't quite figure out what to do to fix this issue for myself, but i did go about backing up another way. I ended up using Remastersys and backed up my hard drive to a live iso. I guess problem solved for me. If anyone cares to still answer the original question for myself and the other general newbies, please feel free. Curiosity still has half of me on this one anyways. Thanks for anyone who took a look at this for me! 

Today i tried to do a full system backup (i mean the file-system, so the contents of the whole hard drive minus music). Everything seemed to backup smoothly aside from a handful of files, which i presume are owned by root. These files are:

/boot/System.map-3.2.0-23-generic-pae
/boot/System.map-3.2.0-24-generic-pae
/boot/vmlinuz-3.2.0-24-generic-pae
/etc/.pwd.lock
/etc/NetworkManager/system-connections/belkin.e68
/etc/apparmor.d/cache/lightdm-guest-session
/etc/apparmor.d/cache/sbin.dhclient
/etc/apparmor.d/cache/usr.bin.evince
/etc/apparmor.d/cache/usr.bin.freshclam
/etc/apparmor.d/cache/usr.lib.telepathy
/etc/apparmor.d/cache/usr.sbin.cupsd
/etc/apparmor.d/cache/usr.sbin.tcpdump
/etc/apt/trustdb.gpg
/etc/at.deny
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
/etc/security/opasswd
/etc/shadow
/etc/shadow-
/etc/ssl/private
/etc/sudoers
/etc/sudoers.d/README
/etc/ufw/after.rules
/etc/ufw/after6.rules
/etc/ufw/before.rules
/etc/ufw/before6.rules
/lib/ufw/user.rules
/lib/ufw/user6.rules
/lost+found
/root
/run/clamav/freshclam.pid
/run/crond.reboot
/run/cups/certs
/run/lightdm
/run/lock/whoopsie/lock
/run/samba/messages.tdb
/run/samba/winbindd_privileged
/run/shm/pulse-shm-3979679936
/run/shm/pulse-shm-863518462
/run/udisks
/run/wpa_supplicant
/var/backups/group.bak
/var/backups/gshadow.bak
/var/backups/passwd.bak
/var/backups/shadow.bak
/var/cache/apt/archives/lock
/var/cache/cups/job.cache
/var/cache/cups/job.cache.O
/var/cache/cups/ppds.dat
/var/cache/debconf/passwords.dat
/var/cache/ldconfig
/var/cache/lightdm/dmrc
/var/cache/samba/netsamlogon_cache.tdb
/var/cache/samba/winbindd_cache.tdb
/var/lib/apt/lists/lock
/var/lib/clamav/mirrors.dat
/var/lib/dpkg/lock
/var/lib/dpkg/triggers/Lock
/var/lib/lightdm
/var/lib/mlocate/mlocate.db
/var/lib/polkit-1
/var/lib/samba/account_policy.tdb
/var/lib/samba/group_mapping.tdb
/var/lib/samba/passdb.tdb
/var/lib/samba/secrets.tdb
/var/lib/sudo
/var/lib/urandom/random-seed
/var/log/btmp
/var/log/installer/casper.log
/var/log/installer/debug
/var/log/installer/partman
/var/log/installer/syslog
/var/log/installer/version
/var/log/lightdm/lightdm.log
/var/log/lightdm/x-0-greeter.log
/var/log/lightdm/x-0-greeter.log.old
/var/log/lightdm/x-0.log
/var/log/samba/cores
/var/log/speech-dispatcher
/var/log/upstart/alsa-restore.log
/var/log/upstart/console-setup.log
/var/log/upstart/container-detect.log
/var/log/upstart/hybrid-gfx.log
/var/log/upstart/modemmanager.log
/var/log/upstart/procps-static-network-up.log
/var/log/upstart/procps-virtual-filesystems.log
/var/log/upstart/rsyslog.log
/var/log/upstart/ureadahead.log
/var/spool/anacron/cron.daily
/var/spool/anacron/cron.monthly
/var/spool/anacron/cron.weekly
/var/spool/cron/atjobs
/var/spool/cron/atspool
/var/spool/cron/crontabs
/var/spool/cups

Presuming these are owned by root, how do i go about backing up the whole hard drive, including these files, with the standard backup application? Run it as root? and how would i go about doing that?

My second question is, say i break my system and have to do a clean install and then restore my previous backup of ubuntu 12.04 to it to bring everything back to previous order, would i have to have these files, or is this over-lookable, or should i just back up only the home folder and forger about a full file-system backup? What would happen if i just restore the file-system backup as is without these skipped files included to a new system? 

Thanks in advance. Hopefully someone can clear this up, as im totally lost here haha. Sorry for the small novel of text :P

---

