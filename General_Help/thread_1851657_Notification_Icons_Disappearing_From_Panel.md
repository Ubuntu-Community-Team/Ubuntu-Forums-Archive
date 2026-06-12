---
title: "Notification Icons Disappearing From Panel"
date: 2011-09-28
forum: General Help
---

### Post by DaimyoKirby on 2011-09-28
Hello there.
So I just recently installed Xubuntu alongside Ubuntu, and it was all going fine.
Just today when I got on to Xubuntu, though, I noticed that my network icon (along with a few others) had disappeared; they appeared when I logged in, and everything was loading, but then they just disappeared. I found the network icon actually became a very thin line on the panel that took me awhile to locate:
[IMG]http://i.imgur.com/H5ePul.jpg[/IMG]
Anyone know why this is happening?
Does anyone know how I can fix this?

---

### Post by dino99 on 2011-09-28
sudo dpkg-reconfigure -phigh -a

---

### Post by DaimyoKirby on 2011-09-28
Well, that didn't solve the problem.
This was what your command outputted:
```
alden@alden-laptop:~$ sudo dpkg-reconfigure -phigh -a
[sudo] password for alden: 
update-rc.d: warning: /etc/init.d/acpi-support missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
acpid stop/waiting
acpid start/running, process 3528
dpkg-maintscript-helper: warning: environment variable DPKG_MAINTSCRIPT_NAME missing
dpkg-maintscript-helper: warning: environment variable DPKG_MAINTSCRIPT_PACKAGE missing
 * Starting AppArmor profiles                                                   Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
                                                                         [ OK ]
 * Reloading AppArmor profiles                                                  Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
                                                                         [ OK ]
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service apport stop

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) utility, e.g. stop apport
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service apport start

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the start(8) utility, e.g. start apport
start: Job failed to start
invoke-rc.d: initscript apport, action "start" failed.
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: key FBB75451: "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>" not changed
gpg: Total number processed: 2
gpg:              unchanged: 2
atd stop/waiting
atd start/running, process 3877
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service avahi-daemon stop

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) utility, e.g. stop avahi-daemon
avahi-daemon stop/waiting
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service dbus force-reload

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the reload(8) utility, e.g. reload dbus
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service avahi-daemon start

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the start(8) utility, e.g. start avahi-daemon
avahi-daemon start/running, process 3968
Rebuilding /usr/share/applications/bamf.index...
update-alternatives: using /usr/share/man/man7/bash-builtins.7.gz to provide /usr/share/man/man7/builtins.7.gz (builtins.7.gz) in auto mode.
 * Disabling additional executable binary formats binfmt-support         [ OK ] 
 * Enabling additional executable binary formats binfmt-support          [ OK ] 
 * Stopping bluetooth                                                    [ OK ] 
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service dbus force-reload

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the reload(8) utility, e.g. reload dbus
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service udev reload

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the reload(8) utility, e.g. reload udev
 * Starting bluetooth                                                    [ OK ] 
update-initramfs: Generating /boot/initrd.img-2.6.38-11-generic
Updating certificates in /etc/ssl/certs... 0 added, 0 removed; done.
Running hooks in /etc/ca-certificates/update.d....
updating keystore /etc/ssl/certs/java/cacerts...
done.
done.
Your console font configuration will be updated the next time your system
boots. If you want to update it now, run 'setupcon' from a virtual console.
update-initramfs: Generating /boot/initrd.img-2.6.38-11-generic
cron stop/waiting
dpkg-maintscript-helper: error: couldn't identify the package

```
Does this tell you anything?

---

