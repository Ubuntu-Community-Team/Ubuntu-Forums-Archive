---
title: "reboots"
date: 2009-12-10
forum: General Help
---

### Post by Qwerty990 on 2009-12-10
Hi there guys! I'm new here, and it's a lot of time that I don't practice my English, so, be merciful XD

I'm writing in relation to a problem which arose on my Kubuntu distro after the upgrade to Karmic: My laptop suddenly reboot, without any forewarning, in different situations (such as surfing the web - lightweight pages - or using mplayer), at a variable startup time.

At first, I thought to a overheat, but acpitool -t say it'ok (about 50°C), then I reckoned about a similar issue I had using another distro (arch), issue that I solved switching to the ATI proprietary drivers instead of the open ones. Thus I've tried the same solution on Kubuntu (using envy), but X says "device not found" and the screen continue to be black, unless I use again the radeon driver. However the 3 D acceleration seems to work fine, and this confirms that:

> qwerty@darkstar:~$ glxinfo | grep rendering
direct rendering: Yes

So, finally, I really have no idea about a possible solution to my trouble, and hope that your experience may help.

Here I post same infos about my laptop:
> qwerty@darkstar:~$ uname -a
Linux darkstar 2.6.31-16-generic #52-Ubuntu SMP Thu Dec 3 22:00:22 UTC 2009 i686 GNU/Linux

qwerty@darkstar:~$ lspci | grep ATI
03:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X700 (PCIE)

This is a (very) partial log file about a critic event happened a few days ago:

> qwerty@darkstar:~$ grep 'Dec  9 23' * | sed -n -e '/23:48/,/23:54/p' > /home/omen/log
daemon.log:Dec  9 23:48:41 darkstar wpa_supplicant[1034]: CTRL-EVENT-SCAN-RESULTS 
daemon.log:Dec  9 23:49:41 darkstar wpa_supplicant[1034]: CTRL-EVENT-SCAN-RESULTS 
daemon.log:Dec  9 23:50:41 darkstar wpa_supplicant[1034]: CTRL-EVENT-SCAN-RESULTS 
daemon.log:Dec  9 23:51:41 darkstar wpa_supplicant[1034]: CTRL-EVENT-SCAN-RESULTS 
daemon.log:Dec  9 23:53:06 darkstar avahi-daemon[924]: Found user 'avahi' (UID 108) and group 'avahi' (GID 114).
daemon.log:Dec  9 23:53:06 darkstar avahi-daemon[924]: Successfully dropped root privileges.
daemon.log:Dec  9 23:53:06 darkstar avahi-daemon[924]: avahi-daemon 0.6.25 starting up.
daemon.log:Dec  9 23:53:06 darkstar avahi-daemon[924]: Successfully called chroot().
daemon.log:Dec  9 23:53:06 darkstar avahi-daemon[924]: Successfully dropped remaining capabilities.
daemon.log:Dec  9 23:53:06 darkstar avahi-daemon[924]: No service file found in /etc/avahi/services.
daemon.log:Dec  9 23:53:06 darkstar avahi-daemon[924]: Network interface enumeration completed.
daemon.log:Dec  9 23:53:06 darkstar avahi-daemon[924]: Registering new address record for fe80::203:dff:fe35:54eb on eth0.*.
daemon.log:Dec  9 23:53:06 darkstar avahi-daemon[924]: Server startup complete. Host name is darkstar.local. Local service cookie is 201789558.

I think that the 53d minute is referred to the reboot time, so I don't think it's useful (but the previous logs are related with wpa supplicant), nevertheless I prefer to post whatever I've. Thus, to achieve this goal, I attach the whole logfile to this message.

Thanks to whoever tries to help me ^^
Bye!

---

### Post by Qwerty990 on 2009-12-13
no hints for me? :(

---

