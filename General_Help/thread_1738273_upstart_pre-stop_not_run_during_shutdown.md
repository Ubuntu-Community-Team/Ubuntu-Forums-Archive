---
title: "upstart pre-stop not run during shutdown"
date: 2011-04-24
forum: General Help
---

### Post by Nate B on 2011-04-24
Hello all.

I'm running Ubuntu server, hosting a virtual machine using an upstart job.  I've got it launching on startup, and shutting down the host on exit, but I can't seem to get it to suspend when the host shuts down.  If I use 'initctl stop vmservice', then the suspend happens correctly - but if I 'shutdown -h now' or 'reboot', it looks like it's just getting killed (I tried putting a sleep in the pre-stop script, and that behaves the same way).  Any help would be appreciated.

I'm rather new to upstart, so I'd appreciate any other feedback, too (including, am I doing the "right" thing by calling shutdown in a post-stop?).

my job (the 'start on' was snagged from kdm.conf; .startvm and .stopvm just start and suspend the VM):

> start on (filesystem
          and started dbus
          and (graphics-device-added fb0 PRIMARY_DEVICE_FOR_DISPLAY=1
               or drm-device-added card0 PRIMARY_DEVICE_FOR_DISPLAY=1
               or stopped udevtrigger))
stop on runlevel [016]

pre-stop script
    exec su -c "/home/unprivileged_user/.stopvm" - unprivileged_user
end script

env XORGCONFIG=/etc/X11/xorg.conf
exec su -c "xinit /home/unprivileged_user/.startvm -- /etc/X11/xinit/xserverrc :0" - unprivileged_user

post-stop script
    shutdown -h now
end script

---

