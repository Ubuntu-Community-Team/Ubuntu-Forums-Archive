---
title: "Is there a way to repair my current 10.04 install?"
date: 2010-10-26
forum: General Help
---

### Post by redfox1160 on 2010-10-26
Okay... I did something really stupid... I wanted to install the newest version of Python available, so I typed in *sudo apt-get remove python* to "remove the current version". I let it go for a while not realizing what it was deleting... It deleted a lot of things (including the ubuntu software center). I stopped it immediately but damage was already done...:( Does anyone know if I can repair the current installation? What would I need to do that? Thanks!

---

### Post by Verbeck on 2010-10-26
have you tried installing the removed packages?


here's what i got [might have some programs you may not want]
```

The following packages will be REMOVED:
  aisleriot alacarte apport apport-gtk apt-xapian-index aptdaemon apturl
  apturl-common at-spi baobab byobu capplets-data checkbox checkbox-gtk
  command-not-found compiz compiz-fusion-plugins-extra compiz-gnome
  compiz-plugins compizconfig-settings-manager computer-janitor
  computer-janitor-gtk desktopcouch empathy eog evince evolution
  evolution-couchdb evolution-data-server evolution-exchange
  evolution-indicator evolution-webcal file-roller firefox firefox-branding
  firefox-gnome-support gconf-editor gconf2 gdm gdm-guest-session gedit gimp
  gksu gnome-about gnome-applets gnome-applets-data gnome-codec-install
  gnome-control-center gnome-dictionary gnome-doc-utils gnome-exe-thumbnailer
  gnome-mag gnome-mahjongg gnome-media gnome-media-common gnome-menus
  gnome-orca gnome-panel gnome-panel-data gnome-power-manager
  gnome-screensaver gnome-screenshot gnome-search-tool gnome-session
  gnome-session-bin gnome-session-canberra gnome-settings-daemon gnome-sudoku
  gnome-system-log gnome-system-monitor gnome-terminal gnome-terminal-data
  gnome-user-guide gnome-user-guide-en gnome-utils gnomine
  gstreamer0.10-plugins-good gucharmap gwibber gwibber-service hplip
  hplip-data ibus ibus-pinyin ibus-table indicator-applet
  indicator-applet-session indicator-me indicator-session indicator-sound
  jockey-common jockey-gtk language-selector language-selector-common
  launchpad-integration libbonoboui2-0 libgail-gnome-module libgksu2-0
  libgnome-media0 libgnome-vfs2.0-cil libgnome2-0 libgnome2-common
  libgnome2-perl libgnome2-vfs-perl libgnome2.24-cil libgnomekbd-common
  libgnomekbd4 libgnomepanel2.24-cil libgnomeui-0 libgnomevfs2-0
  libgnomevfs2-common libgnomevfs2-extra libgstfarsight0.10-0
  libgweather-common libgweather1 libgwibber0 libmetacity-private0
  libpanel-applet2-0 libpurple-bin libpurple0 libsyncdaemon-1.0-1
  libtelepathy-farsight0 libubuntuone-1.0-1 light-themes lsb-release metacity
  metacity-common mousetweaks nautilus nautilus-data nautilus-sendto-empathy
  nautilus-share network-manager network-manager-gnome nvidia-common
  nvidia-settings onboard openoffice.org-gnome pitivi python-appindicator
  python-apport python-apt python-aptdaemon python-aptdaemon-gtk
  python-argparse python-avahi python-brlapi python-cairo python-compizconfig
  python-configglue python-couchdb python-crypto python-cups
  python-cupshelpers python-dbus python-debian python-desktopcouch-records
  python-egenix-mxdatetime python-egenix-mxtools python-farsight python-gconf
  python-gdbm python-glade2 python-gmenu python-gnome2 python-gnomeapplet
  python-gnomecanvas python-gnomekeyring python-gnupginterface python-gobject
  python-gobject-cairo python-gst0.10 python-gtk2 python-gtksourceview2
  python-gtkspell python-httplib2 python-ibus python-imaging python-indicate
  python-launchpad-integration python-launchpadlib python-lazr.restfulclient
  python-lazr.uri python-libproxy python-libuser python-libxml2 python-louis
  python-mako python-markupsafe python-newt python-notify python-oauth
  python-openssl python-pam python-papyon python-pexpect python-pkg-resources
  python-problem-report python-protobuf python-pyatspi python-pycurl
  python-pygoocanvas python-pyicu python-pyinotify python-pyorbit
  python-rdflib python-serial python-simplejson python-smbc
  python-software-properties python-speechd python-telepathy
  python-twisted-bin python-twisted-core python-twisted-names
  python-twisted-web python-ubuntuone python-ubuntuone-client
  python-ubuntuone-storageprotocol python-virtkey python-vte python-wadllib
  python-webkit python-wnck python-xapian python-xdg python-xkit
  python-zope.interface quadrapassel remastersys rhythmbox
  rhythmbox-plugin-cdrecorder rhythmbox-plugins
  rhythmbox-ubuntuone-music-store screen-resolution-extra seahorse
  sessioninstaller simple-scan software-center software-properties-gtk
  system-config-printer-common system-config-printer-gnome
  system-config-printer-udev system-config-samba telepathy-butterfly
  telepathy-haze tomboy totem totem-common totem-mozilla totem-plugins
  tsclient ubiquity ubiquity-frontend-debconf ubufox ubuntu-artwork
  ubuntu-desktop ubuntu-docs ubuntu-minimal ubuntu-sso-client
  ubuntu-system-service ubuntu-tweak ubuntu-wallpapers ubuntuone-client
  ubuntuone-client-gnome ufw unattended-upgrades update-manager
  update-manager-core update-notifier update-notifier-common
  usb-creator-common usb-creator-gtk vinagre vino xchat xchat-common
  xul-ext-ubufox yelp

```

---

### Post by redfox1160 on 2010-10-26
> **Verbeck said:**
> have you tried installing the removed packages?


I was going to but I don't know what packages were removed. Is there a way to check which packages I removed last?

---

### Post by Quackers on 2010-10-26
Try System > Admin > Synaptic Package Manager > File > History

---

### Post by redfox1160 on 2010-10-26
I am actually unable to get back onto desktop. I am at work, and had to leave. I couldn't lock my computer so I shut it off. I just turned it back on and this is the login prompt I got: [http://i.imgur.com/sT6n7.jpg](http://i.imgur.com/sT6n7.jpg)
When I log on I get a black screen... is this fixable?

---

### Post by sisco311 on 2010-10-26
That looks like KDM. Are you using Ubuntu or Kubuntu?

Anyway, first switch to a virtual console (Ctrl+Alt+F1), log in and try fixing the broken packages:
```
sudo apt-get install -f
```
Then try installing ubuntu-minimal and ubuntu-desktop (or kubuntu-desktop):
```
sudo apt-get install ubuntu-minimal ubuntu-desktop
```

---

### Post by Quackers on 2010-10-26
Have you tried ctrl+alt+F1 or F2
can you get a login prompt that way?

Edit: Aha! sisco arrived :-)

---

### Post by redfox1160 on 2010-10-26
I did Ctrl+Alt+F1 and logged in. I ran
```
sudo apt-get install -f
```
and
```
sudo apt-get install ubuntu-minimal ubuntu-desktop
```
Then, I realized I wasn't connected to a network so I ran the following
```
/etc/init.d/networking start
```
and got the following back
```
/usr/bin/python: can't find '__main__.py' in '/usr/share/command-not-found'
```

I'm guessing that this means I can't connect to the internet to download the packages. Any suggestions? Thanks again for all the help.

---

### Post by Quackers on 2010-10-26
Ethernet cable? Not sure but worth a try maybe.

---

### Post by redfox1160 on 2010-10-26
> **Quackers said:**
> Ethernet cable? Not sure but worth a try maybe.

when I try to start networking now, I get this:

```
start: Rejected send message, 1 matched rules; type="method_call", sender=":1.12" (uid=1000 pid=1423 comm="start) interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" requested_reply=0 destination="com.ubuntu.Upstart" (uid=0 pid1 comm="/sbin/init"))
```

(Sorry my responses are taking long, I'm at work)

EDIT:
if config returns the following
```
lo      Link ecap:Local Loopback
        inet addr: 127.0.0.1 Mask: 255.0.0.0
        inet6 addr:  ::1/128 Scope:Host
        UP LOOPBACK RUNNING MTU:16436  Metric:1
        RX packets:238 errors:0 dropped:0 overruns:0 frame:0
        TX packets:238 eroors:0 dropped:0 overruns:0 carrier:0
        collisions:0 txqueuelen:0
        RX bytes:47217 (47.2KB) TX bytes:47217 (47.2KB)

```

---

### Post by sisco311 on 2010-10-26
How do you connect to the Internet?

---

### Post by redfox1160 on 2010-10-26
> **sisco311 said:**
> How do you connect to the Internet?
I use wicd, but if I type that into the terminal I get this error again:
```
/usr/bin/python: can't find '__main__.py' in '/usr/share/command-not-found'
```

---

### Post by sisco311 on 2010-10-26
> **redfox1160 said:**
> I use wicd, but if I type that into the terminal I get this error again:
```
/usr/bin/python: can't find '__main__.py' in '/usr/share/command-not-found'
```

Yep, wicd-daemon depends on python. :(

You have to figure out a way to set up your connection without wicd. Could you please tell as some details about the network? Wired or wireless? Encrypted?

Or you could boot a LiveCD (or Live USB), set up the connection, chroot into Ubutnu and reinstall the packages.

---

### Post by redfox1160 on 2010-10-26
> **sisco311 said:**
> Yep, wicd-daemon depends on python. :(

You have to figure out a way to set up your connection without wicd. Could you please tell as some details about the network? Wired or wireless? Encrypted?

Or you could boot a LiveCD (or Live USB), set up the connection, chroot into Ubutnu and reinstall the packages.

I'll try to use a LiveCD to chroot into Ubuntu. I don't have time now. Thanks for all the help!

---

### Post by sisco311 on 2010-10-26
You're welcome!

For reference here is the script I use to chroot into Ubuntu:
```
#!/bin/bash

############################################################################
# variables                                                                #
############################################################################

# device name of the root partition
ROOT="**/dev/sda1**"

# mount point of the new root partition
MOUNT="**/mnt/natty**"

# list of virtual filesystems and additional config files
ARGS="dev dev/pts proc sys etc/resolv.conf"

# list of additional devices and their mount pont. 
# device names must be separated by the mount point with a colon (:)
# e.g. /dev/sda2:/home 
AMOUNT=""

# user name
UNAME="**sisco**"

############################################################################
# start the chroot environment                                             #
############################################################################

# add user to the list of allowed users to make connections to the X server.
sudo -u $USER xhost SI:localuser:$UNAME

# create the mount point & mount the root partition
mkdir -p $MOUNT
mount $ROOT $MOUNT

# mount the virtual filesystems & resolv.conf to enable the network
for i in $ARGS; do
  mount --bind /$i $MOUNT/$i
done

# mount additional partitions:
for i in $AMOUNT; do
  mkdir -p ${MOUNT}${i//*:/}
  mount ${i//:*/} ${MOUNT}${i//*:/}
done

# start the chroot 
chroot $MOUNT sudo -i -u $UNAME


```

---

### Post by katykat on 2010-10-26
Try:
/sbin/dhclient3 

That may restart the networking. 
(Dont know if it uses python...)

---

### Post by sisco311 on 2010-10-26
> **katykat said:**
> 
(Dont know if it uses python...)

If you have a (working) Ubuntu installation, you can check it ;) 
```
sisco@acme:~$ dpkg -S /sbin/dhclient3
dhcp3-client: /sbin/dhclient3
sisco@acme:~$ apt-cache depends dhcp3-client
dhcp3-client
  Depends: debianutils
  Depends: dhcp3-common
  Depends: libc6
 |Depends: debconf
  Depends: <debconf-2.0>
    cdebconf
    debconf
  Suggests: resolvconf
  Suggests: avahi-autoipd
  Suggests: apparmor
  Conflicts: dhcp-client
  Conflicts: samba-common

```

and yep, the command may work. 


@OP:
In case of a static ethernet connection, something like:
```
sudo ifconfig eth0 192.168.0.100 up
```should bring up the device. 

In case of a wireless connection, this guide should help: [thread=571188]How To: Manual Network Configuration without the need for Network Manager[/thread]

---

### Post by redfox1160 on 2010-10-27
> **sisco311 said:**
> If you have a (working) Ubuntu installation, you can check it ;) 
```
sisco@acme:~$ dpkg -S /sbin/dhclient3
dhcp3-client: /sbin/dhclient3
sisco@acme:~$ apt-cache depends dhcp3-client
dhcp3-client
  Depends: debianutils
  Depends: dhcp3-common
  Depends: libc6
 |Depends: debconf
  Depends: <debconf-2.0>
    cdebconf
    debconf
  Suggests: resolvconf
  Suggests: avahi-autoipd
  Suggests: apparmor
  Conflicts: dhcp-client
  Conflicts: samba-common

```

and yep, the command may work. 


@OP:
In case of a static ethernet connection, something like:
```
sudo ifconfig eth0 192.168.0.100 up
```should bring up the device. 

In case of a wireless connection, this guide should help: [thread=571188]How To: Manual Network Configuration without the need for Network Manager[/thread]

Okay,

I have the time to try to fix this now. I just ran
```
sudo ifconfig eth0 192.168.0.100 up
```
and my eth0 came back up, but I was unable to ping outside ip addresses, so I ran this
```
sudo /sbin/dhclient3 
```
and I was able to ping them! I just ran
```
sudo apt-get install ubuntu-minimal ubuntu-desktop
```
I'll report back when it is finished installing. Thanks again for all the help, and sorry for the late responses!

---

### Post by redfox1160 on 2010-10-27
It is fixed!
I did encounter a problem where I could not connect to us.archives.ubuntu.com, but that can be solved by running the following code, then running the apt-get command
```
sudo dhclient -r;sudo dhclient
```
Thanks everyone for all the help!

---

### Post by sisco311 on 2010-10-27
You are welcome!

BTW, python 3.1.2 is in the repos, you can install it alongside the default python.

---

### Post by redfox1160 on 2010-10-27
> **sisco311 said:**
> You are welcome!

BTW, python 3.1.2 is in the repos, you can install it alongside the default python.

I actually just did that. I am having a problem though (this might be a result of the damage I did). When I try to run my python program, the following error occurs
```
/usr/bin/python: can't find '__main__.py' in '/usr/share/command-not-found'
```
Do you know what is causing this? Thanks.

---

### Post by sisco311 on 2010-10-27
> **redfox1160 said:**
> I actually just did that. I am having a problem though (this might be a result of the damage I did). When I try to run my python program, the following error occurs
```
/usr/bin/python: can't find '__main__.py' in '/usr/share/command-not-found'
```
Do you know what is causing this? Thanks.

You have to install the command-not-found package, but to be sure that you have all the packages installed by default in Ubuntu, install the ubuntu-standard meta-package. ubutnu-standard does not depend directly on python but some of its dependencies (like command-not-found) do.

---

### Post by redfox1160 on 2010-10-27
> **sisco311 said:**
> You have to install the command-not-found package, but to be sure that you have all the packages installed by default in Ubuntu, install the ubuntu-standard meta-package. ubutnu-standard does not depend directly on python but some of its dependencies (like command-not-found) do.

Thank you SO MUCH! You have been very helpful! I can't thank you enough!

---

### Post by sisco311 on 2010-10-27
My pleasure!

---

