---
title: "Descriptions of Startup Applications"
date: 2012-09-19
forum: General Help
---

### Post by twipley on 2012-09-19
There is an useful command to show default, although hidden startup applications:
```
sudo sed -i 's/NoDisplay=true/NoDisplay=false/g' /etc/xdg/autostart/*.desktop
```
(source: [https://help.ubuntu.com/community/ShowHiddenStartupApplications](https://help.ubuntu.com/community/ShowHiddenStartupApplications))

I am posting a list of names, commands, and comments of those default startup programs. It would be useful if people could contribute by posting descriptions where there is none.

Name
Command
Comment

AT-SPI D-Bus Bus
/usr/lib/at-spi2-core/at-spi-bus-launcher --launch-immediately

Backup Monitor
/usr/lib/i386-linux-gnu/deja-dup/deja-dup-monitor
Schedules backups at regular intervals

Bluetooth Manager
bluetooth-applet
Bluetooth Manager applet

Certificate and Key Storage
/usr/bin/gnome-keyring-daemon --start --components=pkcs11
GNOME Keyring: PKCS#11 Component

Chat
telepathy-indicator
Telepathy Indicator Service

Desktop Sharing
/usr/lib/vino/vino-server --sm-disable
GNOME Desktop Sharing Server

Files
nautilus -n

GNOME Settings Daemon
/usr/lib/gnome-settings-daemon/gnome-settings-daemon

GPG Password Agent
/usr/bin/gnome-keyring-daemon --start --components=gpg
GNOME Keyring: GPG Agent

GSettings Data Conversion
gsettings-data-convert
Migrates user settings from GConf to dconf

Gwibber
gwibber-service
Update your microblog and view others' statuses

Mount Helper
/usr/lib/gnome-settings-daemon/gnome-fallback-mount-helper
Automount and autorun plugged devices

Network
nm-applet
Manage your network connections

Onboard
onboard

Orca screen reader
orca --disable splash-window

Personal File Sharing
/usr/lib/gnome-user-share/gnome-user-share
Launch Personal File Sharing if enabled

PolicyKit Authentication Agent
/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
PolicyKit Authentication Agent

PulseAudio Sound System
start-pulseaudio-x11
Start the PulseAudio Sound System

Screensaver
gnome-screensaver
Launch screensaver and locker program

Secret Storage Service
/usr/bin/gnome-keyring-daemon --start --components=secrets
GNOME Keyring: Secret Service

SSH Key Agent
/usr/bin/gnome-keyring-daemon --start --components=ssh
GNOME Keyring: SSH Agent

Ubuntu One
/bin/sh -c '[ -d "$HOME/Ubuntu One" ] && ubuntuone-launch'

Update Notifier
update-notifier
Check for available updates automatically

User folders update
xdg-user-dirs-gtk-update
Update common folders names to match current locale

Zeitgeist Datahub
zeitgeist-datahub
Start the Zeitgeist Datahub for passive loggers

---

