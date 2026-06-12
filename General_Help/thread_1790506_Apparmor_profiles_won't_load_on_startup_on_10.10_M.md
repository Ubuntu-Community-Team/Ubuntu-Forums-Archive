---
title: "Apparmor profiles won't load on startup on 10.10 Maverick"
date: 2011-06-25
forum: General Help
---

### Post by Abir Valg on 2011-06-25
Using Ubuntu 10.10. I installed apparmor-profiles which dumped lots of profiles into /etc/apparmor.d.
Acc.to docu, AppArmor should load all those profiles on startup, yet whenever I reboot, aa-status gives me:

3 profiles are loaded.
3 profiles are in enforce mode.
   /sbin/dhclient3
   /usr/lib/NetworkManager/nm-dhcp-client.action
   /usr/lib/connman/scripts/dhclient-script
0 profiles are in complain mode.
0 processes have profiles defined.
0 processes are in enforce mode :
0 processes are in complain mode.
0 processes are unconfined but have a profile defined.

Here is the contents of /etc/apparmor.d (including two custom profiles for skype and opera):

abstractions
bin.ping
cache
disable
force-complain
home.wwwwww.apps.browsers.opera-11.00-1156.i386.linux.opera
home.wwwwww.apps.skype_static-2.2.0.35.skype
local
program-chunks
sbin.dhclient3
sbin.klogd
sbin.syslogd
sbin.syslog-ng
tunables
usr.bin.chromium-browser
usr.bin.evince
usr.bin.firefox
usr.lib.dovecot.deliver
usr.lib.dovecot.dovecot-auth
usr.lib.dovecot.imap
usr.lib.dovecot.imap-login
usr.lib.dovecot.managesieve-login
usr.lib.dovecot.pop3
usr.lib.dovecot.pop3-login
usr.sbin.avahi-daemon
usr.sbin.cupsd
usr.sbin.dnsmasq
usr.sbin.dovecot
usr.sbin.identd
usr.sbin.mdnsd
usr.sbin.nmbd
usr.sbin.nscd
usr.sbin.smbd
usr.sbin.tcpdump
usr.sbin.traceroute

There really seem to be no configfile which tells AA which profiles to load. AA should just process all profiles in /etc/apparmor.d

Apart from writing a startup script, any ideas how to make AA load profiles the proper/Ubuntu way?

---

