---
title: "all startup scripts past S30gdm do not execute"
date: 2009-08-10
forum: General Help
---

### Post by noahwallach on 2009-08-10
Hi there,

I am trying to figure why all my startup scripts past /etc/rc2.d/S30gdm
are not loading?

Looks like X gets fired up and then the following script do not run:

S50avahi-daemon
S50cups
S50NetworkManager
S50pulseaudio
S50rsync
S50saned
S50system-tools-backends
S70bootlogs.sh
S70dns-clean
S70pppd-dns
S89anacron
S89atd
S89cron
S90binfmt-support
S91apache2
S98usplash
S99acpi-support
S99laptop-mode
S99ondemand
S99rc.local
S99rmnologin
S99stop-readahead


here is the S30gdm script


--- snip --

$ pwd
/etc/rc2.d
$ less S30gdm
#! /bin/sh
#
# Originally based on:
# Version:      @(#)skeleton  1.8  03-Mar-1998  [email]miquels@cistron.nl[/email]
#
# Modified for gdm, Steve Haslam <steve@arise.dmeon.co.uk> 14mar99
# modified to remove --exec, as it does not work on upgrades. 18jan2000
# modified to use --name, to detect stale PID files 18mar2000
# sleep until gdm dies, then restart it 16jul2000
# get along with other display managers (Branden Robinson, Ryan Murray)
05sep2001


echo
echo
echo !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
echo at GDM
sleep 10


set -e

# To start gdm even if it is not the default display manager, change
# HEED_DEFAULT_DISPLAY_MANAGER to "false."
HEED_DEFAULT_DISPLAY_MANAGER=true
DEFAULT_DISPLAY_MANAGER_FILE=/etc/X11/default-display-manager
PATH=/sbin:/bin:/usr/sbin:/usr/bin
DAEMON=/usr/sbin/gdm
PIDFILE=/var/run/gdm.pid
UPGRADEFILE=/var/run/gdm.upgrade

if [ -e $UPGRADEFILE -a "$1" != "restart" -a "$1" != "force-reload" ]; then
         SSD_ARG="--startas $DAEMON"
         rm -f $UPGRADEFILE
else
         SSD_ARG="--exec $DAEMON"
fi

# Allow cdd to override the config
if [ -f /etc/gdm/gdm-cdd.conf ]; then
         CONFIG_FILE="--config=/etc/gdm/gdm-cdd.conf"
fi


-- snip ---

---

